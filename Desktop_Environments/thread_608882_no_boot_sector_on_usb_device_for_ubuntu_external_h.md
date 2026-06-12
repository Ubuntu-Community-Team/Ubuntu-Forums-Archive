---
title: "no boot sector on usb device for ubuntu external hdd"
date: 2007-11-10
forum: Desktop Environments
---

### Post by jabour on 2007-11-10
Hi Everyone,

I have a couple of issues.

This is my first time trying to run Ubuntu. I recently purchased a western digital passport external hard drive. I used the live CD on my dell desktop to install Ubuntu onto my external drive and was successful. I did not have the time to see that my computer would boot to windows as usual.

I then left out of town and tried to boot Ubuntu from my external drive onto my dell laptop, but when attempting this I receive the message **"no boot sector on USB device"**. The only way I was even able to see that message was because I had to modify my boot sequence to not even boot from my internal hard drive and let it hang at that screen. 

**Questions:**

Now my questions, to those who I hope can answer, is this ...
[COLOR="Red"]
**What do I have to do to boot Ubuntu from my external hard drive onto my laptop?**[/COLOR] [COLOR="Red"][SIZE="2"](For those doing a quick scan through my post, I already have Ubuntu installed on this drive)[/SIZE][/COLOR]

AND

[COLOR="Red"]**Based on what I have read so far online, do I have to fear that my desktop at home is going to require my USB to be plugged in to boot to Windows?**[/COLOR] I have tried to read all about GRUB and the MBR (Master Boot Record), but I have limited understanding. I have been kind of fearing to try the whole process of installing Ubuntu on my external hard drive with my laptop until I have learned whether or not my computer at home was affected with my stupidity.

I am a first time brand new user of Ubuntu and really would appreciate some help, because I really want to use it! 

Thank you in advance to anyone who can help!

---

### Post by jabour on 2007-11-10
Could my problem be that I am using the external drive as a backup drive for my data while using the other partition for Ubuntu?

I need help someone. Save me from this pain!

---

### Post by traderpats on 2007-11-10
I have an external hard drive booting Ubuntu.  When you installed the OS did you set  the  boot to  "/device/sdb"  or whaterver your external hard drive is?  If not then the install most likely modified your MBR on the internal drive.  If that was the case you would not have a boot sector on the external drive.  When you have the usb drive off and boot the machine do you get the grub menu for Windows and Ubuntu?  If so then that is what happened.

---

### Post by jabour on 2007-11-12
I tried doing that, but I am not sure if I did it correctly. Since my last post I went through mounds of documentation. I found I had a couple of problems.

First off thank you for the reply!

Yes, I did write to my MBR of my internal drive. After reading GRUB documentation it seems that my problem with getting windows to boot was because I had my internal drive underneath my USB drive in the BIOS boot order, and improper mapping within GRUB. For whatever reason Windows hates being second in the BIOS drive order according to the documentation I have read. 

Since Ubuntu, which is located on my USB external hard drive, was the first hard drive in my BIOS boot order and labeled hd1 in the device.map file and menu.lst file it caused me to receive the Error 17, "can not mount drive", when I tried to boot it up through the GRUB boot menu. I received error 21 when I tried to boot Windows from the GRUB boot menu, its BIOS location was below my USB drive in my BIOS boot order. Error 5 happened when I did not have my USB drive plugged in when booting up my computer.

In order to stop getting ERROR 5, 17, and 21 messages from happening I had to do a few things. I first booted up Ubuntu by using the GRUB command line from the GRUB boot menu. I did this by changing my Ubuntu root to (hd0,1) from (hd1,1) in the menu selector. If you are unfamiliar with this you can type "e" which will take you to another menu allowing you to change the root. (   i.e root (hd1,1) to (hd0,1)    ). It will be reset after restarting, but this allowed me to boot Ubuntu removing the Error 17 I was getting. Once inside I performed the following in a terminal session in GRUB...

grub> map (hd0) (hd1)
grub> map (hd1) (hd0)

This changed the logical mapping of my hard drives back to their proper order. I then rebooted and put my windows drive on top of my USB external drive in my BIOS boot order. This stopped my Error 21 from occurring and allowed me to boot Windows. I still was getting Error 5 if I did not have my external drive installed when booting my computer up.

I have since removed GRUB from my MBR of my internal drive by using fixmbr in the recovery console window. This obviously stopped anything GRUB from happening since GRUB was no longer on my internal drive.

**Still not there yet**

I would love to hear a quick and easy solution to put Ubuntu on my USB external hard drive. I would also love the solution for putting the GRUB boot loader onto the USB external drive next to Ubuntu rather then it getting written to my MBR on my internal hard drive.

Any solution and I would be most grateful. As a note I have seen posts relating somewhat to doing what I have wished for, but I have yet to see a great simple solution to do it.

---

### Post by logos34 on 2007-11-12
['How to install Grub from a live Ubuntu cd']("http://ubuntuforums.org/showthread.php?t=224351")

The 'find' command may show (hd0,1) or (hd1,1) depending on how it sees the drives in the bios.  Just make sure that the 'setup' command points to the same drive as the root partition. So if '(hd1,1)', then 'setup (hd1)'.

If I understand you correctly, since you already edited root line in menu.lst to '(hd0,1)', then you should be able to set the bios to boot the usb, then go right into ubuntu.

See this thread:
[http://ubuntuforums.org/showthread.php?t=80811](http://ubuntuforums.org/showthread.php?t=80811)
(-->post #502)

---

