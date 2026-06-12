---
title: "Autostart applications with root access"
date: 2007-03-19
forum: Desktop Environments
---

### Post by DaveT on 2007-03-19
Hiya

Im trying to autostart a few apps in Xubuntu at start up but they need to have root access to operate as i like.

I know ive read somewhere how to do it but cant for the life of me remember how to do it or where i read it.

could someone please point me in the right direction?

Thanks in advance

Dave

---

### Post by Death_Sargent on 2007-03-19
simply put "gksu" infornt of the command this will prompt you to to give a password for each app that needs root acess (not sure how well this works with more than one app) Now if someone could tell me how to subvert the need to give a password without removing my password entirely im all ears

---

### Post by DaveT on 2007-03-19
Thank you for the reply

That is currently my setup having to put the password in at boot up.

I'm pretty sure though that i read somewhere about a boot script that operated as root and that applications can be placed into this script. it does seem as tho im imagining it though as i can find no reference to anywhere for it.

Thanks again

Dave

---

### Post by mike_tyrell on 2008-02-01
Hey there
if you have not found a fix yet for your problem this is what I found

[http://www.uluga.ubuntuforums.org/showthread.php?p=3840986](http://www.uluga.ubuntuforums.org/showthread.php?p=3840986)

my problem was I want to auto-start "sudo modprobe lirc_serial" at the begining so I followed the instructions on this link and wrote "(my_user) ALL= NOPASSWD: /sbin/modprobe lirc_serial"

and worked fine. I dont know it this works for you

take care

---

