---
title: "Evolution not connecting to GroupWise"
date: 2006-09-01
forum: Desktop Environments
---

### Post by RoundBear on 2006-09-01
I have a GroupWise 6.0 Server and when I try to connect Evolution to it I receive the following message:

Unable to authenticate to GroupWise server.Please enter the GroupWise password for ...

I have played around with changing the hostname.  I have used the name of the server, the IP address (with and without the port), the url of my domain as well as many other variations.  Nothing gets me connected.  What am I doing wrong?  Please help.

Tom

---

### Post by tigerpants on 2006-11-14
I would really really like to know the answer to this question, i have the same problem with groupwise 7.0 and evolution - anyone????

---

### Post by SBDJ on 2006-11-20
You need to make sure you have enabled SOAP on the Groupwise server.

In ConsoleOne, browse to the Post Office Agent (POA under the Post Office Object itself) and right click > Properties.

Select the Groupwise Agent Properties tab, and enable SOAP. Click OK and Evolution should now connect fine :)

---

### Post by ewayte on 2007-11-30
I realize this thread is a year old, but check that the SOAP port is being blocked by a firewall.  My university blocks the SOAP port via firewall and I have to connect via the VPN in order to use Eveolution to connect to GroupWise.

---

