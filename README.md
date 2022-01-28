# DNS-server-using-python
The domain name system (DNS) is sometimes referred to as the “phone book” of the Internet.
You can connect to our website by typing in the IP address in the address bar of your browser, but it’s much easier to type in umbrella.cisco.com.DNS was invented
so that people didn’t need to remember long IP address numbers (like phone numbers) and could look up websites by human-friendly names like umbrella.cisco.com instead. 
Authoritative DNS nameservers are responsible for providing answers to recursive DNS nameservers about where specific websites can be found.
And here we implemented an Authoritative DNS nameserver.

Initially we create a socket with address as the loopback address and port as 53(Designated port for DNS).
Then we wait till we receive any DNS request from a client, for the given request we need to form a DNS Response which we need to send back to the client. 
So the Response message is created in the function “buildresponse”. First the Transaction ID for the response header is the same as that of the request header.
Then in the “getflags” function we add the required flags for the response header.Then we set the no of query or question(QDCOUNT) as 1.
Then answer count, it depends on how many answers you have in your zone file, here for a given request we need to find the domain name and the question type. 
Then based on the question type, if it’s ‘A’(means IPV4) we have to fetch all the json files on that domain name whose count would be the answer count. 
Then set the nameserver count and additional count as 0. 
Then as the final step we need to create the DNS body(Query and Answer) and combining the header, Query and the Answer we get the DNS response, 
which needs to be sent back to the client.
a
