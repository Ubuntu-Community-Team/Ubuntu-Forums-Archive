---
title: "Gftp client problem on 8.10 64 bit"
date: 2009-03-30
forum: General Help
---

### Post by barlaventoexpert on 2009-03-30
I am running Intrepid 8.10 64 bit on an Acer 4310 Laptop.

Spec:
Linux Kernal 2.6.27-14 - server
GNOME 2.24.1

I look after the virtual dedicated server of a client with several website aboard.

I use Gftp for file transfer.

Since last week I have been unable to connect to the virtual server using the Gftp client.

I get the following error:

Connected to xxxxx-xxx.eu:21
220---------- Welcome to Pure-FTPd [TLS] ----------
220-You are user number 1 of 50 allowed.
220-Local time is now 10:03. Server port: 21.
220 You will be disconnected after 15 minutes of inactivity.
USER xxxxxx
331 User xxxxxx OK. Password required
PASS xxxx
230-User xxxxxx has group access to:  xxxxxx
230 OK. Current restricted directory is /
SYST

500 ?
TYPE I

215 UNIX Type: L8
PWD

200 TYPE is now 8-bit binary 
Invalid response '2' received from server.
Disconnecting from site xxxxxx.eu

I though at first that the problem with the ftp server on the virtual server. I restarted this service and the problem continued. I then rebooted the server and the probel still continued.

I then turned to my machine.

I found that I had no problem ftp'ing to the virtual server with the command line in terminal nor when I connected using Places»»Connect to Server

The problem must then lie with the Gftp client (v. 2.0.18).

I have searched the web and there have been reports of similar problems on various distros over the years but no resolution. 

I find it strange that it has just started.

Any comments or help would be appreciated.

---

