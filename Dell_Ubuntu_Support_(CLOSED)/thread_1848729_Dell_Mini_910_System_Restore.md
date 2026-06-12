---
title: "Dell Mini 910 System Restore"
date: 2011-09-23
forum: Dell Ubuntu Support (CLOSED)
---

### Post by KCahill on 2011-09-23
Hello,
 
I'll start with some background. I had this mini laptop for 3 years. I mainly used it to take notes, because it's easier to carry to class than my XPS. Around 8 months ago, I decided to update it (I avioded doing so because I have a feeling something will go wrong), it ended up messing the computer.
 
I'll explain a little about it. I can acess the main menu but when I try to load up Office, Internet or anything else it says "failed command". I found on the Web that I should system restore it by using an opitcal drive. Well, I set it down for months, mainly because of my anger that I have a worthless computer and that I shouldn't have updated it. Today an opitcal drive came in. I put the Ubuntu OS disc in and tried booting it when it started up. It didn't work. I tried with the Dell Insipirion OS disc; the same thing happened. When I tried to open the disc up it said on the computer that there was "no media in drive". When I put an audio CD in it loaded the songs up, but the music wouldn't play. 
 
I'm really at my wits end with this computer, if anyone knows of anyway I can fix this thing so I can use it; I'd be forever grateful.
 
Thank You for your time,
 
Kerry Cahill

---

### Post by ugm6hr on 2011-09-23
I would suggest you just install a new version from scratch.
You can do this using any USB drive >1GB. This removes the need for a CD drive too (in case that's the problem).
I have a Mini 910, and still use Ubuntu 11.04 on it - although I suspect 11.10 should work just fine too (as should Linux Mint 11).
If you want to try installing one of these - just reply back saying which you want to try, and I can help you through the process.
Let me know what other operating system you have access to, because you'll need to download and create a "Live USB"

---

### Post by KCahill on 2011-09-23
The CD I have is for the 8.04. How do I download the new software via USB? I'd download the 11.04 if it will work.

Thank You for your reply.

---

### Post by ugm6hr on 2011-09-24
Download from: [http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)
Select 11.04 32-bit
You didn't tell me what other computer you will be using to download / create the USB - but the link should help you to do it if you select the appropriate options in Q2.
Just report back if you have problems.
PS: I made an error - I'm using 10.10, but have been planning to move to Mint 11 (based on 11.04) - which does work.
Also - after making the LiveUSB - you have to boot from it (plug in USb, turn on, press Del) and then type "live" to run it.

---

### Post by KCahill on 2011-09-25
Sorry forgot to put OS. I'm using my XPS Vista. I'll keep you up to speed. 
Thanks!

---

### Post by KCahill on 2011-09-25
It appears I cant get passed step 1. I downloaded it just as it implied and then downloaded the USB installer. When I try to open the ISO File to install to the USB; its nowhere to be found. It looks like Im stuck in another rut. Do youhave any suggestions?
 
Thanks!

---

### Post by mikewhatever on 2011-09-25
So, where is the ISO file that you've downloaded?
Also, Step 1 says 'Insert a USB stick with at least 2GB of free space'. Any problems there?

---

### Post by KCahill on 2011-09-25
I fix it. I got the stick in the mini and booted the software but it won't let me install 11.04 because I don't have an internet connection and 4.4 GB.

---

### Post by KCahill on 2011-09-25
I tried to fix the Internet connection but it says I'm missing the firmware. I tried to fix the drivers and it says archive failed. Guys I think this is a FUBAR mini. I'll post anything new.

---

### Post by mikewhatever on 2011-09-25
You are talking about the wireless, right? Dell uses Broadcom cards a lot, and the firmware for them is not in the ISO. Try connecting a cable instead. 
You can install the wireless firmware later from the repositories.

---

### Post by KCahill on 2011-09-25
I'll try that tomorrow but what about the 4.4 GB problem? It's telling me the 'hard drive has health problems".

---

### Post by mikewhatever on 2011-09-25
How much space do you have? How large is the hdd?
Can you quote the 'health problem' message exactly as is. There might be just some reallocated sectors, which is no big deal.

---

### Post by ugm6hr on 2011-09-25
Sorry - I forgot that some 910's had 4GB SD cards (mine has 8GB).

I have never installed 11.04 - but there are reports that 4GB should be enough - [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/775124](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/775124) - although you do need to do a little manual editing (see comment 2)

I would suggest installing without internet - it is not necessary. It will have a red cross by it - but it doesn't stop the installation. Ensure you select the option to overwrite your HD (I believe the default is to install alongside the existing OS).

If there is a problem with the HD, just give as much detail here as possible - we can try and help diagnose the problem.

---

### Post by KCahill on 2011-09-26
I tried doing the Alt F2 thing but I cant seem to get it to work. The Disk Ultility menu comes up and says the "Hard Drive has health problems". So I click examine and it brings me to the Disk Ultility. The Hard Drive is 3.8 GB and the File System is 690 MB.

---

### Post by ugm6hr on 2011-09-26
What Alt-F2 thing?

I'm afraid I don't know much about Hard Drive failures - it might be worthwhile reading this:
[http://ubuntuforums.org/showthread.php?t=1787631](http://ubuntuforums.org/showthread.php?t=1787631)

It would be sensible to click on "SMART data" to run some diagnostics from Disk Utility and report back any numbers that aren't "green".

Try and give as much information here as possible - even include screenshots if possible - since it's almost impossible to follow what's going on otherwise.

---

### Post by KCahill on 2011-09-26
Marker says in that post:
 
"Run the live CD, press alt+f2 and type:
gksu gedit /usr/lib/ubiquity/plugins/ubi-prepare.py
Then on line 310, change "min_disk_size = size * 2" to "min_disk_size = size * 1.4"

Is that I am suppose to do? The Link you sent about HD problems that sounds like what its sending me. I'll try the SMART and post my findings.

---

### Post by KCahill on 2011-09-26
When I try to do a self test it tells me HD has health problems. Below the following attributes are in red: 32, 41, 46, 48, 54, 68, 118 and 178.

---

### Post by mikewhatever on 2011-09-27
Well, if the hdd is broken, look for replacement, preferably something larger then 4GB.

---

### Post by ugm6hr on 2011-09-27
> **KCahill said:**
> Marker says in that post:
 
"Run the live CD, press alt+f2 and type:
gksu gedit /usr/lib/ubiquity/plugins/ubi-prepare.py
Then on line 310, change "min_disk_size = size * 2" to "min_disk_size = size * 1.4"

Is that I am suppose to do? 
Yes - that is the "fix" to allow installation on a HD smaller than 4.4GB.

> **KCahill said:**
> When I try to do a self test it tells me HD has health problems. Below the following attributes are in red: 32, 41, 46, 48, 54, 68, 118 and 178.
I'm afraid I don't know these attribute IDs off the top of my head.
But if there are lots giving warnings, I'd suggest biting the bullet and replacing the HD.

---

