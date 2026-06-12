---
title: "Disc burning (and reading) problems - ubuntu 9.04 64bit"
date: 2009-05-06
forum: General Help
---

### Post by jejeman on 2009-05-06
Hello every one,

I'm having difficulties when burning cds or dvds. The issue is that when i start burning proces with brasero everything becomes "choppy": mouse pointer motion, sound and overall performance of OS.
I can see in system monitor that my cpu load is around 50%
in top:
Tasks: 122 total,   9 running, 113 sleeping,   0 stopped,   0 zombie
Cpu(s): 35.6%us, 24.4%sy,  0.0%ni,  0.0%id,  0.0%wa, 40.0%hi,  0.0%si,  0.0%st
Mem:   2034868k total,  2019532k used,    15336k free,   380412k buffers
Swap:  1108444k total,     8464k used,  1099980k free,  1151816k cached

I dont know how to calculate cpu usage in top it looks like its 100%

The speed of recording that brasero shows is 0.2x altohught i set 12x (in this example). So it estimates that recording will be 30min long. After a while when brasero reaches 50% he stops displaying the % done and looks dead with 0% done. the dvd drive is still working, and choppynes is on, speed numbers are changing so i guess burning is continued. also i can see wodim in processes. the burning is done and i can see and read all files from disc. so we can say that burning was sucessful. although brasero reports problems.
reinstalling brasero didnt change enything. I installed xfburn same thing. i installed gnomebaker it just crashes before i put all the files in compilation.
I get choppynes also when reading discs but much less than when recording.
i check the dma with hdparm and it looks ok:
DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 *udma4

In kubuntu 8.10 32bit which i had before didn't notice this issues. Also in win XP sp2 32bit i don't have this issues.
the ubuntu 9.04 64bit is clean install not an upgrade.

i'm looking for help to resolve this issue. i've attached the brasero log and hdparm info.

hardware:
Athlon64 3000
motherboard GA-K8U-939
2 GB ram
PIONEER DVD-RW  DVR-112D
Pioneer DVD-ROM ATAPIModel DVD-120S

---

### Post by danwood76 on 2009-05-06
Me and this person are having the same issue.
Possibly a bug (if he is using 64 aswell)?
[http://ubuntuforums.org/showthread.php?t=1150554](http://ubuntuforums.org/showthread.php?t=1150554)

---

### Post by bethnesbitt on 2009-07-24
Same problem here as well.  I can burn anything but multiple files.  I can even burn an iso image to a cdr but all of a sudden I cannot burn an iso image to a dvdr or multiple directory files to a dvdr.  This is the error I receive when using growisofs:
:-[ PERFORM OPC failed with SK=3h/POWER CALIBRATION AREA ERROR]: Input/output error
:confused:

> **jejeman said:**
> Hello every one,

I'm having difficulties when burning cds or dvds. The issue is that when i start burning proces with brasero everything becomes "choppy": mouse pointer motion, sound and overall performance of OS.
I can see in system monitor that my cpu load is around 50%
in top:
Tasks: 122 total,   9 running, 113 sleeping,   0 stopped,   0 zombie
Cpu(s): 35.6%us, 24.4%sy,  0.0%ni,  0.0%id,  0.0%wa, 40.0%hi,  0.0%si,  0.0%st
Mem:   2034868k total,  2019532k used,    15336k free,   380412k buffers
Swap:  1108444k total,     8464k used,  1099980k free,  1151816k cached

I dont know how to calculate cpu usage in top it looks like its 100%

The speed of recording that brasero shows is 0.2x altohught i set 12x (in this example). So it estimates that recording will be 30min long. After a while when brasero reaches 50% he stops displaying the % done and looks dead with 0% done. the dvd drive is still working, and choppynes is on, speed numbers are changing so i guess burning is continued. also i can see wodim in processes. the burning is done and i can see and read all files from disc. so we can say that burning was sucessful. although brasero reports problems.
reinstalling brasero didnt change enything. I installed xfburn same thing. i installed gnomebaker it just crashes before i put all the files in compilation.
I get choppynes also when reading discs but much less than when recording.
i check the dma with hdparm and it looks ok:
DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 *udma4

In kubuntu 8.10 32bit which i had before didn't notice this issues. Also in win XP sp2 32bit i don't have this issues.
the ubuntu 9.04 64bit is clean install not an upgrade.

i'm looking for help to resolve this issue. i've attached the brasero log and hdparm info.

hardware:
Athlon64 3000
motherboard GA-K8U-939
2 GB ram
PIONEER DVD-RW  DVR-112D
Pioneer DVD-ROM ATAPIModel DVD-120S

---

### Post by danwood76 on 2009-07-24
That sounds like a burner problem as opposed to a software issue.
DVD writing and CD writing use different lasers so its possible that the DVD laser is dying or the drive is.

My writing speed is fine now in jaunty and in karmic with brasero and nautilus.

---

### Post by claypole on 2009-11-22
Try upgrading the DVDRW firmware (worked for me) [http://ubuntuforums.org/showthread.php?t=915674](http://ubuntuforums.org/showthread.php?t=915674)

---

