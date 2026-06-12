---
title: "Ubuntu 16.04 locks up when display turns off"
date: 2017-05-02
forum: Desktop Environments
---

### Post by Steve_Corman on 2017-05-02
I have just set up a desktop box with Ubuntu 16.04.  It is working fine, except it locks up when the display shuts off per system settings under brightness & lock.  I researched this a little and found [this thread]("https://askubuntu.com/questions/485481/ubuntu-14-04-doesnt-wake-up-after-screen-is-locked-and-blank") that suggests editing /etc/default/grub to set 

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash usbcore.autosuspend=-1"
```

[This thread]("https://unix.stackexchange.com/questions/91027/how-to-disable-usb-autosuspend-on-kernel-3-7-10-or-above") that says the parameter you have to change on recent Ubuntu > 15.01 releases is "autosuspend_delay_ms". 

 I have tried both of these changes, each time followed by 

```
sudo update-grub
cat /sys/module/usbcore/parameters/autosuspend
```

And the value comes back as 2. 

I'm not sure why the change isn't working.  Am I doing something wrong?  I'm also wondering if maybe the usb autosuspend isn't what's causing the problem, since some other stuff I read suggested this is implemented for laptop installations where power saving is an issue.  I don't know what the "2" value that it's set to means.  Maybe it means "desktop installation" or something.

Any suggestions how to proceed?

---

### Post by Xian on 2017-05-02
Take a look at this thread -- specifically "Solution 1". 

[https://askubuntu.com/questions/772056/keyboard-stops-working-ubuntu-16-04/892783](https://askubuntu.com/questions/772056/keyboard-stops-working-ubuntu-16-04/892783)

---

### Post by Steve_Corman on 2017-05-03
That did the trick, thank you!  I don't get why this isn't an option at install, or why it's not configurable in system settings > power.  It's going to cause the same problem for anyone with a desktop install that has usb kb/mouse.

---

### Post by Steve_Corman on 2017-05-03
Alas, I spoke too soon.  It came back OK a few times, but the problem just reoccurred and I double checked that autosuspend is still -1.  So I guess it's something else.  Any idea what it could be?

---

