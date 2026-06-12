---
title: "Cannot disable USB automount"
date: 2011-01-25
forum: Desktop Environments
---

### Post by awp2513_ on 2011-01-25
Hi,

My goal is to prevent gnome from mounting and opening up a file browser when any device is plugged in (USB, CD/DVD) for a Desktop User account. I am using Ubuntu 10.04 Netbook Remix

I modified several settings in Nautilus (Edit --> Preferences --> Media (tab). I Selected "Never prompt or start programs on media insertion" and unchecked "Browse media when inserted".

I restarted the system, but when I plug in a USB mass storage device the file browser window still appears and the device is mounted.

I dug down into gconf and found the following registry keys that I believe are of interest:

/apps/nautilus/preferences/media_automount                  (unchecked)
/apps/nautilus/preferences/media_automount_open         (unchecked)
/apps/nautilus/preferences/media_autorun_never             (checked)

Has anybody run into this problem and found a solution? Modifying the keys I mentioned above worked for everyone else that has asked the "disable automounting" question (that I've found). Some very old posts mentioned gnome-volume-manager, but it is not installed on my system.

EDIT:

This seems to only happen when the Netbook Launcher is started. If Netbook Launcher is removed from the list of startup programs and the system is restarted, I can insert devices without getting a pop-up window and without the device being mounted.



Any suggestions or sources of information would be appreciated.

Thanks

---

### Post by Krytarik on 2011-01-26
I did a not so short web search on that matter. In fact, you want to disable the "autorun" feature, but have the drive mounted automatically, right?! Unfortunately I didn't find a solution. Try searching for the right keywords, maybe you'll have more luck then, when you search even harder.

---

### Post by ka0s_nz on 2011-02-26
I'm having the same problem, but with DVDs (/dev/sr0). I have made all the same preference changes as above, but DVDs continue to automount when inserted into the drive.

---

