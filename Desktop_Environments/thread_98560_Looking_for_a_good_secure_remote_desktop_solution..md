---
title: "Looking for a good secure remote desktop solution..."
date: 2005-12-03
forum: Desktop Environments
---

### Post by sinisterguy on 2005-12-03
Hello,

I was wondering what would be the best way to set up a remote desktop connection to my ubuntu box. I saw the solution on ubuntuguide.org but it said that it was not secure. I would also have to know what ports it uses as I am behind a router. Also, if possible I'd like to be able to specify which ports to use.

I need to be able to access my box at school sometimes and having my programs, bookmarks etc would be greatly beneficial. Because it is at school I'd also need an online client capable of connecting to my PC (something written in Java or the like).

---

### Post by kosmic on 2005-12-03
you can use SSH or FreeNX or VNC, to secure the conections don't use password to conect, instead configure it so you can  use a public key and don't allow root to login remotely, and you should be fine :)
 
It should be port 22 that you have to open in your router

---

### Post by HermanAB on 2005-12-03
SSH is installed with X-forwarding turned on by default.  Therefore, after logging in to a remote box, you can run any program remotely.

Like this:
$ ssh [email]johndoe@mybox.com[/email]
password
$ nautilus

So, provided that you know the name of the program you want to run, you can run anything at all - word processor, editor, browser, whatever.

If you insist on running a remote desktop and you have a very fast network connection, then you can tunnel VNC over SSH, by forwarding the required ports.  Here is some VNC info:
[http://www.aerospacesoftware.com/vnc-howto.html](http://www.aerospacesoftware.com/vnc-howto.html)

However, VNC type things are just so sloooow, compared to SSH, that I never use it.  I use SSH for everything.  For example, my email client is running on another machine and I have been too lazy to move my mail to my notebook.  I just SSH to the machine and run thunderbird.  It will only take a minute to copy the mailboxes, but I just can't be bothered...

Cheers,

Herman
[http://www.aerospacesoftware.com/linuxhowtos.html](http://www.aerospacesoftware.com/linuxhowtos.html)

---

### Post by DrBair on 2005-12-03
FreeNX all the way!  
If you need access to a desktop session that is currently running do VNC over FreeNX. 

FreeNX is faster than microsofts RDP in my experience. Even though I don't like microsoft I'll admit that RDP is pretty quick. Unsecure, but quick.  FreeNX benefits from all traffic going over a builtin SSH server so everything is securely encrypted.

---

### Post by TeeSeeJay on 2005-12-03
[QUOTE=DrBair]FreeNX all the way!  
If you need access to a desktop session that is currently running do VNC over FreeNX. 

FreeNX is faster than microsofts RDP in my experience. Even though I don't like microsoft I'll admit that RDP is pretty quick. Unsecure, but quick.  FreeNX benefits from all traffic going over a builtin SSH server so everything is securely encrypted.[/QUOTE]

How is RDP "unsecure"? With the exception of encryption negotiation and public key exchange, RDP and terminal services are encrypted in both directions.

---

### Post by sinisterguy on 2005-12-03
X-forwarding seems like a very good idea, but I need to be able to run it in windows without installing anything. If it is an independant binary i'm fine but I can't install anything. Also, is it possible to change the port that ssh uses? I think my school has all ports blocked except http, ftp and a few other proprietary ones.

---

### Post by cwaldbieser on 2005-12-04
[QUOTE=TeeSeeJay]How is RDP "unsecure"? With the exception of encryption negotiation and public key exchange, RDP and terminal services are encrypted in both directions.[/QUOTE]
This link explains how it is vulnerable to man-in-the-middle attacks.  It is from 2003, so it could be a bit dated, though:
[http://www.oxid.it/downloads/rdp-gbu.pdf]("http://www.oxid.it/downloads/rdp-gbu.pdf")

---

### Post by crouton on 2005-12-04
VNC-over-SSH is pretty secure, it does take some setup to get right and it will slow down the connection slightly. You could also do RDP-over-SSH, same issues as above.  I don't have any experience with FreeNX so can't comment on it.

VNC and RDP both have nice features the other doesn't, so I'd say give them both a try and settle on one, then secure it via SSH.

---

### Post by TeeSeeJay on 2005-12-04
[QUOTE=cwaldbieser]This link explains how it is vulnerable to man-in-the-middle attacks.  It is from 2003, so it could be a bit dated, though:
[http://www.oxid.it/downloads/rdp-gbu.pdf]("http://www.oxid.it/downloads/rdp-gbu.pdf")[/QUOTE]

It's been updated this year, so it doesn't seem too dated.

Thanks for the link. That's some good reading.

---

