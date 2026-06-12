---
title: "Huge ubuntu crash"
date: 2005-12-19
forum: General Help
---

### Post by george_apan on 2005-12-19
Hi all! I've been using ubuntu for about 3 weeks now and I was really satisfied with the whole thing until a couple of days ago. My laptop crashed really bad and the system could not boot at all. I'm sorry I don't have any error message details but I'll try to remember as much as I can.

First of all, I should note that I had my laptop's HD configured in just one ext3 partition, which is the default ubuntu installation. What happened is that as I was working on my pc (I was doing some id3 tag editing on mp3s) I started getting error messages that everything (and I mean everything) was read-only and I could not access anything. All programs would not load and I thought that maybe a reboot would be appropriate. It turned out that this was not possible either (I waited for about 10mins) so I just turned the power off. During reboot I started getting weird (for me at least) error messages about corrupt superblocks and invalid magic numbers. Now I sure have no idea what a superblock is and the last time I heard of a thing such as a magic number probably was in a Harry Potter movie. Anyway ubuntu prompted me to fix all that and I answered yes. Sadly, nothing appeared to be fixed as I still could not boot. I tried another reboot (and another and another) but all I got was the same error messages again and nothing more.

I decided I should put a live-CD in and do an fsck from there. So I booted up a knoppix CD and started checking my hard drive. fsck came up with countless errors reporting that every inode on my HD is corrupt and asked me if I wanted to fix them. Somewhere in there I was informed by an error message that journaling capabilities had been disabled and that my file system was turned to ext2. After all the fixing (??) was done I took a look with konqueror at the HD and all that was there was a lost+found directory with about 1000 directories in it all numbered like #xxxxxx. At that point I became certain that there was no chance I could bring my system back up and all I was left to do was try to locate my home folder to see if that had survived. After a little search I fortunately found my home folder intact under a #1210049 directory. So I backed that up to an external HD and installed ubuntu once again. This time I chose to use separate /, /boot and /home partitions (the latter is reizer). Oh, I forgot to write that everything in my laptop's HD was marked as root read-only and could only access anything as root. 

Now, does anybody have any idea why that happened? Was it a hardware failure? I now have the exact same HD running for two days with no problems but I don't know if this will happen again. Or was it an ext3 failure? Or maybe a ...virus??? (is there such a thing?)

Now I know I'm not going back to that other operating system anyway and I'm quite happy with the way ubuntu works but I wouldn't want to have another crash like this. So any hints would be welcome.

Cheers,

George

---

### Post by BathroomNinja on 2005-12-19
try running the following command from the terminal
```
badblocks /dev/hda
```  (or sda if you have a Serial ATA drive)

What does it report?

Also, yes, there are virus's in linux, however they are much more uncommon than in windows but always a possibility.

---

### Post by george_apan on 2005-12-19
badblocks reports nothing at all. So if I get it right is it safe to assume that this was not an HD failure?

---

### Post by giftnudel on 2005-12-19
No, this sounds like an extremely bad crash. There is a big chance, that this will happen again, so back up your data regularly (daily in your case) and wait for the next crash. To be on the safe side, buy a new harddisk ... . It could also have been the only crash and you can work with it for the rest of the laptop's life.
This sounds always easy when it's not your own money, but in this case, this is actually a good alternative unless you can find another cause for that error.

Anyhow, I will give you with some precautions, so that this will not happen again. 
I don't know if you know some of this, it's common sense, but most of the people forget it or won't think it will happen to them (I'm including myself here!):
Do not use your laptop on a "soft" surface like on your knees, the sofa, some pillow, in bed, etc. as there is a big chance of a harddisk head crash when the laptop is moved while it's on. To show an analogy, the head of the harddisk can be compared to a military fighter jet flying at full speed 30 cm's above the ground. Therefore, do not move your Laptop around, when it's on. Put it on a table or so, when you use it. If you need to move it, hibernate it or shut it off. It's really easy to kill your harddisk if you move your laptop while its on.
Really, take this seriously, many of my friends (and myself) have had this problem once on a laptop.

so far, 
giftnudel

---

### Post by george_apan on 2005-12-19
Thanks for the advice giftnudel but I always use my laptop on my desk. So all I have to do is wait and hope things don't go bad again...

---

