---
title: "[SOLVED] Mouse clicks useless in fluxbox"
date: 2008-01-02
forum: Desktop Environments
---

### Post by GandalfNK on 2008-01-02
Hi,

after months of using fluxbox without any problems at all, it has just started behaving rather strangely: Wherever I click, whether it's in the fluxbox menu or in some application, mouse (and touchpad) clicks always seem to be interpreted as being directed at the desktop, e.g. when I right-click on something in Firefox or Thunderbird the fluxbox desktop menu opens in that place, on top of the application. Similarly, left-clicking on anything at all has no effect except for closing the fluxbox menu when that is open.

I can still use all my applications and control them via the keyboard, but that's quite inconvenient - especially web surfing just isn't much fun without being able to use the mouse.

The whole mess seems to have started when I defined a couple of harmless new hotkeys in fluxkeys and then used Reconfigure in the fluxbox menu.

I have restarted X and rebooted the computer several times to no avail and am now using a rather under-configured installation of Xfce that at least allows me to use my precious touchpad.

Does anyone have any helpful thoughts on my problem and on how I might be able to solve it?

---

### Post by urukrama on 2008-01-02
You probably changed something in your keys file (in ~/.fluxbox/keys). If you haven't set up a lot of custom keys, you could easily remove that file and copy the default key configuration file into ~/.fluxbox

The default file is either in /usr/share/fluxbox/keys or /usr/local/share/fluxbox/keys

What 'harmless' keys did you add?

---

### Post by GandalfNK on 2008-01-02
Ah, you were right, there was something wrong with my ~/.fluxbox/keys file. When comparing it to the default file (which solved my problem), I noticed that somehow in those lines meant to govern the reaction to clicks on the desktop, the "OnDesktop" had been replaced by "none", apparently making the opening/closing of the desktop menu the standard reaction to mouse-clicks anywhere.

I have corrected this in my own, heavily modified keys file and now everything's working just fine :)

Thanks for your help urukrama!

---

### Post by urukrama on 2008-01-02
You're welcome. 

You can mark your thread 'Solved' in the 'Thread tools' menu (just above the first post on the right). Your thread title will then have [SOLVED] in front of it.

---

### Post by cknight on 2008-01-03
Most likely you used Fluxkeys to modify your keys file via a graphical user interface.  This program will corrupt your keys file in several ways including the mouse clicks.  In the future limit your keys file editing to text editors as no valid GUI editor exists for fluxbox at the moment which won't corrupt your keys file.

---

