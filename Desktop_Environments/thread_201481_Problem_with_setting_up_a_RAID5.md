---
title: "Problem with setting up a RAID5"
date: 2006-06-21
forum: Desktop Environments
---

### Post by Harokey on 2006-06-21
EDIT: Oops this probably should have gone into general support not desktop support, oops. 

Okay This is pissing me off...

I have 3 300 gig harddrives. I want to run then in a software RAID5.

I also have a 200gig drive which i want to use as my system drive.

```
/dev/hda = 200 gig drive
/dev/hdb = 300 gig drive
/dev/hdg = 300 gig drive
/dev/hde = 300 gig drive

```

Now I had ubuntu installed onto /dev/hda1 and everything was peachy. Then I went to setup the raid.

I ran the following command:

mdadm --create --verbose /dev/md0 --level=5 --raid-devices=3  /dev/hdb1 /dev/hdg1 /dev/hde1

After this happened the computer starting acting really slow. Eventually the machine completly just froze. When I tried to reboot it, I got an error: 

```
...
* Starting RAID devices... 
mdadm: /dev/md0 has been started with 2 drives (out of 3) and 1 spare.    [ ok ]
...
* Starting Enterprise Volume Management System...
*** glibc detected *** double free or corruption (!prev): 0x0806b328
```

And it just hangs there. It also does this when I try to boot back into the ubuntu live cd. I have a knoppix cd and can boot into that however. 

While in knoppix, I formatted all of the 300 gig drives, and tried to set the raid up in knoppix.

I thought it was strange that it made one of my drives a hot spare ... So I specefically made it build with no hot spares.

ie --spare-drives=0 or whatever (I can't look up the man page right now)

It eventually locked up when this happened as well.

Now i've downloaded the alternate install, and am trying to set up the linux raid in that. I've gotten to the point of formatting the raid as ext3 but then the screeen just sits at the blue with the little gray bar in the bottom. 

There's a bunch of errors in terminal 4 (ctrl+alt+f4) that all say:

udevd-event[28203]: create_node: symlink(hda1, /dev/discXX) failed: File exists

(where XX is a number, let it be 4,8,12,16,20,24,28)

I need to know why the **** this is happening.

/dev/hda and /dev/hdb are both on the motherboard, but /dev/hdg and /dev/hde are both on a promise ATA controller card. Could the problem be with the controller card?

I was having problems with this machine locking up in linux before, but I thought it was because the system drive had bad sectors on it, maybe its not.

---

### Post by Harokey on 2006-06-22
bump.

I ended up installing windows on the machine, and made a raid0 out of the three drives just for kicks, and it all seems to be working fine. So it seems like there's something weird with linux thats causing my machine to lockup, as opposed to the hardware.

---

### Post by RAOF on 2006-06-22
Looking at this:
[QUOTE=Harokey]...
mdadm --create --verbose /dev/md0 --level=5 --raid-devices=3  /dev/hdb1 /dev/hdg1 /dev/hde1
...[/QUOTE]
Are there actually partitions on those 3 harddrives?  Did you perhaps mean **/dev/hdb /dev/hdg /dev/hde**?

I'm not really familiar with the raid setup, but if you didn't have partitions created on those drives it'd probably freak out :)

---

### Post by Harokey on 2006-06-22
[QUOTE=RAOF]Looking at this:

Are there actually partitions on those 3 harddrives?  Did you perhaps mean **/dev/hdb /dev/hdg /dev/hde**?

I'm not really familiar with the raid setup, but if you didn't have partitions created on those drives it'd probably freak out :)[/QUOTE]

Yes I made partitions. I also formatted them all ext3 before i tried fromt he knoppix cd. 

The first time I tried the partitions were made but they were not formatted.

It still did not work when i tried setting them up in the ubuntu alternative install. The system still froze up. 

I've been filling up the raid0 that i made in windows and i haven't had any problems yet. So either i'm doing something wrong in linux to set them up, or ubuntu (or maybe debian, as i had the problem in knoppix as well) has some sort of bug with my controller maybe?

Oh i should also mention that running that code, mdadm --create ..... sucessfully starts, and it starts creating the array, it crashes somewhere during the creation. I did notice that the creation was happening very slow. As I did a cat /proc/mdstat it was only going at about 600k/s.

---

### Post by [2]BoxingFiend on 2006-06-22
software raid require type fd. not 83.

so when creating a software raid, you need to create your partitions as type fd (linux raid autodetect), create the raid via mdadm --create ..., then do format the /dev/mdX with your prefer filetype

ps.  rather than doing cat /proc/mdstat to see the status of the build. use 

watch -n 6 cat /proc/mdstat

---

