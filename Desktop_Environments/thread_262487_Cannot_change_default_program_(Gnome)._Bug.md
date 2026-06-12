---
title: "Cannot change default program (Gnome). Bug???"
date: 2006-09-21
forum: Desktop Environments
---

### Post by theseeker on 2006-09-21
Hi there. 

I've got this weird problem with ubuntu dapper. I cannot change the default application that is associated with any file types. For instance, I want to have Acrobat handle my double clicks on .pdf documents, I go right-clicking a pdf file--> properties--> open with and click on Acrobat button, but it DOES NOT change, it sticks to the selection it already has, in this occasion it is Document Viewer! Is this some kind of bug? It is getting really annoying. 

Please provide some help here. 

Thanx beforehands!

Giorgos

---

### Post by theseeker on 2006-09-21
In fact, when i try > gksudo nautilus and then do the properties--> open with procedure, everything goes as planned and the default program changes, but only for root user. Does this have to do with user permissions? Thanx for your (if any!) help!

Giorgos

---

### Post by dmartin on 2006-09-21
Is it possible you came from another version of Linux, and kept your home directory, or parts of your home directory?  I've had similar problems when I did that.  You often get config files owned by the wrong uid.

---

### Post by theseeker on 2006-09-21
No, it is a clean installation of ubuntu dapper, including the /home dir. The only updates and upgrades I've done, are through apt-get update, upgrade, dist-upgrade... What is wrong? I hope it can be solved someway..!

---

### Post by aysiu on 2006-09-21
Try this: ```
sudo chown -R theseeker:theseeker /home/theseeker
``` Substitute your real username for what I've put at *theseeker*

---

### Post by theseeker on 2006-09-21
aysiu, thank you so very much! It does solve the problem indeed. Is it possible to explain to me a bit of what went wrong? I have some unix knowledge, just give me a hint, I like to learn! 

Lots of thanx!

---

### Post by aysiu on 2006-09-22
Well, I know what happened, but now how it happened. You said it was a fresh install, right?

Somehow, a configuration file changed ownership to root so that you couldn't modify it. The command I gave changed the ownership back to you.

The only obvious way I know of changing ownership of configuration files accidentally is using *sudo* with a graphical applications. More info here:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by blu30n3 on 2007-06-24
im having the same issue and that didnt work for me.. if u have any more solutions id be glad to hear them .. thnx
  oh also mine was working fine for a long time, i think i might have imported some stuff from previous system but not much and i didnt start experiancing issue till much later

---

