---
title: "DVD Plays Slowly and Locking Folders"
date: 2006-01-19
forum: General Help
---

### Post by Goober on 2006-01-19
Hi Ubuntonians! (or is that Ubuntonites?)

Anyways I have a problem and a question.

Problem: My DVDs are playing slowly.  They jerk and just don't run smooth like they should.  It's not bad, but its noticable, and irritating.  I tried this: [http://www.ubuntuguide.org/#speedupcddvdrom](http://www.ubuntuguide.org/#speedupcddvdrom), but apparently my dma is already set to On, so that didn't solve anything.  Is there anything else I can do?  I can play DVDs in Windows seamlessly, smooth as a bell, so I know its not my video card.  Can anybody help me?

Question: I have some items in some folders that I don't want other people to access if they are using my Computer.  All that I want to do is to password protect those folders.  I normally am the only one using this computer, but, sometimes, my parents need to use it, and, well, the information there is private.  Is it possible for me to Lock that particular folder?  If so, how?  I tried searching, and didn't find anything really that answered this.

Thanks for your help in advance.

Goober.

---

### Post by darth_vector on 2006-01-19
you can make the folder so that no one else can read it. something like```
chmod -R 600 foldername
```should do it.

---

### Post by Matt Yun on 2006-01-19
1) So you've done "hdparm -d1 /dev/cdrom0"?  Please post the output of "hdparm -i /dev/cdrom"

