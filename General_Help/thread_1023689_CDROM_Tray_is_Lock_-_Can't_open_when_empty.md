---
title: "CDROM Tray is Lock - Can't open when empty"
date: 2008-12-28
forum: General Help
---

### Post by Scoubidou on 2008-12-28
Hi guys,

I've looked in the forum but haven't find the answer to this specific question so here it goes.

Once I've used the CD once to let say, watch a DVD or burn something and I unmount/eject it (by right clicking on the CD on the desktop) and close the tray it won't reopen. I tried to push the CD eject button, nothing.. Right-click & Eject in Nautilus get the message : Enable to mount media. There is probably no media in the drive.

Even these shell command don't work :

```

$ sudo eject cdrom 
$ sudo eject -t cdrom 
$ sudo eject /dev/cdrom 
$ sudo eject -t /dev/cdrom 
$ sudo eject cdrom0 
$ sudo eject -t cdrom0 
$ sudo eject /media/cdrom 
$ sudo eject /media/cdrom0
$ umount cdrom
umount: cdrom is not mounted (according to mtab)
$ umount /dev/cdrom
umount: /dev/cdrom is not mounted (according to mtab) 

```

Well, you get the picture.
To open the drive, I have to put something (a staple) in the little hole to physically unlock the drive. Then I can put a CD and open/close the drive with the eject command. I can do wathever I want (watch a DVD, burn something, etc) and use the eject/unmount command. But I after that I wan't to put a new media I have to put the staple back in the hole. A reboot will also fix the problem, but I don't like this Windows like fix.
As you can imagine this is VERY annoying.

I'm using Hardy, the drive works find in Windows so I know it's the the drive itself.

Any ideas?

Thanks a lot.

---

### Post by dcstar on 2008-12-28
> **Scoubidou said:**
> 
.........
To open the drive, I have to put something (a staple) in the little hole to physically unlock the drive. Then I can put a CD and open/close the drive with the eject command. I can do wathever I want (watch a DVD, burn something, etc) and use the eject/unmount command. But I after that I wan't to put a new media I have to put the staple back in the hole. A reboot will also fix the problem, but I don't like this Windows like fix.
As you can imagine this is VERY annoying.

I'm using Hardy, the drive works find in Windows so I know it's the the drive itself.

Any ideas?

Thanks a lot.

Is the drive set to be a Slave without a Master device on the IDE cable?

---

### Post by ibuclaw on 2008-12-28
Does your CD drive open when you press the mechanical eject?

What type of CD-Rom drive are you using?

Regards
Iain

---

### Post by Scoubidou on 2008-12-28
tinivole : No, as stated in my first post, the Eject (mechanical) button doesn't work in Ubuntu but does in Windows. 
The button will also work after a fresh reboot. (Now uptime 11days)
As for the brand, I believe it's a "standard oem" dvd-rom no real brand.. 

dcstar : I haven't checked that but I really doubt it is set to slave. I'll have a look later.. I guess if it is, I have to set it to master, right? It's the only IDE drive as my HDs are SATA.

What's next? :)

---

### Post by Vantrax on 2008-12-28
Check it shows in /dev if it does, then you can manually add it to /etc/fstab

It should look something like:
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by cariboo on 2008-12-28
There should be a small hole in the faceplate of the CD-rom drive, unfold a paperclip and insert it in the hole and push until the drive pops open. Put a cd in the drive and wait for it to be recognized, use either the eject command or the button on the drive to eject the disk.

I had the same thing happen to me, and that is the way I got the drive to work again.

Jim

---

### Post by Scoubidou on 2008-12-29
Cariboo : As I said in my first post, it works with a staple/paper clip/toothpick but I have to do that EVERY time there's NO CD/DVD inside. I don't think that's normal. 

Vantrax : I already have that line in /etc/fstab

Is there a command to reactivate the mechanical Eject button?

---

### Post by 0mcg0 on 2009-01-08
This is a frustrating problem.  I think it only happens with certain hardware. My system is an hp laptop. I believe the culprit is brasero...
it seems to unmount the drive after ejecting the disk and when the drive isn't mounted it can't be opened.  The solution is to just open a shell and
mount the drive.

 mount /dev/cdrom 

should do the trick then 

 eject -v

Also if you notice it is happening with brasero give gnomebaker a try instead.

---

### Post by anubhavrocks on 2009-01-08
try these commands:
```
eject -rv
eject -sv
```

Can you also post the output of these commands.

---

### Post by davey.moore on 2009-01-08
thank you 0mcg0,

your two commands did the trick!
Even though the first one gave me "mount: No medium found", then I executed the 2nd one and it worked (while it hadn't worked before).

---

### Post by jtpoole99 on 2009-08-08
Regardless of what I do, I still can't open my drive tray the regular way.  I'm starting to think my drive is malfunctioning since none of the commands here work all the time.  The eject command works after I've typed it into a terminal about four or five times.  Most of the time my only option of opening the drive is using a paper-clip to insert in the hole.  I know this isnt normal operation, but pressing the eject button does not work all the time, not even when the computer is rebooting into Ubuntu.  Is this a drive problem or OS problem?

From CD Trayed in Statesboro, GA  USA

---

### Post by jonathanlemoine on 2011-10-27
It could be that an application is locking your drive so the button on the drive is disabled. Use "eject -i 0" to unlock. I'm not sure but if your device is not /dev/cdrom then you may have to specify it.

---

