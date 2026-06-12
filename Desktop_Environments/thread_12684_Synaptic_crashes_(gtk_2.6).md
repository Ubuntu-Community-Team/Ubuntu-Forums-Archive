---
title: "Synaptic crashes (gtk 2.6)"
date: 2005-01-26
forum: Desktop Environments
---

### Post by kwisatz on 2005-01-26
I've an Ubuntu 4.10 on my HP laptop. Yesterday I wanted to update gaim with the latest version (1.1.1) from the hoary repository...this package depends from libgtk 2.6...yes, I was stupid ok...It's WRONG mixing warty and hoary packages but yesterday I didn't know this...

Now when synaptic show the dependencies of a packages that I want to install...I click "OK" and it crashes without an error message, neither in console. 
I have just read on a post on this forum that there is a synaptic 0.55 package but I didn't find it and if I try to install it from hoary repository there were too MANY packages to update and I don't want to make more damages...

What could I do?

Thank you in advance and sorry for my poor english :)

kwisatz

---

### Post by albersag on 2005-01-26
[QUOTE=kwisatz]I've an Ubuntu 4.10 on my HP laptop. Yesterday I wanted to update gaim with the latest version (1.1.1) from the hoary repository...this package depends from libgtk 2.6...yes, I was stupid ok...It's WRONG mixing warty and hoary packages but yesterday I didn't know this...

Now when synaptic show the dependencies of a packages that I want to install...I click "OK" and it crashes without an error message, neither in console. 
I have just read on a post on this forum that there is a synaptic 0.55 package but I didn't find it and if I try to install it from hoary repository there were too MANY packages to update and I don't want to make more damages...

What could I do?

Thank you in advance and sorry for my poor english :)

kwisatz[/QUOTE]
 Try apt-get via console.

Or update to hoary. I think back updates are as dangerous as mixing.

If only gtk was modified. Try on shel apt-remove gtk.....

And then modify to warty repositories and apt-get install gtk...

---

### Post by Rule on 2005-01-26
try adding the backport repo to your sources.list

deb [http://ubuntu-bp.sourceforge.net/ubuntu/](http://ubuntu-bp.sourceforge.net/ubuntu/) warty-backports main universe

---

### Post by kwisatz on 2005-01-26
I've found synaptic 0.55 from [http://packages.debian.org/unstable/admin/synaptic](http://packages.debian.org/unstable/admin/synaptic) and now it works but I have now a problem with menus. I hope you can help me...

There isn't Synaptic menu item and now I cannot add any item in the menus! 
If I browse applications:// with Nautilus I found my application but if I add ANY new item it doesn't show! 

I can't find any information on how gnome menus work...
could you help me?

Thanx in advance,

kwisatz

---

### Post by jdong on 2005-01-26
Please don't install debian Synaptic on Ubuntu. Ubuntu heavily customizes their synaptic!


Add Warty Backports repositories. They contain the most recent Synaptic from Hoary. (0.55+CVS)

See the "Welcome" sticky in the backports forum.

---

### Post by kwisatz on 2005-01-26
Ok, I just installed Synaptic 0.56CVSetc...etc...

now on Computer/System configuration there is Synaptic menu item! 
But I can't still add any new item on the menus! 

Thanks,

kwisatz

---

