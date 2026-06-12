---
title: "Problem with dual booting XP and Ubuntu"
date: 2009-03-15
forum: General Help
---

### Post by Danman IX on 2009-03-15
Hello all, I'm new to Ubuntu and I've enjoyed it very much so far. But here is my issue. I had XP already installed, Ubuntu was 2nd.

I currently have a RAID0 for XP Pro (2 Barracuda's 500 Gig's each) and a single Maxtor 250 gig'r dedicated to Ubuntu. I installed Ubuntu 8.10 on my Maxtor HDD (Freshly formatted using NTFS, used up the whole thing for Ubuntu) Left my 2 Barracuda's untouched. 

No problems with the install, very clean and defaults all the way. When I rebooted after Ubuntu installed, XP loaded with no prompt from GRUB as if I had done nothing. XP worked fine, so what I had to do was change the order of my drives in my BIOS (Maxtor first then my Nvidia RAID)

That got Ubuntu booting just fine and all worked with no problems (mostly...freezing all the time have to hard-boot) I rebooted from Ubuntu and went into the GRUB options (hit ESC) damn thing is that XP isn't listed there, should I have installed the bootloader elsewhere?

It's a pain in the azz to have to go into my BIOS and re-order my drives if I want to boot XP or Ubuntu, how do I get GRUB to see my XP OS?

I did see an "advanced" option at the end of Ubuntu install, asked where I wanted to install the bootloader, I wasn't sure what to do so I left it at default.

Thanks in advance

---

### Post by mhgsys on 2009-03-15
You could edit your menu1.st and put in your XP manually.

open a terminal:
```

 sudo nano /boot/grub/menu.lst

```

Then scroll down to the next line and add:

title           Microsoft Windows XP 
root            (hd?,?)
savedefault
makeactive
chainloader     +1

Not sure what disk your xp is on I left this ?.?
Anyway: I'm sure you get my drift.

---

### Post by Danman IX on 2009-03-16
I'll give it a go, thanks.

Post the results shortly.

---

### Post by Danman IX on 2009-03-16
> **mhgsys said:**
> You could edit your menu1.st and put in your XP manually.

open a terminal:
```

 sudo nano /boot/grub/menu.lst

```

Then scroll down to the next line and add:

title           Microsoft Windows XP 
root            (hd?,?)
savedefault
makeactive
chainloader     +1

Not sure what disk your xp is on I left this ?.?
Anyway: I'm sure you get my drift.

So I tried changing the (hd__) to 0,0 then 1,1 but got different errors both times. When I changed it to 0,0 then selected Windows XP from GRUB I got a "missing NTLDR" and had to reboot. Then I tried 1,1 and it said "no such partition exists". Is there a way to see how Ubuntu has labeled my XP drives to I could input the right numbers?

if it is 0,0 then what's with the "missing NTLDR" error?

Thanks again for the help.

---

### Post by mhgsys on 2009-03-16
check if your bios has the right disk selected to boot from , also unplug all external disks.

and try to boot again, 

I'm searching other solutions in case this doesn't work

also: seems like hd0,0 is the correct one: Do you have Xp as your primary master?

---

### Post by Danman IX on 2009-03-16
> **mhgsys said:**
> check if your bios has the right disk selected to boot from , also unplug all external disks.

and try to boot again, 

I'm searching other solutions in case this doesn't work

Thanks for the feedback but if you read my original problem both XP and Ubuntu are working as they should but to do that I have to go into the BIOS and change the order of my drives to boot either XP or Ubuntu. 

What I'm trying to do is make GRUB see my XP OS so that I don't have to enter my BIOS every time I want to switch. But GRUB only loads when my Ubuntu drive boots first, if my RAID boots first then XP boots normally with no prompt to dual boot. I then tried adding XP manually to the "menu.lst" but I'm getting some errors. I'm not sure how else to describe my problem, but that's it.

I appreciate the feedback, and please keep them coming.

---

### Post by mhgsys on 2009-03-16
ah, 

Hope I get it right this time. 
You might want to try this Window's entry:

```

title Windows XP 
root (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
savedefault
makeactive
chainloader +1

```

in that case you can leave the grub on the ubuntu drive (where your bios boots from right?) and you wouldn't have to reinstall grub into the win drives mbr.

---

### Post by Danman IX on 2009-03-16
> **mhgsys said:**
> ah, 

Hope I get it right this time. 
You might want to try this Window's entry:

```

title Windows XP 
root (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
savedefault
makeactive
chainloader +1

```

in that case you can leave the grub on the ubuntu drive (where your bios boots from right?) and you wouldn't have to reinstall grub into the win drives mbr.

Ha-ha.. nice one!

Looks like that did it, XP booted nicely from GRUB and Ubuntu booted normally if I just let it boot uninterrupted. Thanks a bunch for your help, good man!

Just for kicks, what did that command do exactly? just so that I have some idea... 

thanks again!

---

### Post by mhgsys on 2009-03-16
Basically : It fools your windows Xp, wanting to be on the primary hard disk , first partition.
Since you boot from your ubuntu disk, where grub is located : the ubuntu drive = hd0
you want windows to think it's on the primary hard disk.(hd0)

so you: 
let (hd0) think it's (hd1)
and let (hd1) think it's (hd0)

---

### Post by Danman IX on 2009-03-16
Awesome... thanks man.

---

### Post by mhgsys on 2009-03-16
your absolutely welcome.

---

