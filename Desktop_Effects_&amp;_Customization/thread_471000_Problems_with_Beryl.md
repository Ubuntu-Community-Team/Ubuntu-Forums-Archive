---
title: "Problems with Beryl"
date: 2007-06-11
forum: Desktop Effects &amp; Customization
---

### Post by RelativelyQuantum on 2007-06-11
Hi all.

I recently downloaded Beryl after hearing some interesting things about it, but can't for the life of me get it to work, e.g., do *anything*. Are there any dependencies I don't have installed? Let me give a bit of background info; I installed Edgy onto my Sony Vaio, then upgraded to Feisty when it was released. I installed Beryl and its configuration manager (not the simplified one, the standard). When I attempted to enable the desktop effects, NOTHING HAPPENED. Well, nothing besides the fact that my built-in desktop effects were disabled.

In other words, HOW DO YOU USE BERYL?! Any recommendations would be appreciated.

---

### Post by Lord_Alda on 2007-06-11
Do you even have a graphics card?

---

### Post by RelativelyQuantum on 2007-06-11
I know I do, as there were certain things I needed it for in Suse. I'm just not sure what type it is.

Is there any way to find out through Ubuntu?

---

### Post by kajunogueira on 2007-06-11
Hi..
I installed the Ubuntu 7.04 and the Beryl-emerald, but my windows of the Ubuntu had been without that bar that has the button to close and to maximize. I searched and I found some solutions. To make download of themes and to install in the Beryl, but my Beryl-manager does not have the options to install new themes. How I can fix this problem?

---

### Post by RelativelyQuantum on 2007-06-11
How did you download Beryl again?

---

### Post by bobodwaisman on 2007-06-12
I am having problems with beryl too. I found a code for an intel graphics chipset 945. It is as follows:

Code Sample:

sudo apt-get install xserver-xorg-video-intel
sudo dpkg-reconfigure -phigh xserver-xorg
sudo /etc/init.d/gdm restart

Even though, I have done this installation. When I tested beryl, whichever icon the cursor points to gets fuzzy and unreadable. The taskbar below disappears too.

---

