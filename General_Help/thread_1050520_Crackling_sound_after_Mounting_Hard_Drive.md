---
title: "Crackling sound after Mounting Hard Drive"
date: 2009-01-25
forum: General Help
---

### Post by eckeroo on 2009-01-25
Recently I added an extra 40 hard disk to my system.

It's logical name is sdb and I partitioned it using GParted with an ext3 filesystem + primary parition.

I created a mount point on /mnt/data

Found the UUID with > $ sudo blkid

Amended my fstab accordingly by adding the following lines at the end:

> # /dev/sdb1
UUID=0e90714c-b69c-4ac0-a682-69790c7508a8 /mnt/data ext3 defaults 0 2 

Restarted and found my hard disk had mounted nicely. Near enough 40Gb was available to me on /mnt/data

Unfortunately a side affect had emerged: a frequent crackling sound was now present whenever I played any audio on anything including Rythmbox, firefox or during DVD playback with VLC. I know this as unmounting the drive stopped the sound crackling and returned everything as before. My pulse-audio is configured correctly and plays all audio well when my 2nd hard disk is unmounted.

Mounting an extra hard disk should not cause problems and I don't know what I may have done to trigger it.

System:
OS: Hardy 8.04
Processor: 1733MHz [2100] Athlon XP [palamino] processor
MB: ASUS A7M266
Memory: 1Gb 266DDR PC2100
Boot Hard disk: 20Gb IDE
2nd Hard disk: 40GB IDE (currently unmounted until problem is solved)
Graphics card: Nvidia GeForce 3 Ti 200
Soundcard: Soundblaster Live! Value
Network card: Realtek RTL-8029(AS)
Wireless Network Card: RT2561/RT61 802.11g PCI [Edimax]
USB controller: 5 port USB 2.0 PCI Card (VIA chipset)
 
Regards

eckeroo

---

### Post by eckeroo on 2009-01-26
*bump*

---

### Post by eckeroo on 2009-02-08
I am no longer confident of my earlier diagnosis identifying the mounting of new hard disk as a trigger for the sound to crackle. The longer I play songs, the worse the crackling becomes.

It may help if I describe the crackling in more detail:

The crackling occurs at noisy parts of a song. I can reduce the crackling by turning down the master volume (Alsa mixer). The sound quality is slightly dull and not as clear as it should be.

The sound quality of my MP3s are fine. I've checked them on my portable MP3 player.

Are there any more diagnostics I can carry out to identify or locate my audio problem?

---

### Post by ugm6hr on 2009-02-08
In alsamixer, make sure you turn off / mute all inputs (e.g. mic, CD etc).

Then try again.

---

