---
title: "laptop not booting into gnome but CLI"
date: 2009-04-14
forum: Desktop Environments
---

### Post by afbase on 2009-04-14
I'm running Intrepid Ibex and normally my computer will boot directly to gnome.  This morning I can no longer do that.  The boot process seems to go through every step without a hitch and suddenly it boots to command line instead of giving me the standard GUI login before going into GNOME. 

I recently changed the login screen to a custom login screen found on the gnome's artwork page.  But it hasn't been a problem.  I'm wondering if that is the issue, but I have my doubts since I haven't had an issue with the custom login screen.  

Once in CLI, I try to open gnome:

```
sudo gdm
```It returns that it is already running, so I:

```
ps -aux
```That returns that the process is running by user root.  

Any ideas? 

Thanks.

---

### Post by p_quarles on 2009-04-14
> **afbase said:**
> I'm running Intrepid Ibex and normally my computer will boot directly to gnome.  This morning I can no longer do that.  The boot process seems to go through every step without a hitch and suddenly it boots to command line instead of giving me the standard GUI login before going into GNOME. 

I recently changed the login screen to a custom login screen found on the gnome's artwork page.  But it hasn't been a problem.  I'm wondering if that is the issue, but I have my doubts since I haven't had an issue with the custom login screen.  

Once in CLI, I try to open gnome:

```
sudo gdm
```

It returns that it is already running, so I:

```
ps -aux
```

That returns that the process is running by user root.  

Any ideas? 

Thanks.

The new login theme may or may not be the problem, but we can find out by replacing the display manager (this isn't a big deal, and it's easy to undo):
```
sudo apt-get install kdm
```
When prompted, choose to make kdm the default display manager. Then:
```
sudo /etc/init.d/kdm start
```
If this starts up the graphical environment successfully, you can then go into the Gnome tool for changing the login screen and revert it to its old settings. Then you can change back to gdm by running:
```
sudo dpkg-reconfigure gdm
```
and selecting gdm as the default this time.

If that doesn't work, please post any error messages you received after running the command to start kdm.

---

### Post by afbase on 2009-04-14
> **p_quarles said:**
> The new login theme may or may not be the problem, but we can find out by replacing the display manager (this isn't a big deal, and it's easy to undo):
```
sudo apt-get install kdm
```When prompted, choose to make kdm the default display manager. Then:
```
sudo /etc/init.d/kdm start
```If this starts up the graphical environment successfully, you can then go into the Gnome tool for changing the login screen and revert it to its old settings. Then you can change back to gdm by running:
```
sudo dpkg-reconfigure gdm
```and selecting gdm as the default this time.

If that doesn't work, please post any error messages you received after running the command to start kdm.

I had forgotten that I had  to reset my resolution in my last session last night in GNOME by:
```
gksudo displayconfig-gtk
```

It seems that GNOME didn't like that when I booted my computer this morning.  I fixed it by going into the recovery mode and resetting the resolution by going to System>Preferences>Screen Resolution on the Gnome Toolbar

Everything seems to be working fine now. Thanks.

I did try your method, however I found out quite fast that my wireless connection was not working when Ubuntu booted to CLI and I was too lazy to move my laptop near my router at that time.

---

