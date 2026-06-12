---
title: "16GB USB stick problems"
date: 2008-12-20
forum: General Help
---

### Post by cmistake on 2008-12-20
I'm having problems with my 16GB USB stick. When I try to copy files in to it I get stuck after a couple of seconds, then the process stops, the stick get unmounted and all I get is an error. 
First I thought the problem was with the FS, so I formatted it to Fat32 for multiplatform use. Doing that did me no good, so I thought maybe the stick is broken, and decided to test it on another machine. I plugged it into a windows machine, formatted it there to fat32 and everything worked perfectly. Now I'm stuck with this. I've even switched to another distribution while wondering what the heck is wrong, but nothing has changed. I use an external HD and USB with that works perfectly.

---

### Post by DGortze380 on 2008-12-20
> **cmistake said:**
> I'm having problems with my 16GB USB stick. When I try to copy files in to it I get stuck after a couple of seconds, then the process stops, the stick get unmounted and all I get is an error. 
First I thought the problem was with the FS, so I formatted it to Fat32 for multiplatform use. Doing that did me no good, so I thought maybe the stick is broken, and decided to test it on another machine. I plugged it into a windows machine, formatted it there to fat32 and everything worked perfectly. Now I'm stuck with this. I've even switched to another distribution while wondering what the heck is wrong, but nothing has changed. I use an external HD and USB with that works perfectly.

What is the error message?
Try moving the file via the terminal and post any output.

---

### Post by caribbean_hatch on 2008-12-20
Could be a short in your usb port to the motherboard. Check to see if it's loose. Try testing it with other usb devices...

---

### Post by mdurham on 2008-12-20
FWIW, I have two Toshiba (identical looking) sticks. One works in the front USB connectors and one doesn't. Both work 100% on the rear USB connectors. All my other sticks work on front and rear. Who knows???
Cheers, Mike

---

### Post by DGortze380 on 2008-12-21
Identical looking doesn't mean a ton... I've found things like USB hard drives and thumb drives use a lot of different power ranges... Ports also vary in power output.

---

### Post by cmistake on 2008-12-21
I get en "I/O error" when copying. While playing around I also managed to format my external HD. Damn. :) All I had there was everything, so I don't really have much left to copy to my USB stick :)

---

### Post by cmistake on 2008-12-21
I've now tested the USB stick on 2 different Windows computers, and both worked. I've tested it with 6 different USB ports on my computer, and all of them work perfectly with other devices, like my external HD, mouse and keyboard. The stick just refuses to work. I've also tried it with 2 different distributions, so the problem is not with my install. 

**dmesg** gives me this when I plug in the stick

```
[ 2399.700058] usb 6-9: new high speed USB device using ehci_hcd and address 17
[ 2399.834831] usb 6-9: configuration #1 chosen from 1 choice
[ 2399.835280] scsi9 : SCSI emulation for USB Mass Storage devices
[ 2399.842612] usb 6-9: New USB device found, idVendor=0951, idProduct=1607
[ 2399.842624] usb 6-9: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 2399.842629] usb 6-9: Product: DataTraveler 2.0
[ 2399.842633] usb 6-9: Manufacturer: Kingston
[ 2399.842637] usb 6-9: SerialNumber: 00147808E477A8C07FFF0034
[ 2399.843231] usb-storage: device found at 17
[ 2399.843238] usb-storage: waiting for device to settle before scanning
[ 2404.840322] usb-storage: device scan complete
[ 2404.841171] scsi 9:0:0:0: Direct-Access     Kingston DataTraveler 2.0 1.00 PQ: 0 ANSI: 2
[ 2405.003587] sd 9:0:0:0: [sdb] 31506432 512-byte hardware sectors (16131 MB)
[ 2405.004303] sd 9:0:0:0: [sdb] Write Protect is off
[ 2405.004313] sd 9:0:0:0: [sdb] Mode Sense: 23 00 00 00
[ 2405.004318] sd 9:0:0:0: [sdb] Assuming drive cache: write through
[ 2405.008307] sd 9:0:0:0: [sdb] 31506432 512-byte hardware sectors (16131 MB)
[ 2405.009220] sd 9:0:0:0: [sdb] Write Protect is off
[ 2405.009230] sd 9:0:0:0: [sdb] Mode Sense: 23 00 00 00
[ 2405.009235] sd 9:0:0:0: [sdb] Assuming drive cache: write through
[ 2405.009242]  sdb: sdb1
[ 2405.376008] sd 9:0:0:0: [sdb] Attached SCSI removable disk
[ 2405.376008] sd 9:0:0:0: Attached scsi generic sg2 type 0
[ 2406.140358] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!

```

Yeah, seems all good to me. Now let's see what I get when I try to copy files and get the "I/O error"

