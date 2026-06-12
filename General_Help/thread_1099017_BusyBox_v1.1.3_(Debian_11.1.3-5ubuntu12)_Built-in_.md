---
title: "BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu12) Built-in shell (ash)"
date: 2009-03-17
forum: General Help
---

### Post by urymics on 2009-03-17
Hello, first of all forgive me for posting this topic( I've seen quite a few of the same problems)
but even with so many of the same problems, i cannot seem to find a solution.

I have been running Ubuntu 8.04 for about...3-4 weeks perfectly...and i Loved every minute of it. but today after school I boot up my laptop and see this [COLOR="Red"]BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu12) Built-in shell (ash)[/COLOR] I have no idea what to do...

All the threads I've seen about this is from people that ran ubuntu from a live CD. I installed ubuntu from Wubi via Windows XP Pro. I have not tried to modify anything on the Linux folders...or anything that could have caused this.

Another suggestion about this probelm was that the installation had gone wrong...but I have been using Ubuntu for a couple of weeks just fine. 

One other suggestion was mutliple drives. I only have one a 100gb Hard drive.  Any help will be greatly appriciated.

P.S forgive any typos that i might have. typing this on IE and I have a 10 page paper due tomorrow that i should be working on...(kind of in hurry to spell check...sry)

---

### Post by urymics on 2009-03-18
Anyone??

---

### Post by geirha on 2009-03-18
When the kernel starts loading, it first loads a tiny linux system into memory. That tiny linux system's job is to detect some of the hardware and load the proper modules (drivers) for it so that it can continue to the next stage of the boot. One thing is that it needs to load the correct driver for the harddrive controller so that it can find and mount the / filesystem. If this early stage fails, you'll be sent to a shell in this tiny linux system, which is what you are getting. It's mostly useful for the developers and experienced users, which actually knows what to do in that shell.

Anyway, try typing "exit" in the shell. This should make it retry the stuff that it failed at, and will probably fail again, but hopefully it will print a useful error message, and if it does, post it here.

One possibility is that the filesystem the ubuntu virtual harddrive is located on is corrupted somehow. Try running a filesystem check in Windows and see if that helps.

There's also a way to mount your ubuntu filesystem(s) from windows. That will allow you to retrieve the documents and finish them in Windows. [https://wiki.ubuntu.com/WubiGuide#How can I access the Wubi files from Windows?](https://wiki.ubuntu.com/WubiGuide#How can I access the Wubi files from Windows?)

---

### Post by jmszr on 2009-03-18
urymics,
       This worked for me when I used Wubi:                                           Boot into Windows, Goto "My Computer", Right click the drive that you have installed Ubuntu in.Click Properties.
Select the "Tools" tab and click "check now" under error checking (On Vista, You might be asked for administrative rights). Make Sure "Automatically fix file system errors" is checked and click Start. After The checking is done, restart the pc by using the start menu(Do Not hard reboot) and try using ubuntu now.

---

### Post by LowSky on 2009-03-18
This is why I hate WUBI, its garbage IMHO!!!!

JMSZR idea might work but I suspect why for another reason.

Wubi installs Ubuntu into a windows folder usually a NTFS type of file system. this file system has a known reaction of being unstable in other operating systems like Ubuntu.. becaus people sometime fail to unmount the drive correctly, heck even Windows can be blamed for this.

Just boot into windows, then shutdown correctly and then try to boot into ubuntu as normal, everything should work

---

### Post by jmszr on 2009-03-18
LowSky,
        When I was using Wubi this error would occur to people fairly often. Sometimes> Just boot into windows, then shutdown correctly and then try to boot into ubuntu as normal, everything should workwould do the job,sometimes not. The suggestion I gave was intended to hit two birds with one stone (so to speak). Unless,of course,it was something else (entirely possible with Wubi). I think the concept of Wubi is a worthy one - the problem is you have to run it in Windows (talk about casting pearls before swine).

---

