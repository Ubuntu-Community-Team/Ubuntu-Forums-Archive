---
title: "Agh!! I think I killed my computer!!!!"
date: 2008-01-06
forum: Dell  Ubuntu Support
---

### Post by valerie.wilhelm on 2008-01-06
When I try to log on to my computer, which runs linux/ubuntu 7.10, this is what it shows:
starting up....
loading, please wait...
kinit: name_to_dev_t(/dev/disk/by-uuid/5ef2fc7b...
= sda5 (8,5)
kinit: trying to resume from /dev/disk/by-uuid/5ef2fc7b-23be-464d-9f5...
kinit: no resume image, doing normal boot...

Ubuntu 7.10 valerie-laptop tty1

valerie-laptop login:

then I input my login info, and it tells me this:

the programs included with the ubuntu system are free software; the exact distribution terms for each program are described in the individual files in /usr/share/doc/*/copyright.

Ubuntu comes with no warranty, to the extent permitted by law.
valerie@valerie-laptop:~$

I tried sudo apt-get install ubuntu-desktop, and it told me that some of the programs could not be verified, and would I like to continue (it tells me this for EVERY program I've tried to install in this limbo-like state) and I say yes, and then it says unable to fetch files. How do I fix this???? I am somewhat of a newbie.....

---

### Post by gilf on 2008-01-06
Try booting up your LiveCD and when starting up, try the option to check the CD disk first.

I had similar problems when I tried to install a system from a bad CD.

If it passes that test, then try a memory check. I also had a laptop that would overheat and lose a memory location with similar results

If that test passes after a while, try booting normally from the LiveCD.

If you can do that, it's fairly likely Grub's menu.lst is booting you into command line mode instead of full fledged desktop mode, and you'll have to fix that.

---

### Post by xptweakerntn on 2008-01-06
The next time you boot into the terminal...
boot it, log into your name, like always. try this:
sudo /etc/init.d/gdm start
if gnome is installed, this should start it. if not, perhaps you need to edit your sources file, and install the kubuntu-desktop or ubuntu-desktop.

---

### Post by gilf on 2008-01-06
Why is the desktop missing, though?

Desktop should have been installed already, unless CD was bad. System should be reinstalled from a good CD if so.

If desktop is present, then system should have booted into it, unless Grub is bad or misconfigured.

.

---

