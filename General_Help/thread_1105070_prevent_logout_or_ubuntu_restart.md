---
title: "prevent logout or ubuntu restart"
date: 2009-03-24
forum: General Help
---

### Post by bfuzze on 2009-03-24
I lock my computer overnight and when I come in in the morning, it looks like Ubuntu has logged me out and/or restarted.  Normally it's not a problem, but I need to run an import script that takes a while and can't get Ubuntu to stay logged in.

I modified the System > Preferences > Power Management settings so that it should 'Never' go to sleep if inactive.

I also checked the BIOS power management setting and they're all turned off.

I'm not sure if it is going to 'sleep', 'hibernating', or some other setting that might be causing this.

I'm using Ubuntu 8.04 (Hardy).

Thanks

---

### Post by albandy on 2009-03-24
> **bfuzze said:**
> I lock my computer overnight and when I come in in the morning, it looks like Ubuntu has logged me out and/or restarted.  Normally it's not a problem, but I need to run an import script that takes a while and can't get Ubuntu to stay logged in.

I modified the System > Preferences > Power Management settings so that it should 'Never' go to sleep if inactive.

I also checked the BIOS power management setting and they're all turned off.

I'm not sure if it is going to 'sleep', 'hibernating', or some other setting that might be causing this.

I'm using Ubuntu 8.04 (Hardy).

Thanks

Ensure the cpu it's not overheated, my computers are working 24h without rebooting or powering off.

---

### Post by bfuzze on 2009-03-24
In my experience if a computer overheats it shuts down, but then how is it rebooting.  Unless there is an auto power-on feature.  Perhaps I should not have used the word *restarting* in my initial post.  I don't think the computer is restarting, I think it's Ubuntu that is logging me out.

---

### Post by albandy on 2009-03-24
it's a notebook?

---

### Post by kanikilu on 2009-03-24
> **bfuzze said:**
> In my experience if a computer overheats it shuts down, but then how is it rebooting.  Unless there is an auto power-on feature.  Perhaps I should not have used the word *restarting* in my initial post.  I don't think the computer is restarting, I think it's Ubuntu that is logging me out. Hmm, it kind of sounds like GDM of Xorg is crashing or closing and then auto-restarting...maybe :?:

If that's the case, have you checked your logs for any clues? There might be something useful in /var/log/Xorg.0.log, messages or syslog...

---

### Post by bfuzze on 2009-03-24
albandy: It's not a laptop.

kanikilu:  Unfortunately, I've rebooted a couple of time this morning trying to determine the problem which seems to have overwritten the logs from last night.  I guess I'll have to reproduce the problem (wait until tomorrow) to check the logs, unless there's another place it may have been reported.

---

### Post by mocoloco on 2009-03-24
Turn off your screensaver, load up on caffeine, and sit in front of the system all night. Don't even think about getting up to use the bathroom, or that's when it will happen.

Seriously though I am curious about this one.

---

### Post by albandy on 2009-03-24
first disable gdm
sudo /etc/init.d/gdm stop
then a text terminal will appear
login in it
type startx to start the graphical environment from your user
if works all night it's a gdm issue

---

### Post by bfuzze on 2009-03-26
Something mocoloco mentioned about the screensaver reminded me of a time I saw a significant system slowdown while the screensaver (4D Hypertorus, 2 monitors) was running.  

I turned the screensaver to 'blank' and locked the computer last night and ubuntu did NOT reboot or log out.  

I can't be sure that the screensaver is/was the cause of the problem, but I think it is at least related.  Possibly the combination of the import script and the screensaver over the course of a number of hours caused some sort of memory issue.  

This wasn't the first time it had occurred and I don't recall what if any apps were running in past occurences.  I'm not running any scripts tonight, so I'll turn the screensaver back on, close all apps, and lock it overnight and see if I can narrow it down.  

Thanks for the input.

---

### Post by tuberculo on 2009-03-29
I also have this problem. I was away from the computer for some hours and when I came back I was logged out. There was another user logged in the system that was not logged out. 
That is not the first time in Hardy. In Debian that never happened.

In the logs I can see this: 

daemon.log:
> Mar 28 23:39:55 principal gdm[5477]: WARNING: gdm_slave_xioerror_handler: Erro fatal no X - Reinicializando :0 
"Erro fatal no X - Reinicializando" means X fatal error - restarting.

auth.log:
> Mar 28 23:39:55 principal gdm[5477]: pam_unix(gdm:session): session closed for user ga

---

### Post by dcstar on 2009-03-29
> **bfuzze said:**
> I lock my computer overnight and when I come in in the morning, it looks like Ubuntu has logged me out and/or restarted.  Normally it's not a problem, but I need to run an import script that takes a while and can't get Ubuntu to stay logged in.
.........

And do you have your system set to automatically install all updates?

---

### Post by tuberculo on 2009-04-01
Found a related bug:
[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/152648](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/152648)

This one also affects me and I thing it is related: 
[https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/244737](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/244737)

---

