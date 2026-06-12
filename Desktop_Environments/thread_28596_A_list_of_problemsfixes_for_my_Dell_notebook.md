---
title: "A list of problems/fixes for my Dell notebook"
date: 2005-04-20
forum: Desktop Environments
---

### Post by Pausanias on 2005-04-20
I have installed Hoary on my Dell Precision M70. Here is a review of the system for those of you who are interested.

[Notebookreviews.com review](http://www.notebookreview.com/forums/topic.asp?TOPIC_ID=14929)

I am making a list of problems I've had on the machine, and how I've fixed them, in the hopes that it may help others who have been having issues with a Dell. I am only listing issues that I could not resolve by searching the forums or reading the [Ubuntu Guide](http://www.ubuntuguide.org). Please read the Ubuntu Guide before posting questions here. I will update this list as I have further information. Please post on this topic if you have any further information.

[list]
[*]**Problem**: On an NVIDIA system, the X11 screen always freezes after boot. The graphical screen comes up, the mouse cursor works, but I just see Ubuntu freeze on the brown screen.

**Solution**: The answer is to install the NVIDIA drivers and upgrade to the 2.6.12 kernel. For a detailed howto, check out [https://wiki.ubuntu.com/InstallingUbuntuOnADellPrecisionM70](https://wiki.ubuntu.com/InstallingUbuntuOnADellPrecisionM70)


[*]**Problem**: OK, I upgraded, and everything seems to work great, except that now I get random freezes once a week or so. They are completely unpredictable, and no messages are written to any logs. Mouse and keyboard are frozen, and there is no way to access or reboot the computer except by holding down the power button.

**Solution**: *If* your freezes are completely random and irreproducible *and* none of the system logs show any error messages just before the freeze, the likely culprit is bad I/O handling of your optical (CD or  DVD) drive. You won't believe this, but the solution is to always leave a CD in your drive. There is a problem in the 2.6 kernel with libata. A patch in the works to fix it. Until then, just stick a CD-ROM in there and you should be OK. Post here if it doesn't work for you. Read more on this [on this Inspiron 9300 page](http://rtr.ca/dell_i9300/).


[*] **Problem**: How do I get GNOME to open certain files with my preferred applications, instead of the default ones (e.g. Totem for video files)?

**Solution**: Basically, you should create a directory structure called .local/share/applications, copy certain files from /usr/share/applications, and edit them. Here is an example of how to change the default player for movies from totem to vlc, assuming you've installed vlc:
```

cd
mkdir -p .local/share/applications
cd .local/share/applications
sed "s/[Tt]otem/gvlc/g" /usr/share/applications/defaults.list > defaults.list
sed "s/[Tt]otem/gvlc/g" /usr/share/applications/mimeinfo.cache >mimeinfo.cache

```
The above code replaces the word and command "totem" for "gvlc" in the relevant files. defaults.list controls double-click actions on your desktop, while mimeinfo.cache controls helper applications. "gvlc" refers to the "/usr/share/applications/gvlc.desktop" created when you installed vlc. You could also create your own ".desktop" file and put it in the .local/share/applications directory. To do the same for mplayer, just replaced gvlc with mplayer in the above. 
Note that I did not always have success getting this to work inside firefox, but luckily firefox allows you to specify helper applications by hand. Be aware that firefox handling of wmv files appears to be [buggy](https://bugzilla.mozilla.org/show_bug.cgi?id=250914).


[*] **Problem**: I want to try the official NVIDIA drivers directly from their site. When I try to uninstall the nvidia-kernel-common module as recommended [here](http://www.ubuntulinux.org/support/documentation/faq/Official_nVidia), (syn)apt(ic) wants to uninstall a package called linux-686 or linux-386. Is this safe to do? Will it uninstall my kernel?

**Solution**: Yes, it is safe. That is a placeholder package in the restricted repository and not needed by the system. The kernel image is in a different package.


[*]**Problem**: My sound speakers work fine, but when I plug in a headphone, no sound comes out, out of the speakers or out of the headphones.

Edit: As a poster below mentions, my original solution was overkill. Under  Applications->Sound and Video->Volume Control, select the ALSA control panel from the File menu and turn on the headphones. 

[/list]

---

### Post by diebels on 2005-04-20
[QUOTE=Pausanias]sudo apt-get install alsamixergui
alsamixergui &[/QUOTE]gnome-volume-control does not have this if you change the the displayed device from oss-mixer to alsa-mixer?

---

### Post by Pausanias on 2005-04-21
[QUOTE=diebels]gnome-volume-control does not have this if you change the the displayed device from oss-mixer to alsa-mixer?[/QUOTE]

It does, but I didn't know it was there at the time. Pretty obscure for a first time user if you ask me.

---

### Post by usergentoo on 2005-04-21
It seems the Nvidia drivers are not playing well with the 2.6 kernel. I dont beleive its nvidia I would imagine its the kernel. You can use the old drivers 6111, and they work with 2.6 kernel but not the 7xxx series.

You can also drop back to the 2.4 kernel and the 7174 drivers work. 

Ive notice thie same problems on the Nvidia forums, Gentoo forums, Mandrake forums, and several other linux forums. 

So for the time being Im sticking with the "nv" drivers. Hopefully someone will find a fix soon.

---

### Post by Pausanias on 2005-04-22
Updated with more information on the nvidia freeze bug and with a GNOME helper applications hint.

---

### Post by Pausanias on 2005-06-13
Posted an update describing my final fix for the random hard-freezing problem.

---

### Post by usergentoo on 2005-06-13
This is how I fixed mine and other laptops I own, gateway, toshiba, and a dell.
In the bios there is a setting for your display. One being lcd the other being crt and another being crt/lcd. I choose the crt/lcd and all my laptops with the geforce go now work. 

I didnt have to change anything in any config files for it to work. i left everthing default with a fresh install of Ubuntu and added the nvidia drivers. And it worked out of the box.

I also tried several different live cd distro's and they all work now also.
I wish i did this 2 years ago when I was still using gentoo.

Anyway maybe this will help. ive noticed on other forums Ive posted this it helped several people.

---

### Post by Pausanias on 2005-06-16
Well, at least on the Precision M70, that option in the BIOS is now gone. The BIOS in the Precision laptops has many options missing compared to my old Inspiron 4100. There is no lcd/crt (though there still is a button), and there is no hardware control of the screen-off function.

Incidentally, I could not get xscreensaver to turn off my precision's screen with 2.6.10; with 2.6.11, it now works beautifully.

---

### Post by Pausanias on 2005-06-26
Updated to point to the Wiki describing the exact procedure for upgrading to the Breezy kernel: [https://wiki.ubuntu.com/InstallingUbuntuOnADellPrecisionM70](https://wiki.ubuntu.com/InstallingUbuntuOnADellPrecisionM70)

---

### Post by samjam on 2005-07-05
With the original Hoary kernel I could write my DVD's about 50% of the time, usually only the first attempt after a boot, and then I would have to reboot.

I have followed the instructions to update to kernel 2.6.12 (thanks; BTW these need ammending to instruct to remove/purge nvidia-glx otherwise [I believe] /etc/init.d/nvidia busts up the glx lib symlinks and then X won't start unless you disable glx or uninstall the nvidia driver followed by nvidia-glx and then re-install the nvidia drivers]

ANYWAY

I still get 50% failures writing DVD,s with error messages like this:

[4296015.180000] ata2: command 0xa0 timeout, stat 0xd0 host_stat 0x21
[4296015.180000] SCSI error : <1 0 0 0> return code = 0x2

Sometimes it works, sometimes it doesn't.  No pattern.

Any clues?

I'm running hoary 5.04 with all the updates and kernel 2.6.12 and gcc 3.4 as per the instructions

(BTW should we symlink back to gcc 3.3 after compiling the kernel and nvidia drivers?)

Sam

---

### Post by Pausanias on 2005-07-05
> **samjam]With the original Hoary kernel I could write my DVD's about 50% of the time, usually only the first attempt after a boot, and then I would have to reboot.

I have followed the instructions to update to kernel 2.6.12 (thanks said:**
>  /etc/init.d/nvidia busts up the glx lib symlinks and then X won't start unless you disable glx or uninstall the nvidia driver followed by nvidia-glx and then re-install the nvidia drivers]

ANYWAY

I still get 50% failures writing DVD,s with error messages like this:

[4296015.180000] ata2: command 0xa0 timeout, stat 0xd0 host_stat 0x21
[4296015.180000] SCSI error : <1 0 0 0> return code = 0x2

Sometimes it works, sometimes it doesn't.  No pattern.

Any clues?

I'm running hoary 5.04 with all the updates and kernel 2.6.12 and gcc 3.4 as per the instructions

(BTW should we symlink back to gcc 3.3 after compiling the kernel and nvidia drivers?)

Sam
 Thanks for the info; I'll update the wiki.

Regarding the DVD burning problem, what machine are you using, what specs?

On my precision m70 I've only tried burning CDs so far (using burn:// in Nautilus). It's worked fine and burned with maximum speed. I'll try to burn a DVD at some point this week when I get a chance and post the result here.

---

### Post by samjam on 2005-07-06
I'm using a full-spec'd Dell Precision M70
Intel(R) Pentium(R) M processor 2.00GHz

The dvd writer is identified thus:
Jul  5 09:08:55 localhost kernel: [4294669.487000] ata1: dev 0 cfg 49:2b00 82:346b 83:5b29 84:6003 85:3469 86:9a09 87:6003 88:203f
Jul  5 09:08:55 localhost kernel: [4294669.487000] ata1: dev 0 ATA, max UDMA/100, 195371568 sectors:
Jul  5 09:08:55 localhost kernel: [4294669.491000] ata1: dev 0 configured for UDMA/100
Jul  5 09:08:55 localhost kernel: [4294669.491000] scsi0 : ata_piix
Jul  5 09:08:55 localhost kernel: [4294669.491000]   Vendor: ATA       Model: FUJITSU MHV2100A  Rev: 0000
Jul  5 09:08:55 localhost kernel: [4294669.491000]   Type:   Direct-Access                      ANSI SCSI revision: 05
Jul  5 09:08:55 localhost kernel: [4294669.491000] ata2: SATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xBFA8 irq 15
Jul  5 09:08:55 localhost kernel: [4294669.796000] ata2: dev 0 cfg 49:0b00 82:0210 83:1000 84:0000 85:0000 86:0000 87:0000 88:0407
Jul  5 09:08:55 localhost kernel: [4294669.796000] ata2: dev 0 ATAPI, max UDMA/33
Jul  5 09:08:55 localhost kernel: [4294669.796000] ata2: dev 0 configured for UDMA/33
Jul  5 09:08:55 localhost kernel: [4294669.796000] scsi1 : ata_piix
Jul  5 09:08:55 localhost kernel: [4294669.797000]   Vendor: SONY      Model: DVD+-RW DW-D56A   Rev: PDS3
Jul  5 09:08:55 localhost kernel: [4294669.797000]   Type:   CD-ROM                             ANSI SCSI revision: 05
Jul  5 09:08:55 localhost kernel: [4294669.808000] Attached scsi generic sg0 at scsi0, channel 0, id 0, lun 0,  type 0
Jul  5 09:08:55 localhost kernel: [4294669.809000] Attached scsi generic sg1 at scsi1, channel 0, id 0, lun 0,  type 5
Jul  5 09:08:55 localhost kernel: [4294669.815000] SCSI device sda: 195371568 512-byte hdwr sectors (100030 MB)
Jul  5 09:08:55 localhost kernel: [4294669.815000] SCSI device sda: drive cache: write back
Jul  5 09:08:55 localhost kernel: [4294669.815000] SCSI device sda: 195371568 512-byte hdwr sectors (100030 MB)
Jul  5 09:08:55 localhost kernel: [4294669.815000] SCSI device sda: drive cache: write back
Jul  5 09:08:55 localhost kernel: [4294669.815000]  /dev/scsi/host0/bus0/target0/lun0: p1 p2 p3 p4 < p5 p6 p7 p8 >
Jul  5 09:08:55 localhost kernel: [4294669.899000] Attached scsi disk sda at scsi0, channel 0, id 0, lun 0
Jul  5 09:08:55 localhost kernel: [4294669.908000] sr0: scsi3-mmc drive: 62x/62x writer cd/rw xa/form2 cdda tray
Jul  5 09:08:55 localhost kernel: [4294669.908000] Uniform CD-ROM driver Revision: 3.20
Jul  5 09:08:55 localhost kernel: [4294669.908000] Attached scsi CD-ROM sr0 at scsi1, channel 0, id 0, lun 0

The output:
Jul  6 09:34:29 localhost kernel: [4297123.541000] ata2: command 0xa0 timeout, stat 0xd0 host_stat 0x21
Jul  6 09:34:29 localhost kernel: [4297123.541000] SCSI error : <1 0 0 0> return code = 0x2

is generated from a command such as
growisofs -Z /dev/dvd -J /path/to/some/files

dvdrecord also fails but not with scsi timeouts (which prevent growisofs from being killed) but sense errors which I will post in a minute after I reboot. (I'm expirementing with mkisofs and growisofs on the dvd image as that worked last night)

Sam

---

### Post by Pausanias on 2005-07-06
Hi. I was able to write a DVD without problems (using mkisofs + right clicking on the iso on the desktop). However, I did check my dmesg and it seems I have a different DVD writer:

[4294671.552000] ata1: dev 0 ATA, max UDMA/100, 117210240 sectors: lba48
[4294671.552000] ata1: dev 0 configured for UDMA/100
[4294671.552000] scsi0 : ata_piix
[4294671.552000]   Vendor: ATA       Model: HTS726060M9AT00   Rev: MH4O
[4294671.552000]   Type:   Direct-Access                      ANSI SCSI revision
: 05
[4294671.553000] ata2: SATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xBFA8 irq 15
[4294671.874000] ata2: dev 0 cfg 49:0b00 82:0000 83:0000 84:0000 85:0000 86:0000
 87:0000 88:0407
[4294671.874000] ata2: dev 0 ATAPI, max UDMA/33
[4294671.891000] ata2: dev 0 configured for UDMA/33
[4294671.891000] scsi1 : ata_piix
[4294671.927000]   Vendor: _NEC      Model: DVD+-RW ND-6500A  Rev: 202C
[4294671.927000]   Type:   CD-ROM                             ANSI SCSI revision
: 05
[4294671.969000] Attached scsi generic sg0 at scsi0, channel 0, id 0, lun 0,  ty
pe 0
[4294671.969000] Attached scsi generic sg1 at scsi1, channel 0, id 0, lun 0,  ty
pe 5

---

### Post by samjam on 2005-07-07
Well for the second time, growisofs to burn an already created DVD seems to work fine, so indications are that growisofs ... -J ..., when it forks and pipes the ISO back to itself, are the ones that have the scsi timeout.

I still think this is a kernel problem as it leaves the main growisofs process in an un-killable state and strace attached also cannot be killed, however the temp solution may lie in growisofs, I'll do some more tests to be sure and then make a report here and possibly to the growisofs developers.

Sam

---

### Post by samjam on 2005-07-07
No joy; "works fine" meant "has actually started writing" although my laptop locked up at the end (I'm getting more crashes since I upgraded to 2.6.12 than on 2.6.10)

However after boot, burning an ISO gives the same scsi timeout.

Without wanting you to waste DVD's, I would be interested to knowif it is persistently successful with your NEC writer.

Sam

---

### Post by samjam on 2005-07-07
I'm open to the possibility that it could be bad DVD media so I will try on windows, but here is how dvdrecord fails, but does not lock up the dvd writer until reboot
(Interesting is the "dvdrecord: Input/output error. write_g1: scsi sendcmd: no error" message)

# dvdrecord -dao dev=1,0,0 driveropts=burnfree OO.iso

Cdrecord 1.11a15 (i386-pc-linux-gnu) Copyright (C) 1995-2001 J\uffffrg Schilling
scsidev: '1,0,0'
scsibus: 1 target: 0 lun: 0
Linux sg driver version: 3.5.33
Using libscg version 'schily-0.7'
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   :
Vendor_info    : 'SONY    '
Identifikation : 'DVD+-RW DW-D56A '
Revision       : 'PDS3'
Device seems to be: Generic mmc2 DVD.
Using generic SCSI-3/mmc DVD-R(W) driver (mmc_mdvd).
Driver flags   : SWABAUDIO BURNFREE
Supported modes: PACKET SAO
Starting to write CD/DVD at speed 2 in write mode for single session.
Last chance to quit, starting real write in 0 seconds. Operation starts.
trackno=0
dvdrecord: Turning BURN-Free on
dvdrecord: Input/output error. write_g1: scsi sendcmd: no error
CDB:  2A 00 00 19 82 C6 00 00 1F 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 0A 00 00 00 00 21 02 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x21 Qual 0x02 (invalid address for write) Fru 0x0
Sense flags: Blk 0 (not valid)
cmd finished after 0.006s timeout 200s
write track data: error after 0 bytes
Sense Bytes: 70 00 00 00 00 00 00 0A 00 00 00 00 00 00 00 00 00 00

I will also check for new firmware for the drive

Sam

---

### Post by Pausanias on 2005-07-07
OK, I will try to burn a DVD using growisofs when I get a chance.

Here is another thought. If 2.6.10 works better for you, use 2.6.12 to make the image, and then when you're ready to burn a DVD, boot into recovery mode in 2.6.10, and do the burning there.

Personally, I can't see how Linux can be ready for the desktop when it has all these problems running on new hardware. Linux for a server is great, sure, but on the desktop you really can't have all these random problems/freezes and be competitive. Sure, the die-hard crowd like us will live with it, but personally I think it's a bit of a shame that the default Windows installation is more stable than the default Hoary installation on our system (Precision M70, and quite a few Dell Latitudes as well).

---

### Post by samjam on 2005-07-08
My windows colleagues are also having DVD writing problems.

Dell have release (and withdrawn?) a firmware update linked from many places as [http://ftp.us.dell.com/rmsd/R102639.EXE](http://ftp.us.dell.com/rmsd/R102639.EXE) but no longer there.

The google cache of a [http://216.239.59.104/search?q=cache:j3Qv3qtQnicJ:support.dell.com/support/downloads/type.aspx%3Fc%3Dus%26cs%3DRC956904%26l%3Den%26s%3Dhied%26SystemID%3DLAT_PNT_PM_D600%26os%3DWW1%26osl%3Den%26deviceid%3D8102+DW-D56A+firmware&hl=en&client=firefox](http://216.239.59.104/search?q=cache:j3Qv3qtQnicJ:support.dell.com/support/downloads/type.aspx%3Fc%3Dus%26cs%3DRC956904%26l%3Den%26s%3Dhied%26SystemID%3DLAT_PNT_PM_D600%26os%3DWW1%26osl%3Den%26deviceid%3D8102+DW-D56A+firmware&hl=en&client=firefox) dell support page shows that it fixes some media problems but this page is no longer available.

I did track it down to [ http://support.jp.dell.com/jp/jp/download/document.asp?dn=302819]( http://support.jp.dell.com/jp/jp/download/document.asp?dn=302819)Dell Japan but I am consulting Dell technical support before I try it.

I also note that I get HAL failures and a refusing to shutdown or even sync if I boot with a blank DVD in the DVD drive. Where should I report this?

Sam

---

### Post by samjam on 2005-07-08
No joy under linux with upgraded firmware, I tried the dell-recalled PDS6 and also some LiteOn PST3 which is a few months newer than my original PDS3 but still no joy.

I don't get a SCSI timeout but I get DVD write protect errors and such stuff so I can't write anything, so I'm back to PDS3. I'll need to do some more tests against windows with the various versions to show where the problem lies, I will report more news when I get it, but not for a few days.

Sam

---

### Post by samjam on 2005-07-15
Its just as bad under windows, with two different types of media so I'm taking it up with Dell.

As for the scsi timeout, I think it is just that - linux gives up sooner that windoes does, its nothing particularly "wrong" with the kernel.

The Lite-On firmware and the Dell PDS6 software quickly reject the disk.

Anyway, Dell identify a hardware fault by this error:
Sense: 03  ASC: 73  ASCQ: 03 (Command 2A)

and will send a replacement drive.

Sam

---

### Post by Pausanias on 2005-07-15
I was still experiencing random freezes despite the upgrade to 2.6.12. Looks like somebody finally found out why. It was libata. It seems the DVD drives shipping with some Dell systems are confusing libata---basically, the polling system for seeing whether a  CD has been inserted in the drive was causing the system to freeze up. The solution for now is to leave a CDROM in your drive if you are still experiencing irreproducible random freezes. Seems to have worked for me thus far. I have updated the top post to reflect this.

---

### Post by samjam on 2005-08-17
[QUOTE=Pausanias]I was still experiencing random freezes despite the upgrade to 2.6.12. Looks like somebody finally found out why. It was libata. It seems the DVD drives shipping with some Dell systems are confusing libata---basically, the polling system for seeing whether a  CD has been inserted in the drive was causing the system to freeze up. The solution for now is to leave a CDROM in your drive if you are still experiencing irreproducible random freezes. Seems to have worked for me thus far. I have updated the top post to reflect this.[/QUOTE]

Yep, this tip works for me too, tested over a couple of weeks.

Thanks

Sam

---

### Post by samjam on 2005-09-09
For those of us with the Sony DVD writer who have been plagued with problems, DELL have released PDS7 firmware update recetly, which I hope will give us all joy.

No more timeouts that require reboots, etc etc

Sam

---

### Post by conorb on 2005-09-23
Hey,

I'm wondering if anyone has had any luck with suspend and/or hibernate with the M70?

On the wiki's hardware support page it says that suspend *does* work

For me, the suspend itself seems to work but the machine won't resume. It comes up and the CD-Rom gets some activity but the screen doesn't come on and the attached USB mouse doesn't come back to life.

Has anyone tried the hibernate package? Software suspend 2 sounds promising..

I'm using breezy at the moment (though it isn't very up to date)

Thanks for any help!

Conor

---

### Post by samjam on 2005-10-06
[QUOTE=conorb]Hey,
I'm wondering if anyone has had any luck with suspend and/or hibernate with the M70?
On the wiki's hardware support page it says that suspend *does* work
For me, the suspend itself seems to work but the machine won't resume. It comes up and the CD-Rom gets some activity but the screen doesn't come on and the attached USB mouse doesn't come back to life.
Has anyone tried the hibernate package? Software suspend 2 sounds promising..
I'm using breezy at the moment (though it isn't very up to date)
Thanks for any help!
Conor[/QUOTE]

I've been looking at the NVidia docs for their mobile 3D chipsets and suspend support. For windows Nvidia won't supply drivers! You MUST get them from the laptop manufacturer, who do all the freaky suspend putting and and such. 

Perhaps (I don't know) their linux drievrs don't suspend well; I don't know.

Sam

---

### Post by Alexander Kirillov on 2005-10-07
[QUOTE=Pausanias]
 **Problem**: How do I get GNOME to open certain files with my preferred applications, instead of the default ones (e.g. Totem for video files)?

**Solution**: Basically, you should create a directory structure called .local/share/applications, copy certain files from /usr/share/applications, and edit them.[/QUOTE]

Why not use the standard way of doing it, as described, e.g.,  [here]("http://ubuntuguide.org/#changedefaultfiletypeprogram")?

---

### Post by sympeltun on 2007-02-15
im not sure if someone figured out the problem with your ubuntu not playing sound through headphones.. please try double clicking on teh volume icon on your gnome bar.. then enabling the headphone support. 

i'm hoping that would solve the problem..

Good luck in your quest to making your laptop ubuntu problems go away.

---

