---
title: "changing the display manager"
date: 2008-03-14
forum: Desktop Environments
---

### Post by carbonrodney on 2008-03-14
hey guys,

a while ago i upgraded to kde4, disliked it and reverted to kde3.blah. but i kept all the packages and stuff so i can still run kde4 apps. 

it all worked fine until recently when i wanted to configure the login manager, and realised my kde3 system settings interface changed it for kdm but not kdm-kde4. 

i did a bunch of searches, without result, and finally found a way to do it by browsing the contents of the /etc/rc4.d/ files. so i thought i'd share...

if you have them installed (kind of important), and you want to change from kdm <-> gdm <-> kdm-kde4 <-> xdm <-> whatever...

  $ sudo emacs /etc/X11/default-display-manager

so ******* easy... once you know where to look :P

---

### Post by vs8 on 2008-03-18
I'm an Ubuntu newbie, I'm test driving it on my girlfriend's laptop and my desktop. It's been good on the laptop. But I'm having a trouble in the desktop pc. I installed KDE 3.5.8, and made the mistake of enabling it as the default desktop enviroment thinking that it was the same KDE found in PCLos which has konqueror as the file browser. Once I installed it I restarted the PC saw the kubuntu bootsplash and then KDM screen like I supposed would happen. I started using this KDE, didn't like it at all on Ubuntu and removed it. Now I want my GDM back and the original Bootsplash screen but I don't have enough permissions to edit the text file.

This is none sense, why Ubuntu won't let me edit this file like it's supposed to? What is this permission thing? I've been doing administrative stuff by just giving the password of the user. Do I have to create a root profile or something?

Thank you!

---

### Post by carbonrodney on 2008-05-29
dude, you need to do some research on how unix systems operate... stat!


do this...

1.
$ sudo emacs /etc/X11/default-display-manager

2.
change kdm to gdm in the text file. SAVE IT!!

3.
then restart and when it asks you to log in make sure you click session=GayNOME instead of session=KDE.

good luck and merry christmas

---

