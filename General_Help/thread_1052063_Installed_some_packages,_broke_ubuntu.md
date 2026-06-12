---
title: "Installed some packages, broke ubuntu"
date: 2009-01-27
forum: General Help
---

### Post by nesquik r0x on 2009-01-27
I've been searching for the last couple of days and can't find any help.

I should have checked whether the stuff was already installed, but it was late and I was sleepy.

So, what I did was download a few packages, glib, pango, and atk, into /usr/local/src.  I ./configure 'd and make / make install 'd them.  Worked fine for glib, then pango.  Then atk wouldn't let me make because I needed a higher version of glib (which I installed).  So I figured I'd restart my system to let the changes take effect, and then install atk.  When I tried to boot up, ubuntu starts, and I see the background color of my login screen, and then it just hangs.  Nothing comes up besides the background.  I tried ctrl+alt+f1 and then logged in and tried startx, but again, no luck.  Am I hosed?  Is there any way to back up to my last update without a gui?

---

### Post by taurus on 2009-01-27
Everytime you install, upgrade, or whatever plan you have for glib, you have to be real careful because most of the programs depend on the glib.  

Sounds to me like you installed a version of glib that is not sitting well with your Ubuntu.  You can try to remove the version of glib that you installed by going into the directory that you built it (./configure && make && sudo make install), then see if you can uninstall it with

```
sudo make uninstall
```
Reboot and see what happens.

---

### Post by nesquik r0x on 2009-01-27
So I tried the sudo make uninstall, and it's still not working for me.  I don't know what the deal is ..

[EDIT]
Went in to /usr/local/ and deleted everything to do with glib pango and gio (was I supposed to do gio?)
All I know is, it works now (seemingly)

---

