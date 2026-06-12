---
title: "Un-installing the kubuntu desktop"
date: 2009-06-25
forum: Desktop Environments
---

### Post by sukhiaatma on 2009-06-25
Hey guys,

Its been, like 5 months now that i have switched over from "Vista" to ubuntu ..And I must say I m loving every second of making the switch.
I was comfortable with what Ubuntu gave me by default (gnome)
But wanted to know more I tried out Kubuntu the KDE version of ubuntu.

I referred this tutorial here..[HTML]http://www.psychocats.net/ubuntu/kde[/HTML] to get it installed, The link also provides how to remove it.


Admist of enjoying the whole new KDE I messed up a few things with the panel and desktop.I then searched up how to restore it but could not get the default one.I then un-installed kubuntu desktop and reinstalled it via synaptic in gnome hoping that wld be fixed but it has been in vain so far.


The question I ask is :

Why when I have uninstalled a package it leaves its settings behind.

Also how can I make a fresh install of the Kubuntu desktop on my Ubuntu  so that i dont have the old settings. 

Rather as the title reads how to I make a complete un-install of all kubuntu related stuff in my comp

* I have already tried  [HTML]http://www.psychocats.net/ubuntu/puregnome[/HTML]

---

### Post by days_of_ruin on 2009-06-25
I think instead of "remove"ing the kde packages you need to "purge" them.

So in the command given for removing kde replace "remove" with "purge".

---

### Post by sukhiaatma on 2009-06-25
> **days_of_ruin said:**
> I think instead of "remove"ing the kde packages you need to "purge" them.

So in the command given for removing kde replace "remove" with "purge".
I tried that but it did nto work out. I reinstalled the KUbuntu desktop and the default panel is still now showing up.

---

### Post by days_of_ruin on 2009-06-25
Try deleting the ~/.kde folder.

---

### Post by pizza-is-good on 2009-06-25
I'm having a similar problem.
 
I downloaded, and tried Kubuntu, and didn't like. Tried removing it through Synaptic (I originally added it through Synaptic as well), but I still get the Kubuntu load screen when I boot. It's not a big problem, but it's a little annoying.
 
Originally installed Kubuntu in 8.10, and currently using 9.04. I'd hoped that the update would somehow take car of it...
 
Anyone having same problem? or any ideas?
 
Thanks

---

### Post by londonali1010 on 2009-06-25
If you uninstall via the Synaptic Package Manager, there are two options to uninstall, "Mark for Removal" and "Mark for Complete Removal".  The complete removal option will delete all your settings as well.

---

### Post by Durden on 2009-06-25
rm -rf ~/.kde
rm -rf ~/.qt*

You don't screw up the "install" of KDE when messing around as a user. You can just mess up your personal configuration. You can delete it all and start from scratch with the above commands.

I would recommend booting into gnome to do this. The moment you remove the .kde directory kde will likely make a new one if you're logged into KDE at the time.

---

