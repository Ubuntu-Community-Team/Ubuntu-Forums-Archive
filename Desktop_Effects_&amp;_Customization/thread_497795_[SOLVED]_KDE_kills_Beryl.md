---
title: "[SOLVED] KDE kills Beryl?"
date: 2007-07-10
forum: Desktop Effects &amp; Customization
---

### Post by eidauk on 2007-07-10
Can anyone explain why Beryl works just fine in Gnome, but when I install KDE it gives me a white screen with no GUI?

I've followed this thread at Ubuntuforums to get my ATI card to work with Gnome and Beryl:

[http://ubuntuforums.org/showthread.php?t=399643&highlight=beryl+ati+200m](http://ubuntuforums.org/showthread.php?t=399643&highlight=beryl+ati+200m)

This particular HowTo has me log on with XGL to get Beryl working as a work around for a poor ATI driver. I think when I run KDE I have to log on by choosing a KDE environment session. Is there a way to get KDE by logging on with XGL? Maybe that would solve my problem.

(I'm using Linux Mint Cassandra distro)

---

### Post by Happy_Man on 2007-07-10
Yeah, there's a way... could you post your XGL startup files here please?

---

### Post by eidauk on 2007-07-10
I'm a noob. Can you tell me how to do that?

---

### Post by eidauk on 2007-07-16
I got it working! I followed [this]("http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_XGL#Adding_an_Xgl_login_session") in the Beryl Wiki. In short I replaced:

*exec dbus-launch --exit-with-session gnome-session*

with

*exec startkde*

in my /usr/local/bin/startxgl.sh file.

Pretty simple

---

