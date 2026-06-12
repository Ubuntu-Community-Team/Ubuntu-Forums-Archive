---
title: "HELP:  How to restore Dell Mini 9?"
date: 2009-07-01
forum: Dell Ubuntu Support (CLOSED)
---

### Post by jem556 on 2009-07-01
I've had a **Dell Mini 9** for a couple of months and really like it for my intended purpose of being a small/compact travel device for email and web surfing. It worked perfectly until yesterday when I was lured into letting it download a sizeable list of software upgrades by the system update manager...now it is screwed to hell.
 
What is the best way to restore this machine to the original factory config as delivered? 
 
*I have the Dell/Ubuntu 8.04+ LTS Recovery CD...but of course, no CD drive in the Mini 9. 
 
*I tried copying all the CD files to a USB jump drive, but the Mini 9 refused to run the .exe file from this device. 
 
*I tried configuring the Mini 9 to boot from the USB jump drive, but got an error saying the usb drive did not contain a bootable partition.
 
Any help and/or advice will be greatly appreciated!

---

### Post by goofynewf on 2009-07-01
I had an issue like that with my Dell Mini.   I installed an update and my keyboard didnt work.  Have you tried to call Dell?   I shipped mine to them twice.  The first time we thought it was the keyboard, but when I received it back and still had the problem, realized it was the o/s.  Like you, I do not have external CD drive.  I believe if you do, you can reinstall the o/s.   I have not had an issue since, but I just installed an update so we will see what happens.  
Warning, in case you haven't call Dell, I found it very difficult to get someone to help me with an Ubuntu system.

---

### Post by tyroeternal on 2009-07-02
I had this same issue as well, and was completely stumped until I realized that there is a .img file on the recovery disk that you can use to make a restore usb drive.

You should be good if you use the .img file on the recover cd and the instruction here: [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

Edit:  The sizeable list of updates was because dell holds onto the updates and releases them in large update groups.  Supposedly this is for testing purposes, but it is not a perfect system by any stretch of the imagination.

---

### Post by jem556 on 2009-07-02
I was able to restore my Mini 9 with the Dell Ubuntu Restore disk by utilizing an old CD drive from a dead PC and connecting it to the M9 via a USB drive adapter cable I had been using with an old harddrive for an external backup drive on my desktop PC.
 
In order to get the M9 to boot from the CD and initialize the restore disk, I first had to go to the BIOS setup and disable the M9 harddrive and make the external usb CD drive the boot drive. (just putting the CD drive 1st in order for the boot device did not work...the CD drive would initialize but skip on to the HD and boot the system, ignoring the restore disk) After the restore had finished, I went back to BIOS setup and enabled the harddrive again.
 
For those who may be interested, ie, having similar problems after installing updates, here are some of the issues I had after allowing the M9 update manager to download and install the software updates:
 
1. Got error messages saying the root drive was 100% full. I think this was due to failures in the update process...I found what looked to be 'huge' system backup files on the drive that I could not delete.
 
2. Glitches in the desktop interface. For example, when clicking the system exit icon, instead of getting the dialog to select, LOGOFF, CHANGE USER, SHUTDOWN, etc., the menu bar would just disappear and I would have to hold the power button to complete a shutdown.
 
3. Shutdowns took a lot more time and lines of error code scrolled by before finally turning off.
 
4. Firefox/Mozilla was updated to a different version and became virtually useless. I could no longer bookmark sites and login data (id/passwords) could not be saved...basic navigation was erratic. Basically, the browser became unusable.
 
I don't know what other problems there may have been, because this is as far as I got before getting fed up with it and doing the restore...

---

### Post by snowpine on 2009-07-02
Do yourself a favor; install the latest Ubuntu (9.04) and don't worry about the special Dell version. Much less hassle, saner updates.

---

### Post by tyroeternal on 2009-07-02
I agree with snowpine.  Jaunty is going to have all the security updates and the latest packages, plus you will not have to worry about another Dell mega-update blowing your system away.  Things should even work faster with the latest release.

---

### Post by Talon2 on 2009-07-03
You might be better satisfied if you go with 9.04 Netbook Remix.

Even though the original 8.04 performed reasonably well, give or take a few bugs, 9.04 NR works very well.

---

### Post by jimrz on 2009-07-04
> **Talon2 said:**
> You might be better satisfied if you go with 9.04 Netbook Remix.

Even though the original 8.04 performed reasonably well, give or take a few bugs, 9.04 NR works very well.

+1 

UNR 9.04 performs better on my Vostro A90 (same as Mini 9 except it is sold through the Dell small business section) than did the original Dell 8.04 install and the install from usb stick was both easy and flawless.

---

### Post by Ragtop on 2009-11-28
My mini-9 came from the Dell outlet store refurb operation today with no operating system installed.  The disks with the 'putr said "already installed", but when I booted the li'l critter the first time I got the Dell splash screen, instructions for setup and boot options and "No loader" with a blinking cursor.

I copied the CD files to a pen drive, but it wouldn't boot.  I got the msg: "Pen drive Without Operating System.  Remove pen drive and reboot.".  This, of course just takes me in circles.:confused:

After reading some posts here, I have doubts about the Dell version of Ubuntu.  However, the disk I got with the Mini9 is not Dell branded.  It's labeled "Ubuntu 8.04  + LTS recovery media" and the copyright is to Canonical Ltd.

My plans are to get the 9.10 netbook remix, but I'd really like to have an OS up and working soon.  

Any help or suggestions greatly appreciated.):P

Thanks in advance!

BC

---

