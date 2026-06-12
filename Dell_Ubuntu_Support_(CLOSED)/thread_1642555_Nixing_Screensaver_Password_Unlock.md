---
title: "Nixing Screensaver Password Unlock"
date: 2010-12-10
forum: Dell Ubuntu Support (CLOSED)
---

### Post by WilhelmGGW on 2010-12-10
Recently I installed the 10.10 Netbook Remix on my Dell Mini 9. Works GREAT in every way, except..

I can't figure out how to eliminate having to re-enter my password every time the screen saver engages.  I've looked and looked for how to do it on this version, and I can't find it.

Can someone help me?  Thanks so much.

---

### Post by fjgaude on 2010-12-10
Well, it's easy if you have Configuration Editor in the Applications/Systems Tools menu: click desktop/gnome/lockdown then click on the disable_lock_screen. That's it. I'm sure you can do the same if dconf.

Let us know how it goes.

---

### Post by WilhelmGGW on 2010-12-10
> **fjgaude said:**
> Well, it's easy if you have Configuration Editor in the Applications/Systems Tools menu

That's the problem. The netbook remix doesn't have a menu bar with System Tools in it.  And no Configuration Editor anywhere to be found.  I have used Ubuntu desktop for years.  I know what you're talking about there.  Just how do I do a similar thing on the abbreviated netbook remix?

---

### Post by fjgaude on 2010-12-10
> **WilhelmGGW said:**
> That's the problem. The netbook remix doesn't have a menu bar with System Tools in it.  And no Configuration Editor anywhere to be found.  I have used Ubuntu desktop for years.  I know what you're talking about there.  Just how do I do a similar thing on the abbreviated netbook remix?

Well, I used Remix for a few days then dropped it for the classic gnome desktop. If I remember, go to terminal, use sudo apt-get install gconf. Then you will have to find where it has been placed. You might have to use terminal to run it. You might can install Configuration Editor if you can find its name then it will show in your System Tools or System block. Okay, here's its name: **gconf-editor**... so you have it now. Go for it.

Let us know how you do.

---

### Post by WilhelmGGW on 2010-12-10
For posterity, here's how I did it -- *all in the GUI!*

Applications > System > Main Menu > System Tools > check Configuration Editor to activate > close window to save > reboot

Applications > System > Configuration Editor > desktop/gnome/lockdown > check disable_lock_screen > close window > reboot

Issue solved.

---

### Post by fjgaude on 2010-12-10
Very good... I forgot the "main menu" was even there!

Anyway, issue is fixed.

---

