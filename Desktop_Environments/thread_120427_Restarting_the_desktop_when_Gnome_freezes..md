---
title: "Restarting the desktop when Gnome freezes."
date: 2006-01-21
forum: Desktop Environments
---

### Post by Bubbles on 2006-01-21
My understanding is if the Gnome desktop freezes up one can press ctrl-alt-backspace to restart the GUI.  However, all this does for me is shut off my monitor (no video input) and nothing else.  I tried typing in "startx" thinking perhaps a terminal shell was opened but not visible.  No Luck.

The same happens if I press ctrl-alt-F1 to get a terminal.  My monitor shuts off stating "no video input".  Pushing the reset button on my case to reboot is the only viable option.

I know Linux is still running okay because this once happened while downloading a large-ish flie.  My ADSL modem download LED was still flashing away, so I let it finish, rebooted the machine, and sure enough the file had downloaded okay.  

My hardware is:  AthlonXP 3200+, 1 gig DDR400 dual channel RAM, nForce2 chipset, ATI Radeon X800, 8.20.8 drivers, NEC LCD w/ DVI input.

---

### Post by Pragmatist on 2006-02-03
I was having a similar problem.  Can you make it freeze?  If not, how often does it freeze?  Have you tried:
1. start Ubuntu normally
2. switch consoles (CTRL-ALT-Fn  where n is 2, 3, 4, 5, or 6)
3. type: /etc/init.d/gdm stop
4. type: startx

Does the freeze happen in this environment?  The other things you might want to try are to ssh into your machine from another machine and when the crash occurs you can analyze what is going on with the othe box.  Also, does the problem occur when you use a live CD like Ubuntu's or Knoppix or even some other distro??

---

