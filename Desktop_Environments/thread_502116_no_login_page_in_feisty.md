---
title: "no login page in feisty"
date: 2007-07-16
forum: Desktop Environments
---

### Post by williemerwe on 2007-07-16
Hi,

I have Ubuntu 7.04 installed.  At first, it didn't detect the correct screen resolution, so found a workaround for that.  Now, I want to use VNC to access the device, which is not that difficult to get up and running.  Works great.  Problem is that I want to be able to reboot the server remotely with VNC and be able to log into it again after booting with VNC - no Ubuntu login.  While playing with settings to tell Ubuntu not to give the login screen, I must've done something wrong somewhere...  Now, when I boot the server, I only get a black screen with the little busy-icon, no login screen appears.

I installed SSH before I caused this issue, so can still access the server's CLI.

Any suggestions?

---

### Post by williemerwe on 2007-07-16
Some further info:
When I press Ctrl + Alt + F1, I get to the TTY and can work from there (in addition to being able to SSH into it).
I tried # /etc/init.d/gdm restart and it restarts the Gnome, but goes back to the same black screen.
It seems like both the keyboard & mouse works, but it hangs.

Please, any help will be appreciated

---

### Post by princemanjee on 2007-07-16
Ok so i was screwing around just looking and trying to tweak the look and feel and I stumbled across this login selection screen and i selected something other than the default and now i cant get into X... is there a way i can log in from TTY and select a differant session manually or?   where is the file i edit that gets me back to the way things were??    new to linux so dont know the flie system or the location of all the config files yet...

---

### Post by williemerwe on 2007-07-17
princemanjee,

Same thing as what happened to me.  These damn fingers.....
I really need this PC up and running, so couldn't wait any longer - I formatted and reinstalled Feisty :(, but all's good again now.

---

