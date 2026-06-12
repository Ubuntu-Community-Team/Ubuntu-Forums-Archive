---
title: "Network scanner using saned: libusb permission problems"
date: 2006-07-25
forum: Desktop Environments
---

### Post by kikinovak on 2006-07-25
Hi,

I'm just sinking my teeth into setting up a scanner for use in a LAN. I've read the various docs, HOWTO's and FAQ's on sane-project.org, but I have one small problem that I can't seem to solve. (So far, the scanner works OK locally on the server machine...). I've installed sane as well as sane-utils.

# scanimage -L (as root) gives the following output:

root@bertha:/etc# scanimage -L
device `epson:libusb:001:003' is a Epson Perfection610 flatbed scanner

(Yes, I've reactivated the root account... I'm an ex-Slacker, and I'm accustomed to different security policies :-D )

But the following doesn't work, so it's obviously a permission problem:

# su -s /bin/sh - saned
$ scanimage -L

I've been 100% GNU/Linux for something like five years, so I know the ins and outs of devfs as well as udev. With devfs, you could easily make a chmod something /dev/scanner0. With udev, it was just a matter of setting permission in /etc/udev/rules.d/udev.rules. 

But this is libusb, meaning my device file is (according to the output of scanimage -L as root) /proc/bus/usb/001/003. Let's see:

root@bertha:/etc# ls -l /proc/bus/usb/001/003
-rw-r--r-- 1 root root 50 2006-07-25 07:26 /proc/bus/usb/001/003

**Now the question: how can I change permissions of that device file in a persistent way?** I vaguely know something about hotplug, but never really sunk my teeth into that. In other words: what script sets permissions on that device file? Doing it with a simple chown saned:saned won't get me far, as my changes will be lost either upon reboot, or upon replugging the scanner. I know the quick and dirty way would be to write a local script to re-chown on boot time, but I like doing things properly.

Any suggestion for that would be greatly appreciated.

---

### Post by simonn on 2006-07-25
Weird.

Do you have /etc/udev/rules.d/45-libsane.rules?

Your scanner is listed in the copy on my system (and I have not made any modifications to it).

This should set the the group of the device to scanner. You just need to make all users you want to give permission to use the scanner members of the scanner group

---

### Post by kikinovak on 2006-07-25
I ended up finding that file, among the usual suspects. Permissions are set indeed for root:scanner... but saned needs root:saned permissions. There you go. So I fixed that.

One step beyond: trying to get my remote host to connect to saned... and wondering why he won't.

Cheers,

Niki

---

### Post by Coburn on 2006-11-20
This is a discussion between experienced users about something I need to know.  I am a gnubie (<1yr on Linux).

I'm using an Epson CX5000.  I duplicated and tweaked a line in the rules file to add my product and device ID's, but obviously there is something I'm missing here.  What's all that about permissions?

I can find the scanner as root, but not as me.  Need some clarification here.

Thanx

---

### Post by Coburn on 2006-11-24
Update:  got the scanner running.  It was a matter of going into Device Manager, looking at the list, and then changing the permissions on the basic /dev device and on the more scary looking one: /sys/devices/pci0000:00/0000:00:07.2/usb1/1-1/1-1:1.1.

---

