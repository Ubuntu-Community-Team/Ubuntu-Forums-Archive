---
title: "RDP to Windows Server Help"
date: 2007-04-25
forum: Desktop Environments
---

### Post by Live2Speed on 2007-04-25
Hi everyone!

I'm new to Ubuntu and loving it so far. 

I do have one problem I can not seem to get around. I have done a search and did not see this topic come up yet.

I am trying to RDP to a windows server 2003 box. I know it works through windows but when I use Ubuntu I get a funky error.  It says "the systems could not log you on. Make sure your user name and domain are correct. etc". The system is not on a domain, its on a work group. I am sure the user name and password are correct.. am I missing something? I am giving it all the information I would if I were doing it trough windows but nothing.

Thanks much guys.

---

### Post by trekuhl on 2007-04-25
can you explain what steps you are taking to get to this error? running rdekstop from terminal or using another app?

i have been using tsclient which has a gui similar to that of the windows built-in client mstsc.exe 

get it from terminal: sudo apt-get install tsclient

make sure to uncheck the alternate fullscreen -F switch if you want to run fullscreen.

---

### Post by jpatton on 2007-04-25
Are you using the included tsclient program to connect? I know I received some similar errors on a different rdp program, can't remember the name of it, but it's because of the increased encryption in 2003 server. If it's purely an authentication issue, try connecting to your server like this:

servername\username

Not sure if that will help, but good luck.

---

### Post by Live2Speed on 2007-04-25
I am using the built-in client, I also installed krdp with the same results. I have tried server\user name but still nothing. It's like it does not like the password  I am typing in or that the user name I am sending it is wrong somehow. 

Basically i go to:

Applications > Internet > Terminal server client.
Input the IP and select RDP (also tried RDPv5)
hit connect
Input user name and PW
Error

I have also filled in all other information with the exception of client host name (I don't know what it is? I never set it or told it what i wanted it to be?). since it's on a work group I'm not sure what to put into the domain (?) but blank does not seem to work either.

Edit* nvm I found the host name

---

### Post by jpatton on 2007-04-25
Under domain enter the NetBIOS name of the server, that's what I have listed in mine and I know mine works fine.

Computer = IP
Protocol = RDPv5
Username = me
Password = pass
Domain = servername
Client Hostname = name of linux box
Protocol File =

That is my setup and I used this connection just last night with no problems connecting to Windows Server 2003, Windows Home Server, and Longhorn

---

### Post by trekuhl on 2007-04-25
if you are connecting with the old RDP client ok in winXP then the new 6.0 client is not required and not your problem. i know that server 2003 does not require by default the new client, only if certain settings in GP are set.

---

