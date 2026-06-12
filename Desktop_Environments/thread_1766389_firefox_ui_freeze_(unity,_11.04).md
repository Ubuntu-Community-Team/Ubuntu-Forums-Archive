---
title: "firefox ui freeze (unity, 11.04)"
date: 2011-05-24
forum: Desktop Environments
---

### Post by cong06 on 2011-05-24
The Firefox UI is periodically freezing. I haven't managed to blame something in particular, though it's possible it happened after I installed the latest version of flash through "Flash-Aid".

During these Firefox freezes, the menu works, but the general UI does not. Mousing over buttons produces no effect, and the mouse can't interact with the page. The only part that works is the minimize, maximize, restore, close buttons, and the menus.
Since the menus work, I can open a new window and continue my browsing without closing firefox.

I can also tell it to open a new tab, or to open a file.

If I open a new tab, the display view (where the page is displayed) reacts as if a new page is created, and the cursur shows up in the address bar. However I can't type in the address bar, and the UI is still frozen.
If I open a file, again, the display shows the new file, but the UI is still frozen and the mouse can't interact with the text from the file.


Sometimes if I "restore" the window (dragging the menu bar down), and them maximize it again, it fixes. Sometimes it doesn't.

---

### Post by slibuntu on 2011-06-21
Having the same problem. I'm not really sure when it started, but dragging the window down and back up again does the trick.

The window is registering clicks and changing state.. for example, in Chrome, if I click somewhere on the page and then 'fix' the problem by dragging it down from the menu bar, the page that I clicked on will have loaded. 

I can't seem to find a bug related to it, I'm going to keep looking.

---

### Post by cong06 on 2011-06-21
Well, my progress has been this so far:

It happened more often when I had Barlesque installed, but since I disabled it I've still experienced it occasionally.

When it does happen, it seem to be related to a network disconnect. Where my connection is still available/connected, but I can't access servers.
By that I mean, the Network Manager thinks I'm connected, but I have no bandwidth.

---

### Post by Talon2 on 2011-06-24
I am seeing this problem as well.  My system is on Ubunutu 11.04 but I am not using Unity.  It seems to me that this problem is Firefox specific.

---

### Post by buanzo on 2011-09-03
Same happening here, but I noticed that only when thunderbird is open (mmmm another mozilla product) while I use flash from within firefox.

---

### Post by cong06 on 2011-09-03
Hm. I haven't had problems with it recently, now that I think about it.
I've also been using flash-aid.

Can you try [Flash-Aid](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/) to update your flash to the lastest version, so we can see if that helps?

---

### Post by buanzo on 2011-09-03
OK guys, maybe this is related to other bug, please test this and let me know if it worked for you:


Run this command: gksudo gedit /etc/adobe/mms.cfg

You might find a line like this:

EnableLinuxHWVideoDecode=1

Replace the 1 by 0:

EnableLinuxHWVideoDecode=0

If there is no such line, add it: EnableLinuxHWVideoDecode=0

Then save file file, reboot the system.

---

