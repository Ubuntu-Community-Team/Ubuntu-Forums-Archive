---
title: "Wierd harddrive errors since Dapper upgrade"
date: 2006-06-23
forum: Desktop Environments
---

### Post by eniacpx on 2006-06-23
Ever since I upgraded my breezy system to dapper, I continuously get these errors in my syslog:

```

[17264667.884000] ide: failed opcode was: unknown
[17264667.884000] end_request: I/O error, dev hdb, sector 160432210
[17264667.884000] Buffer I/O error on device hdb1, logical block 160432147
[17264669.468000] hdb: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[17264669.468000] hdb: dma_intr: error=0x40 { UncorrectableError }, LBAsect=1604
32207, high=9, low=9437263, sector=160432207
[17264669.468000] ide: failed opcode was: unknown
[17264669.468000] end_request: I/O error, dev hdb, sector 160432207
[17264669.468000] Buffer I/O error on device hdb1, logical block 160432144
[17264671.008000] hdb: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[17264671.008000] hdb: dma_intr: error=0x40 { UncorrectableError }, LBAsect=1604
32208, high=9, low=9437264, sector=160432208
[17264671.008000] ide: failed opcode was: unknown
[17264671.008000] end_request: I/O error, dev hdb, sector 160432208
[17264671.008000] Buffer I/O error on device hdb1, logical block 160432145
[17264672.540000] hdb: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[17264672.540000] hdb: dma_intr: error=0x40 { UncorrectableError }, LBAsect=1604
32209, high=9, low=9437265, sector=160432209
[17264672.540000] ide: failed opcode was: unknown
[17264672.540000] end_request: I/O error, dev hdb, sector 160432209
[17264672.540000] Buffer I/O error on device hdb1, logical block 160432146
[17264674.084000] hdb: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[17264674.084000] hdb: dma_intr: error=0x40 { UncorrectableError }, LBAsect=1604
32210, high=9, low=9437266, sector=160432210
[17264674.084000] ide: failed opcode was: unknown
[17264674.084000] end_request: I/O error, dev hdb, sector 160432210
[17264674.084000] Buffer I/O error on device hdb1, logical block 160432147
[17264675.656000] hdb: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[17264675.656000] hdb: dma_intr: error=0x40 { UncorrectableError }, LBAsect=1604
32207, high=9, low=9437263, sector=160432207
[17264675.656000] ide: failed opcode was: unknown
[17264675.656000] end_request: I/O error, dev hdb, sector 160432207
[17264675.656000] Buffer I/O error on device hdb1, logical block 160432144
[17264677.216000] hdb: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[17264677.216000] hdb: dma_intr: error=0x40 { UncorrectableError }, LBAsect=1604
32208, high=9, low=9437264, sector=160432208
[17264677.216000] ide: failed opcode was: unknown
[17264677.216000] end_request: I/O error, dev hdb, sector 160432208
[17264677.216000] Buffer I/O error on device hdb1, logical block 160432145
[17264678.756000] hdb: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[17264678.756000] hdb: dma_intr: error=0x40 { UncorrectableError }, LBAsect=1604
32209, high=9, low=9437265, sector=160432209
[17264678.756000] ide: failed opcode was: unknown
[17264678.756000] end_request: I/O error, dev hdb, sector 160432209
[17264678.756000] Buffer I/O error on device hdb1, logical block 160432146
[17264680.308000] hdb: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[17264680.308000] hdb: dma_intr: error=0x40 { UncorrectableError }, LBAsect=1604
32210, high=9, low=9437266, sector=160432210
[17264680.308000] ide: failed opcode was: unknown
[17264680.308000] end_request: I/O error, dev hdb, sector 160432210
[17264680.308000] Buffer I/O error on device hdb1, logical block 160432147

```

The above message show up hundreds of times over the past several days.

When this starts to happen the drive remounts itself read-only. Any ideas?

---

### Post by Sniffer on 2006-06-23
Did you make an Update from Breezy to Dapper

