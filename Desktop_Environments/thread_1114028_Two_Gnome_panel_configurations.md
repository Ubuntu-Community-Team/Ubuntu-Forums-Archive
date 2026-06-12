---
title: "Two Gnome panel configurations"
date: 2009-04-02
forum: Desktop Environments
---

### Post by Cyc. on 2009-04-02
I'm relatively new to ubuntu but I've managed to get it all set up how I like. I'm running Ubuntu 8.10 on a laptop. Usually I have a second monitor plugged in. Which is what is causing my problem. I have configured it so I have 4 panels two on each monitor, however if I boot into Ubuntu without the second monitor plugged in the panels aren't responsive at all. I end up having two at the bottom and the ones at the top which are usually auto-hide wont display at all.

What I would like to do is have it so when I boot up I can have two configurations one for single monitor with 2 panels and one for dual with 4. Any help would be greatly appreciated.

Thanks,
Cyc

---

### Post by Sam Lars on 2009-04-03
I don't use the Gnome panel, but I've been looking at similar things switching between one and two monitors.
Does the panel use entries in Gconf to control that sort of thing?  If it does, you can set those values from the command line, maybe in a script based on your monitor config.  When I get back to Linux I may check more on this.

---

### Post by Cyc. on 2009-04-04
From exploring as far as I can tell the file in home/.gconf/apps/panel/general has a toplevel_id_list which seems to store the names of all the panels in. If anyone could confirm this, it would be very helpful.

So if I were to write a script that changed this file, to remove two of the panels in the list and another to re enter the two panels. How would I load this script before logging in or booting up Ubuntu?

---

### Post by Sam Lars on 2009-04-04
In your Preferences main menu, it will be Sessions or Startup Applications.  You can add scripts to run when you log in.

---

### Post by Cyc. on 2009-04-04
Ok will try and read more about sessions tomorrow and look into writing a script, thanks for your help Sam.

---

### Post by Tekmoor on 2009-11-07
Hi Cyc. I'm wondering if you ever got this script working? I am using dual monitors and I'd like the second monitor to hide it's panel when I'm only using one monitor.

---

### Post by Cyc. on 2009-11-08
No sorry I didn't manage to.

---