2) The easiest way to do this is to create separate accounts for your parents (so that they don't need to use yours), then put your confidential folder in your /home directory, and do the following:

user$ chmod -R 700 ~/private_folder

This will set the permissions on your ~/private_folder so that it is unreadable from anyone other than the owner of the folder (ie. you).  

However, this will not stop anyone from booting a LiveCD, mounting your hard-disk, and then browsing the contents.  If you are concerned about this possibility, then you will need to look into encrypted filesystems.

---

### Post by Goober on 2006-01-19
nathan13@nathan13:~$ hdparm -d1 /media/cdrom1

/media/cdrom1:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Inappropriate ioctl for device
nathan13@nathan13:~$

According to the Ubuntu Guide, the dma should be set to 1.

Note that I didn't try any of the other steps in the Ubuntu Guide for Speeding up DVDs, since this one didn't work.

As for the Locking Folder, I think I'll just put the info to disk, and take it off of my computer, what you suggested sounds a bit tricky.  But thanks anyway!

---

### Post by GTvulse on 2006-01-19
> **Goober]Hi Ubuntonians! (or is that Ubuntonites?)
[/quote]
That would be ubuntero (that's the name given to those who have signed the Ubuntu Code of Conduct).
[quote=Goober]
[snip]

Problem: My DVDs are playing slowly.  They jerk and just don't run smooth like they should.  It's not bad, but its noticable, and irritating.  I tried this: [http://www.ubuntuguide.org/#speedupcddvdrom](http://www.ubuntuguide.org/#speedupcddvdrom), but apparently my dma is already set to On, so that didn't solve anything.  Is there anything else I can do?  I can play DVDs in Windows seamlessly, smooth as a bell, so I know its not my video card.  Can anybody help me?
[/quote]

Is your drive a  S(erial)ATA drive? If so, hdparm will not help at all. It only (kind of) works with P(arallel)ATA drives, at least not until kernel 2.6.15 plus patches (that is it may work in Dapper, if I have read corectly the last two month archives of Ubuntu's kernel developers list and LKML  said:**
> 
Question: I have some items in some folders that I don't want other people to access if they are using my Computer.  All that I want to do is to password protect those folders.  I normally am the only one using this computer, but, sometimes, my parents need to use it, and, well, the information there is private.  Is it possible for me to Lock that particular folder?  If so, how?  I tried searching, and didn't find anything really that answered this.


Not really. As long as they can have access to your account, or have access to administrative commands (with sudo) or to booting up into single user mode, there is nothing you can do to impede directory browsing.

Rather, if you really want things to be private you'll need to use some encryption facility. The Linux kernel provides a [deprecated encryption mecanism based on the loop driver]("http://www.tldp.org/HOWTO/Cryptoloop-HOWTO/"), and a new system called [dm-crypt]("http://www.saout.de/misc/dm-crypt/") based on the same subsystem as the RAID and LVM services.  Both are relatively easy to use but demand some studying to make good use of them and work best with dedicated partitons. A third party solution is to use [TrueCrypt]("http://www.truecrypt.org/") which makes it trivial to created encrypted containers as partitions or files (that you can rebind as mouting points within your home directory, this applies to all three encryption systems). The latter Linux port is very recent, so it may have wrinkles to iron out yet. It is a plus that there are deb packages for Ubuntu.

---

### Post by Goober on 2006-01-19
I have no idea what kind of Drive I have, how would I find that out?  The specs for it are in my Sig, but, well, that's kind of all I know about it ... 

Thanks for the reply, though, very informative!

---

### Post by nanotube on 2006-01-20
Hi,

my dvds are also playing jerkily. here is the output from my hdparm -i:

dfolkins@groovy4:[~]$ hdparm -i /dev/cdrom

/dev/cdrom:

 Model=HL-DT-STCD-RW/DVD-ROM GCC-4240N, FwRev=E112, SerialNo=
 Config={ Fixed Removeable DTR<=5Mbs DTR>10Mbs nonMagnetic }
 RawCHS=0/0/0, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=unknown, BuffSize=0kB, MaxMultSect=0
 (maybe): CurCHS=0/0/0, CurSects=0, LBA=yes, LBAsects=0
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4
 DMA modes:  sdma0 sdma1 sdma2 mdma0 mdma1 mdma2
 UDMA modes: udma0 udma1 *udma2
 AdvancedPM=no
 Drive conforms to: device does not report version:

 * signifies the current active mode

so it appears that udma2 is on... any suggestions?

Thanks! :)

---

### Post by alingatong on 2006-01-20
nanotube:

try these steps:

1. open terminal and type
sudo hdparm /dev/hdc

2. see if dma=on
3. if not type,
sudo hdparm -d1 /dev/hdc

this will set this on
4. edit hdparm.conf by:
sudo gedit /etc/hdparm.conf

5. at the bottom of the file, add these lines

/dev/hdc {
dma = on
}

editing the hdparm.conf will ensure that once you restart the pc, dma will be turned on. I think failing to do so means you always have to manually turn on dma. This worked for me. I followed this in the ubuntu wiki.

---

### Post by alingatong on 2006-01-20
nanotube:

try these steps:

1. open terminal and type
sudo hdparm /dev/hdc

2. see if dma=on
3. if not type,
sudo hdparm -d1 /dev/hdc

this will set this on
4. edit hdparm.conf by:
sudo gedit /etc/hdparm.conf

5. at the bottom of the file, add these lines

/dev/hdc {
dma = on
}

editing the hdparm.conf will ensure that once you restart the pc, dma will be turned on. I think failing to do so means you always have to manually turn on dma. This worked for me. I followed this in the ubuntu wiki.

---

### Post by alingatong on 2006-01-20
nanotube:

try these steps:

1. open terminal and type
sudo hdparm /dev/hdc

2. see if dma=on
3. if not type,
sudo hdparm -d1 /dev/hdc

this will set this on
4. edit hdparm.conf by:
sudo gedit /etc/hdparm.conf

5. at the bottom of the file, add these lines

/dev/hdc {
dma = on
}

editing the hdparm.conf will ensure that once you restart the pc, dma will be turned on. I think failing to do so means you always have to manually turn on dma. This worked for me. I followed this in the ubuntu wiki.

---

### Post by GeneralZod on 2006-01-20
[QUOTE=Goober]nathan13@nathan13:~$ hdparm -d1 /media/cdrom1

/media/cdrom1:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Inappropriate ioctl for device
nathan13@nathan13:~$

According to the Ubuntu Guide, the dma should be set to 1.[/QUOTE]

If you read the output, you'll see that it tried to set the DMA on your harddrive, but failed :)

You should try again, this time using sudo:

```

sudo hdparm -d1 /media/cdrom1

```

and post the output here.

---

### Post by nanotube on 2006-01-20
Hi, I did what you suggested, alingatong, and here is the output

$ sudo hdparm /dev/hdc

/dev/hdc:
 multcount    =  0 (off)
 IO_support   =  0 (default 16-bit)
 unmaskirq    =  0 (off)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 65535/16/63, sectors = 78140160, start = 0

so dma is on. Any other suggestions?

---

### Post by alingatong on 2006-01-21
nanotube. yes DMA is already on. have edited your hdparm.conf? edit it. then restart then see if there are improvements.

also try to repeat the steps i gave you but instead of /dev/hdc use /dev/cdrom. how many cdroms do you have on that machine?

---

### Post by kosmic on 2006-01-21
Hi to protect your files use GPG, if you need a frontend use SEAHORSE :)

---

### Post by nanotube on 2006-01-25
hey alingatong,

setting dma on with -d1 worked and now dvd plays back flawlessly. thanks!
i also edited hdparm.conf just for the next time i reboot. :)

btw, i looked around and found that my cdrom drive was /dev/hda... with symlinks to /dev/dvd and /dev/cdrom. so i had to play with hda, not with hdc. 

Thanks for your help!

---