or

Clean Install of Dapper??

---

### Post by eniacpx on 2006-06-23
Update from Breezy.

---

### Post by Sniffer on 2006-06-23
[QUOTE=eniacpx]Update from Breezy.[/QUOTE]

Well maybe your update do Dapper just ruin your system...and you got that I/O erros.. i dont think either that you will get much replies to solve this one.

So i would suggest that you copy your vital data and do a clean install of Dapper...that should put your system error free.

PS: I don't know why but i never trusted Big updates.... most of the times brings annoying probs](*,) 

Like updating win2k to winxp.

---

### Post by ifokkema on 2006-06-23
Did you do a fsck check on that drive?

---

### Post by Ocxic on 2006-06-23
yes do an fsck on the drive. also if fsck gives you any errors, i would suggest using your harddrive manufacture's diagnostic on that drive, ussually said software can be downloaded from ther manufactures site for free.

---

### Post by eniacpx on 2006-06-23
fsck just kinda sits there, with no obvious status change, or progress, and it generates more of these errors in the console. I am going to try an fsck from and old live cd and see what I get.

---

### Post by ifokkema on 2006-06-24
[QUOTE=eniacpx]fsck just kinda sits there, with no obvious status change, or progress, and it generates more of these errors in the console. I am going to try an fsck from and old live cd and see what I get.[/QUOTE]
Do you have a different OS that you can test the drive with? Maybe a Breezy Live CD somewhere? Just to be 100% sure this ain't a driver problem. If fsck starts complaining about these errors, maybe there's something wrong with your IDE cable/controller?

---

### Post by efaithfarm on 2006-06-27
[QUOTE=eniacpx]Ever since I upgraded my breezy system to dapper, I continuously get these errors in my syslog:

```

[17264667.884000] ide: failed opcode was: unknown
[17264667.884000] end_request: I/O error, dev hdb, sector 160432210
[17264667.884000] Buffer I/O error on device hdb1, logical block 160432147
[17264669.468000] hdb: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[17264669.468000] hdb: dma_intr: error=0x40 { UncorrectableError }, LBAsect=1604
32207, high=9, low=9437263, sector=160432207
[17264669.468000] ide: failed opcode was: unknown
[17264669.468000] end_request: I/O error, dev hdb, sector 160432207
[17264669.468000] Buffer I/O error on device hdb1, logical block 160432144
[17264671.008000] hdb: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[17264671.008000] hdb: dma_intr: error=0x40 { UncorrectableError }, LBAsect=1604
32208, high=9, low=9437264, sector=160432208
[17264671.008000] ide: failed opcode was: unknown
[17264671.008000] end_request: I/O error, dev hdb, sector 160432208
[17264671.008000] Buffer I/O error on device hdb1, logical block 160432145
[17264672.540000] hdb: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[17264672.540000] hdb: dma_intr: error=0x40 { UncorrectableError }, LBAsect=1604
32209, high=9, low=9437265, sector=160432209
[17264672.540000] ide: failed opcode was: unknown
[17264672.540000] end_request: I/O error, dev hdb, sector 160432209
[17264672.540000] Buffer I/O error on device hdb1, logical block 160432146
[17264674.084000] hdb: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[17264674.084000] hdb: dma_intr: error=0x40 { UncorrectableError }, LBAsect=1604
32210, high=9, low=9437266, sector=160432210
[17264674.084000] ide: failed opcode was: unknown
[17264674.084000] end_request: I/O error, dev hdb, sector 160432210
[17264674.084000] Buffer I/O error on device hdb1, logical block 160432147
[17264675.656000] hdb: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[17264675.656000] hdb: dma_intr: error=0x40 { UncorrectableError }, LBAsect=1604
32207, high=9, low=9437263, sector=160432207
[17264675.656000] ide: failed opcode was: unknown
[17264675.656000] end_request: I/O error, dev hdb, sector 160432207
[17264675.656000] Buffer I/O error on device hdb1, logical block 160432144
[17264677.216000] hdb: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[17264677.216000] hdb: dma_intr: error=0x40 { UncorrectableError }, LBAsect=1604
32208, high=9, low=9437264, sector=160432208
[17264677.216000] ide: failed opcode was: unknown
[17264677.216000] end_request: I/O error, dev hdb, sector 160432208
[17264677.216000] Buffer I/O error on device hdb1, logical block 160432145
[17264678.756000] hdb: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[17264678.756000] hdb: dma_intr: error=0x40 { UncorrectableError }, LBAsect=1604
32209, high=9, low=9437265, sector=160432209
[17264678.756000] ide: failed opcode was: unknown
[17264678.756000] end_request: I/O error, dev hdb, sector 160432209
[17264678.756000] Buffer I/O error on device hdb1, logical block 160432146
[17264680.308000] hdb: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[17264680.308000] hdb: dma_intr: error=0x40 { UncorrectableError }, LBAsect=1604
32210, high=9, low=9437266, sector=160432210
[17264680.308000] ide: failed opcode was: unknown
[17264680.308000] end_request: I/O error, dev hdb, sector 160432210
[17264680.308000] Buffer I/O error on device hdb1, logical block 160432147

```

