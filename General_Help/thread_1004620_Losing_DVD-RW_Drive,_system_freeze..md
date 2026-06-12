---
title: "Losing DVD-RW Drive, system freeze."
date: 2008-12-07
forum: General Help
---

### Post by kubug on 2008-12-07
Hi all,

I got a problem that has me somewhat baffled. My dad has an ASUS A8V-Deluxe motherboard with a VIA K8T800 chipset. What happens to the computer (this has happened to the last 3 versions of Ubuntu, but not prior) is that the DVD Drive works for the first little while and then all of a sudden stops responding. Finally the computer will freeze after a couple of hours or days.

We already changed the DVD Drive and we tried 4 different cables. Nothing changed.

Here is the kernel log about the DVD drive first starting in DMA/66 and the slowly going down to PIO0 mode. 

```
Dec  7 09:23:52 werner-desktop kernel: [  677.128060] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
Dec  7 09:23:52 werner-desktop kernel: [  677.128090] ata3.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
Dec  7 09:23:52 werner-desktop kernel: [  677.128095]          cdb 1e 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
Dec  7 09:23:52 werner-desktop kernel: [  677.128101]          res 40/00:02:00:08:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
Dec  7 09:23:52 werner-desktop kernel: [  677.128113] ata3.00: status: { DRDY }
Dec  7 09:23:52 werner-desktop kernel: [  677.128146] ata3: soft resetting link
Dec  7 09:23:52 werner-desktop kernel: [  677.308508] ata3.00: configured for UDMA/66
Dec  7 09:23:52 werner-desktop kernel: [  677.308541] ata3: EH complete
Dec  7 09:24:02 werner-desktop kernel: [  687.309336] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
Dec  7 09:24:02 werner-desktop kernel: [  687.309366] ata3.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
Dec  7 09:24:02 werner-desktop kernel: [  687.309372]          cdb 1e 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
Dec  7 09:24:02 werner-desktop kernel: [  687.309378]          res 40/00:02:00:08:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
Dec  7 09:24:02 werner-desktop kernel: [  687.309391] ata3.00: status: { DRDY }
Dec  7 09:24:02 werner-desktop kernel: [  687.309426] ata3: soft resetting link
Dec  7 09:24:02 werner-desktop kernel: [  687.488294] ata3.00: configured for UDMA/66
Dec  7 09:24:02 werner-desktop kernel: [  687.488323] ata3: EH complete
Dec  7 09:24:12 werner-desktop kernel: [  697.488053] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
Dec  7 09:24:12 werner-desktop kernel: [  697.488080] ata3.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
Dec  7 09:24:12 werner-desktop kernel: [  697.488086]          cdb 1e 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
Dec  7 09:24:12 werner-desktop kernel: [  697.488092]          res 40/00:02:00:08:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
Dec  7 09:24:12 werner-desktop kernel: [  697.488104] ata3.00: status: { DRDY }
Dec  7 09:24:12 werner-desktop kernel: [  697.488138] ata3: soft resetting link
Dec  7 09:24:12 werner-desktop kernel: [  697.672188] ata3.00: configured for UDMA/66
Dec  7 09:24:12 werner-desktop kernel: [  697.672229] ata3: EH complete
Dec  7 09:24:22 werner-desktop kernel: [  707.672049] ata3.00: limiting speed to UDMA/44:PIO4
Dec  7 09:24:22 werner-desktop kernel: [  707.672065] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
Dec  7 09:24:22 werner-desktop kernel: [  707.672086] ata3.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
Dec  7 09:24:22 werner-desktop kernel: [  707.672089]          cdb 1e 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
Dec  7 09:24:22 werner-desktop kernel: [  707.672092]          res 40/00:02:00:08:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
Dec  7 09:24:22 werner-desktop kernel: [  707.672099] ata3.00: status: { DRDY }
Dec  7 09:24:22 werner-desktop kernel: [  707.672132] ata3: soft resetting link
Dec  7 09:24:22 werner-desktop kernel: [  707.852426] ata3.00: configured for UDMA/44
Dec  7 09:24:22 werner-desktop kernel: [  707.852454] ata3: EH complete
Dec  7 09:24:32 werner-desktop kernel: [  717.854292] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
Dec  7 09:24:32 werner-desktop kernel: [  717.854318] ata3.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
Dec  7 09:24:32 werner-desktop kernel: [  717.854324]          cdb 1e 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
Dec  7 09:24:32 werner-desktop kernel: [  717.854330]          res 40/00:02:00:08:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
Dec  7 09:24:32 werner-desktop kernel: [  717.854342] ata3.00: status: { DRDY }
Dec  7 09:24:32 werner-desktop kernel: [  717.854375] ata3: soft resetting link
Dec  7 09:24:32 werner-desktop kernel: [  718.032462] ata3.00: configured for UDMA/44
Dec  7 09:24:32 werner-desktop kernel: [  718.032487] ata3: EH complete
Dec  7 09:24:42 werner-desktop kernel: [  728.032056] ata3.00: limiting speed to UDMA/33:PIO4
Dec  7 09:24:42 werner-desktop kernel: [  728.032073] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
Dec  7 09:24:42 werner-desktop kernel: [  728.032091] ata3.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
Dec  7 09:24:42 werner-desktop kernel: [  728.032094]          cdb 1e 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
Dec  7 09:24:42 werner-desktop kernel: [  728.032097]          res 40/00:02:00:08:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
Dec  7 09:24:42 werner-desktop kernel: [  728.032104] ata3.00: status: { DRDY }
Dec  7 09:24:42 werner-desktop kernel: [  728.032137] ata3: soft resetting link
Dec  7 09:24:43 werner-desktop kernel: [  728.212320] ata3.00: configured for UDMA/33
Dec  7 09:24:43 werner-desktop kernel: [  728.212368] ata3: EH complete
Dec  7 09:24:43 werner-desktop kernel: [  728.212393] sr 2:0:0:0: ioctl_internal_command return code = 8000002
Dec  7 09:24:43 werner-desktop kernel: [  728.212402]    : Sense Key : Aborted Command [current] [descriptor]
Dec  7 09:24:43 werner-desktop kernel: [  728.212415]    : Add. Sense: No additional sense information
Dec  7 09:25:13 werner-desktop kernel: [  758.216031] ata3.00: limiting speed to PIO4
Dec  7 09:25:13 werner-desktop kernel: [  758.216042] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
Dec  7 09:25:13 werner-desktop kernel: [  758.216052] ata3.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
Dec  7 09:25:13 werner-desktop kernel: [  758.216053]          cdb 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
Dec  7 09:25:13 werner-desktop kernel: [  758.216054]          res 40/00:02:00:08:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
Dec  7 09:25:13 werner-desktop kernel: [  758.216058] ata3.00: status: { DRDY }
Dec  7 09:25:13 werner-desktop kernel: [  758.216080] ata3: soft resetting link
Dec  7 09:25:13 werner-desktop kernel: [  758.396238] ata3.00: configured for PIO4
Dec  7 09:25:13 werner-desktop kernel: [  758.396257] ata3: EH complete
Dec  7 09:25:43 werner-desktop kernel: [  788.392050] ata3.00: limiting speed to PIO3
Dec  7 09:25:43 werner-desktop kernel: [  788.392068] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
Dec  7 09:25:43 werner-desktop kernel: [  788.392087] ata3.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
Dec  7 09:25:43 werner-desktop kernel: [  788.392089]          cdb 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
Dec  7 09:25:43 werner-desktop kernel: [  788.392092]          res 40/00:02:00:08:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
Dec  7 09:25:43 werner-desktop kernel: [  788.392099] ata3.00: status: { DRDY }
Dec  7 09:25:43 werner-desktop kernel: [  788.392133] ata3: soft resetting link
Dec  7 09:25:43 werner-desktop kernel: [  788.572362] ata3.00: configured for PIO3
Dec  7 09:25:43 werner-desktop kernel: [  788.572390] ata3: EH complete
Dec  7 09:26:13 werner-desktop kernel: [  818.572050] ata3.00: limiting speed to PIO0
Dec  7 09:26:13 werner-desktop kernel: [  818.572065] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
Dec  7 09:26:13 werner-desktop kernel: [  818.572083] ata3.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
Dec  7 09:26:13 werner-desktop kernel: [  818.572086]          cdb 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
Dec  7 09:26:13 werner-desktop kernel: [  818.572089]          res 40/00:02:00:08:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
Dec  7 09:26:13 werner-desktop kernel: [  818.572097] ata3.00: status: { DRDY }
Dec  7 09:26:13 werner-desktop kernel: [  818.572127] ata3: soft resetting link
Dec  7 09:26:13 werner-desktop kernel: [  818.752436] ata3.00: configured for PIO0
Dec  7 09:26:13 werner-desktop kernel: [  818.752471] ata3: EH complete
```

