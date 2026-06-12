---
title: "Ati+XGL+KDE?"
date: 2007-09-12
forum: Desktop Effects &amp; Customization
---

### Post by zepfan on 2007-09-12
Is an install of FGLRX XGL possible in Kubuntu? Everytime in enable the driver in monitor settings, the screen gets garbled and i have to reinstall kubuntu. I'm 100% new to kubuntu but i've been using ubuntu for about a year now. Any one have any ideas?
My graphics card is a XTI x300 in a dell 9300 laptop.

---

### Post by JBAlaska on 2007-09-12
This is a older [Guide](https://help.ubuntu.com/community/CompositeManager/Xgl), but it's a good one.

---

### Post by kellemes on 2007-09-12
Before tweaking xorg make a backup of /etc/X11/xorg.conf so you can simply replace it when things go wrong.. reinstalling the hole system is not needed at all.
Also.. Videocard-related issues often leave there marks in /var/log/Xorg.0.log so keep an eye on that.

---

### Post by zepfan on 2007-09-12
OK so thank you. I installed an XGL session,and installed the FGLRX driver. It all works fine except for one thing.
When i go to system settings an the Monitor and Display module, I get this. 


The Module could not be loaded, Possible reasons:
1. An error occurred during your last KDE upgrade leaving an orphaned control module.
2. You have old third party modules lying around.


It's not the end of the world, but is there anyway to fix this, or is it normal for KDE?

Edit: Also is there any fix for holing down the shift key to force log off? I always forget and i get logged off!

---

### Post by pheonixind on 2007-09-12
I was not aware XGL ran with KDE.  I thought it was a Gnome thing only.  This rocks!

(Still a Gnome fan tho. :guitar: )

---

### Post by zepfan on 2007-09-12
Yea, I didn't know it was possible, I figured there had to be a way, but it had to be a lot more work, It was pretty simple.

---

### Post by zepfan on 2007-09-12
> **zepfan said:**
> 
When i go to system settings an the Monitor and Display module, I get this. 


The Module could not be loaded, Possible reasons:
1. An error occurred during your last KDE upgrade leaving an orphaned control module.
2. You have old third party modules lying around.


It's not the end of the world, but is there anyway to fix this, or is it normal for KDE?

Edit: Also is there any fix for holing down the shift key to force log off? I always forget and i get logged off!

No one has any idea on this ?:confused:

---

