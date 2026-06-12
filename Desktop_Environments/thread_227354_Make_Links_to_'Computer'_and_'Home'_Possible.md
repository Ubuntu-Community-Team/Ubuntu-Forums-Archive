---
title: "Make Links to 'Computer' and 'Home' Possible?"
date: 2006-08-01
forum: Desktop Environments
---

### Post by dpaint4 on 2006-08-01
Okay, I'm an interface junky, and I love the new default icon set, and also, I've come from years on a series of Amigas, Macs, and Windows PCs.

So, I want to make links to 'Computer' and 'Home' on my desktop and it has proven a lot trickier than making links to anything else on the system.

The option isn't given when I right-click as with normal locations or applications, and when I try to manually do it by creating a launcher on the desktop, my links to "Computer:///" and "usr/home/" get me nowhere.

Is there a way to do this that I'm overlooking? 

Sorry in advance for the frivelous request. I fully realize how unimportant this is, but that new 'Computer' icon in Tangerine is GORGEOUS.

---

### Post by OffHand on 2006-08-01
[http://ubuntuforums.org/showthread.php?t=210287&highlight=home+computer+icon+desktop](http://ubuntuforums.org/showthread.php?t=210287&highlight=home+computer+icon+desktop)

---

### Post by apjone on 2006-08-01
have a look at  gconf-editor and its in there some where,  you can also have media appear as an icon when inserted

---

### Post by Tomosaur on 2006-08-01
To get a link to home:

Right click > Create Launcher
Name it 'Home'
In the command box, just type 'nautilus'.
Set your icon, click ok. Double click this new launcher and you should get to your home directory.

To link to 'Computer':

Same again, but your command should be 'nautilus computer://'

---

### Post by dpaint4 on 2006-08-01
Thanks a lot; that's just what I needed to know.

---

