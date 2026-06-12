---
title: "DVD ISO creation"
date: 2006-01-16
forum: Desktop Environments
---

### Post by qferret on 2006-01-16
I was having such a bear of a time that I started documenting my failures (and small successes), hoping to make it easier on the next guy to search the forum...  ;-)

I am now pretty much stumped though & could use some pointers.
While I wait for a response, I'm going to look @ growisofs & see if I can get that to create an ISO image...

-----------------------------------------------------------------------------

1. I compiled dvdbackup & tried to rip the movie. I had previously installed the software necessary for playback
	a. libdvdread kept choking on assorted keys while decrypting them.
	b. After researching for a while, it turned out to be that I hadn't set a region for my new burner yet....
	c. I used regionset (available @ [http://linvdr.org/projects/regionset/)](http://linvdr.org/projects/regionset/)). dvdbackup was then able to decrypt all keys (as the DVD was region 1, of course)

2. dvdbackup then began failing, saying it couldn't seek to such & such sector, so I decided to move on & try VOBcopy.
	a. VOBcopy went all the way through like it was supposed to.
	b. I can't seem to get DVD Decrypter or DVD Shrink to find my drive under wine and for some reason it won't let me open the ripped files from there either (<rant> not surprised...I NEVER have much luck with wine....if the app runs under wine, there's extremely good odds I don't need it as there is a native Linux equivelant  </end rant>, soooo.... I fired up vmware (I keep a 2000 pro vm around for college classes) and installed DVD Decrypter and DVD Shrink in that. Neither app sees my DVD drive under vmware (although I can PLAY the DVD from there with no issues), so it's a good thing I did the VOBcopy. It lets me open the DVD files from the host drive. I proceed to create the iso image with DVD Shrink. It fails on chapter 13. I try again. It fails on chapter 13. Anyone care to guess where the seek errors were coming from when using dvdbackup? I'm guessing chapter 13....

3. While looking at possibilities, I notice that all of the filenames are in lower case....not acceptable for DVD format.
	a. I whip up a quick sh script to rename all files using uppercase. It failed!!!
	b. grrrrr....vfat implementation ignores POSIX filename compliance by default for better Windows compatibility I suppose...fat32 partition (remember the 2000 pro vm I mentioned?) ;-)
	c. Noooooooo problem. I added "shortname=winnt" to the mount options for that partition in /etc/fstab and rebooted
	d. Cool...filenames are all in upper case when ripping now.
	e. Tried again...failed in same spot. Oh well....the file names WOULD have gotten me somewhere along the line.

4. I tried with dvdbackup again. It WORKED!!!!!
	a. I don't know how the lower case file names would give the "seek" messages from before, but that's all that changed (unless the DVD is just craptastically mastered and it was sheer coincidence that it went this time...which I'm hoping at this point... I'd hate to go through this on every DVD...it would be easier to buy a new one when my kids scratch it beyond repair) ;-)

5. I try DVD Shrink to create the iso again.
	a. It fails again, this time at the end of chapter 2
6. I try creating an img with k3b
	a. It fails...same spot
7. I use dvdbackup with the -T switch to snag chapter 2 and copy it into the other directory.
	a. k3b fails again. Same spot.
8. I use dvdbackup to rip chapter 3
	a. k3b fails yet again.
	b. I notice that VTS_3_0.VOB is only 104 k. Ripping it again gives a file of the same size.
9. I use dvdbackup with -F to grab the main feature only
	a. It grabs chapters 2 & 3... & 3 is 104k
	b. I check the original DVD....chapter 3 IS 104k.....  protection? 
10. I delete chapter 3 from the directory structure and try k3b again
	a. Fails. Same spot. wtf?
	b. I rename the next few chapters to one lower to see if it gets further in the process. (4 -> 3, 5 -> 4, etc)
	c. Failed again, looks like the same spot. But upon further checking, the next VOB is a small menu (2.8 MB...pretty small in the grand scheme of 7.6 GB) & the one after that is 104 K again....
11. I now go for broke. It's cure or kill time.
	a. I go through all remaining chapters, delete the 104 K ones (and one 208 K one), and rename the rest to get a numerical order again.
	b. NOTE: Most of the VOB files had previews for icons in Nautilus...the offending ones had the default "Gnome foot"
	c. k3b......FAILED!!!!! OK...It failed in the SAME spot again. It has to be something in chapter 2....which is the main feature.... Damn!
12. While poking around, I noticed k3b wasn't set for UDF. I wasn't overly optimistic, but I tried it. It failed.
13. Re-authored in shrink, losing all menu functionality, but the analysis was successful. ISO creation....Failed
14. The files are ripped & play from the HDD...files are files are files to a burner right?
	a. Let's try a different movie, just to see if it's the process or the movie. I learned a lot the first time through, so if it is the movie causing the headache, the second one should be a breeze...
	b. Movie 2 failed.... same basic spot .... 53% through the ISO creation.

---

### Post by qferret on 2006-01-16
OK, not possible to go to an iso in growisofs
I tried mkisofs...

FINALLY, a somewhat meaningful error message.

```
52.67% done, estimate finish Mon Jan 16 21:04:28 2006
File size limit exceeded
```

I'll google this bad boy now. Anyone know off the top of their head how to work around the apparent 4 GB file size limit? Is it because I have the file on a vfat partition? (I may have to check my ext3 & see if I have enough free space to try it)   ;-)

---

### Post by qferret on 2006-01-16
AAAARRRRGHHHH!!!!!

fuxxored by Windows again! LOL

Fat32 has 4 GB file size limit. I don't currently have enough free space on my ext3 partition for a dvd.....

Will post again once I get that taken care of and prove/disprove that the issue is resolved.

---

### Post by Nikusan on 2006-01-16
With regard to your Wine / DVD Shrink / Drives not being detected problem, check out [this How-To]("http://ubuntuforums.org/showthread.php?t=78611"). It explains how to use winecfg to detect your drives.

---

### Post by RAOF on 2006-01-16
[QUOTE=qferret]AAAARRRRGHHHH!!!!!

fuxxored by Windows again! LOL

Fat32 has 4 GB file size limit. I don't currently have enough free space on my ext3 partition for a dvd.....

Will post again once I get that taken care of and prove/disprove that the issue is resolved.[/QUOTE]
Yup, FAT32 is the devil.  

If you have enough free space to copy all the stuff off the FAT32 drive (in linux **or** windows), you could reformat that partiton ext3 and use the Windows ext2/3 filesystem driver from [www.fs-driver.org](www.fs-driver.org) to read/write to it from windows.  Proper permissions/journaling in linux, and no stupid 4GB filesize limit!

---

### Post by qferret on 2006-01-16
Thanks Nikusan, but the dvd shrink was pretty much a desperation move. I'd rather use the native tools that I can shell script once I get them all working correctly together. (Ya, I could probably shell script the shrink too, but why? I have a DVD+RW DL drive...)   ;-)

---

### Post by qferret on 2006-01-16
YA BABY!!!!

damn fat32 LOL

Got enough space on my ext3 & created an .img file with k3b
Mounted it in my w2k vm to test it. vmware saw it as a valid DVD with menus & everything. Burning it on a DVD now.

Recap for unsuspecting newbies who happen accross my rants....

dvdbackup... use it. It's a simple command & it works.
Key decryption errors - use regionset to set your drive's region code
Seek errors - Crappy master copy....may work if you keep trying a few times.

ISO creation:
Fat32 is a big NO-NO... 4 GB limit...

mkisofs to create iso
growisofs to burn it to a DVD (or growisofs straight to the DVD from the file tree....I prefer to test the process before making coasters as DVD's are still spendy)

^^^^^
K3b uses both tools in a GUI for those who are a.) Still used to Windows or b.) tired of typing for the day   ;-)

Next project:

seeing if dd will really pull a PS2 Game  :D

---

### Post by RAOF on 2006-01-16
[QUOTE=qferret]...
dvdbackup... use it. It's a simple command & it works.
Key decryption errors - use regionset to set your drive's region code
Seek errors - Crappy master copy....may work if you keep trying a few times.
...[/QUOTE]
A note to the unwary:  You will only be able to regionset your drive a limited number of times - typically 5.  Bear this in mind ;)

---

### Post by qferret on 2006-01-17
[QUOTE=RAOF]A note to the unwary:  You will only be able to regionset your drive a limited number of times - typically 5.  Bear this in mind ;)[/QUOTE]


Good point, but in my case it was a new drive & linux doesn't automagically set it to the region of the first DVD you play.  ;-)

Regionset tells you how many user changes and vendor changes you have left if it can get the info from the drive.

---

### Post by crispy_420 on 2006-01-17
Ever try k9copy?
Or xDVDShrink?

---

### Post by qferret on 2006-01-17
[QUOTE=crispy_420]Ever try k9copy?
Or xDVDShrink?[/QUOTE]


Nope...& no need to now

rip.sh
iso.sh
burn.sh

Doesn't a whole lot simpler (without looping LOL)

---

