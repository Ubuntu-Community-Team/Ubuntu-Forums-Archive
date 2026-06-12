---
title: "Unable to mount cd"
date: 2005-04-23
forum: Desktop Environments
---

### Post by Lamber on 2005-04-23
Hi,

i'm trying to copy an audio cd. The problem is, the audio cd isn't mountable. There's nothing wrong with my cd player, because I can mount other cd's.
> 
robert@ubuntu:~ $ sudo mount /media/cdrom0/ -o unhide
mount: wrong fs type, bad option, bad superblock on /dev/hda,
       or too many mounted file systems 

Burning with k3b or xcdroast doens't work either, because the cd cannot be found.

Does anyone knows how to solve this problem?

Many thanks, 

Lamber

---

### Post by andvaranaut on 2005-04-23
An Audio-CD is not mountable because it does not have a filesystem, but raw audio data. In fact, when you insert an Audio-CD in the driver, the system will not mount it; instead, a CD player will be run. You don't need to mount it to copy it, either. 

Have you tried using the CD-Copy option in k3b? It works okay for me. If the audio CD can not be found, maybe it is a problem with the drive (I can imagine it not being able to read audio-CD's; it's strange, but I have seen weirder things happen). Does an AudioCD player pop up when you insert the CD in the driver?

Good luck

---

### Post by Trab on 2005-04-24
ive had this problem too, as andvaranaut said, you cannot "mount" an audio CD, but their should be some audio ripping programs in ur multimedia menu...Sound Juicer CD ripper (check synaptic if u dont have it) i havent gotten it to work well, but i havent tried hard.... also i read something about nero comming out for linux, if thats true i highly reccomend it for ripping cds (it worked well on windows...)
good luck
-Trab

---

