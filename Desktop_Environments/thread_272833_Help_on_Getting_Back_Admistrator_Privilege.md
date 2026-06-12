---
title: "Help on Getting Back Admistrator Privilege"
date: 2006-10-07
forum: Desktop Environments
---

### Post by vc8 on 2006-10-07
Hello,

I got everything working, but I accidentally uncheck under users and group's properties, administrator privelege, how do I get it back. I can't install anything or do anything that relates to administrative task.  Pls. help.](*,)

---

### Post by codejunkie on 2006-10-07
reboot your computer and at the grub menu choose (recovery mode) this will take you into a terminal only mode with full root privileges kinda like dos now enter ```
adduser yourusername admin
``` and reboot your computer by pressing ctrl+alt+delete this should give you back your admin privliges hope this helps.

---

### Post by aysiu on 2006-10-07
codejunkie's right on.

Full instructions here:
[http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo)

---

### Post by vc8 on 2006-10-07
I tried doing what codejunkie says and asked for my root pwd and says login incorrect.

---

### Post by aysiu on 2006-10-07
Recovery mode shouldn't ask you for a root password unless you'd previously enabled a root password.

Well, too late now.

Do you have a live CD?

---

### Post by vc8 on 2006-10-07
Yes, I have a live cd.  This password thing happened to me the first time I installed ubuntu, I thought there's something wrong with my keyboard.  I did enabled root pwd.  For some reasons, when I type in my pwd it says incorrect.  Is that has something to do with windows since I have it install on another drive?

---

### Post by aysiu on 2006-10-07
If you don't enable a root password, you can reboot into recovery mode and be root immediately.

If you do enable a root password, when you reboot into recovery mode, you'll be prompted for your root password.

If you don't remember your root password, boot the live CD, mount your Ubuntu partition, and hand-edit the /etc/group file.

Do you need help mounting your Ubuntu partition?

---

### Post by vc8 on 2006-10-07
Yes, pls. I do need help mounting.  Pls. bear with me I'm a newb, and tnx for the help I really appreciate it.

---

### Post by aysiu on 2006-10-07
Okay. Mounting in Ubuntu is a little involved (unlike Mepis and Knoppix, which have a single-click working mount--if you have a Mepis or Knoppix CD, use that instead of Ubuntu, for sure).

Boot up the live CD.

Open a [terminal](http://www.psychocats.net/ubuntu/terminal).

In the terminal, paste this command in ```
sudo fdisk -l
``` That last letter is a lowercase *L*, not the number *one* or an uppercase *i*.

Depending on how complicated your partition layout is, you should see what location your Ubuntu partition is. Let's say, for the sake of this example, it's /dev/hda1

Make a mount point: ```
sudo mkdir /media/recovery
``` Mount your partition: ```
sudo mount -t ext3 /dev/hda1 /media/recovery
``` Open Nautilus as root ```
gksudo nautilus
``` Browse to /media/recovery/etc

Before editing the *group* file, make a backup copy first.

Then, in the *group* file, add your username to the *admin* section.

Reboot, and you should be back in the *admin* group.

---

### Post by vc8 on 2006-10-07
ok, I'll give it a try I'll let you know how it'll go, thanks.

---

