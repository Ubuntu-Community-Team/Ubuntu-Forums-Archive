---
title: "Please help, lost my desktop"
date: 2011-11-01
forum: Desktop Environments
---

### Post by niranjan_rao on 2011-11-01
I have this machine at least for last 6 months and its relatively new machine. I had 11.04 working perfectly fine and 11.10 with some minor issues. Since yesterday I started noticing some weired problems in desktop after the update. Decided to reboot and dont get get my desktop back at all.

I decided to do a fresh install and live cd boots fine and shows me the desktop and ui in general as expected. However when I boot from hard disk, I dont get graphics environment at all.

I can login from terminal prompt and can ssh to the box. So it seems to be working normally apart from window manager part.

Tried irc, a kind person - holstein walked me thru basic triage, but gave up finally.

Can provide any details, log files if required. 

please help.

---

### Post by typhoon_tip on 2011-11-01
Have you tried to login into Unity 2D ? Sounds like a video card problem to me.

When you login, click the "gear" icon, and pick "Ubuntu 2D". See if the desktop is back.

---

### Post by niranjan_rao on 2011-11-01
That is the problem - no login screen - no GUI at all.

---

### Post by typhoon_tip on 2011-11-02
> **niranjan_rao said:**
> That is the problem - no login screen - no GUI at all.

Where exactly it freezes at ? At the Ubuntu-with-dots splash or at blank slightly purple screen ?

---

### Post by typhoon_tip on 2011-11-02
Anyway, either of the above may mean video card issue, useless check. Try this:

- Boot the computer
- Immediately after the BIOS screen, press shift and keep it pressed
- A grub boot menu should come up
- Choose start in recovery mode of your top "latest" kernel version
- If you can reach a menu, then pick reconfigure graphics
- Set back the default configuration or failsafe configuration
- See if it starts

---