```
[ 2566.588024] usb 6-9: reset high speed USB device using ehci_hcd and address 17
[ 2581.700089] usb 6-9: device descriptor read/64, error -110
[ 2596.916045] usb 6-9: device descriptor read/64, error -110
[ 2597.132039] usb 6-9: reset high speed USB device using ehci_hcd and address 17
[ 2612.244049] usb 6-9: device descriptor read/64, error -110
[ 2627.460032] usb 6-9: device descriptor read/64, error -110
[ 2627.683356] usb 6-9: reset high speed USB device using ehci_hcd and address 17
[ 2638.088032] usb 6-9: device not accepting address 17, error -110
[ 2638.200042] usb 6-9: reset high speed USB device using ehci_hcd and address 17
[ 2648.608014] usb 6-9: device not accepting address 17, error -110
[ 2648.608054] usb 6-9: USB disconnect, address 17
[ 2648.608263] sd 9:0:0:0: Device offlined - not ready after error recovery
[ 2648.608283] sd 9:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 2648.608286] end_request: I/O error, dev sdb, sector 1010143
[ 2648.609818] sd 9:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 2648.609822] end_request: I/O error, dev sdb, sector 1010383
[ 2648.628761] sd 9:0:0:0: [sdb] READ CAPACITY failed
[ 2648.628764] sd 9:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 2648.628768] sd 9:0:0:0: [sdb] Sense not available.
[ 2648.628786] sd 9:0:0:0: [sdb] Write Protect is off
[ 2648.628788] sd 9:0:0:0: [sdb] Mode Sense: 00 00 00 00
[ 2648.628790] sd 9:0:0:0: [sdb] Assuming drive cache: write through
[ 2648.628904] sd 9:0:0:0: [sdb] READ CAPACITY failed
[ 2648.628906] sd 9:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 2648.628908] sd 9:0:0:0: [sdb] Sense not available.
[ 2648.628925] sd 9:0:0:0: [sdb] Write Protect is off
[ 2648.628927] sd 9:0:0:0: [sdb] Mode Sense: 00 00 00 00
[ 2648.628929] sd 9:0:0:0: [sdb] Assuming drive cache: write through
[ 2648.629400] __ratelimit: 12 messages suppressed
[ 2648.629403] Buffer I/O error on device sdb1, logical block 1
[ 2648.629405] lost page write due to I/O error on sdb1
[ 2648.629410] Buffer I/O error on device sdb1, logical block 510
[ 2648.629412] lost page write due to I/O error on sdb1
[ 2648.629414] Buffer I/O error on device sdb1, logical block 511
[ 2648.629416] lost page write due to I/O error on sdb1
[ 2648.629418] Buffer I/O error on device sdb1, logical block 512
[ 2648.629420] lost page write due to I/O error on sdb1
[ 2648.629422] Buffer I/O error on device sdb1, logical block 513
[ 2648.629424] lost page write due to I/O error on sdb1
[ 2648.629426] Buffer I/O error on device sdb1, logical block 514
[ 2648.629427] lost page write due to I/O error on sdb1
[ 2648.629429] Buffer I/O error on device sdb1, logical block 515
[ 2648.629431] lost page write due to I/O error on sdb1
[ 2648.629433] Buffer I/O error on device sdb1, logical block 516
[ 2648.629435] lost page write due to I/O error on sdb1
[ 2648.629437] Buffer I/O error on device sdb1, logical block 517
[ 2648.629439] lost page write due to I/O error on sdb1
[ 2648.629441] Buffer I/O error on device sdb1, logical block 518
[ 2648.629442] lost page write due to I/O error on sdb1
[ 2648.630201] FAT: bread failed in fat_clusters_flush
[ 2648.630280] FAT: unable to read inode block for updating (i_pos 16156428)
[ 2648.659588] FAT: FAT read failed (blocknr 574)
[ 2648.659727] FAT: FAT read failed (blocknr 510)
[ 2648.748327] usb 6-9: new high speed USB device using ehci_hcd and address 18
[ 2663.860045] usb 6-9: device descriptor read/64, error -110
[ 2668.185917] FAT: FAT read failed (blocknr 574)
[ 2668.186197] FAT: FAT read failed (blocknr 510)
[ 2669.267823] FAT: unable to read inode block for updating (i_pos 16156428)

```

I googled the error message I get and found out that this is propably a kernel bug. [https://launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/54273](https://launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/54273)

I used
```
sudo rmmod ehci-hcd
```

and everything seems to work just fine. Copying files on to the stick is slow, around the speed of usb 1.1, but at least it works. It is possible that the issue is with poor internal USB cabling quality of my computer, though the problem exists when I use the ports on the back of my computer. I can't fully confirm this, couse after formatting the stick around 30 times and trying everything twice I'm not even sure the stick was in usable state when I plugged it to a port on the backside of my computer.

As far as I know the command I used allows the USB device to work at lower speeds instead of ending the copy with an error like in my case. 

I'm not adding a SOLVED tag just yet. I want to hear if anyone has anything to say about this, or if there's a better solution. One that would allow me to have higher speeds. My external HD works with high speeds on the same port, so there are still some questions. Could the stick just be that crappy? Nope. It works fast on Windows systems.

---

### Post by my_key on 2008-12-31
I have exacly the same problems with my Kingston Datatraveler 16 gb. Reading from it is fine, but when writing to it I get the errors described above. The command "sudo rmmod ehci-hcd" solves the issue and my speed seems around the same as before issuing the command.

Thanks

---

### Post by my_key on 2009-01-01
I get the sames speeds after issuing that command in Ubuntu as I have in Windows XP (I had to drive to my parents to test this :) ). 

That being said, this is a very slow device to write to. Reading speeds are fine.

---

### Post by ByteJuggler on 2009-01-01
> **cmistake said:**
> I get en "I/O error" when copying. While playing around I also managed to format my external HD. Damn. :) All I had there was everything, so I don't really have much left to copy to my USB stick :)

Try Testdisk or as a last resort, Photorec or Foremost/Scalpel/MagicRescue or similar, to see if you can get your data (or some of it) back.    [This page]("https://help.ubuntu.com/community/DataRecovery#head-d6059ccf5604d2fbce38a1274ea79c6c0a2e94fb") and [this page ]("http://goinggnu.wordpress.com/2008/02/14/recover-deleted-files-from-memory-card/")may be useful.

---

