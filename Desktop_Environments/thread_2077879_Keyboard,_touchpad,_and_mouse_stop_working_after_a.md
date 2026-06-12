---
title: "Keyboard, touchpad, and mouse stop working after a random amount of time"
date: 2012-10-29
forum: Desktop Environments
---

### Post by skylen on 2012-10-29
Hi,
I installed Xubuntu 12.10 amd64 on my MacBook Pro 5,2.  Formerly I've been running (and still retained, fortunately), Ubuntu 12.04 LTS amd64 on my other partition.

The install process went smoothly with the usual Ubuntu-on-MacBook noted quirks like needing 'nomodeset' added to GRUB boot commands.

However, after booting to the Xubuntu desktop WHICH IS SWEET and using it for a few minutes, my keyboard and mouse stopped responding.  I could not switch to another VT with Ctrl-Alt-F1, and could not get any other response.  My USB mouse, the laptop keyboard, and the laptop trackpad all stopped responding.

I ssh'd in from another machine and I see that the system is still working fine, and in fact I can start X programs on the laptop remotly by doing something like "DISPLAY=:0 xev" and I see the program window on the laptop screen.

I've tried both nvidia-current and nvidia-experimental drivers, but had lockups with both.  Sometimes it locks up immediately when the lightdm login screen is shown at boot, I just get the blinking cursor in the password field, but can't do anything.  Other times I can log in and use it for a while.

I also tried booting in text mode by editing the GRUB command line's "quiet splash" part with "text" and the running "startx" after logging in to the text console.  As before, I could use it for 20 minutes or so, then it locked up.

No pattern so far as to when it locks up, I haven't run any particular programs, and as I said before it even happened on the lightdm login screen.

The Xorg.0.log file and other log files don't provide any insight that I can see -- *nothing* was logged at the moment when the keyboard/mouse input stopped working.

How can I debug the cause of this?

Thanks for any help.

---