All leads to believe that it is an issue with the motherboard. I have found a link here:

[https://kerneltrap.org/mailarchive/linux-kernel/2008/11/9/4108614]("https://kerneltrap.org/mailarchive/linux-kernel/2008/11/9/4108614") 

that mentions another person having issues with the A8V. The reply was that he should check his cabling. Which we did. Still nothing.

Then I found this link:

[http://ubuntuforums.org/showthread.php?t=14640]("http://ubuntuforums.org/showthread.php?t=14640")

which talks about being able to enable the DMA in /etc/modules by putting the 'via82cxxx' in there. 

MY QUESTION: Is the last link still relevant? Is this included now in the kernel? Are there other suggestions for trouble shooting?

Thanks already.

---

### Post by kubug on 2008-12-07
Ok, making the changes to /etc/modules seems to have solved nothing.

It took a lot longer now to get an error and reseting the link. But it's still doing the same thing.

```
Dec  7 11:06:07 werner-desktop kernel: [ 2194.945127] ata4: soft resetting link
Dec  7 11:06:07 werner-desktop kernel: [ 2195.124928] ata4.00: configured for UDMA/33
Dec  7 11:06:07 werner-desktop kernel: [ 2195.124957] ata4: EH complete
Dec  7 11:06:14 werner-desktop kernel: [ 2202.125124] ata4: soft resetting link
Dec  7 11:06:14 werner-desktop kernel: [ 2202.305298] ata4.00: configured for UDMA/33
Dec  7 11:06:14 werner-desktop kernel: [ 2202.305330] ata4: EH complete
Dec  7 11:06:21 werner-desktop kernel: [ 2209.305126] ata4: soft resetting link
Dec  7 11:06:21 werner-desktop kernel: [ 2209.485299] ata4.00: configured for UDMA/33
Dec  7 11:06:21 werner-desktop kernel: [ 2209.485330] ata4: EH complete
Dec  7 11:06:28 werner-desktop kernel: [ 2216.484066] ata4.00: limiting speed to UDMA/25:PIO4
Dec  7 11:06:28 werner-desktop kernel: [ 2216.484188] ata4: soft resetting link
Dec  7 11:06:28 werner-desktop kernel: [ 2216.665307] ata4.00: configured for UDMA/25
Dec  7 11:06:28 werner-desktop kernel: [ 2216.665356] ata4: EH complete
Dec  7 11:06:28 werner-desktop kernel: [ 2216.665402] sr: Sense Key : Aborted Command [current] [descriptor]
Dec  7 11:06:28 werner-desktop kernel: [ 2216.665411] sr: Add. Sense: No additional sense information
Dec  7 11:06:38 werner-desktop kernel: [ 2226.665126] ata4: soft resetting link
Dec  7 11:06:38 werner-desktop kernel: [ 2226.845297] ata4.00: configured for UDMA/25
Dec  7 11:06:38 werner-desktop kernel: [ 2226.845329] ata4: EH complete
Dec  7 11:06:48 werner-desktop kernel: [ 2236.845056] ata4.00: limiting speed to PIO4
Dec  7 11:06:48 werner-desktop kernel: [ 2236.845134] ata4: soft resetting link
Dec  7 11:06:49 werner-desktop kernel: [ 2237.025304] ata4.00: configured for PIO4
Dec  7 11:06:49 werner-desktop kernel: [ 2237.025335] ata4: EH complete
Dec  7 11:06:59 werner-desktop kernel: [ 2247.025057] ata4.00: limiting speed to PIO3
Dec  7 11:06:59 werner-desktop kernel: [ 2247.025133] ata4: soft resetting link
Dec  7 11:06:59 werner-desktop kernel: [ 2247.205330] ata4.00: configured for PIO3
Dec  7 11:06:59 werner-desktop kernel: [ 2247.205364] ata4: EH complete
Dec  7 11:07:09 werner-desktop kernel: [ 2257.205058] ata4.00: limiting speed to PIO0
Dec  7 11:07:09 werner-desktop kernel: [ 2257.205137] ata4: soft resetting link
Dec  7 11:07:09 werner-desktop kernel: [ 2257.385436] ata4.00: configured for PIO0
Dec  7 11:07:09 werner-desktop kernel: [ 2257.385467] ata4: EH complete
```

---

### Post by kubug on 2008-12-07
Ok, I found the bug report for this. I figured I wouldn't be the only one.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/231575]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/231575")

It is "good" to know too that it doesn't only happen in ubuntu. Here is the fedora forum that talks about the same issue.

[http://forums.fedoraforum.org/showthread.php?t=192186]("http://forums.fedoraforum.org/showthread.php?t=192186")

It seems that it has to do with libata and VIA chipsets.

---

