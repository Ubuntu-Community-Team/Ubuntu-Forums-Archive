---
title: "help me to know"
date: 2009-06-23
forum: General Help
---

### Post by linkasingh on 2009-06-23
hi everyone
i have installed ubuntu using wubi i like ubuntu and want to install it on entire hard drive and want to remove vista.

i have two drives C: where windows has been installed and D: where all my data is located.

so tell me should i have to backup all of data which is in D: drive.

thanks

---

### Post by synapsys on 2009-06-23
You should always back up your data before messing with hard drive partitions or installing operating systems....just in case.... That being said, since you have a C: and D: drive then you already have two partitions on your hard drive. You could install Ubuntu over the first partition (C:) and leave D: untouched.

---

### Post by anystupidname on 2009-06-23
I would assume "D:" is a partition/volume and not a drive. Either way, when you install Ubuntu it will not lose your D: partition/disk unless you specifically tell the installer to overwrite it. Once you've installed Ubuntu and booted it, it should automatically mount your NTFS Vista D: partition which will make the data on it available to you. It should be mounted as /dev/sda2 or /dev/sda3 depending on which partition becomes the swap partition and whether D: is a partition or disk. Obviously, the most prudent course of action is to backup the contents of the D: partition as $#1t DOES happen. Welcome to the family :)

---

### Post by blueridgedog on 2009-06-23
You could disconnect "D" if you are really worried.  Install Ubuntu then reconnect it when you are finished.  You wont impact "D" unless you tell the installation to install there or manually adjust the partitions.

As an aside, you should have a backup of your data period (I keep two...yes I am paranoid, but I have a great deal of data from years of projects and email back to 1994).

---

### Post by RJ12 on 2009-06-23
With you using Wubi its not possible.(what Ive heard) What Wubi does is creates a virtual disk inside Windows and fakes Ubuntu into thinking its real. So if you want to use up all of your disk like I did you need to burn the iso you downloaded from the Ubuntu site pop it in your CD drive. Close any windows that pop up then restart the computer. Make sure you have your bios set to boot from CD first. You may not have to do that but chances you will. If it boots into vista when you restart then change the Bios settings then save and change then either click Try Ubuntu without making changes (may not have the without making changes) this is too test if your hardware is compatible see if you can get internet to work. If you know this all works just click Install Ubuntu then it will pull up the installation follow the instructions from there and when you want to take up the full disk choose Guided-Use entire disk. After it completes it will ask you to reboot. Choose to do so and viola you have your Ubuntu install waiting at the login window

Glad to see you moving to Ubuntu

---

### Post by 3rdalbum on 2009-06-23
@RJ12: Read the original post more carefully.

I'd advise to disconnect the 2nd hard disk (the one that Windows calls "D:"). That way, you can't even ACCIDENTALLY erase the wrong hard disk :-)

Turn the power off and open your computer, the second hard disk will have either a ribbon-style cable for the data, or a small red-coloured cable for the data. There will also be another cable there for the power - either a big plug with four wires coming off it, or a small thin plug with lots of pins. Pull out the power cable and you're all set.

---

