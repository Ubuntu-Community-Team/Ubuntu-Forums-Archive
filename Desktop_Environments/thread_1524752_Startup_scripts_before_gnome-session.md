---
title: "Startup scripts before gnome-session"
date: 2010-07-05
forum: Desktop Environments
---

### Post by liquidsunshine@gmail.com on 2010-07-05
I'm trying to set up a system to synchronize files between two computers (I'll call them client and server).  I'd like to have the client synchronize with the server after logging in but before starting the *gnome-session* (to prevent conflicts in gconf files and such).  My synchronization script is a wrapper for *Unison*, and I have that working fairly well already.  

I've explored the option of using an *Xsession*/*Xinitrc* script instead of using the Gnome option from GDM, but I like having the ability to shut down/suspend/hibernate from within the gnome-session and none of that works with the *Xsession* approach.

I've tried setting up a */etc/gdm/PreSession* script to accomplish this, but *PreSession* does not block the gnome-session from starting, so my synchronization script does not finish before *gnome-session* starts.

Does anyone have any advice on how to run and finish a script after logon (so my files are decrypted and able to be used) but before *gnome-session* starts (to avoid synchronization conflicts)?

---

