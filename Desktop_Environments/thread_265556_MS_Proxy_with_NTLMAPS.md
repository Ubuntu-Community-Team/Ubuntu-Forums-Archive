---
title: "MS Proxy with NTLMAPS"
date: 2006-09-26
forum: Desktop Environments
---

### Post by plc on 2006-09-26
Hello All,

I have spent the good part of three days on this problem and I am now at a loss.  I am a high school teacher keen to setup a Linux user group for my students.  I have installed Ubuntu Linux on a PC to get things tested but Synaptic and apt-get will not pass through our infernal MS proxy.

I have tried just putting the proxy server address and port number into Gnome, Synaptic and apt-get.  None of these worked. I then added 
http:: proxy "http://username: password@proxyaddress:8080/" (spaces after colons inserted to avoid smileys) but this also failed.

I thought I had found the solution in the forums when I discovered ntlmaps.  I installed this and set it up, putting in the proxy address, proxy port, my domain name and both my username and password.  I then pointed the apt-get .conf file to 127.0.0.1: 5865 and it will not work.  Now I have also tried inserting localhost: 5865 and I have also tried inserting this address into Synaptic.  I also pointed the Network proxy setting in Gnome to localhost to no avail. Nothing works; I still get the 407 error.

I have edited the ntlmaps server.cfg file a number of times but all options fail.

Interestingly I can point Firefox to localhost:5865 and it still asks for a username and password.  My assumption is that the ntlmaps is failing to authenticate to the MS server, otherwise Firefox would not ask for a password and Synaptic and apt-get would work.

Has anyone else had this problem with ntlmaps or is it a server issue with me?

For the sake of Linux running at my school I would appreciate some wisdom.

Kind regards,
Paul

p.s. Posting this from home because the NSW Dept. of Education blocks Ubuntu Forums.  Curse them.

---

### Post by pirolla on 2006-10-25
I'm having the same problem but with pear.
I could reach the internet with apt by starting ntlmaps configured correctly and setting the http_proxy env. var. with http://<username>:<password>@127.0.0.1:5865.

If I discover something I put it here...

Kind regards,
Pirolla.

---

### Post by 4tro on 2006-11-22
all the solutions i found on this forum require a plain text password to be entered in a config file.
My supervisor will never allow this and it sounds kinda stupid to me too....
entering a plain text password for proxy access not only sounds stupid, it is stupid.

---

### Post by ntufar on 2007-01-12
> **4tro said:**
> all the solutions i found on this forum require a plain text password to be entered in a config file.
My supervisor will never allow this and it sounds kinda stupid to me too....
entering a plain text password for proxy access not only sounds stupid, it is stupid.

In /etc/ntlmaps/server.cfg change:

NTLM_TO_BASIC:0
    to
NTLM_TO_BASIC:1

From documentation:
# This option makes APS try to translate NTLM authentication to very usual "Basic"
# scheme. Almost all http clients know it. With this option set to 1 user will be requested
# by his browser to enter his credentials and these username and password will be used by
# APS for NTLM authentication at MS Proxy server or Web server.
# In such a case different users can use one runnig APS with their own credentials.

---

### Post by yusufk on 2007-05-08
what about GAIM/MSN, is there a way to get this to connect via ntlmap?

---

