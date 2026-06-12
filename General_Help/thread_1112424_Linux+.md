---
title: "Linux+"
date: 2009-03-31
forum: General Help
---

### Post by cowboy.bebop on 2009-03-31
So I was curious as to know what important aspects I should learn in Linux that would be a great deal of help to prepare me for the Linux+ Cert. I understand on how to use Linux and how it almost to me, feels like a windows environment (even that the environment is way off) navigating my way using the file manager, desktop usage, partition manager and the command prompt among other things. I eventually hope to move forward to my Security+ Cert I just need to know other important factors that I should go over?

---

### Post by kanikilu on 2009-03-31
I'm not certified, but I'd saying knowing how to do things from the command-line is probably the most useful tip I can give. I doubt they are going to care much if you know how to copy and paste a file with nautilus ;)

I'd probably try to learn the basics of things like setting up common services (ssh, apache, samba), process management (top, ps, kill), session management (screen, virtual terminals), user/group administration (adduser, addgroup) and common utilites like grep, sed, awk, find, etc. That's certainly not an exhaustive list, though...

I'd also find out what distribution "Linux+" uses. If you need to know RHEL, learning on Ubuntu isn't going to help with some things (package management, for instance).

---

### Post by mb_webguy on 2009-04-01
+1

Remember that the various desktop environments aren't Linux.  They're just applications that run on Linux.  Knowing your way around Gnome isn't going to help you get your Linux certification any more than knowing your way around Office is going to help with Windows certification.

You'll need to know how to use the command line and write shell scripts, the filesystem hierarchy standard and the purposes of the various system directories, what run levels are and how to use them, what GRUB and LILO are and how to use them, how to configure iptables, etc.  These aren't really things you're going to learn without delving into the command-line.

You *may* need to know a bit about the various desktop environments, and certainly about the X window system, but Linux certification tends to me more oriented towards the server side of things, so graphical environments aren't a high priority.

---

### Post by xenophed on 2009-04-01
I do have cert and I found that the guide at [http://www.tldp.org/LDP/sag/index.html](http://www.tldp.org/LDP/sag/index.html) will answer most questions with [http://www.tldp.org/LDP/lfs/html/index.html](http://www.tldp.org/LDP/lfs/html/index.html)

---

### Post by doas777 on 2009-04-01
ok. Certs.

the best approach to getting a cert is to get a good study guide. personally Sybex has never steered me wrong, but cisco press screws everyone who picks it up.

also make sure that the current version of the test is not going to be retired next month, and that it matches your guide.

read it cover to cover. mark the stuff you need to review, review, practice test, and take the sucker. it'll prolly work out fine for ya.

BTW, the sec+ is pretty easy, so you won;t have any big problems just getting it, if you think it'll be a while before your ready for the linux+

---

### Post by markharding557 on 2009-04-01
if you want to be an expert or engineer or whatever on linux then you must be a user first.
one must walk before learing to run

---

