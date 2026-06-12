---
title: "Desktop problems after Natty Narwhal upgrade"
date: 2011-05-07
forum: Desktop Environments
---

### Post by techkid on 2011-05-07
Hi all.

I'm having trouble with my Ubuntu installation after upgrading to version 11.04 (Natty Narwhal). It boots fine, both to Ubuntu and Windows, but when I reach the desktop in Ubuntu, it doesn't seem to respond to anything. No mouse clicks, no keyboard commands, except Ctrl+Alt+Delete.

When I reinstalled Ubuntu 11.04 after the upgrade, it started up fine to the Gnome desktop. So I thought things had worked out, and updated the video drivers. Then, when it restarted, the problems came back.

Does anyone have any advice on what to do from here? Should I go back to 10.10? Thank you in advanced.

---

### Post by techkid on 2011-05-08
Hope I haven't stumped people...

---

### Post by sikander3786 on 2011-05-08
If your computer stops responding to keyboard and mouse, there is not much we can do right away sadly.

So the problem started again after installation of graphics drivers. Which graphics card is there and which version of drivers is installed?

Later when we get your mouse/keyboard working, this link might help you.

[http://ubuntu4beginners.blogspot.com/2011/04/missing-top-and-side-panels-in-unity.html](http://ubuntu4beginners.blogspot.com/2011/04/missing-top-and-side-panels-in-unity.html)

Before that, we need you to press and hold down <Shift> key right from your Bios screen until you see the Grub menu. Highlighting the first entry, press 'e' to edit it. At the end of line with 'quiet splash', type 'acpi=off' (without quotes). Press Ctrl + X to continue boot. Is the keyboard and mouse responsive now?

---

### Post by techkid on 2011-05-12
Thanks for the advice. I printed it out (so not to bugger it up) and edited GRUB as you posted, but nevertheless it does the same thing.

The graphics card I have is nVidia GeForce 7300 LE 128MB. I can't tell specifically the driver version, but when I did the reinstall, it did say it was the latest version.

I hope this helps.

---

### Post by sikander3786 on 2011-05-12
Try 'noapic' instead of acpi=off as mentioned in the above post. Or press Esc at the hanged up screen? Does it show some text? Can you reproduce it here?

---

### Post by Krytarik on 2011-05-12
Your card is one of those blacklisted for at least Unity, so there are some known issues with those and the proprietary driver:
[https://bugs.launchpad.net/ubuntu/+source/nux/+bug/728745](https://bugs.launchpad.net/ubuntu/+source/nux/+bug/728745)

So try the "nouveau 3D" driver instead, quite a lot of users with various Nvidia cards/chips seem to have success with those.

When you are at the login screen:
- press Ctrl+Alt+F1 to switch to a console
- log in there
- follow these instructions to install/enable the "experimental" driver, which should be listed there:
[http://blog.danfego.net/2009/11/fixing-nvidia-driver-issues-on-ubuntu-karmic/](http://blog.danfego.net/2009/11/fixing-nvidia-driver-issues-on-ubuntu-karmic/)
- reboot by pressing Ctrl+Alt+Del

Greetings.

---

### Post by techkid on 2011-05-13
Well, I didn't have experimental drivers available to me to use, but I did end up getting Ubuntu to work using the previous version drivers. I am finally able to log in to and experience the Unity desktop.

Thank you all for your help.

---

