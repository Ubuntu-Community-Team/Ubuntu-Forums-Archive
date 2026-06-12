---
title: "Only 'no effects' sessions load correctly"
date: 2011-04-30
forum: Desktop Environments
---

### Post by thecapsaicinkid on 2011-04-30
If I choose 'Ubuntu' (i.e Unity) or 'Classic' then no bars/menus load and I'm left with just a desktop. Chossing 'Classic No Effects' is the only sessions which gives me menu bars.

I'm guessing this is related to the 3D driver not functioning correctly. Natty 11.04, Compaq 6720s laptop, intel onboard gfx.

---

### Post by thecapsaicinkid on 2011-05-01
Any ideas?

---

### Post by markjensen on 2011-05-01
I have the same thing going on. Upgraded from a Xubuntu/fluxbox install. I'm trying to figure out the source and the solution...

---

### Post by markjensen on 2011-05-01
Found the following threads here on UbuntuForums, and they worked for me.  Have Unity working fine now.

[http://ubuntuforums.org/showthread.php?t=1744758](http://ubuntuforums.org/showthread.php?t=1744758)
shows a handy command to check hardware setup for unity requirements:
```
/usr/lib/nux/unity_support_test -p
```
My hardware passed that check.

When I tried to start unity from a terminal, it failed with a
> Couldn't find a perfect decorator match; trying all decorators
Found no decorator to startso I checked for that text on the forums here and found this thread:
[http://ubuntuforums.org/showthread.php?p=10741462#post10741462](http://ubuntuforums.org/showthread.php?p=10741462#post10741462)

I did what it said there:```
cd ~
rm -rf .gnome .gnome2 .gconf .gconfd .metacity

sudo apt-get remove ubuntu-desktop

sudo apt-get install ubuntu-desktop
```which wipes your existing user preferences for your desktop and re-creates.

Hope this helps you out as well!

---

### Post by thecapsaicinkid on 2011-05-01
Clearing the hidden folders in the user directory worked, good job :D

---

