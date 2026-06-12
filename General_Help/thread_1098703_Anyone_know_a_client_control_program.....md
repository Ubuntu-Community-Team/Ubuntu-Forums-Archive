---
title: "Anyone know a client control program...."
date: 2009-03-17
forum: General Help
---

### Post by Akumos on 2009-03-17
Hi, I work at a school of over 400 computers and we have recently upgraded 50. So we have decided to install Ubuntu on them. We have a linux server running KDE desktop which a printer is installed on and the others all reach it fine but they are joined to our windows domain using Likewise so students can log in.

However, we need a remote management program. Something like remote desktop or Lan View so that we can see the screens and take control of the clients either from our server or from Windows.

Any ideas of where to head?

---

### Post by HermanAB on 2009-03-17
VNC is good for a training situation.

If you actually want to reduce the administration load of managing a bunch of machines, google for 'NFS root'.

Cheers,

Herman

---

### Post by fieroboom on 2009-03-17
Just to add to Herman's post, here is some good info, and it's what I use as a guide or "refresher" when I'm setting up vnc for someone:
[http://lifehacker.com/software/how-to/set-up-vnc-on-ubuntu-in-four-steps-317125.php](http://lifehacker.com/software/how-to/set-up-vnc-on-ubuntu-in-four-steps-317125.php)

Don't worry about the comments regarding it being unsafe; they are referring to running vnc over the internet without any encryption/security. Since you will be in your school's LAN, it shouldn't present any security risks for you to run vnc.
:D
-Paul

---

### Post by defishguy on 2009-03-17
I use iTalc to administer my students machines in conjunction with Webmin.  The combination is fantastic!


***[iTalc]("http://italc.sourceforge.net/")***
***[Webmin]("http://www.webmin.com/")***

Good luck!

---

### Post by rick71 on 2009-03-18
I also use iTalc and Webmin.

At the moment, I use iTalc mostly to monitor lab computers, and to shut them  down, however, it will also allow you to use the master as a demo (full screen or window) and if your NICs support Wake On Lan, you can start them too.

I starting using Webmin when a bug resurfaced in Gnome (it is now seems to be fixed again) prevented me from do some administration remotely. One thing you can do with Webmin when administering a server, is to have it manage your local users and Samba user at the same time, if you use its user management module.

---

