---
title: "Defrag NTFS"
date: 2010-03-03
forum: Desktop Environments
---

### Post by NiGhtMarEs0nWax on 2010-03-03
is there any way I can defrag NTFS? i heard ntfstool could do the job, but i can't see how.

---

### Post by NiGhtMarEs0nWax on 2010-03-03
bump.

---

### Post by andrea000 on 2010-03-03
why are you trying to defrag NTFS from ubuntu?That
can be done from windows.Your dual booting with
windows right?

---

### Post by NiGhtMarEs0nWax on 2010-03-04
that wasn't the question i asked, thanks for making the situation clear to me, it all makes sense now. ;)

anyway, let's say I had an NTFS formatted NAS and I wasn't dual booting with windows, how would I go about defragging the drive?

Thank you. :)

---

### Post by Gralgrathor on 2010-07-05
Bump

Are there any tools available for Ubuntu to defrag an NTFS-drive? I have an Ubuntu system accessing an NTFS volume, with too little spare space to setup a Windows dual boot system, and I've lost my screwdriver, so transplanting the drive into a Windows machine is not an option (even if I had an extra Windows machine), and I'm low on cash, so buying an extra drive isn't really an option either...

Gr,


Gr.

---

### Post by allein on 2010-07-07
I just spent some time googleing ([www.google.com](www.google.com)) and it would seem that there is no NTFS defragger for Ubuntu :)
If I were you, I'd invest in a screwdriver ;)

---

### Post by morrie on 2011-03-17
I'm looking for this, too.  Except I know I just used one awhile back..
[]("http://ubuntuforums.org/showthread.php?t=1074020")

---

### Post by patrick_the_fat on 2011-04-24
> **andrea000 said:**
> why are you trying to defrag NTFS from ubuntu? That can be done from windows.

You can't resize an NTFS partition in GParted unless it's defragmented.

You can't defrag NTFS unless you have Windows, or use bootable software to do the job (most you have to pay for, and you need a thumb drive or CD burner, plus support for booting off these mediums).

If you convert from Windows to Ubuntu, you need to have at least 1/2 your disk free of partitions, so that you can have a large enough Linux partition to move all of your documents from the Windows drive to the Linux drive (and Windows does not allow the resizing of partitions without losing all data..)

What this means: Converting from a Windows NT-based OS with all your documents to a Linux-based OS, you have to meet these strict requirements (which most users don't.. how many Windows users honestly have only half their disk used by an NTFS partition? Most users don't even know what a partition is.).  You are basically "stuck" with an NTFS partition, which does get fragmented and ends up being used in Linux until you decide to go through a painful process of research and trial-and-error.

I have set up an SSH tunnel to transfer 76GB over WiFI just so I can get rid of my NTFS partition (it says it's going to take 300 hours, and it's using all my bandwidth).  That idea, and an hour of my time, is out the window.  I'm just using thumb drives, but still, the copy process likes to freeze and it's still going to take me a week to move all the information from my laptop onto my desktop.

There is definitely a need for an NTFS defragging tool in Linux.

---

