---
title: "Did I rewrite my file system?!?"
date: 2009-06-13
forum: General Help
---

### Post by ubucrap on 2009-06-13
I'm on a Dell laptop with 2.0 ghz duo core Intel processor, 320gb hdd.
This is what happened.
I was running XP in Virtual Box on Ubuntu Ibex.
Inside XP I was running iTunes and was syncing my iPod. 
I moved out of the VB "window" to remove a usb thumb drive, and when I ejected it, it asked if I would like to "empty the trash" so I did.
As soon as I started emptying the trash, things started dissapearing off of my desktop. It happened VERY quickly. In about 5 seconds 1/2 my desktop was gone, then my screen blinked and I lost the background picture.
I was so thoroughly confused, so I tried to close VB, which took a moment, but did respond and closed out.
Then I tried to open System Monitor one 3 different desktops, but it froze on each one. I then quit Transmisison, bit torrent client, and everything was gone but two files from my desktop.
I rebooted and everything is gone, except the programs on my applications dropdown menu.
I can still log in. My user account is still there, and every program I had is still referenced in my applications menu, but all of my files are gone. All of my word documents, all 30gb of music, all videos, all 10gb of pictures, etc.
I can log into my account & VB is still there, and still will run, but both of the partitions I had are gone (one of WinXP & one of OPENsolaris).
I had shared about 3 directories, which were all located in the Desktop directory, with the WinXP VB partition & had installed VB Guest additions.
Earlier in the evening, I had plugged that usb jump drive into a machine running Vista to share a file. That file would not copy to Vista and Vista would not eject the volume.
Three: I had added that jump drive to my VB list of hardware. I think I mentioned earlier, when I plugged in the drive, I was running VB with XP running and my iPod syncing. And I wasn't paying attention to the fact that my virtualized XP machine had probably connected the drive as well, so I unmounted it from Ubuntu OS, but I don't know what it was doing in the XP OS.

The reason I mention this is because my log files are ripe with "Filesystem panic" errors due to "invalid access to FAT"
All of that to say. This is only the second time I've really looked at the logs since my using Ubuntu, and I don't know what it is saying. To me it seems the information is still there, but rewritten in a new FAT or something like that? (I don't really know what I'm talking about, it is just a guess).
I'm hoping that someone will be kind enough to help me to know if I can resolve this issue based on the log file that I've attached. It is the "syslog" (from about the time of the error).
I appreciate all the help guys!

---

### Post by trecool999 on 2009-06-13
Is your iPod plugged in or out?
And have you got a Live CD?

---

### Post by ubucrap on 2009-06-13
> **trecool999 said:**
> Is your iPod plugged in or out?
And have you got a Live CD?

During the crash, my iPod was plugged in.
I have a Live CD, but I was not using it at the time. I have had Ubuntu as my only standard operating system on this machine for about 1.5 years.

---

### Post by ubucrap on 2009-06-16
Alright, I found one that stumped the gurus.
SCORE:
me - 1 guru - 10

I'm gaining....

---

