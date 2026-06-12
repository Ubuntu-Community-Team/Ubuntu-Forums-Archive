---
title: "cd rom mount problem"
date: 2005-12-10
forum: General Help
---

### Post by HokeyFry on 2005-12-10
i am using ubuntu hoary on an older laptop for school. I just recently recieved my ubuntu breezy cd and tried to upgrade it, but when i try to mount the CD rom, i get an error, "No medium found". I have no idea how to fix this, and for the record, i had trouble running the CD ROM on windows too, many years ago. I have tried switching the CD ROM bay, but it still doesnt work. Also for the record, the floppy drive works when I put it in.

---

### Post by taurus on 2005-12-10
And for the record, why don't you boot your machine while the CD is in the drive!  Why do you have to mount it first if you want to upgrade your Ubuntu?  Also, make you have set your BIOS to boot from CD-ROM first...

---

### Post by HokeyFry on 2005-12-10
well, i was reading how to do it using synaptic and i would rather do it that way. its kinda wierd, cause i can boot from the cd, but i can't use it once ubuntu loads.

This also poses as a problem if I want to use a CD for something in the future, not just for upgrading.

---

### Post by taurus on 2005-12-10
If you want to upgrade your system using apt-get, then just replace hoary with breezy in /etc/apt/sources.list.  

On the other hand, how did you try to mount the CD!  Does it look something like 

sudo mkdir /mnt/cdrom
sudo -t iso9660 /dev/hdc /mnt/cdrom
(assuming that your CD-ROM is /dev/hdc!!!)

---

### Post by HokeyFry on 2005-12-10
forgot to mention -- no means of internet access anytime on this anytime soon. I think you are not seeing the point of this post. It is not for a way to upgrade hoary to breezy. It is to find a way to fix the cdrom problem.

**EDIT** didnt see the 2nd part of your post. ill try that.

---

### Post by taurus on 2005-12-10
Okay, let's try this again.  How did you mount your CD-ROM then???

---

### Post by HokeyFry on 2005-12-10
when i do the line "sudo -t iso9660 /dev/hdc /mnt/cdrom", i get an illegal command warning

nvm, fixed it. put mount after sudo. however, i still get the same error: "no medium found"

---

### Post by taurus on 2005-12-10
You said it's an old laptop!  I think your CD-ROM on your laptop is busted!  To make sure that's the case, see if you can boot Ubuntu using another machine with the same CD...

---

### Post by HokeyFry on 2005-12-10
it works on my other desktop just fine.

Like i said before its confusing to me because when i put a floppy bay int there, it works fine. But any cdrom bay i put in returns the same error.

and to what you said about how i try to mount it, i did your way as well, but normally i use:

"sudo mount /dev/hdc" and "sudo mount /dev/hdc /media/cdrom"

---

### Post by taurus on 2005-12-10
If your floppy works but not the CD-ROM in the same bay, then I would have to say that your CD-ROM is probably dead.

---

### Post by HokeyFry on 2005-12-10
not possible. all three work in my dads work laptop. as i said befopre, i have had problems with this for several years, since i had windows 95/98 (cant remember) on this thing.

one thing may help if i know this: what does it mean if a medium cant be found?

---

### Post by HokeyFry on 2005-12-10
ok, new problem. my laptop wont launch the ubuntu 5.04 or 5.10 cd from bootup, nor either live cd. This is wierd, because i just used the hoary live cd earilier today. i checked my bios and it IS set to boot from cd/dvd rom.

I swear if i didnt absolutely need this laptop i would go to ohio and buy fireworks, then have some fun in the woods behind my house with that hunk of junk!!! KABOOOOM!!!!!!!

---

### Post by roach of discord on 2005-12-31
I have the same CDROM issue, and my cd rom is definitely not dead.

---

### Post by Knoia on 2006-07-30
Did anyone ever figure out a solution to this? I have the same CD-ROM issue. It won't mount and never attempts to read discs, even on boot up.

---

### Post by Knoia on 2006-07-30
Unfortunately, it looks like my CD-ROM is simply dead. I tried swapping it out with a good one from another computer, and it's running fine now. Oh well.

---

