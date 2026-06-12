---
title: "Can't get my Ubuntu desktop after I login!!!"
date: 2007-03-16
forum: Desktop Environments
---

### Post by tuxy on 2007-03-16
All of a sudden I can't get my desktop after I GDM login. I can see the cursor and Ubuntu's brown blank screen. This thing happened after I tried Ubuntu's Fiesty Fawn Live CD. But I don't think a live CD will have an effect on Ubuntu stable desktop.

I have tried everything in resolving this issue, Googled, searched forums for answers but no luck! Finally I have reinstalled "gdm" by **apt-get remove** and **apt-get install gdm** Still no luck. I am not sure by removing and reinstalling gdm will install the whole Gnome desktop system because it was just a 12MB install. Feels like gdm is the just login application. Am I right?

Anyways these are the errors(EE) in /var/log/Xorg.0.org file. 
[B](EE)Failed to load /usr/lib/xorg/modules/extensions/libGLcore.so 
(EE)Failed to load module GLcore(loader failed, 7)
(EE)AIGLX:Screen 0 is not DRI capable[/B]

In fact, I started getting the first 2 errors only after I reinstalled gdm.
The last AIGLX error is the main culprit which made me to experiment :)

Strange thing is there used to be another error(EE) in Xorg.0.org file 
(EE) Error loading Key map /var/lib/xkb/server-0.xkm which disappeared after I reinstalled gdm.

I am running Ubuntu Edgy Eft 6.10 on 2.6.17-11-386

Any suggestions or advise will be greatly appreciated.

---

### Post by tzulberti on 2007-03-16
You should try: "sudo dpkg-reconfigure xserver-xorg"...
It seems that there is a problema with the xorg configuration file... In the modules options try disableling dri and glx...

---

### Post by tuxy on 2007-03-16
Hi,

I have reconfigured through dpkg-reconfigure xserver-xorg and disabled DRI and GLX. Now I get an error **(EE) Error loading Keymap /var/lib/xkb/server-0.xkm**
I did notice keyboard layout config when I was configuring through dpkg-reconfigure and left most of the options to default. I am using Logitech wireless KB and mouse. 
I left the default options as KB US and 104key.

How to find out the KB config setup, I mean to look into more options for KB?

Thanks for the quick reply.

---

### Post by tuxy on 2007-03-16
Some how I managed to find the Keyboard rules in /etc/X11/xkb/rules
but no luck. I have found few logitech cordless KB models and I have tried few of them in xorg.conf and its still the same I get the same "key map" error.

Very strange I never had this sought of problem before with this KB issue. I have been using this wireless KB on Ubuntu for the past 2 years and no issues at all. I never have to configure the KB separately. Ubuntu automatically recognizes it.

---

### Post by rajaiskandarshah on 2007-03-17
i have a similar problem on ubuntu 6.10 on compaq nx6120 notebook since early this morning.

i get the login page, enter my username and password, but i dont get to my desktop, instead i still get the same login page.

not tried fiesty fawn, nor did i install anything yesterday.

appreciate any help.

---

### Post by tuxy on 2007-03-17
Hi Raja,

Can you please post **grep EE /var/log/Xorg.0.log** result.

Thank you

---

### Post by tuxy on 2007-03-17
Any help guys?

---

### Post by tuxy on 2007-03-17
Issue resolved! I have reinstalled Gnome desktop by **apt-get install gnome-desktop**
I was missing my Ubuntu desktop and impatient :)

There should be a way around. If any one has an answer please post the solution.

---

### Post by rajaiskandarshah on 2007-03-18
ok found out the real cause for my problem.

i had run out of hard disk space. hence gdm will not log into gnome.

solution: boot into terminal and delete unncessary files with rm command (got rid about 100mb) then exit into gdm. log in as usual.

---

