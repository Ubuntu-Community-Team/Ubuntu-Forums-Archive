---
title: "HP Pavilion blues"
date: 2006-02-27
forum: Desktop Environments
---

### Post by bowenit on 2006-02-27
I have an hp pavilion celeron 500 that is refusing ALL breeds of linux.  I'm in the blues with the machine due to the fact that I have no ability to boot from live cd or install.  I can't put anything on this lump of spare parts but bill's junk.:mad: :mad: :mad:

---

### Post by Resurrection on 2006-02-27
I'm running Breezy on a HP Pavilion 510n right now.  My specs:
1.2 Celeron
512 Mb (It originally had 256, but I upgraded it)
Two hard drives (Windows XP on the Master, and Ubuntu on the Slave, both on Primary IDE.

One problem that I had when installing is that I had to remove all add-in PCI cards that I had put in the thing.  I kept having install problems until I figured out that it did not like my nVidia video card.  I pulled it, and it works great with just the onboard graphics.

One question, are you sure you have good install discs?  I have to ask since you didn't mention whether you got ShipIt discs, or you burned them yourself.  This might be the source of your problem.  I had burned the install .iso too quickly the first time, so I burned it again at lowest speed, and it went passed the problems I was having originally.  Then I figured out the graphics card thing.  

Can you be more specific about what install issues you are having?

---

### Post by Jason_25 on 2006-02-27
Sounds like a bad cd drive or a bad burn.  Way more information is needed as well.

---

### Post by bowenit on 2006-02-28
Sorry I can't believe that I forgot linux is all about the specifics.

I Have the shipt disks (The ones that ubuntu ship from the web page)
I have an HP Pavilion 6630 with the following.

i Celeron 500
192 Mb Ram (64 X 3)
a 32 X CD Rom drive
2 IDE (10.2 & 80 GB)
V.90 Modem (Conetix 56 Win / Fax Modem)

The folowing is built prefab onto the m/b

Crystal Audio
Intell 810 chipset graphics

my monitor is a :Hansol 720E 17 "

I am not new to linux I just hate the fact that I have to resort to using bill gates crap on this thing.  I have tried all maner of knowen good install disks on a veriety of CD Rom drives it simply tells me no I cant work.

---

### Post by Jason_25 on 2006-02-28
Does it boot the windows cd or do you need floppies to do it?  You can always initiate the linux install with a floppy.

---

### Post by prion on 2006-08-29
I have a pavilion too and experienced installation problems too.  Ubuntu live cds worked for me, but in order to install I had to use the addition parameters: "vga=771 gdth=disable:y".  I hope this helps.

---

