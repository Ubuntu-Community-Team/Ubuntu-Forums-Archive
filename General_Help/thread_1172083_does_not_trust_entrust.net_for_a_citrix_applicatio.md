---
title: "does not trust entrust.net for a citrix application"
date: 2009-05-28
forum: General Help
---

### Post by ebodnaruk on 2009-05-28
I am trying to log on to a citrix client, running Ubuntu.  I downloaded the ICAClient but when I try to log in it says I do not trust entrust.net.  I saw similar posts, and followed the instructions below in this previous post:

[SIZE=2]Re: you have not chosen to trust "Entrust.net Secure Server Certification..                     
                     Posted:                     Dec 14, 2006 10:48 AM                                                                                                      [[IMG]http://forums.citrix.com/images/up-10x10.gif[/IMG]]("http://forums.citrix.com/message.jspa?messageID=492000#492000")                                                          in response to: [Kurt  Gallmann]("http://forums.citrix.com/message.jspa?messageID=492000#492000")                                                                                                              [/SIZE]                                                        
                      [[IMG]http://forums.citrix.com/images/reply-16x16.gif[/IMG]]("http://forums.citrix.com/post%21reply.jspa?messageID=551251")       [Reply]("http://forums.citrix.com/post%21reply.jspa?messageID=551251")      
               	         [SIZE=2]Kurt,

The following works for me:-
1) Make sure that Citrix ICA Client is installed 
2) Go to entrust.ne[/SIZE] [SIZE=2]t/developer and click on Download Root Certificat[/SIZE][SIZE=2]es 
3) Select Personal Use, and click on Download Certificat[/SIZE][SIZE=2]es 
4) Download entrust_ss[/SIZE][SIZE=2]l_ca.cer and entrust_ss[/SIZE][SIZE=2]l_ca.der to your desktop 
5) Open a terminal, and enter the following:
cd /Applicati[/SIZE][SIZE=2]ons/Citrix\ ICA\ Client/key[/SIZE][SIZE=2]store/cacert[/SIZE][SIZE=2]s/
cp -p ~/Desktop/[/SIZE][SIZE=2]entrust_ssl_[/SIZE][SIZE=2]ca.* .
ln -s entrust_ss[/SIZE][SIZE=2]l_ca.cer entrust_ss[/SIZE][SIZE=2]l_ca.crt 
6) Exit the terminal, and try your Citrix session again. 

There might be some unnecessar[/SIZE] [SIZE=2]y steps there, and this might all be fixed by downloadin[/SIZE][SIZE=2]g the latest release of the ICA client, but this works for me now. 

(originall[/SIZE] [SIZE=2]y blogged at [http://scruss.com/blog/2006/12/14/when-you-really-havent-chosen-not-to-trust-citrix-mac-os-x-and-entrust-certificates](http://scruss.com/blog/2006/12/14/when-you-really-havent-chosen-not-to-trust-citrix-mac-os-x-and-entrust-certificates)[/SIZE][SIZE=2])[/SIZE]
_____________________________
[SIZE=2]Well, I still have the problem...when I use the ls command in the terminal, my new entrust_ssl_ca.crt is a light blue color instead of a green co[/SIZE]lor.  I think this means that the file is seen as a directory or normal file instead of an executable.  Is this the problem, or is there something else going on????

Thanks,
Ethan

---

### Post by SailGreen on 2009-06-10
I can't answer your question about the blue vs green files.  However, if you're simply trying to get Citrix Receiver to work, I found the easiest of the solutions offered was to copy the appropriate Entrust.net crt files from /usr/share/ca-certificates/mozilla to /usr/lib/ICAClient/keystore/cacerts/.

---

### Post by nsrini on 2009-09-27
The second option , of just copying all the certificates into citrix folder worked perfectly.

---

### Post by cpare on 2011-08-13
Rather than do the copy and double the files up, just link to them
```
sudo ln -s /usr/share/ca-certificates/mozilla/* /usr/lib/ICAClient/keystore/cacerts/
```

---

