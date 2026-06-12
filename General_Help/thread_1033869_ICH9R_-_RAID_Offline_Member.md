---
title: "ICH9R - RAID Offline Member"
date: 2009-01-07
forum: General Help
---

### Post by kubug on 2009-01-07
UPDATE: This will work too if you only have Windows running on your computer. You don't need to be running Ubuntu for this fix to work!

Here it goes: I got myself a DFI P35-T2RS with an Intel P35 and a ICH9R Raid chipset. I put three 160GB HDD's in RAID 0 and enjoy almost 200MB/s read speeds. 

All nice and such, but ...

It seems that when I turn the computer off, all three HDD's go into a "Offline Member" state. Meaning, the RAID is turned off. 

I am not sure what I need to do to permanently fix this, but for now, I can bring the RAID back by doing the following (this needs to be done after every time I turn the computer back on):

- boot up with the Ubuntu Live CD - [http://www.ubuntu.com/getubuntu/download]("http://www.ubuntu.com/getubuntu/download")

- once the live CD has booted, open a terminal window and enter the following:

```
sudo apt-get install dmraid
```

Press 'Y' to confirm the install, and once the installer is done, reboot.

Ta-da, your raid is back!

I will post again to let you know what I did to permanently fix this issue (if I get to fix it).

---

### Post by fjgaude on 2009-01-07
You are able to boot into Ubuntu on a BIOS raid0 using **dmraid**? Amazing!

---

### Post by kubug on 2009-01-07
Yeah, I first did it in 7.04 and have had it ever since then. Fakeraid was supported on the installer in Fedora 4. I am still surprised that it still doesn't work out of the box on ubuntu, even thought it has gotten a lot easier.

I actually am triple booting (Vista & XP, I need them for software testing... but am 99% of the time in Ubuntu), and it works great.

Here are the instructions on how to get it to work: [https://help.ubuntu.com/community/FakeRaidHowto]("https://help.ubuntu.com/community/FakeRaidHowto") 
It only takes an extra 10 minutes to set it up.

---

### Post by fjgaude on 2009-01-08
Thanks a bunch... this is good news for those wishing to go this route.

---

### Post by fjgaude on 2009-01-08
Thanks a bunch... this is good news for those wishing to go this route.

---

### Post by helzayat on 2009-02-13
> **kubug said:**
> UPDATE: This will work too if you only have Windows running on your computer. You don't need to be running Ubuntu for this fix to work!

Here it goes: I got myself a DFI P35-T2RS with an Intel P35 and a ICH9R Raid chipset. I put three 160GB HDD's in RAID 0 and enjoy almost 200MB/s read speeds. 

All nice and such, but ...

It seems that when I turn the computer off, all three HDD's go into a "Offline Member" state. Meaning, the RAID is turned off. 

I am not sure what I need to do to permanently fix this, but for now, I can bring the RAID back by doing the following (this needs to be done after every time I turn the computer back on):

- boot up with the Ubuntu Live CD - [http://www.ubuntu.com/getubuntu/download]("http://www.ubuntu.com/getubuntu/download")

- once the live CD has booted, open a terminal window and enter the following:

```
sudo apt-get install dmraid
```

Press 'Y' to confirm the install, and once the installer is done, reboot.

Ta-da, your raid is back!

I will post again to let you know what I did to permanently fix this issue (if I get to fix it).

Did you ever find a fix for this? I have the exact same problem: Raid0 array works fine in Windows and survives warm boots and resets. Powering down the computer results in all drives appearing as "offline members". Boot into Ubuntu 8.04 (I have dmraid installed) and immediately restart - problem solved. Next time I power down I have the same problem.

---

### Post by kubug on 2009-02-14
Well, I think I had somewhat of a compounded problem. First, I added a 3rd HDD, which came from a OEM system. It was the same make/model, but with specialized firmware, and I had no way to flash it to the same firmware as the others, and in fact it wasn't recommended at all.

That was my first issue I think I had, since that drive ALWAYS seemed to go out of sync with the others. I finally ended up removing the drive again, and settling with less space/speed. So I only have two drives. How many do you have?

My second problem was most likely the Windows drivers supplied by Intel. If I only went into Ubuntu, I would not have any problems. But as soon as I booted into the Windows side of things, I got issues. What I finally did was install the latest drivers from Intel and also install the RAID tool. I did a RAID test with it (took a couple hrs, but it can be interupted.)

I have to be honest, I forgot to post about this, so I forget a lot of the details I did to finally settle this down. 

It seemed that as soon as I removed the 3rd drive and I updated the drivers in Windows, it didn't go funny anymore.

---

### Post by helzayat on 2009-02-14
I have two WD 1TB drives in the array, plus two more drives that are not RAID. I multiboot between XP Pro, XP Pro x64, Windows 7 beta and Ubuntu. I've downloaded and installed all the latest Intel RAID software, and also run the RAID test. Whichever OS I boot into, if I shut down the computer the two drives appear as offline members when I turn it on again.

---

### Post by kubug on 2009-02-14
Quick question: Did you use the drives in a previous RAID setup? 

It seemed to me that that was one of the issues I had too. When I would take off the 3rd drive from the RAID, it would keep showing up as a RAID member. I even "dd'ed" my drives to "clean" them up from any remains, but something was still set on them so that the RAID controller pick it up as a RAID member.

From what I recall (and I apologize for being unsure here, I really should have written everything down here) I installed Windows XP and then the Intel RAID software, from which I then removed all the RAID members. I then reformatted all the drives and then setup my RAID again (this time with the two drives). That is the last thing I remember doing. It all took hours to complete, but when done it was fine on my end. Of course, this would wipe out any data on your drives, and it may take a lot longer on your setup. 

Sorry I can't be of more help here.

---

### Post by helzayat on 2009-02-16
I did have the drives on a different RAID controller (the Gigabyte/JMicron controller on the same mother board) before. I have over 500GB on the array, so that for now, booting into Ubuntu first after each power down is more attractive than backing up the array and rebuilding it. Thanks for all your help, I know exactly how it is when you remember doing something and wish you'd written it all down!

---

### Post by helzayat on 2009-02-19
OK, I fixed it, then broke it, then fixed it again. After biting the bullet and backing up the RAID drive, I went into the Intel Matrix Storgage ROM Configuration and reset the the disks in the array to Non-RAID. Shutdown, rebooted and went back into the Configuration Utility (CTL-I) and recreated the RAID array using the exact same settings. Shutdown again, rebooted into Windows and ran testdisk to find and save the partition table. Rebooted, went into Disk Management to reset the drive letters the way they were, and ta-da! everything was back. Shutdown, powered up again and the drives were Online and the RAID was working. 
Breaking it was simple: I booted the Intrepid Desktop CD (64-bit). Some complaints about /dev/sdd (one of the array members) flew by, and when I shut down and restarted they were both Offline again. Fixed it the same way as above. Booted the 8.10 Alternate CD - same problem, had to fix it a third time.
So it seems that in my case, Ubuntu 8.10 breaks my RAID. I may have better luck if thoroughly erase both drives before rebuilding the RAID, but I haven't done that.

---

### Post by GRRS on 2009-04-14
Could you tell me what you are using to control your multibooting? I'm about to do this but FakeRaid doesn't say anything about multiboot management.

Currently running 8.10 AMD64 with VMWare supporting multiple OS's but I want to be able to boot into the actual OS'es.
Thanks ahead of time for the reponse.:KS

> **helzayat said:**
> I have two WD 1TB drives in the array, plus two more drives that are not RAID. I multiboot between XP Pro, XP Pro x64, Windows 7 beta and Ubuntu. I've downloaded and installed all the latest Intel RAID software, and also run the RAID test. Whichever OS I boot into, if I shut down the computer the two drives appear as offline members when I turn it on again.

---

### Post by kubug on 2009-04-14
* bleh.... something is wrong with my computer *

---

### Post by kubug on 2009-04-15
> **GRRS said:**
> Could you tell me what you are using to control your multibooting? I'm about to do this but FakeRaid doesn't say anything about multiboot management.

Currently running 8.10 AMD64 with VMWare supporting multiple OS's but I want to be able to boot into the actual OS'es.
Thanks ahead of time for the reponse.:KS

Have you had a chance to look at the Docs? I used them, and it was quite easy.

[https://help.ubuntu.com/community/FakeRaidHowto#Ubuntu%208.10%20(Intrepid%20Ibex)%20Installation]("https://help.ubuntu.com/community/FakeRaidHowto#Ubuntu%208.10%20(Intrepid%20Ibex)%20Installation")

---

### Post by dallastrubunt on 2009-05-23
I had the same problem before I ever got around to dual-booting. Updating my motherboard's BIOS fixed it.

My system:
Gigabyte GA-EP45-UD3R (rev. 1.1) motherboard, with two drives configured in a RAID 1 Mirror plugged into the ICH10R FAKERAID southbridge (this motherboard has a secondary Gigabyte RAID controller I never tried).  The mirror volume is the system's only storage, containing the OS and all data.

After installing Windows 7 RC 64-bit on the first partition, I could restart the machine over and over without any problems, but if I shutdown and did cold start, the RAID would fail with the same "OFFLINE MEMBER" messages you report. 

I was consistently able to get back into Windows with the following workaround:
1) boot from the Ubuntu Live CD
2) open GParted - this step somehow "wakes up" the HD-MB connection
3) warm-restart back into windows. 

My GA-EP45-UD3R motherboard shipped with an F6 BIOS (dated 2009/01/13). Updating the BIOS to F9 (dated 2009/04/16) completely fixed the problem.

**Important**
Updating the BIOS will reset "SATA RAID/AHCI Mode" to its default "Disabled."  On your first boot after updating the BIOS, remember to change this BIOS setting back to "RAID." I forgot this step and ended up breaking my mirror.  No biggie for RAID 1, but I don't know what would happen to an array with striping.

Now that Windows works reliably, I am going to try installing Ubuntu on the second partition using these instructions: [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