### Post by arctic on 2005-12-19
I had experienced exactly the same thing on my lappy and thought it might be related to my DMA/UDMA problems (timeouts) with the stupid Hitachi harddisk I have. I filed a bug and was asked to upgrade, using the Dapper flight-2 CD. My timeouts are now gone and I hope that my box won't crash again. It's been stable lately and I really ask myself if DMA was not only causing timeouts on my box but also causing my fatal crash. So I suggest you check your /var/log/messages file. If you find some DMA errors reported there, then you will have exactly the same problem I had, which can be fixed using kernel 2.6.15 of Dapper.

---

### Post by giftnudel on 2005-12-19
Oh, I hate this, when you would have said "Oh I dropped my laptop from second floor, now that makes sense" this would have been far more useful. Anyhow, hardware failures are most of the times neither understandable nor predictable (by the user) so there is not much one can do about it other than hope that it doesn't happen again. Unfortunately, the only thing to do against it, is to buy a new notebook/harddisk.
You might want to talk to your laptop manufacturer/seller about this isssue, since if you only used it on a desk, I would try to reclaim it (and get a new harddrive if possible). 
The problem left: If they don't find anything, you might need to pay for the inconviniences (so: shipping and so on) you caused them ...

giftnudel

---

### Post by george_apan on 2005-12-19
OK I did a less /var/log/messages|grep DMA and all I got was this:
```
Dec 16 19:04:21 localhost kernel: [4294670.910000]     ide0: BM-DMA at 0xff00-0x ff07, BIOS settings: hda:DMA, hdb:DMA
Dec 16 19:04:21 localhost kernel: [4294670.910000]     ide1: BM-DMA at 0xff08-0x ff0f, BIOS settings: hdc:DMA, hdd:DMA
Dec 16 19:04:21 localhost kernel: [4294674.538000] hda: 39070080 sectors (20003 MB) w/1806KiB Cache, CHS=38760/16/63, UDMA(33)
Dec 16 19:04:21 localhost kernel: [4294697.919000] parport0: PC-style at 0x378 ( 0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
Dec 17 10:35:21 localhost kernel: [4294670.675000]     ide0: BM-DMA at 0xff00-0x ff07, BIOS settings: hda:DMA, hdb:DMA
Dec 17 10:35:21 localhost kernel: [4294670.675000]     ide1: BM-DMA at 0xff08-0x ff0f, BIOS settings: hdc:DMA, hdd:DMA
Dec 17 10:35:21 localhost kernel: [4294674.303000] hda: 39070080 sectors (20003 MB) w/1806KiB Cache, CHS=38760/16/63, UDMA(33)
Dec 17 10:35:21 localhost kernel: [4294697.869000] parport0: PC-style at 0x378 ( 0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
Dec 18 12:40:18 localhost kernel: [4294670.784000]     ide0: BM-DMA at 0xff00-0x ff07, BIOS settings: hda:DMA, hdb:DMA
Dec 18 12:40:18 localhost kernel: [4294670.784000]     ide1: BM-DMA at 0xff08-0x ff0f, BIOS settings: hdc:DMA, hdd:DMA
Dec 18 12:40:18 localhost kernel: [4294674.415000] hda: 39070080 sectors (20003 MB) w/1806KiB Cache, CHS=38760/16/63, UDMA(33)
Dec 18 12:40:18 localhost kernel: [4294699.729000] parport0: PC-style at 0x378 ( 0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]

```
I don't think any of these are error messages, right? And I only have an hda, not hdb, hdc or hdd.

Regarding sending the laptop back to its manufacturer, well this would not work simply because it is already four years old! :)

---

### Post by arctic on 2005-12-19
Correct, no DMA timeouts on your box. So let's cross fingers and hope the best. :rolleyes:

---

### Post by Snocrash on 2005-12-19
I used to have a problem like this on my Desktop. I would get the same type of errors then the drive would go dead and I would have to reformat it. The drive would then work for a couple of weeks or months and then bang, same thing..... I got a new drive and it worked for a while and Bang, same thing.

3 drives and almost a full year later, I finally traced it down to the hardware. In my case it was an old PCI ATA card I had in the box. I replaced it and have had no problems since.

Backup, Backup, Backup!!!!!!!

Hardware problems can be a pain to find.

Best of luck,

-Sno

---

