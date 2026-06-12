---
title: "No sound in XFCE BLACKBOX or FLUX.. esd no autorun??"
date: 2005-09-28
forum: Desktop Environments
---

### Post by thewayofzen on 2005-09-28
When i login to a gnome session my sound works.  every application.. or sound for anything works flawlessly.   If i issue the following command

ps -aux | grep esd 


I get proof that esd is infact running.


The problem though is that when i login to XFCE4, Fluxbox or Blackbox i have no sound and get errors from rhythmbox and no sound at all from gaim.   If i manually initiate esd from console everything works perfectly.. what i need to know is how i can login to an xfce session and have sound JUST WORK.  I dont want to have to start it up myself..  is there a way to tell esd to run regardless of what WM im using?

PLEASE HELP!?!?

delaney/zen

---

### Post by psychicdragon on 2005-09-28
Hey,

I use Xfce myself and used to have a similar problem. I used to have a script in ~/Desktop/Autostart that would run esd whenever Xfce started up. The downside to this method is that you can end up with more than one esd process if you log out and you have to kill esd if you want to play a game or something.

The easiest way to get audio working properly is to change the gstreamer audio sink.

Run gstreamer-properties and change the output sink from esd to alsa.

If you want to change the levels run alsamixer in a terminal.

---

### Post by DeprecatedBehaviour on 2006-12-23
I realise this is a long dead thread, but it came up multiple times in my searching, so for anyone else who may be looking for an answer to this. Here is my solution (for XFCE).

I wrote a script to start the ESD daemon, as thewayofzen suggested, except I made mine only start the daemon if it wasn't running (to overcome the multiple-instance problem mentioned), then, using the XFCE Autostart manager. I have that script run when I start. Easy.

More comprehensive details (the script etc.) are here: [http://blog.everyone-here.is-a-geek.com/2006/12/23/auto-start-esd-esound-in-xfce/]("http://blog.everyone-here.is-a-geek.com/2006/12/23/auto-start-esd-esound-in-xfce/")

---

