---
title: "Uninstall Ubuntu"
date: 2006-02-21
forum: Desktop Environments
---

### Post by sevir on 2006-02-21
I'm sorry guys, I love Ubuntu, however I need the h.d. space.
Forgive my naivity, but I don't know how to uninstall.
On my computer, Ubuntu is on it's own h.d. with no partitions.
I've tried formating to no avail.
 Thank you for your assistance. :???:

---

### Post by Tiede on 2006-02-21
The best way I can think of to uninstall ubuntu is to format the hd, which you **should** be able to do... What program are you using to format the disk? Was the drive mounted when you were trying to format it?
Post ```
fdisk -l
``` so I can take a peak at it for a sec.

---

### Post by bmathis on 2006-02-21
If you cant format your hard disk for some reason try a debug script to wipe out the MBR and all the partition tables follow these steps:

Boot with a DOS floppy that has "debug" on it; run "debug". At the '-' prompt, enter the following: 

```
f 9000:0 200 0
a
mov dx,9000 
mov es,dx 
xor bx,bx 
mov cx,0001 
mov dx,0080 
mov ax,0301 
int 13 
int 20


```

Press <Enter> to exit assembly mode and press "g" to execute, then "q" to quit "debug". Your HD is now wiped and you should be able to use any disk partition program or Windows/Linux install disks to format the hard drive.

---

### Post by sevir on 2006-02-21
[QUOTE=Tiede]The best way I can think of to uninstall ubuntu is to format the hd, which you **should** be able to do... What program are you using to format the disk? Was the drive mounted when you were trying to format it?
Post ```
fdisk -l
``` so I can take a peak at it for a sec.[/QUOTE]

I'm sorry, I don't know if it was mounted.
i just tryied formatting from the terminal and that button in the admin. tools>disks that says format.
i'm afraid i need a step-by-step

---

### Post by Tiede on 2006-02-21
You cannot format a disk from within it. What you have to do is run the LiveCD if you have one, or download a partitioner for windows and format from one of them.
But going in the System->Administration-Disks menu won't format the disc for you.

---

### Post by Tiede on 2006-02-21
I'm not gonna stick around long, but you can always check on the IRC channel #ubuntu if you are in a hurry. Just go to Applications->Internet->XChat IRC. The default channel is ubuntu's. You will certainly find someone there who can help you.

---

### Post by sevir on 2006-02-21
thanks for your advise, turns out i could do it from Win.
lol, sorry for asking for your advise and then not fallowing it, but that info. will come in handy in the future.

---

### Post by sevir on 2006-03-10
Hey all,
Problem solved, unfortunitly by a crash.
I had to overwrite both my h.d.s.:confused: :( :evil:

---