The above message show up hundreds of times over the past several days.

When this starts to happen the drive remounts itself read-only. Any ideas?[/QUOTE]

I'm having this same issue, except for a few quirks:

1. This is what happens when i boot, and it keeps going for close to ten minutes and then i get a root prompt. (That's when i use the recovery console.)
2. After getting the root prompt, i tried doing startx kdm and it gave me errors saying that xterm wasn't installed. 
3. I ran apt-get install kubuntu-desktop and realized that somehow the entire Kubuntu desktop was no longer installed. This concerned me.
4. For some reason, i can't get apt-get to complete the installation of the kubuntu-desktop package, as it now says "Temporary failure resolving 'archive.ubuntu.com'". I really don't think it's my internet connection, since i dual-boot with Windows XP and have no problems connecting to the internet on that side. It has also given me the same thing on two different connections, one at work and one at my folks' house. Just 33.6 MB left to download, too. It seemed to be working for a while, as it had 200+ MB when it started, but it stopped resolving the address at one point and now it's stuck.

My system is a Dell Inspiron B120, and I had been running Breezy without incident before trying to upgrade everything. Any help would be greatly appreciated!

---

### Post by ifokkema on 2006-06-28
[QUOTE=efaithfarm]I'm having this same issue, except for a few quirks:

1. This is what happens when i boot, and it keeps going for close to ten minutes and then i get a root prompt. (That's when i use the recovery console.)
2. After getting the root prompt, i tried doing startx kdm and it gave me errors saying that xterm wasn't installed. 
3. I ran apt-get install kubuntu-desktop and realized that somehow the entire Kubuntu desktop was no longer installed. This concerned me.
4. For some reason, i can't get apt-get to complete the installation of the kubuntu-desktop package, as it now says "Temporary failure resolving 'archive.ubuntu.com'". I really don't think it's my internet connection, since i dual-boot with Windows XP and have no problems connecting to the internet on that side. It has also given me the same thing on two different connections, one at work and one at my folks' house. Just 33.6 MB left to download, too. It seemed to be working for a while, as it had 200+ MB when it started, but it stopped resolving the address at one point and now it's stuck.

My system is a Dell Inspiron B120, and I had been running Breezy without incident before trying to upgrade everything. Any help would be greatly appreciated![/QUOTE]
Sounds to me like Linux had problems reading/writing to your root partition. It threw errors, freaked out, and gave you the recovery console to fix it.
startx, installing kubuntu-desktop and all that, are attempts to continue either way. Chances are however, that the problem is getting worse when you try to ignore this error. Results from running any of these commands are not reliable, since Linux has problems with it's root partition.

Boot from the Live CD and fsck your drive and soon as possible.

---

