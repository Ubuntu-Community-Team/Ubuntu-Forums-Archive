---
title: "Set a Global Proxy in Ubuntu/Xubuntu"
date: 2006-07-14
forum: Desktop Environments
---

### Post by shuttleworthwannabe on 2006-07-14
I am behind a proxy (corporate), but can access the www using a username and password. I have set the FF coonection to use proxy and it works fine. The problem is I can't access Ubuntu repos for apps using either synaptic or Terminal. I am currently using Xubuntu (but will be chnaging to Ubuntu or even Kubuntu when I get a faster machine at work).

How do I get to set a Global Proxy setting so that all applications that require to connect outside the LAN can get access. NOTE: synaptic has a setting to allow for proxies but it seems not to work. Not sure why.

Any suggestions,
Many thanks
swb (In Durban South Africa)

---

### Post by tribaal on 2006-07-14
I had the same problem at school.
To overcome it, you need to export the http_proxy variable to your shell:

```
export http_proxy="http://<your-proxy-adress>:<port>"
sudo apt-get update
sudo apt-get upgrade
```

This should do. Of course, it only affects the shell in which it is exported... so if you want to make it "permanent" you should add the export to the end of your ~/.bashrc file (this way it's being exported every time you start a shell).

Remember that bash scripts get executed in their own shells... you need to export it there too!

Cheers :)

- trib'

**Edit:** Hum didn't see the password part... not sure how to handle this... :(

---

### Post by shuttleworthwannabe on 2006-07-14
Thanks for the quick reply. I have done this in Terminal; but get numerous error (Note I did without the quotes). It apparently requires proxy authentication. How do I prompt into to allow me to provide the user and password for the proxy access.

NOTE: I have tried Kubuntu Live CD and set the Konqueror proxy there and it prompted me to provide authentication. 

How about for other apps? Surely there should be a way to program under networking or something, but I do not see this option in there?

Any other offers?

Thanks

---

### Post by shuttleworthwannabe on 2006-07-14
Okay here is another issue: apps like media players (xfmedia) do not have a setting for proxies. Epiphany too does not have these setings. Now what?

Let me see if I can google this again and come back...

---

### Post by shuttleworthwannabe on 2006-07-16
[http://www.linuxquestions.org/questions/showthread.php?t=454026](http://www.linuxquestions.org/questions/showthread.php?t=454026)
[http://www.ubuntuforums.org/showthread.php?t=183093](http://www.ubuntuforums.org/showthread.php?t=183093)
[http://www.ubuntuforums.org/showthread.php?t=210695&highlight=global+proxy](http://www.ubuntuforums.org/showthread.php?t=210695&highlight=global+proxy)
 
I have tried most of them, but  do not seem to get anywahere; synaptic still moans! (synaptic does not have place to put in the authentication info).
Is this is a bug? I am in Ubuntu Dapper now and have set the network proxy in preferences>network proxy, but it still does not register with synaptic (have set this now to direct connection).
 
Anybody have thoughts on this? Is this a bug?
Thanks

---

### Post by shuttleworthwannabe on 2006-07-16
Ok, as a work around I have discovered this (only works in terminal, NOT synaptic)NOTE: copy with quotes:
[COLOR=Red] export http_proxy="http://username: password@proxyaddress:  port"[/COLOR]

Put that code in terminal and then do
[COLOR=Red] sudo apt-get-update
sudo apt-get upgrade[/COLOR]

In this way at lest you can update the system; and install apps using CLI (pity the wiki in some areas expets us to use synaptic).

Just installed Ubuntu Dapper (157MB of upgrade, man I have missed a lot!)...work bandwidth will choke!
Tah
swb

---

### Post by Noxide on 2006-07-16
Here's what worked for me.
Add the following line to /etc/environment :
```
http_proxy="http://user:pw@proxyaddress:port"
```
I'm not sure when exactly it's loaded, but a restart made it load on my box. You can then see it appear in the output of "export".
This works much like exporting the variable in the shell, only for the entire session.

---

### Post by shuttleworthwannabe on 2006-07-17
Sweet! It works like a charm. Does it work in Synaptic too? or this is a dud-thing?

---

### Post by shuttleworthwannabe on 2006-07-17
I can confirm that this works in synaptic too!! (slow though)

---

