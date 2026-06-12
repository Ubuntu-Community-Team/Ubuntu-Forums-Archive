---
title: "ugly xcursor hand pointer in  kde"
date: 2005-08-30
forum: Desktop Environments
---

### Post by jamboarder on 2005-08-30
This happens only on kde apps (konqueror, etc).  I have an ugly hand pointer when hovering over links, etc. instead of the hand pointer that is part of the kubuntu Human set (or any other cutom set).  If I'm using a gtk app (firefox, synaptic) though the correct pointer is used.  In fact I can move the pointer from say konqueror to firefox and see the difference. Same goes for the arrow+wait and one or two others I can't remember right now.

Anybody else seeing this?  Any ideas?

Thanks

---

### Post by tonysathre on 2005-08-30
try changing your icon theme and see if the problem persists

---

### Post by raven on 2005-08-30
[QUOTE=jamboarder]This happens only on kde apps (konqueror, etc).  I have an ugly hand pointer when hovering over links, etc. instead of the hand pointer that is part of the kubuntu Human set (or any other cutom set).  If I'm using a gtk app (firefox, synaptic) though the correct pointer is used.  In fact I can move the pointer from say konqueror to firefox and see the difference. Same goes for the arrow+wait and one or two others I can't remember right now.

Anybody else seeing this?  Any ideas?

Thanks[/QUOTE]

I believe you have go to
control center/peripherals/mouse/cursor theme
and choose kubuntu default or what ever you like
hope that will correct it

---

### Post by jamboarder on 2005-08-31
Thanks for the ideas.  

I have the Kubuntu Human cursor theme selected in Mouse module under peripherals and it appears the arrow pointer is what it should be as well as other cursor pointers.  But hand pointer in kde apps is not what's shown in the Kubuntu Human theme. Its the ugly xcursor default.  Strange though that when I mov ethe mouse over gtk apps that use the hand pointer, like Firefox, it uses the correct hand pointer from the Kubuntu Human theme. I've tried selecting other cursor themes, restarting X, rebooting and still can't get the Kubuntu Human hand pointer in kde apps.

I'll keep digging around, hopefully someone has an idea or could check to see if they have this behaviour.

Thanks for your help

---

### Post by tonysathre on 2005-08-31
do u have the use gtk themes on kde enabled in the control center? try that if it isnt

---

### Post by deadlands on 2005-09-01
[QUOTE=tonysathre]do u have the use gtk themes on kde enabled in the control center? try that if it isnt[/QUOTE]
 I had the same problem, I installed the JimMac theme(same is Kubuntu Human) from kde-look and it fixed all the issues.

[http://www.kde-look.org/content/show.php?content=28281](http://www.kde-look.org/content/show.php?content=28281)

---

### Post by jamboarder on 2005-09-02
[QUOTE=deadlands]I had the same problem, I installed the JimMac theme(same is Kubuntu Human) from kde-look and it fixed all the issues.

[http://www.kde-look.org/content/show.php?content=28281](http://www.kde-look.org/content/show.php?content=28281)[/QUOTE]
 Thanks deadlands.  This worked greate.  I went ahead and installed it as the system-wide default.

Thanks again!

---

### Post by yongyi on 2005-09-03
[QUOTE=deadlands]I had the same problem, I installed the JimMac theme(same is Kubuntu Human) from kde-look and it fixed all the issues.

[http://www.kde-look.org/content/show.php?content=28281](http://www.kde-look.org/content/show.php?content=28281)[/QUOTE]
how to install it?
i try:
# Open the Control Centre
# Open Peripherals -> Mouse
# Click the Cusor Theme tab
# Click Install New Theme...
# Select the cursor theme archive
but  get Error:
The file 28281-Jimmac0.tar.bz2 does not appear to be a valid cursor theme archive.

---

