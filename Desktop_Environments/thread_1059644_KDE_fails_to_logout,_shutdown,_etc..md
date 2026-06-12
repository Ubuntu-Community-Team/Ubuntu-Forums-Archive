---
title: "KDE fails to logout, shutdown, etc."
date: 2009-02-04
forum: Desktop Environments
---

### Post by Gotaro on 2009-02-04
I recently updated my video drivers to the latest Catalyst 9.1. Things didn't go smoothly, but I learned important things! (Like that aticonfig is just a program to help with xorg.conf editing) The hiccup I had was an error about a line "Disable dri2", which I removed in order to solve the problem and continue with "aticonfig --initial".

So now Kubuntu won't logout, restart, or shutdown successfully through the GUI.. It does the logout sequence (closes programs, chimes logout music), though at least once left Konqueror open, window decoration-less, against a blank background. Other times it's just a blank screen.  Pushing the power button at this point on my PC initiates the **real** shutdown sequence, and the Kubuntu logo appears and reverses the loading bar, like normal, and shuts off..  I can also successfully shutdown with the "sudo shutdown -r now" command, which was suggested in my previous thread.  Even with this method, it still takes significantly longer to shutdown than it used to.  Pushing the power button will [i]always[/i[ successfully shutdown.

Installing the new driver may or may not have been the cause, though messing with Compiz/Emerald and their settings is what I concluded broke KDE the last time this happened.  I didn't fix it last time; I just reinstalled Kubuntu.

Any ideas?

---

