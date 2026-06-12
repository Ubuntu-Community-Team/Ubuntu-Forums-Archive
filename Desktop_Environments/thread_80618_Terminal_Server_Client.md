---
title: "Terminal Server Client"
date: 2005-10-22
forum: Desktop Environments
---

### Post by mit on 2005-10-22
I have to say how impressed i am with Ubuntu in general and with regards to this thread terminal server. :) 

I have used it to connect to a XP machine on my LAN and it works great!  
It will connect using the IP address but not the computer name. This is fine when in the Lan but will it work via my public ip?
Is it ok to leave the domain, client host name and protocol blank, or should they have some text in?

Will it work to connect to a Mac?

---

### Post by mlomker on 2005-10-22
> Is it ok to leave the domain, client host name and protocol blank, or should they have some text in?


I don't know what tool you are using, but they are just front-ends to the rdesktop command-line application.  I just created my own shell scripts and link them to icons.  You can always put the IP address in there instead of the servername.

Example:

```

rdesktop -5 -g1024x768 -uusername -dMYDOMAIN -ppassword -P servername &

```

> Will it work to connect to a Mac?

You'll want to use VNC.

---

### Post by mit on 2005-10-22
Vnc? where can i get that from? :KS

---

### Post by mlomker on 2005-10-22
For Ubuntu you'll search in synaptic.  For the Mac, you could [look here.]("http://www.nyu.edu/its/humanities/docs/vnc.html")

---

### Post by mit on 2005-10-22
Thanks! there are loads of choices under VNC in Synaptic. Should i tick them all?

It asks for the install disc too....

---

