---
title: "Synaptic disappears"
date: 2008-07-17
forum: Desktop Environments
---

### Post by cmarvel on 2008-07-17
Does anyone else suffer Synaptic disappearances if you try to invoke it directly from the desktop?  When I select it from the System>Administration>Synaptic drop down menu, I see the Synaptic launcher icon start up, twirl for about ten or fifteen seconds, and then disappear. No program request for a password, no Synaptic list, nada.  I'm left right where I started, at the desktop.

This DOESN'T happen if I first open a Desktop FOLDER window and select Synaptic from there.  I'm immediately taken to an Authenticate / Authorize window, and, when I enter my password, Synaptic propogates its package list and presents it as it should.

I get the same behavior when I try to launch Hardware Drivers and Hardware Testing after I select System > Administration > Hardware Drivers/Hardware Testing directly from the Desktop.

I'm just curious about this.  Nothing that I can't live with.  Thanks in advance for your response.

---

### Post by stitchmysmile93 on 2008-07-17
Hey I'm not sure what the problem really is I thought it was suppose to work out of the box or w/e.

I'd check to see if you have the following:
gnome-app-install
gnome-applets
gnome-applets-data
gnome-control-center
gnome-desktop-data

Another thing how long have you had this problem ???

---

### Post by coffeecat on 2008-07-17
> **cmarvel said:**
> When I select it from the System>Administration>Synaptic drop down menu, I see the Synaptic launcher icon start up, twirl for about ten or fifteen seconds, and then disappear. No program request for a password, no Synaptic list, nada.  I'm left right where I started, at the desktop.

<snip>

I get the same behavior when I try to launch Hardware Drivers and Hardware Testing after I select System > Administration > Hardware Drivers/Hardware Testing directly from the Desktop.

The same problem is affecting apps needing administrator authentication. There is definitely something wrong here.

Hover your mouse over the main menus in the panel (top left) and right-click. Select 'Edit Menus'. Highlight 'Administration' in the left pane and highlight 'Synaptic Package Manager' in the right pane. Right-click over the highlighted 'Synaptic Package Manager' and choose 'Properties'. What does the field 'Command' say? It should have:

```
gksu /usr/sbin/synaptic
```Yes, that's right - gksu, not gksudo. That took me by surprise. Anyway, whether or not that is what is in that field, open a terminal and type in that line. (You could try 'gksudo /usr/sbin/synaptic' instead/as well - both work equally well for me.) Do you get an error message? Does Synaptic open? Does the same thing happen as with from the menu?

Hopefully, we'll find out whether the menu commands have been corrupted somehow or whether there is a more fundamental problem with gksu/gksudo.

> **cmarvel said:**
> This DOESN'T happen if I first open a Desktop FOLDER window and select Synaptic from there. I'm immediately taken to an Authenticate / Authorize window, and, when I enter my password, Synaptic propogates its package list and presents it as it should.

I don't follow what you are doing here, but perhaps I am missing something. I'm intrigued. Could you describe that again?

> **cmarvel said:**
> I'm just curious about this.  Nothing that I can't live with.  Thanks in advance for your response.

You're more patient than I would be. :) But I think it needs investigating.

---

### Post by cmarvel on 2008-07-18
Problem SOLVED (but I didn't do anything except load about 30 Ubuntu updates after logging my post yesterday).  Thanks, everybody, for your replies.  

An afterthought: boy, has open source computing come a long way.  I first tried Linux ten or twelve years ago-- can't remember which distro, maybe Mandrake or Caldera.  Have gone back four or five times since and now I think I've got something rock solid.  Does my session time tell me that?  It's been three weeks since I loaded Ubuntu and during that time I think I've booted up the Windows XP side of my laptop only once. 

More fun to come! I can't wait to get my hands on an ASUS eee pc a few years from now when the price comes down.

---

