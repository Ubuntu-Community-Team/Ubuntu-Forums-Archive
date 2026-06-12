---
title: "Review of Dell XPS 410n with Ubuntu Feisty preinstalled"
date: 2007-06-01
forum: Dell  Ubuntu Support
---

### Post by benanzo on 2007-06-01
[CENTER][SIZE="6"]Dell XPS 410n with Ubuntu Feisty preinstalled[/SIZE][/CENTER]

I received my XPS with Ubuntu today.  The first thing I will say is that when the Fedex guy delivered it he asked if Dell was having some kind of liquidation sale because he has delivered more Dells today than ever before.  He told me that he had already delivered five and there were eleven more on the truck.  (Just throwing that out there.)
[SIZE="2"][B]
First impression:[/B][/SIZE]

Opening the box I was immediately met with a glaring view of the Windows Vista logo on the giant instruction poster.  The instructions detailed how to use the remote that comes bundled with Vista for use with Vista Media Center (among other things.)  Uggh.  I quickly discarded that to the side.  I rifled through the other documentation provided searching for any sign of a Quick Start pamphlet for Ubuntu...no luck.  Nothing whatsoever in the paper documentation mentioned Ubuntu in any way and nowhere did I even see the Ubuntu logo.  In fact, the Dell XPS 410 Owner's Manual offers a significant amount of information for troubleshooting drivers, but it was all Windows-specific.  Nowhere in the box was an Ubuntu 7.04 "Feisty Fawn" install disc.  No discs of any kind.
[COLOR="Red"]UPDATE:[/COLOR]
After being contacted by Dell, I was informed that I *should have* received an Ubuntu install disc with the system.  I did not, however.  And after reviewing some others' experiences with their machines, I realize that I am in the minority of those who didn't get the disc.

**[SIZE="2"]Specifications:[/SIZE]**

XPS 410n, Intel Core 2 Duo Processor E6420 (2.13GHZ,1066FSB) with 4MB cache
2GB DDR2 SDRAM at 667MHz
NVIDIA GeForce 7300 LE
500GB Serial ATA II Hard Drive(7200RPM)
16X DVD+R/RW CD-RW Combination Drive
Integrated Audio
No monitor (I use an ACER AL1916W 19" Widescreen with DVI)
375 Watt PSU

[SIZE="2"]**First Power-On:**[/SIZE]

I hooked up my gear and powered it on.  This machine is remarkably silent.  The disk spun up and the Dell BIOS screen appeared.  I was required to accept the DELL EULA by pressing "any key" in order to continue the boot process:
[IMG]http://www.starlitworld.com/dell_with_ubuntu/images/EBTS_ENG.BMP[/IMG]

GRUB flashed it's 2 second warning then the familiar Ubuntu Feisty bootsplash appeared.  After a few seconds I was met with a new user wizard set against the default Feisty wallpaper.  This wizard asked me to choose a username/password and a timezone.  I entered the data appropriately and was then sent to the GDM login.  I entered my information and the Ubuntu desktop appeared.  The hostname is preset as **dell**.

[COLOR="Red"]UPDATE:[/COLOR]
The GRUB menu lists an entry for booting to a recovery environment, which I assume is /dev/sda2 (see below).
Here's the [/boot/grub/menu.lst]("http://www.starlitworld.com/dell_with_ubuntu/menu_lst.txt")


**[SIZE="2"]Problems:[/SIZE]**

**Screen Resolution**
My native resolution of 1440x900 was not recognized immediately.  While I don't think this should be a surprise to anyone with a widescreen monitor, I was slightly disappointed.  Since I did not order a Dell monitor with this machine, I cannot say whether it would be the case with those also.  I do, however, think that Dell took some steps to attempt resolution autodetection for some of *(their)* monitors since the default /etc/X11/xorg.conf file included many resolution modes which I don't think it would have otherwise.  X did not see fit to use mine (though it was listed) so it defaulted to 1024x768.  This was an easy fix by going to **System -> Preferences -> Screen Resolution** and changing it, which took effect immediately and without further tinkering.

**Restriced Drivers Manager - nVidia**
Didn't work.  It said it was doing something and showed the nice little download and install meter, then it asked me to reboot...then it killed X when it came back up.  
I had to do this manually:
```
sudo apt-get install nvidia-glx
```
```
sudo dpkg-reconfigure xserver-xorg
```
Select **nvidia** as the driver, not **nv**.

This worked like a charm on the first try (which happened to be while I was in a console after X died.)
[COLOR="Red"]UPDATE:[/COLOR]
In my contact with Dell, I was told that the process of installing the proprietary *nvidia* module via **Restricted Drivers Manager** was tested pretty thoroughly.  And from my review of other accounts with similar hardware, this problem was, again, uncommon.  I am not willing to rule out user error though I followed the obvious steps to enable this functionality.  I will do a system restore in the coming days to re-test this process and will report back.

[COLOR="Red"]UPDATE:[/COLOR]
I have run through a reinstall from the Recovery Console (which was a breeze - took 12 mins to get a factory-default system back.  That's impressive.)  Unfortunately the same problem with resolution detection cropped up again.  This time it defaulted to 1400x1050.
Here's the default [/etc/X11/xorg.conf]("http://www.starlitworld.com/dell_with_ubuntu/FIRST_BOOT-xorg.conf.txt")
Here's the [/var/log/Xorg.0.log]("http://www.starlitworld.com/dell_with_ubuntu/FIRST_BOOT-Xorg.0.log.txt")
You might notice that X thought I was attached to a KVM...which wasn't true.  I tried both DVI and D-SUB connections, both with the same results.  I believe these files are from a D-SUB connection.
The good news though, was that **Restricted Manager** did install the proprietary *nvidia* module without hassle the second go around.  (I wonder if this was related to DVI vs D-SUB and the improper resolution detection? I wish I'd kept the logs from the first time.)  When the machine came back after the *nvidia* module was installed, the proper 1440x900 resolution was present in the **System -> Preferences -> Screen Resolution** menu, and changing it was trivial.

The standard kernel **2.6.20-16-generic** is installed.
[here's the config]("http://www.starlitworld.com/dell_with_ubuntu/config-2.6.20-16-generic.txt")

Dell's configuration of my disk:

```
ben@dell:~$ sudo parted
GNU Parted 1.7.1
Using /dev/sda
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) print                                                            

Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
 1      32.3kB  49.4MB  49.3MB  primary   fat16             
 2      49.4MB  2204MB  2155MB  primary   fat32             
 3      2204MB  2410MB  206MB   primary   ext3         boot 
 4      2410MB  500GB   498GB   extended               lba  
 5      2410MB  5059MB  2649MB  logical   linux-swap        
 6      5059MB  500GB   495GB   logical   ext3              

(parted)
```

[IMG]http://www.starlitworld.com/dell_with_ubuntu/images/Screenshot--dev-sda%20-%20GParted.png[/IMG]

You might be wondering what the two vfat partitions at the front of the disk are:
**/dev/sda1** mounts to **/media/DellUtility**
```
ben@dell:/media/DellUtility$ ls
Adaptec2.mdm  DELLBIO.BIN   IMchEcc.mdm   Nic.mdm       System.mdm
Adaptec.mdm   Dellboot.exe  INT15_88.COM  Parallel.mdm  UsbBist.mdm
ami_raid.mdm  DELLDIAG.COM  IoApic.mdm    Pci.mdm       UsbDevID.mdm
AUTOEXEC.BAT  DELLDIAG.EXE  IR.mdm        Perc2Ada.mdm  USBEHCI.mdm
AUTOEXEC.UP   DellDiag.INI  Keyboard.mdm  PM.MDM        UsbKbd.mdm
BiosMp.mdm    DELLRMK.BIN   LSI.mdm       Pnp.mdm       UsbMass.mdm
CABLES.mdm    DellSys.msm   Memory.mdm    Raid.mdm      Usb.mdm
Cache.mdm     DELLTBUI.EXE  MiscPci.mdm   Scsi.mdm      UsbMouse.mdm
COMMAND.COM   DIR.LST       Mouse.mdm     SEAL.EXE      USBOHCI.mdm
CONFIG.SYS    Diskette.mdm  MpCache.mdm   SEAL.INI      UsbTm.mdm
CONFIG.UP     Disk.mdm      mpmemory.exe  Serial.mdm    UsbUfi.mdm
COPYUP.BAT    Dvd.mdm       NbBatt.MDM    Smbios.mdm    USBUHCI.mdm
Cpu.mdm       GenAudio.mdm  Nbfan.MDM     SMBus.mdm     Video.mdm
DDInit.mim    HDAudio.mdm   NbSvc.MDM     Smi.mdm
DDINIT.MLM    Iaudio.mdm    Nbtherm.MDM   SYMTREE.INI
DELL          IEEE1394.mdm  nic8254x.MDM  SYSBDMON.mdm
```
What is this??
[COLOR="Red"]UPDATE:[/COLOR]
I wont be clearing this partition after all, since *magicfab* pointed out that it is a Dell hardware diagnostics environment implemented in DOS.  I have the tendancy to jump to conclusions when I see anything .EXE

**/dev/sda2** mounts to **/media/OS**
```
ben@dell:/media/OS$ ls
autoexec.bat  COMMAND.COM  DELLBIO.BIN  initrd.gz  misc     ub704img.tgz
cmd.cfg       debs         DELLRMK.BIN  LINLD.COM  scripts  vmlinuz
```

The *debs* directory is empty.  This partition contains a couple utilities to rescue your system like fdisk, vim, etc.

[COLOR="Red"]UPDATE:[/COLOR]
It was suggested below by the keen eyes of *kkass* that the *ub704img.tgz* listed above might be the Ubuntu install image, which turns out to be correct.  I missed that.  I assume that when you boot to the System Restore console, it reinstalls Ubuntu from this image.

[LSPCI]("http://www.starlitworld.com/dell_with_ubuntu/lspci.txt")
[LSUSB]("http://www.starlitworld.com/dell_with_ubuntu/lsusb.txt")

Everything else about the system is rather unremarkable.  It works the same way any other Ubuntu system would.  Beryl installed and runs great (after the nvidia driver was installed properly.)  It uses the default Ubuntu repositories, nothing Dell-specific.  There are no Dell logos anywhere on the desktop and nothing in the menus.  There is no crapware (AKA unsolicited software trial-versions) installed anywhere obvious.  This is basically a vanilla Feisty install.  The only tinkering Dell did, (I think), was add some resos to xorg.conf and add some recovery/diagnostic partitions.

All the essential hardware functions properly.  This includes (non-accelerated) graphics via the Free *nv* driver (default).  Hibernation and suspend both work out of the box with both the *nv* driver and the *nvidia* driver.  All sound playback/recording works without hassle.  This includes headphone sensing, which has been trouble for some.  The CD/DVD-R/W works as it should for burning/erasing discs.  I have not investigated CPUfreq scaling, but will soon.

I cracked open the case and had a look inside and was delighted. They'v got some crazy fan-thing on the CPU that spins almost entirely silently. Everything inside is removable just by lifting a lever or two, or by pinching a clamp. It is very easy to add/remove drives etc. Both the hard disk and the DVD-r/w that shipped with it are SATA2. There are a total of 6 SATA channels, 1 IDE channel (if I remember right) for two drives master/slave, 1 floppy, 3 PCI, 1 PCI-E x16, 2 PCI-E x1, 6 rear USB, 2 front USB, front panel mic/headphone jacks. There is room for a total of two 3.5" internal drives and 2 external 5.25" drives as well as 2 external 3.5" slot for floppy or mem. card reader etc. As I said, everything snaps in/out. It is extremely trivial to add/remove hardware.


[SIZE="2"]**Final Thoughts:**[/SIZE]

I think Dell has done a good thing with this system.  They obviously made an effort with resolution detection (which was going to be sore no matter what) and did an excellent job of keeping the crapware off the system.  If you want a machine that's going to run all the apps you need and do it *well*, and without having to research endlessly for compatible hardware to make one yourself, this machine is good for you.  I have seen nothing that makes this a deal-breaker for the average user...assuming they don't want to enable 3D out of the box.  That still takes some skills.

[COLOR="Red"]UPDATE:[/COLOR]
For more information regarding Dell's Ubuntu machines, they have a [wiki]("http://linux.dell.com/wiki/index.php/Ubuntu_7.04") and a [mailing list]("http://lists.us.dell.com/mailman/listinfo/linux-desktops") (where the Dell devs hang out.)

I want comments!

[COLOR="Red"]AFTER THOUGHTS:[/COLOR]

There have been quite a few criticisms of Dell and Ubuntu regarding the **Restricted Manager** debacle killing my X Server when it rebooted.  I think this criticism is misguided.  It is important to remember whose ultimate fault that was: *nVidia's*.  Ubuntu's ability (or inability) to smoothly load a proprietary module is worthless if we can't support it, if we can't *own* it.  I am sure the nVidia developers can't help but agree.  They no doubt work hard to get their GPUs up-to-snuff for even the most demanding GNU/Linux user.  They are hackers at heart, just like us.  But unfortunately the company that employs them sees them as nothing more than ones and zeros.  Their paychecks are just an impact on the bottom line.  This minimalism strikes deep with every developer of Free software.  If we make it, we *own* it, and we share it to make it better.  Every bullet needs to fly at nVidia.  Or not.  They may never get the clue.  They may just decide to keep their secrets and for that they may just find a smaller and smaller crowd singing their praises.

---

### Post by stmiller on 2007-06-01
Wow very interesting about the partitions. And no Ubuntu CD included? That is rather unexpected. Anyways great review, thanks for the info!

---

### Post by magicfab on 2007-06-01
> **benanzo said:**
> I can, however, assume that Dell took some steps to attempt resolution autodetection for some of *(their)* monitors since the default /etc/X11/xorg.conf file included many resolution modes which I don't think it would have otherwise.
Regarding video, no, this is actually a vanilla install, just as if you had installed from the CD (except for partitioning), using the OEM mode, plus some additions.


> **benanzo said:**
> **/dev/sda1** mounts to **/media/DellUtility**
```
ben@dell:/media/DellUtility$ ls
Adaptec2.mdm  DELLBIO.BIN   IMchEcc.mdm   Nic.mdm       System.mdm
Adaptec.mdm   Dellboot.exe  INT15_88.COM  Parallel.mdm  UsbBist.mdm
ami_raid.mdm  DELLDIAG.COM  IoApic.mdm    Pci.mdm       UsbDevID.mdm
AUTOEXEC.BAT  DELLDIAG.EXE  IR.mdm        Perc2Ada.mdm  USBEHCI.mdm
AUTOEXEC.UP   DellDiag.INI  Keyboard.mdm  PM.MDM        UsbKbd.mdm
BiosMp.mdm    DELLRMK.BIN   LSI.mdm       Pnp.mdm       UsbMass.mdm
CABLES.mdm    DellSys.msm   Memory.mdm    Raid.mdm      Usb.mdm
Cache.mdm     DELLTBUI.EXE  MiscPci.mdm   Scsi.mdm      UsbMouse.mdm
COMMAND.COM   DIR.LST       Mouse.mdm     SEAL.EXE      USBOHCI.mdm
CONFIG.SYS    Diskette.mdm  MpCache.mdm   SEAL.INI      UsbTm.mdm
CONFIG.UP     Disk.mdm      mpmemory.exe  Serial.mdm    UsbUfi.mdm
COPYUP.BAT    Dvd.mdm       NbBatt.MDM    Smbios.mdm    USBUHCI.mdm
Cpu.mdm       GenAudio.mdm  Nbfan.MDM     SMBus.mdm     Video.mdm
DDInit.mim    HDAudio.mdm   NbSvc.MDM     Smi.mdm
DDINIT.MLM    Iaudio.mdm    Nbtherm.MDM   SYMTREE.INI
DELL          IEEE1394.mdm  nic8254x.MDM  SYSBDMON.mdm
```

This is going to get deleted ASAP.  What is this?? A Windows recovery partition?  Did anyone say anything about Windows??

Windows ? These are DOS-based utilities. This is a diagnostics partition. It's a good idea to keep that around at least initially.

> **/dev/sda2** mounts to **/media/OS**
```
ben@dell:/media/OS$ ls
autoexec.bat  COMMAND.COM  DELLBIO.BIN  initrd.gz  misc     ub704img.tgz
cmd.cfg       debs         DELLRMK.BIN  LINLD.COM  scripts  vmlinuz
```

The *debs* directory is empty.  This partition contains a couple utilities to rescue your system like fdisk, vim, etc.

This is the recovery partition.

Regarding the lack of a CD I would call Dell and ask about that!

Cheers,

---

### Post by benanzo on 2007-06-01
good info, I will keep it around for a little while.

---

### Post by kkass on 2007-06-01
I agree with magicfab, keep those dell tools around.  Also, take a quick look at 'ub704img.tgz'.  It is very likely that is the Ubuntu install CD.  I would also bet that you can boot to that partition somehow.

Can you halt Grub and take a look at what options it gives you.  Posting /boot/grub/menu.lst might be interesting as well.  Alternately, take a look at the bios boot options and see what happens when you boot to their recovery partitions.

---

### Post by benanzo on 2007-06-01
I checked the GRUB boot menu and there is an entry for booting to a recovery environment.
I've updated the review.

---

### Post by wormser on 2007-06-01
Did it come with a Designed for Ubuntu Linux?

[IMG]http://zune-downloadz.com/designedforubuntu.jpg[/IMG]

---

### Post by benanzo on 2007-06-01
nope

---

### Post by dwasifar on 2007-06-01
Interesting that it comes with a recovery partition.  I pulled a Dell rep into chat the other day to ask about that, and he assured me with complete certainty that there was no recovery partition, only CDs.

---

### Post by benanzo on 2007-06-01
Or, in my case, no CDs, only recovery partitions.

---

### Post by octathlon on 2007-06-02
Thanks a lot for the review, benanzo!  I wonder why they put the utilities and recovery partitions at the beginning.  I'd rather have the /boot partition first.

---

### Post by orrorin on 2007-06-02
Howz the fan noise? Are you able to run sensors?

I've the XPS 410 with GeForce 8600 GTS; waiting for the beta drivers to stabilize a li'l more. Meanwhile , using the "nv" drivers. Hopefully, when I update the drivers, the fan noise will go away.

---

### Post by HotShotDJ on 2007-06-02
> **dwasifar said:**
>  I pulled a Dell rep into chat the other day to ask about that, and he assured me with complete certainty that there was no recovery partition, only CDs.I generally don't believe what they tell me in Dell's Live Chat.  Earlier this week I was trying to find something, and the person in Dell Live Chat insisted (with complete certainty!) that Dell does not sell any systems with Linux pre-installed -- even after I gave her the link to their Ubuntu systems.  Their representatives do not have up-to-date information.

---

### Post by smoker on 2007-06-02
hme, good review, thanks,

compared to some of the scathing reviews i've read of vista, it seems dell are moving in the right direction with ubuntu.

would you say a complete linux noob could connect and surf, print, etc, with no prior knowledge of ubuntu?

---

### Post by benanzo on 2007-06-02
Absolutely.  Every essential hardware function works perfect out of the box.  Even though the correct resolution was not detected immediately, it would be trivial for a new user to find their proper setting in the menu and adjust it.

---

### Post by frogotronic on 2007-06-02
> **benanzo said:**
> Absolutely.  Every essential hardware function works perfect out of the box.  Even though the correct resolution was not detected immediately, it would be trivial for a new user to find their proper setting in the menu and adjust it.

Do SUSPEND and HIBERNATE work?

Thanks,
- CH

:popcorn:

---

### Post by ageilers on 2007-06-02
Nice to see a major manufacturer stepping up to offer an alternative. Dell is obviously looking for ways to regain it crown. Dell with Opensource, Dell at Walmart.

All Dells come with the Diagnostic partition. It is accessible by hitting the F12 key during POST at startup. This will bring up the alternative boot menu for booting to CD, diskette, USB, etc. as well as BIOS setup and the Diagnostic. Better having it on the hard drive than downloading the 5 floppy set (you probably did not get the floppy drive option anyway). 

It would have been nice of Dell to print some documentation, but they would most likely be creating more garbage that 95% of us would immediately throw in the trash. It works out of the box, can't complain. Most people who are going to order Dell w/Ubuntu know what they are getting into.

---

### Post by librano on 2007-06-02
hi and thanks for the review,

have you tried connecting any peripherals to the machine... eg printer, scanner, digital camera, Palm, etc... did they work? do you know if you plugged in Dell peripherals would they be guaranteed to work out of the box? and to repeat a question... did suspend and hibernation work?

ps. oh and how about posting some cool pics of your new dell with ubuntu... i want to see! maybe a youtube video ;-)

---

### Post by DC@DR on 2007-06-02
Very nice and detailed review.
But I still wonder that why there's no manual or instruction pamphlet of any kind related to Ubuntu (but instead pointing to Vista, wtf?!). That would be good to have smth that instruct average users or point them to the places where they can find help like these Ubuntu forums (Hey, now I think that is it the Dell-Ubuntu deal that they don't include any support instruction so as to force users to pick the support service from Canonical?! If that so, it's BAD behaviour! :-(

---

### Post by psyopper on 2007-06-02
I'm pretty sure that the Windows inserts happen further down the assembly line from the OS install point. Pretty sure the drives get flashed before assembly and the brainers that package don't know and aren't shown the difference between their Linux and Windows machines when it comes time to throw the extras in the box.

It would be nice if there WAS an insert for new Ubuntu users, at least with some rudamentary information about what Linux is and where to go for help.

Next question... Is the Firefox homepage set to the local "Welcome to Ubuntu" page? That may be what Dell accepted as acceptable information for new users...

---

### Post by MepisReign on 2007-06-02
I just sent some emails to friends, I used to work for Dell as a Tech Support Manager. I asked about why the nvidia driver is not preinstalled when it really should since the first impression is the most important one. If I buy a new computer I hope it works perfect right out of the box.
On every Dell OS installation there is always a small FAT32 partition containing the Diagnostics Utility, that utility have the purpose to test the hardware on your computer, don't delete it if you don't have to.

Regards

MepisReign

---

### Post by moscowtime on 2007-06-02
I suspect, that you are not completely correct about the absense of distribution CD. 

Just go to sda2, untar the "ub704img.tgz" and burn the image to CD.

I guess you will have a good install CD for Ubuntu 7.04 (plain vanilla)

Cheers and best wishes
BNK.

---

### Post by trinaryouroboros on 2007-06-02
Aw this is so sad, I had faith in Dell, too. :(

---

### Post by benanzo on 2007-06-02
I've had a day or so now to test all the (non-essential) hardware features of the machine:

- Suspend and Hibernate work perfectly.
- Sound playback works, including headphone jack sensing
- Sound recording works great (Line, rear Mic, front Mic)  I don't have a digital interface so I can't test SPDIF.

I don't have any Dell peripherals (besides the mouse and keyboard that came with the machine) so I can't test if there is any Dell-specific functionality (I doubt it.)

Despite Dell claiming support for their printers with a PostScript driver, I still highly recommend getting an HP printer (which is what I have.)  HP has provided fantastic Free drivers and I don't see any reason why they shouldn't still be recommended over the competition.

As I mentioned in the review, this machine is incredibly quiet.  I cracked open the case and had a look inside and was delighted.  They'v got some crazy fan-thing on the CPU that spins almost entirely silently.  Everything inside is removable just by lifting a lever or two, or by pinching a clamp.  It is very easy to add/remove drives etc.  Both the hard disk and the DVD-r/w that shipped with it are SATA2.  There are a total of 6 SATA channels, 1 IDE channel (two drives master/slave), 1 floppy, 3 PCI, 1 PCI-E x16, 2 PCI-E x1, 6 rear USB, 2 front USB, 1 rear IEEE1394, front panel mic/headphone jacks.  There is room for a total of two 3.5" internal drives and 2 external 5.25" drives as well as 2 external 3.5" slot for floppy or mem. card reader etc.  As I said, everything snaps in/out.  It is extremely trivial to add/remove hardware.

---

### Post by Sweet Mercury on 2007-06-02
> **wormser said:**
> Did it come with a Designed for Ubuntu Linux?

[IMG]http://zune-downloadz.com/designedforubuntu.jpg[/IMG]

I would be surprised if it *was* designed for Ubuntu Linux. This is a new offering, the first try at such a major company breaking away from Windows. So it's probably just put together with the most compatible hardware and such.

The next generation might be actually designed for Ubuntu.

As for the Install CD, maybe since Ubuntu has a new release every 6 months, they don't consider it necessary? A Windows XP reinstall disk would be good for a couple of years, at least.

---

### Post by trinaryouroboros on 2007-06-02
Why in gods name wouldn't they have sent a couple test machines to the Ubuntu team before actually manufacturing and shipping the damn things? This is senseless!

Well, all in all it's looking to be a fun show

:popcorn:

---

### Post by sillygates on 2007-06-02
Thats not the recovery mode from their partition.

As you can see it uses a UUID to identify the partition it needs to boot off of, the UUID is the same in all 3 entries. (its probably single user mode on the running kernel).


I don't know why they mount the recovery partition, it seems like a sumb idea to me. rm -rf / will wipe out the recovery partition along with everything else this way. (unless of course its read only, is it?)

---

### Post by A*p on 2007-06-02
> Restriced Drivers Manager - nVidia
Didn't work. Sure, it said it was doing something and even showed a nice little download and install meter, then it asked me to reboot...then it killed X when it came back up.

How the hell did that not get flagged up in testing? :confused:

---

### Post by Christophe Vanlancker on 2007-06-02
I think it's just normal that Dell doesn't ship Ubuntu cds since they do the same strategy with windows pcs... They just make a a few partitions for their own to put the diagnose apps and the recovery mode in it.

They actually do this with windows because of microsofts crapy security.... If you activate the key of one install cd and register your windows.... and suddenly you want to reinstall windows for what reason so ever, you get windows to say you don't have a proper activation key and the system gives you 30 days to do so.

The trick Dell uses is to recover the system from that special partition... That copy it keeps stored in there is already authenticated, so no mater what happens, you can always restore windows without it asking you for the license key.

They now do the same with Ubuntu... but it isn't really necessary... they could have given you the cd... but on the other hand what if you lost the cd?.... Big deal you say because you can download it off the net.  But it is clear that Dell has customized slightly their version of Ubuntu they keep in the partition.... plus it saves some time than to have to downloaded it back and all.

---

### Post by syko21 on 2007-06-02
Any word on the dell ubuntu laptop?

---

### Post by lynxus on 2007-06-02
I find the lack of CD very bad on Dells part.

Now im assuming most of the people buying one will already know what they are doing.
However!

If we want to bring linux to the mainstream we have to start assuming otherwise!

What of someone turned it on, Entered the wrong setting, screwed up X and was now stuck with a machine with no GUI and no idea what to do?

Ohh lets re-install?

Goes to grab CD provided by the vendor....... .   .    .








Wel done Dell for taking the first step. But please can we all learn from Dells first little mistakes?



.

---

### Post by jrusso2 on 2007-06-02
I don't understand why Dell does not include the Nvidia driver installed by default?  I thought this was supposed to be the only proprietary drive installed.

Anyway it seems like Dell is making a lot of mistakes here and despite them people are buying them.

---

### Post by benanzo on 2007-06-02
It is my understanding that neither Dell nor Ubuntu can ship the proprietary nVidia modules installed by default because it violates the GPL.  (I might be wrong) But I thought you can't ship binary-only modules linked into the kernel without source.  They have to be installed explicitly by the user after-the-fact.

---

### Post by rushtrader on 2007-06-02
> **Christophe Vanlancker said:**
> They actually do this with windows because of microsofts crapy security.... If you activate the key of one install cd and register your windows.... and suddenly you want to reinstall windows for what reason so ever, you get windows to say you don't have a proper activation key and the system gives you 30 days to do so.

That is incorrect.  Dell, and many other major manufacturers, have a special key embedded into their BIOS that Windows recognizes and matches with special certificates on the Dell version of Wndows, which allows it to bypass registration.  You can use any Dell Windows CD on any Dell PC made in the last few years.  Take a machine that was loaded with Windows XP Home and load Windows XP Pro onto it.  It works - just like that.  No registration needed.  I have not tried it with Windows Vista on any of the newer machines, but I would imagine that it likely works.  See e.g.: [http://news.softpedia.com/news/Dell-HP-and-Sony-OEM-Certificates-Used-in-Windows-Vista-Activation-Cracks-48034.shtml](http://news.softpedia.com/news/Dell-HP-and-Sony-OEM-Certificates-Used-in-Windows-Vista-Activation-Cracks-48034.shtml)

RT

---

### Post by duojet on 2007-06-02
if that is true about a bios key for windows (and I'm pretty sure it is, from my experience), what are the odds one could do a dual boot without a key on an ubuntu dell? Considering they were sloppy(?) enough to package vista docs (and that will probably be fixed soon), I wouldn't be totally shocked if they hadn't actually changed the bios. 

however with that said, I'm not sure how many people would care or want a DB setup. I installed that way so my wife could use skype with video, but the novelty's worn off and I haven't booted into windows in months. 

Overall it looks like Dell could be forgiven for the early mistakes. Hopefully this keeps up so that Linux fans can buy near bleeding edge at volume discounts. Of course for this to be the case, more people have to buy them than just a fraction of the existing community. We're SO close to making this something novices can enjoy (my informal standard being anything that takes more than three clicks or a command line to set up is too much for a noob).

---

### Post by rmmst49 on 2007-06-02
how about wireless networking?  did that come up automatically?

also, my two cents:  

it's too bad that dell decided to ship a video card with no available free software 3d drivers available.  It shows that they are interested in selling machines to the community but not supporting the community (as much as they are interested in clearing out old inventory from their video-card warehouse).  

I will buy a machine from dell when EVERYTHING works out of the box like any new computer purchase should.  Like it would if they used hardware that is compatible with free software, i.e. native kernel && xorg drivers.

until then i'm gonna stick with thinkpad's.  the new x61 tablet in particular . . .

---

### Post by jrusso2 on 2007-06-02
> **benanzo said:**
> It is my understanding that neither Dell nor Ubuntu can ship the proprietary nVidia modules installed by default because it violates the GPL.  (I might be wrong) But I thought you can't ship binary-only modules linked into the kernel without source.  They have to be installed explicitly by the user after-the-fact.

How does Freespire do this then?
When I read those articles about Dell selling this I am pretty sure it mentioned that the nvidia driver was going to be the only proprietary driver installed.

---

### Post by gfahey on 2007-06-02
Maybe I'm missing something but, wouldn't it be better to be able to buy a Dell with no OS installed? I'd much rather install my own version of Ubuntu or Debian Etch and configure it. It looks like you'll have to do this anyways so, what's the point of the pre-installed? I mean, if this intended for noobs they will never be able to run anything in terminal (at least not immediately). 

I think it's great to have Dell provide this but, since it's a free distro how much do you pay Dell to do what you can do on your own? 

Come on Dell, give me the option of a virgin computer and let me deflower it. So to speak. I'd buy one. I have plenty of distros lying around and would love that option.

---

### Post by Technophobia on 2007-06-02
> Anyway it seems like Dell is making a lot of mistakes here and despite them people are buying them.

Everyone makes mistakes when starting something new, so give Dell a break. If they don't address the problem soon then people will eventually stop buying

---

### Post by Brian Boyko on 2007-06-02
> **stmiller said:**
> Wow very interesting about the partitions. And no Ubuntu CD included? That is rather unexpected. Anyways great review, thanks for the info!

That's actually par for the course with Dell.  When I reviewed the [XPS 400 for HardOCP]("http://www.hardocp.com/article.html?art=OTI0") back in December 2005, we didn't get a windows CD or even a quick-restore disk-image-on-CD CD.  The only disc image was on the hard drive... 

We considered this absolutely stupid a the time because your ONLY recovery solution: A) Required you to put back all the junk spyware you removed.  B) Required you to lose all the data on the hard drive (instead of installing Windows Over Windows, which sometimes works for recovering from a misconfigured boot sector... oh, and speaking of which... C) did absolutely nothing to protect you in case something ate your boot sector, whether User Error, Spyware, DRM, or Virus.  

Now - Dell has taken those concerns to heart since then and fixed most everything that we pointed out in that article - with a few slip-ups from time to time, but they usually get back on track soon enough.  Here, I'm not nearly as concerned about not having a CD shipped with the product, because unlike Windows, you can just download the latest ISO and burn it.  So if you have an Internet connection, you can get your restore disc.  

Brian Boyko
Author, [30 Days with Linux]("http://consumer.hardocp.com/article.html?art=MTI5OCwxLCxoY29uc3VtZXI=")
Editor, [Network Performance Daily]("http://www.networkperformancedaily.com")

---

### Post by lzy2k1 on 2007-06-02
Talking about the partitions, i have a dell inspiron 6400 with vista home premium (i know im in a ubuntu forum) but i thougt you should know it includes 4 partitions by default:

1: 40 so mbs, its the dell utility thing
2: 10gbs, using vistas own image recovery tool, it has a vista image that will reset the machine to shipped state (can be accessed through system recovery)
3: 99gbs, main partition
4: 2gbs, dell media direct, to watch dvds and movies, listen to music and even watch power point presentations without login to windows.

I havent tried to install ubuntu on this machine because i heard somewhere there was a limit to 3 main partitions per disk, wich are already occupied in my hdd (all but the dell media direct thing). is this true?

oh, and my pc didnt include that much crapware because most of it is for us customers, and i bought it in south america.

---

### Post by bmartin on 2007-06-02
> **jrusso2 said:**
> I don't understand why Dell does not include the Nvidia driver installed by default?  I thought this was supposed to be the only proprietary drive installed.

Anyway it seems like Dell is making a lot of mistakes here and despite them people are buying them.
I agree. If you're buying this computer to move from Windows to Linux, the proprietary drivers should be included. People will want them (I'm glad they had the sense to go with Nvidia). I was told that Dell (and other OEMs) don't ship Windows CDs anymore in an attempt by MS to reduce piracy; there's absolutely no reason that Dell shouldn't include an OS to restore the computer to its original state.

This comes across as very unprofessional to me. I like what Dell's doing, but most of us could've done a better job handling the bundling issues. Maybe Dell should start recruiting from the Ubuntu forums.

---

### Post by sloggerkhan on 2007-06-02
> **gfahey said:**
> Maybe I'm missing something but, wouldn't it be better to be able to buy a Dell with no OS installed? I'd much rather install my own version of Ubuntu or Debian Etch and configure it. It looks like you'll have to do this anyways so, what's the point of the pre-installed? I mean, if this intended for noobs they will never be able to run anything in terminal (at least not immediately). 

I think it's great to have Dell provide this but, since it's a free distro how much do you pay Dell to do what you can do on your own? 

Come on Dell, give me the option of a virgin computer and let me deflower it. So to speak. I'd buy one. I have plenty of distros lying around and would love that option.

Dell does sell comps w/o OS :
(free dos)
[http://www.dell.com/content/topics/segtopic.aspx/ubuntu?c=us&l=en&s=dhs](http://www.dell.com/content/topics/segtopic.aspx/ubuntu?c=us&l=en&s=dhs)

---

### Post by gfahey on 2007-06-02
Is there (finally) support for 5.1 Surround? 

I have never been able to get that with my old Creative Live 5.1. This is one annoyance I wish would be addressed.

Great to hear that suspend and hibernate work though. That's always driven me nuts. I'm looking to get a good laptop for Ubuntu and hopefully Dell will iron out the little irks by then.

---

### Post by bmartin on 2007-06-02
> **lzy2k1 said:**
> I havent tried to install ubuntu on this machine because i heard somewhere there was a limit to 3 main partitions per disk, wich are already occupied in my hdd (all but the dell media direct thing). is this true?
There's a limit to 4 primary partitions, but it's possible to put several other partitions on a single disk. I've never had to use more than 4. I usually use one for /boot, one for swap, and one for /, but on Gentoo installs, one for Portage is useful (Reiser is much faster for compilation). I could see why someone would want to have a fifth, in case they were mounting /home remotely using NFS.

---

### Post by benanzo on 2007-06-02
First thing, everything in the machine except 3D acceleration with the nVidia card is supported by Free drivers.  The only (serious) problem I encountered was when trying to install the proprietary nVidia module, which killed X.  We all know that the proprietary module is totally unsupported and it should be no surprise that it is not installed by default and that it may not be trivial for a non-skilled user to try to get to work. It doesn't matter what the specific problem was to the unknowing user just that when they reboot and it drops to a console with a bunch of X errors, that's bad.  Had I not tried to install the nVidia module, I would have had zero problems whatsoever -- except that I had to select my reso from the list manually which was done while I was still using the *nv* driver.

I know how to install the nVidia module.  I know how to troubleshoot X.  I was just taking the most obvious steps to try and replicate what a new user would do, and that obviously failed.

Ultimately, this is nVidia's problem.  Ubuntu and Dell are simply trying to make the best of a bad situation.  Direct your complaints to nVidia.

The very best thing I think Ubuntu can do in the future to minimize the potential for a new user getting blasted by X errors, is prioritize bulletproof-x.  Always drop to vesa in case of errors.  There has to be a contingency plan.

But again, this is nVidia's fault.

---

### Post by huygens on 2007-06-02
> **benanzo said:**
> Dell's configuration of my disk:
Number  Start   End     Size    Type      File system  Flags
 1      32.3kB  49.4MB  49.3MB  primary   fat16             
 2      49.4MB  2204MB  2155MB  primary   fat32             
 3      2204MB  2410MB  206MB   primary   ext3         boot 
 4      2410MB  500GB   498GB   extended               lba  
 5      2410MB  5059MB  2649MB  logical   linux-swap        
 6      5059MB  500GB   495GB   logical   ext3              
[...]
WOW.  6 partitions for a simple Ubuntu install????  dang.  I would have done 3.  You might be wondering what the two vfat partitions at the front of the disk are:
[...]
The only tinkering Dell did, (I think), was add some resos to xorg.conf and bloat the disk with a million partitions.

Let's put this into perspective :-) There are actually only 3 partitions for Linux, the /boot (sda3), the swap (sda5) and the / (sda6). Actually this is one partition less than the minimum I'm always considering. I always use a separate partition for /home, and sometimes even more dedicated partition (it depends of what I want to do with the computer).
So what are the other "partitions" for?
The 4th partition is actually a "virtual partition". PC computer have been limited since ages with various factors (I still recall that ominous 640kB of memory a certain "genius" had put on DOS/Windows systems...) One of them is that you cannot have more than 4 partitions on a hard disk. So how to create more? You make one of this partition an "extended" one, and within that partition you can create many other ones.
So I said that there are 3 partitions for Linux, then Dell has 2 partitions for rescue, that makes 5. Thus they had to use the extended one. So you see 6 partitions, but you really only have 5. One is a partition container.

Thanks anyway for your review :-)

---

### Post by oylenshpeegul on 2007-06-02
> **syko21 said:**
> Any word on the dell ubuntu laptop?

I am sending this from my new Dell Ubuntu laptop. So far, I am very pleased with it.

It did come with an Ubuntu CD. It's sealed in plastic and has a sticker on it that says

  Your computer is shipped with 
  Ubuntu Desktop Editiion 7.04 
  installed. If you need installation
  or configuration support, see
  [www.ubuntu.com/community](www.ubuntu.com/community).

It also has a recovery partition on the hard drive. I've already used it. When I updated the machine, it bricked it. Upon reboot I got error 17 from grub, so I restored from the recovery partition. It turned out to be an error in the grub.conf, which was triggered by the kernel update. It was easily fixed (in hindsight, I needn't have "recovered" but I didn't know that).

The resolution was initially coming up 1024x768 for me as well. I had to play with it to get 1280x800. I guess this display panel is capable of more, but I would need a better video card to get that. I have the Intel built-in video (the driver is i810).

---

### Post by 9a3eedi on 2007-06-02
Well.. I still can't believe that Dell didn't bundle their PC's with ubuntu discs.. I mean.. come on.. they're like less than a quarter each.. if you are going to mass produce them o.O

Maybe they're designing their own special ubuntu discs, with customized documentation and a nice box for it. Takes time I guess?

---

### Post by bmartin on 2007-06-02
> **gfahey said:**
> Maybe I'm missing something but, wouldn't it be better to be able to buy a Dell with no OS installed? I'd much rather install my own version of Ubuntu or Debian Etch and configure it. It looks like you'll have to do this anyways so, what's the point of the pre-installed? I mean, if this intended for noobs they will never be able to run anything in terminal (at least not immediately). 

I think it's great to have Dell provide this but, since it's a free distro how much do you pay Dell to do what you can do on your own? 

Come on Dell, give me the option of a virgin computer and let me deflower it. So to speak. I'd buy one. I have plenty of distros lying around and would love that option.
Don't go into owning or operating a business. You'll be a dismal failure.

I own a car. My car came assembled and included an owner's manual. I've never opened the owner's manual. When the car breaks down, I take it to a garage to have it fixed. I don't really care what's inside the car; as long as the car works the way I want it to, I'm happy. If someone tried to sell me a car I had to assemble myself, I'd walk away without uttering another word.

Not everyone wants to use the terminal. If someone doesn't want to use the terminal, they shouldn't have to, ever. If my parents had to use a terminal, they'd install XP.

---

### Post by octathlon on 2007-06-02
> **oylenshpeegul said:**
> 
The resolution was initially coming up 1024x768 for me as well. I had to play with it to get 1280x800. I guess this display panel is capable of more, but I would need a better video card to get that. I have the Intel built-in video (the driver is i810).

Two out of the two experiences I've read so far had this problem, one desktop and one laptop.  I do understand the thing about not including a proprietary nvidia driver since there is an open source one available, but what I don't understand is why Dell wouldn't bother to set up the correct native resolution of the monitors that they ship with the computer regardless of the driver they are using.  To me, the whole reason to buy preinstalled is that they make sure the hardware is setup and working correctly out of the box.

Have you tried suspend and hibernate yet?  That's the thing I'm really wondering about!  Maybe you could start a thread with a review of the laptop? :)

---

### Post by gfahey on 2007-06-02
> **bmartin said:**
> Don't go into owning or operating a business. You'll be a dismal failure.

I am quite successful with my own at home business thanks.

---

### Post by slyguyr3 on 2007-06-02
How is the wireless support out of the box?  Are you using the ndiswrapper or was there a natively supported card?

---

### Post by oylenshpeegul on 2007-06-02
> **octathlon said:**
> 
Have you tried suspend and hibernate yet?  That's the thing I'm really wondering about!  Maybe you could start a thread with a review of the laptop? :)

I hadn't yet, but I just did. They both seem to work as advertised. In fact, I guess I had been using suspend without realizing it, since that's what happens when you just close the laptop.

---

### Post by slyguyr3 on 2007-06-02
> **slyguyr3 said:**
> How is the wireless support out of the box?  Are you using the ndiswrapper or was there a natively supported card?

Sorry, I meant to ask first whether you are using wireless networking at all..

---

### Post by oylenshpeegul on 2007-06-02
> **slyguyr3 said:**
> How is the wireless support out of the box?  Are you using the ndiswrapper or was there a natively supported card?

It worked fine right out of the box. It's an Intel card, which has its own driver, so you get the dialogue about Restricted Drivers, but its all set up and ready to go.

---

### Post by fragos on 2007-06-02
The recovery refered to in grub probably just starts Ubuntu at the command line without X.  That's what you get when you install Ubuntu from a CD.

---

### Post by smoker on 2007-06-02
hopefully both dell, and canonical, will be reading this and other reviews and seeing how they can better the dell ubuntu product, and also, hardware manufacturers may take note, if this is a success and they decide they want a slice of the pie, they may be more inclined to produce and distribute the correct linux drivers for their products.

all in all, i haven't read any reviews that contained any major catatrophes, and hope as time goes by, all the little niggles will be sorted, and hopefully sorted by the time dell starts selling ubuntu computers in the UK!:D

---

### Post by camarojones on 2007-06-02
> **oylenshpeegul said:**
> It also has a recovery partition on the hard drive. I've already used it. When I updated the machine, it bricked it. Upon reboot I got error 17 from grub, so I restored from the recovery partition. It turned out to be an error in the grub.conf, which was triggered by the kernel update. It was easily fixed (in hindsight, I needn't have "recovered" but I didn't know that).

Since mine is due here on Tuesday, how would I go about checking the grub.conf for the error? What was the error?

Jones

---

### Post by macewan on 2007-06-02
did bootsplash work? what image does it use?

---

### Post by frogotronic on 2007-06-02
> **oylenshpeegul said:**
> I hadn't yet, but I just did. They both seem to work as advertised. In fact, I guess I had been using suspend without realizing it, since that's what happens when you just close the laptop.

Does HIBERNATE work?

- CH

---

### Post by crazedgremlin on 2007-06-02
Does anyone know if this is a modified or just a regular ubuntu install?

My dad's ibook just died last week so he ordered an ubuntu dell - he wants me to set him up with kubuntu.
If ubuntu is a standard install then all the hardware should be supported under kubuntu, too, because they have the same ubuntu base.
It's coming in on monday :p I'm excited !!
[B]
EDIT:  Answered my own question[/B]
customizations by dell include:
    * Customized Firefox start page
    * Installed the modem driver on notebooks
    * Hardcoded a kernel parameter 'reboot=b' to allow reboots to work properly on desktops. Launchpad bug 114854.
    * Installed the newer xserver-xorg-video-intel-1.9.94 driver from the Universe repository. This fixes issues. 

[http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Customizations](http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Customizations)

---

### Post by oylenshpeegul on 2007-06-02
> **camarojones said:**
> Since mine is due here on Tuesday, how would I go about checking the grub.conf for the error? What was the error?

Jones

You can just inspect your /boot/grub/menu.lst file. The Dell site has details here

[http://linux.dell.com/wiki/index.php/GRUB_error_17_after_kernel_update]("http://linux.dell.com/wiki/index.php/GRUB_error_17_after_kernel_update")

---

### Post by allforcarrie on 2007-06-02
shady bastards.

---

### Post by oylenshpeegul on 2007-06-02
> **cement_head said:**
> Does HIBERNATE work?

- CH

Yes, I think so. Like I said, both suspend and hibernate seem to work as advertised. Suspend is just like closing the cover: a sort of sleep mode that reqires entering your password to get back in. Hibernate is similar, only it actually powers off. When you turn the power back on, there's a brief pause, then you have to enter your password to get back in. Your entire session is just as it was before hibernating. It's the same as if you had only suspended, but the power was actually off completely. Is that what's supposed to happen? It seems to make sense.

---

### Post by tommyr on 2007-06-02
Man this is exciting! Dell finally getting with the program! Linux on a major PC vendor's machines! Kudos to Dell!!!

Tom

---

### Post by GabrielDunn on 2007-06-02
Hopefully one of you lucky peeps with the dell ubuntu laptop can help us out...will anyone be making a copy of that dell flavored ubuntu cd available?  I have an e1705 and I am hoping e dell version will finally solve my broadcom wireless problem.

I would be eternally grateful.\

---

### Post by brokencrystal on 2007-06-02
> **crazedgremlin said:**
> Does anyone know if this is a modified or just a regular ubuntu install?

My dad's ibook just died last week so he ordered an ubuntu dell - he wants me to set him up with kubuntu.
If ubuntu is a standard install then all the hardware should be supported under kubuntu, too, because they have the same ubuntu base.
It's coming in on monday :p I'm excited !!

sudo apt-get install kubuntu-desktop

Done.

---

### Post by oylenshpeegul on 2007-06-02
> **GabrielDunn said:**
> Hopefully one of you lucky peeps with the dell ubuntu laptop can help us out...will anyone be making a copy of that dell flavored ubuntu cd available?  I have an e1705 and I am hoping e dell version will finally solve my broadcom wireless problem.

I would be eternally grateful.\

I don't think this CD is any different from any other Feisty CD. It has the same smiling people pictured at [http://ubuntu.com]("http://ubuntu.com"). This laptop came with the restricted Intel 3945 wireless driver already installed, but I don't think there's anything special for any other wireless cards.

---

### Post by Johnny K on 2007-06-02
Was the 64 bit version of Ubuntu installed by default?

---

### Post by argosreality on 2007-06-02
> **Johnny K said:**
> Was the 64 bit version of Ubuntu installed by default?I highly doubt they're going to install the 64bit version of Ubuntu since 1.) few users are going to want it and 2.) it lacks support for things many moms and pops would use.

Just makes zero sense

---

### Post by argosreality on 2007-06-02
> **oylenshpeegul said:**
> Yes, I think so. Like I said, both suspend and hibernate seem to work as advertised. Suspend is just like closing the cover: a sort of sleep mode that reqires entering your password to get back in. Hibernate is similar, only it actually powers off. When you turn the power back on, there's a brief pause, then you have to enter your password to get back in. Your entire session is just as it was before hibernating. It's the same as if you had only suspended, but the power was actually off completely. Is that what's supposed to happen? It seems to make sense.Sleep mode stores your session in RAM while putting the rest of the system into low power mode. Hibernate will dump everything from the current session to the HD then shut the system off. When you restart, it loads from the HD hence the hesitation in the login.

I'd like to see someone with the laptop due repeated tests of putting to sleep, wake, sleep, etc. Previously when I tested sleep with linux it would work the first time, but generally it would bork it later. Also, could someone test to see if an external monitor works after being woken from sleep?

---

### Post by maniac_X on 2007-06-02
> **benanzo said:**
> I cracked open the case and had a look inside and was delighted.  They'v got some crazy fan-thing on the CPU that spins almost entirely silently.  Everything inside is removable just by lifting a lever or two, or by pinching a clamp.  It is very easy to add/remove drives etc.  Both the hard disk and the DVD-r/w that shipped with it are SATA2.  There are a total of 6 SATA channels, 1 IDE channel (two drives master/slave), 1 floppy, 3 PCI, 1 PCI-E x16, 2 PCI-E x1, 6 rear USB, 2 front USB, 1 rear IEEE1394, front panel mic/headphone jacks.  There is room for a total of two 3.5" internal drives and 2 external 5.25" drives as well as 2 external 3.5" slot for floppy or mem. card reader etc.  As I said, everything snaps in/out.  It is extremely trivial to add/remove hardware.

Since you've peeked inside....just wondering if there is any indication on the mobo who provides thier OEM boards?

---

### Post by benanzo on 2007-06-03
I will post a detailed *lshw* when I get back to that machine.

---

### Post by shawnmos on 2007-06-03
does mp3 playback work out of the box?

---

### Post by benanzo on 2007-06-03
No.  There are no restricted codecs installed by default.  The benefit of them being installed by default is minimal anyway since codec-buddy does such a good job of getting them.

Just double click any restricted format (MP3, AAC, WMA etc including videos) and codec-buddy will automatically prompt you to download and install the necessary codecs.  It's easy.

---

### Post by prox2far on 2007-06-03
I think it's great Dell is selling linux machines, I hope simple guides will allow people to update their CD image when the next Ubuntu version ships.

Seems like I'm the only one bothered by the fact there's no /home partition, does the CD image leave the /home directory untouched when restoring the system since Dell thinks it isn't necessary?

---

### Post by NumberOne on 2007-06-03
Dekk not supplying restore CD's is no new.  Igot a call from a customer abouit 2 years ago who was having problems with a new computer from Dell.  Upon arriving at his office, I ask for the disks that came with the PC.  There were none, said he never received them.  I called Dell and was told that the disks were not shipped because they were not necessary.  He stated that there was a recovery partition on the HD to restore Winblows.  Well the procedure he gave me to get to the recovery partition did not work.  So now I have a customer that has a brand new PC that is unusable because Dell wanted to save the cost of a CD.  Dell said they would send out a set of disks pronto.  So, how much did Dell save from this stratagy of not shipping the cd's.  Well after the hour on the phone with ttech support and them shipping the cd anyway, I'd say they lost money on that deal.

---

### Post by z0phi3l on 2007-06-03
> **NumberOne said:**
> Dekk not supplying restore CD's is no new.  Igot a call from a customer abouit 2 years ago who was having problems with a new computer from Dell.  Upon arriving at his office, I ask for the disks that came with the PC.  There were none, said he never received them.  I called Dell and was told that the disks were not shipped because they were not necessary.  He stated that there was a recovery partition on the HD to restore Winblows.  Well the procedure he gave me to get to the recovery partition did not work.  So now I have a customer that has a brand new PC that is unusable because Dell wanted to save the cost of a CD.  Dell said they would send out a set of disks pronto.  So, how much did Dell save from this stratagy of not shipping the cd's.  Well after the hour on the phone with ttech support and them shipping the cd anyway, I'd say they lost money on that deal.

They save a lot, since the odds of a user needing to restore their system is minimal, it offsets the ,I'll guess 5% of users that actually need the disks

---

### Post by luckyd on 2007-06-03
How much did your system end up costing, all I want in one of these Dells is the capability to run Beryl well, and other basic apps. I don't need a 500 gig harddrive. If your system was above $1000 please reccomend me one that will satisfiy these requirnments for cheaper. :)

P.S. Great Review

---

### Post by NumberOne on 2007-06-03
> They save a lot, since the odds of a user needing to restore their system is minimal, it offsets the ,I'll guess 5% of users that actually need the disks


My guess is that 5% is to small a number when you are dealing with windows.  All it takes is one virus infection and you'll need to reinstall.  Typically the average user has no concept of keeping there virus definitions upto date and this leaves them vulnurable.  Thats just one example of what can and does go wrong in Windows. So 5% no, I would think more like 50%

---

### Post by daradib on 2007-06-03
> **luckyd said:**
> How much did your system end up costing, all I want in one of these Dells is the capability to run Beryl well, and other basic apps. I don't need a 500 gig harddrive. If your system was above $1000 please reccomend me one that will satisfiy these requirnments for cheaper. :)


I don't have a Dell Ubuntu, but I'm pretty sure that the base computers that have Ubuntu (without any upgrades) would be more than enough to run Beryl well and basic apps (even more complicated apps).

---

### Post by daradib on 2007-06-03
My question is, do the computers come with Windows logo keys on their keyboard. I know the reviewer's computer did not come with an Ubuntu CD, or simple documentation, but I would like to know if this is the case for everyone, or for specifically the reviewer. Please say whether or not your Dell Ubuntu came with any papers regarding Ubuntu (like documentation, quick start guide, paper, etc.) or an Ubuntu CD.

---

### Post by Kent84 on 2007-06-03
Dell has made a very positive step forward. The system you got sounds damn sexy. Now I just need to save up some $$ to afford one!

---

### Post by benanzo on 2007-06-03
Yes, the keyboard that shipped with the machine has two Windows logos on the Super keys.

---

### Post by Gen2ly on 2007-06-04
Nice review benanzo, have you had much of a change to test how the nvidia card works?

---

### Post by phaedrus44 on 2007-06-04
Hey Hey!

Nice review.
I bought the XPS 1210 about 2 weeks before Dell announce (again) that they were releasing the ubuntu systems.

The XPS 1210 I have, has the works.  256mb nVidia (64mb, the rest shared), the cOre duo, dvd burn, wireless.....blah blah blah.  I do not remember having one hangup with Edgy install. Beryl worked right away, gimp, scribus...blah blah yaddah yaddah...

The trouble I had was with the media direct partition and the Dell hpa partition that actually will not show up with regular partitioning software....I had to use 3 tools to get rid of the HPA.  Now I am very happy and the system runs like a bat outtttta h   ell.

---

### Post by benanzo on 2007-06-04
I am still benchmarking the nVidia card.  I am running into some problems with Beryl and some stuttering on certain animations.  For instance, when I have three open windows, and I scale them, there is slight stuttering.  But when I run GPU intensive plugins like Rain+Cube at the same time, there is no slowness at all.  This is no doubt to do with the nVidia driver.  I think I'm going to roll back Feisty's nVidia driver and install the latest version to see if the problem still exists.  It could be Beryl as well, though I never experience such problems on my MacBook with the Intel GMA950.  That just shows how much better Free drivers are.

---

### Post by moscowtime on 2007-06-04
> **NumberOne said:**
> Dekk not supplying restore CD's is no new.  Igot a call from a customer abouit 2 years ago who was having problems with a new computer from Dell.  Upon arriving at his office, I ask for the disks that came with the PC.  There were none, said he never received them.  I called Dell and was told that the disks were not shipped because they were not necessary.  He stated that there was a recovery partition on the HD to restore Winblows.  Well the procedure he gave me to get to the recovery partition did not work.  So now I have a customer that has a brand new PC that is unusable because Dell wanted to save the cost of a CD.  Dell said they would send out a set of disks pronto.  So, how much did Dell save from this stratagy of not shipping the cd's.  Well after the hour on the phone with ttech support and them shipping the cd anyway, I'd say they lost money on that deal.

If only you look into the 2-nd Dell partition, you will see there a huge file "UB704img.tgz". Untar this file, burn it to CD, et voila! here is the disk you need.
And for Dell, it is much simpler to write the image to disk, than to ship a physical CD (25 'c is a good chunk of money, when multiplied by tens of thousands...)

However, if there is a problem how to untar a file under Ubuntu, please ask for help in this forum.

Best wishes
BNK

---

### Post by changlinn on 2007-06-05
damn good review. Good to see Dell doing this, when a 12" xps comes out in Australia I'll be there with bells on. Shame they aren't supplying a little documentation, or a case sticker.
For those super keys, I think they will go the same way as the break key and the ps/2 port, they will be called a windows key and our kids won't know why.

---

### Post by prox2far on 2007-06-05
Luckyd:

all the XPS 410n configurations are powerfull enough to run Beryl.

You can get them for as little as 849$ with speakers and monitor or 669$ without speaker and monitor.

---

### Post by sloggerkhan on 2007-06-05
[http://ideastorm.com/article/show/67974](http://ideastorm.com/article/show/67974)

This guy's didn't have vista packaging and such.

---

### Post by luckyd on 2007-06-05
Its to bad that with shipping and tax that XPS 410n goes up to $959.42 :(
I guess my first Ubuntu machine with an intel chip won't end up being one of these Dells :(

---

### Post by thecure on 2007-06-06
> **Johnny K said:**
> Was the 64 bit version of Ubuntu installed by default?

No, I received the Dell XPS 410n this past Friday and it's the 32 bit version. Mine came with a 320GB HD; then I added a 400Gig HD. On that I installed the 64bit server edition then added the Kubuntu desktop... I'll probably go back to Gnome soon. Just wanted to try out KDE. What was crapy though is now I get the  "Do you want to set up a RAID disk?" on every boot. If I turn off RAID I would have to reinstall Ubuntu on both HD's again, which I might do. (If I make the 2nd HD RAID I lose 50 GIG... actually nearly 150 gigs since the original HD is only using 250GIGs for OS.) My actual Ubuntu partion is only 250 Gig out of that 350 gig HD... sad. It's kind of funny because I also got the 20" Dell monitor and the Dell Ubuntu side didn't configure the correct resolution, no big deal, easy to fix, but the Ubuntu side I installed did. I'll have to look when I get home but I don't think it has a firewire port... hope I'm wrong. It is a very quiet system and pretty fast. (E6600 1066FSB; 2gig RAM) I did not get an OS CD which I'm not disappointed in... easy to download. My kernal was the .15 which was updated to .16 as soon as I booted up. Did not have a problem with the NVIDIA driver killing xorg that others did. Would have been nice to get a better video card and perhaps a TV tuner option, but still a nice computer. Incidentally, I had used a $350 off coupon I found online.

---

### Post by towsonu2003 on 2007-06-06
great review :) I was curious about those things - Hope other reviews follow. 

The documentation that came with your desktop having only Vista stuff is a surprise, but not the install disc that didn't come -they do similar stuff with Windows boxes. In fact, I was surprised to hear that they should have included one.

---

### Post by Old Pink on 2007-06-06
Out of interest, on fresh, what do:

locate dell
- and -
whereis dell

Bring up in terminal? :)

---

### Post by fromgi on 2007-06-10
Because your PC was ordered with 2GM of ram, I wonder why Dell created a swap drive.  My current PC (almost 5 years old) has 1GB of ram, and performance improved when I reinstalled Ubuntu without one.

I'm in the process of ordering a XPS-410n.  When I try to [configure a PC]("http://configure.us.dell.com/dellstore/config.aspx?c=us&cs=19&kc=6V440&l=en&oc=DXCWNC1&s=dhs") in the Icon view, images momentarily appear, then disappear for each component.  I have Adobe Flash 9 installed.  Can anyone offer a resolution?

Thanks.

---

### Post by daradib on 2007-06-10
> **fromgi said:**
> When I try to [configure a PC]("http://configure.us.dell.com/dellstore/config.aspx?c=us&cs=19&kc=6V440&l=en&oc=DXCWNC1&s=dhs") in the Icon view, images momentarily appear, then disappear for each component.

Same problem here.

---

### Post by Georgie-o on 2007-06-10
I purchased this exact system with Ubuntu and got it a couple of days ago.  I was interested in perhaps doing a dual boot with Windows and found that Windows does not install on this machine.  I come up with an error shortly into booting tot the Windows CD.  I know I'm not going to get much sympathy on this forum for that problem, but it concerns me because I specifically asked if I wanted to install Windows at a later date, would it work.  She (Dell rep) assured me it would.  I've tried a number of different install disks (XP, XP pro, MCE) and nothing gets past the fist part.  I asked because i did not want a machine that was purposefully crippled or something like that and in case i wanted to sell it in the future and put Vista on it.  Has anyone else gotten this to work?   

I had read in other forums that sometimes XP has problems install with a SATA HD and DVD drive.  Could that be the problem and that maybe Vista would work?

---

### Post by jimbob on 2007-06-10
Are you trying to install XP or Vista?

What is the error and at what point does it occur?
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

... things should be done from the command line the way Nature intended ...

---

### Post by Georgie-o on 2007-06-10
All the ones I tried are XP.  The error occurs right before you get to the screen that asks if you want to install a fresh copy or repair existing (then it formats the drive).  It runs for a only a couple of minutes ans shows the various drivers loading at the bottom of the screen.  It them switches to a differnt tone blue screen and says "windows has shutdown to prevent damage to your hardware...if this is the first time you've seen this message, restart...other wise..."  And then it says a number of different things about the Hard drive, hard drive controller, bios may need to be updated, start Windows in Safe Mode (which is not possible because it's not yet installed).

Any thoughts?

---

### Post by Christophe Vanlancker on 2007-06-10
> **rushtrader said:**
> That is incorrect.  Dell, and many other major manufacturers, have a special key embedded into their BIOS that Windows recognizes and matches with special certificates on the Dell version of Wndows, which allows it to bypass registration.  You can use any Dell Windows CD on any Dell PC made in the last few years.  Take a machine that was loaded with Windows XP Home and load Windows XP Pro onto it.  It works - just like that.  No registration needed.  I have not tried it with Windows Vista on any of the newer machines, but I would imagine that it likely works.  See e.g.: [http://news.softpedia.com/news/Dell-HP-and-Sony-OEM-Certificates-Used-in-Windows-Vista-Activation-Cracks-48034.shtml](http://news.softpedia.com/news/Dell-HP-and-Sony-OEM-Certificates-Used-in-Windows-Vista-Activation-Cracks-48034.shtml)

RT

Yes I can confirm that it works too with Vista. And now that you mention the Bios, that explains why there are popular cracks for Vista who simulate an OEM bios as the first step to bypass successfully Vista's registration.

---

### Post by jimbob on 2007-06-10
Georgie-o:  If I was you I would make loud noises to Dell and that rep who told you it could be done.  There is no reason in the world IMHO that a person can not put what ever he wants on something that he has paid his good money for.

That's the trouble with buying stuff that the OEM manufacturer has had his grubby little elves tinker with.
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by khowe on 2007-06-10
benanzo, could you please post the results of the following?

cat /proc/mtrr

glxgears -printfps

Also, have you ran any game benchmarks?

Thanks for the info!

khowe

---

### Post by benanzo on 2007-06-10
```

ben@dell:~$ cat /proc/mtrr
reg00: base=0x00000000 (   0MB), size=65536MB: write-back, count=1
reg01: base=0x7ff00000 (2047MB), size=   1MB: uncachable, count=1
reg02: base=0x80000000 (2048MB), size=2048MB: uncachable, count=1

```

```

ben@dell:~$ glxgears
9347 frames in 5.0 seconds = 1869.292 FPS
9675 frames in 5.0 seconds = 1934.982 FPS
9781 frames in 5.0 seconds = 1956.174 FPS
ben@dell:~$

```

I have not run any gaming benchmarks yet, but will soon.

---

### Post by khowe on 2007-06-10
The mtrr is wrong, just like on my dell e520.

Doesn't seem to affect anything tho.

---

### Post by khowe on 2007-06-10
```

legg@e520:~$ glxgears
17340 frames in 5.0 seconds = 3467.883 FPS
17324 frames in 5.0 seconds = 3464.634 FPS
17323 frames in 5.0 seconds = 3464.579 FPS
17307 frames in 5.0 seconds = 3461.381 FPS
legg@e520:~$

```

I have the ati x1300 pro (not offered with ubuntu)
e520 with e6300 cpu
1gig ram 

I get 190fps in quake3 @ 1024x768 with all settings on max.

---

### Post by jazzcat on 2007-06-11
> **fromgi said:**
> Because your PC was ordered with 2GM of ram, I wonder why Dell created a swap drive.  My current PC (almost 5 years old) has 1GB of ram, and performance improved when I reinstalled Ubuntu without one.

While I'm waiting on my fiancee's E1505N to arrive, let me share a story.

My primary box is a Shuttle XPC running CentOS 5.  It's configured with 1G ram and 2G swap.  (Hey, I've got over a hundred gig, so I figured what the heck?)

My fiancee has gotten in the habit of *crashing* this machine.  The first time it happened, I was perplexed; she texted me and asked if it's OK to hard-boot it.  WTF?

When I came home that night, she said it was behaving badly again.  So I took a look.

In FireFox, she had about 30 tabs open to various shopping and MySpace sites, all of which used Flash of some sort.  Out of a total of 3G RAM+Swap, there was 1 **mega**byte free.  Firefox and its Flash children had eaten up all available RAM and Swap.  When this happens, and the HD is red-hot from all the thrashing, sometimes a hard boot is needed...

---

### Post by syko21 on 2007-06-11
tell your fiancee to try out epiphany, its mozilla based and uses less resources.

---

### Post by benanzo on 2007-06-11
I don't have any problems with FF in general, just the Flash player.  Even when using Epiphany the Flash player will frequently crash me.

---

### Post by mutenewt on 2007-06-18
I'm considering buying the 410n.  The only component I'm not happy with is the 256MB nVidia Geforce 7300LE TurboCache card.  However, I noticed at the [Dell Ubuntu Wik]("http://linux.dell.com/wiki/index.php/Tech/Video/nVidia#Hardware_Available_from_Dell")i, they suggest the 8600GTS and 8800GTX cards are also available.  These options don't show up at Dell.com.  Anyone know what the scoop is?  Is this a future option?
Thx for the help

---

### Post by mutenewt on 2007-06-18
Decided to post this in the general section.  In hindsight, it seemed to make more sense.  sorry for the double post.

---

### Post by prana on 2007-06-18
> **mutenewt said:**
> I'm considering buying the 410n.  The only component I'm not happy with is the 256MB nVidia Geforce 7300LE TurboCache card.  However, I noticed at the [Dell Ubuntu Wik]("http://linux.dell.com/wiki/index.php/Tech/Video/nVidia#Hardware_Available_from_Dell")i, they suggest the 8600GTS and 8800GTX cards are also available.  These options don't show up at Dell.com.  Anyone know what the scoop is?  Is this a future option?
Thx for the help

Yeah, the default card is not that great for gaming but any other more powerful Nvidia card should be supported by the binary nvidia driver.

By the way, I am supposed to get the 410n tomorrow so I am eagerly waiting to play with it.

---

### Post by librano on 2007-06-18
> **fromgi said:**
> Because your PC was ordered with 2GM of ram, I wonder why Dell created a swap drive.  My current PC (almost 5 years old) has 1GB of ram, and performance improved when I reinstalled Ubuntu without one.

I'm in the process of ordering a XPS-410n.  When I try to [configure a PC]("http://configure.us.dell.com/dellstore/config.aspx?c=us&cs=19&kc=6V440&l=en&oc=DXCWNC1&s=dhs") in the Icon view, images momentarily appear, then disappear for each component.  I have Adobe Flash 9 installed.  Can anyone offer a resolution?

Thanks.

i think in cases with such copious amounts of RAM the swap is a just-in-case thing. The Linux kernel does a good job of managing memory resources... correct me if i am wrong but i think the Linux kernel keeps as much as it can on the RAM unless there is no more RAM left...

---

### Post by benanzo on 2007-06-20
I think swap is used for hibernate images - right?  That could be the reason for the big swap space in relation to the amount of RAM.

---

### Post by daradib on 2007-06-20
> **benanzo said:**
> I think swap is used for hibernate images - right?  That could be the reason for the big swap space in relation to the amount of RAM.

That's what I've heard.

---

### Post by jimbob on 2007-06-20
I have Gdesklets which show memory and swap usage at all times.  Normally there is never any swap activity shown on my system.  However when running XP as a virtual box under Ubuntu you can see it begin to gobble up swap space as soon as I start XP.

So it isn't just for hibernate.
&#65279;________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by Scotty Bones on 2007-06-23
> **ageilers said:**
> Nice to see a major manufacturer stepping up to offer an alternative. Dell is obviously looking for ways to regain it crown. Dell with Opensource, Dell at Walmart.

DELL w/ open source??  Am I the only one thats finds this to be even just a little bit odd.  I mean don't get me wrong, it's about time someone offered Linux as a pre-installed OS choice. But... DELL is a member of the TCPA (Trusted Computing Platform Alliance). An organization that was spearheaded primarily by Microsoft and who's ultimate goal is the death of open source (and "to make the chineese pay", of course!:) ). So, why would a member of this organization provide an open source alternative with their system?  Just something to think about, I have yet to see anyone raise this question.  Hey who knows, maybe this could become a discussion for a whole new thread. I'd love to hear the communities thoughts on this one.

---

### Post by tommyr on 2007-06-23
> **Scotty Bones said:**
> DELL w/ open source??  Am I the only one thats finds this to be even just a little bit odd.  I mean don't get me wrong, it's about time someone offered Linux as a pre-installed OS choice. But... DELL is a member of the TCPA (Trusted Computing Platform Alliance). An organization that was spearheaded primarily by Microsoft and who's ultimate goal is the death of open source (and "to make the chineese pay", of course!:) ). So, why would a member of this organization provide an open source alternative with their system?  Just something to think about, I have yet to see anyone raise this question.  Hey who knows, maybe this could become a discussion for a whole new thread. I'd love to hear the communities thoughts on this one.


Maybe they got out of TCPA? Just a guess, not sure. I'm glad they offer Linux though.

---

### Post by syko21 on 2007-06-23
If they are generating profit from ubuntu sales then they will keep up with it. Then there will always be computers without the tpm so whats the problem? Its the rule of capitalism, if there is a need then there will eventually be a supply.

---

### Post by Scotty Bones on 2007-06-23
> **syko21 said:**
>  Then there will always be computers without the tpm so whats the problem? Its the rule of capitalism, if there is a need then there will eventually be a supply.

**Not true**.  If the TCPA is successful in getting the CBDPTA (Consumer Broadband and Digital Television Promotion Act) bill passed, it will become illegal to import or sell non-tpm enabled computers in the USA.  (yes, that means fines and jail time, on the federal level)
This is one of my biggest reasons for dropping Windows and other MS products.
Listen i'm an extremely happy DELL customer.  I love my Dimension 8300 (its outlasted my previous 2 desktops combined twice over and still running as smooth as the day I got it,) and when its time for a new unit, i'll be returning to DELL for a Ubuntu box.  All i'm getting at is that I would hate to see this offer ended due to "*poor sales*" and then have that used as a propaganda tool to push the tpm issue or to down-play open source.  As far as I can tell they are still associated with the TCPA.  It's still way to early to pass any kinda of judgment, good or bad.  Personally, I hope that this offer from DELL blows up and buries MS six feet deep.  Wishfull thinking maybe, but only time will tell.

---

### Post by daradib on 2007-06-27
> **Scotty Bones said:**
> **Not true**.  If the TCPA is successful in getting the CBDPTA (Consumer Broadband and Digital Television Promotion Act) bill passed, it will become illegal to import or sell non-tpm enabled computers in the USA.  (yes, that means fines and jail time, on the federal level) 

I thought the bill was basically killed back in 2002 by the rejection of the bill by Senator Pat Leahy, chairman of the Senate Judiciary Committee.

---

### Post by syko21 on 2007-06-27
Bills don't die as long as there is money in it for supporting them.

---

### Post by Scotty Bones on 2007-07-02
Yes it was. This is actually the second bill. The first was called the SSSCA (Security Systems Standards and Certification Act).  Its basically the exact same bill, just renamed.  And I have no doubt that they will try it again under a different name.  

_Side Note_.....
It almost doesn't matter anyway because of MS business practices.  i.e. the digital driver signing that was introduced with xp.  In XP you have the option to ignore the the warning about the driver not having a digital signiture from MS, but with Vista this option to bypass has been completely removed, if the driver has no sig it can not be installed turning your new hardware into nothing more than a paper weight.  This means that if a HW manufacture wants their device to operate in vista it will cost them a lot of money and extra work.  because of this they may decided to bypass linux support all together (which would really really suck) figuring it to be too much extra work.   Thats the problem with this monopoly, there is more than one way to skin a cat.  If they can not get congressional support, they slowly build it into the OS any way (remember Netscape).  Hopefully many more major manufacturers follow DELL's lead and begin supporting linux (even if it isn't ubuntu).  This seems to be the only way were are going to slow this giant and its shady business practices down.  And I really hope that for our sake DELL does not screw this opportunity up, because again... I love my dell.

---

### Post by cosborn72 on 2007-07-03
> **dwasifar said:**
> Interesting that it comes with a recovery partition.  I pulled a Dell rep into chat the other day to ask about that, and he assured me with complete certainty that there was no recovery partition, only CDs.

Weird, 

My XPS 410 came with a Ubuntu CD.

---

### Post by crazedgremlin on 2007-07-03
> **cosborn72 said:**
> Weird, 

My XPS 410 came with a Ubuntu CD.

my dad's inspiron e1505n came with a cd, too (in addition to a recovery partition)

BTW Dell reps don't know anything

---

### Post by benanzo on 2007-07-03
I got a call yesterday from a Dell rep asking me how I liked the XPS with Ubuntu and if there was anything they could do to make it better.

I was really surprised.  I think Dell might actually be taking this seriously.

---

### Post by dragon1711 on 2007-08-01
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
4127 frames in 5.1 seconds = 813.445 FPS
4972 frames in 5.0 seconds = 988.678 FPS
4972 frames in 5.0 seconds = 992.663 FPS

I have optiplex740 dell with x1300 pro, AMD turion 64x2 and 2GB RAM. and I fail to install ati driver (even restricted ones).  
Would you be so kind as to tell how did you manage to do it?

---

### Post by aborza on 2007-09-05
This has been a fabulous review and a great discussion thread. I have been trying to get out of the windoze trap for years and have tried many versions of nix. All of them have required me to become a programmer and spend entirely too much time trying, often unsuccessfully, to fix problems (drivers etc.). Sort of reminds me of dealing with OS2. I loved OS2....but the problems and the inability to run the programs I need, forced me to windoze.

I have installed ubuntu 7.04 on a dedicated machine and when running some excell templates in open office the boots were so slooooow as to be useless. I need to run crossover optimization programs for active and passive loudspeaker systems and to do loudspeaker measurements on my computers. All the programs to do this at a high quality level are windoze programs and involve using a high quality sound card like some of the M-Audio products. My guess is that there are probably no drivers for my use. Also I cannot use my simulation/optimization progs either. The only nix prog I have been able to find in this field is Kfilter and it is old, not maintained and insufficient for my use.

Is there a way to run my progs in nix? Is there a VM of some sort other than Wine (that does not know my progs) to get the job done? Or do I have to suffer a dual boot senario?

Ubuntu is more than sufficient for web surfing, word processing and playing with images...but I need more. Suggestions? I want to get away from windoze.

As for the Dell foray into the nix environment, I was thinking of buying one of their laptops with ubuntu installed. But after reading the article and this thread I am giving it another thought. Please help me to see the light in the darkness. And please assure me that the light is not another nix train coming at me.

---

### Post by Louis Cypher on 2007-09-15
I just received my XPS 410n this week.  After installing Ubuntu on an old laptop I decided Linux had reached the point where I can use it as my primary OS.  I add the 22inch LCD which is awesome coming from a 13in laptop :)  The biggest problem I had was getting the Nvidia driver running correctly.  I have always had trouble with video drivers under Linux.  As suggested I tried System -> Administration -> Restricted Drivers Manager to enable my Nvidia drivers but I always get the error "Your hardware does not need any restricted drivers."  I even did a fresh install of Feisty but no go.  What ended up working for me was [Envy]("http://albertomilone.com/nvidia_scripts1.html")  I was skeptical but it did the trick.  My test was to see if I could get World of Warcraft running.  Well it does and I get way better framerates than I did under M$ XP.  So glad I moved to Ubuntu.  Woot

---

### Post by daradib on 2007-09-15
> **Louis Cypher said:**
> I just received my XPS 410n this week.  After installing Ubuntu on an old laptop I decided Linux had reached the point where I can use it as my primary OS.  I add the 22inch LCD which is awesome coming from a 13in laptop :)  The biggest problem I had was getting the Nvidia driver running correctly.  I have always had trouble with video drivers under Linux.  As suggested I tried System -> Administration -> Restricted Drivers Manager to enable my Nvidia drivers but I always get the error "Your hardware does not need any restricted drivers."  I even did a fresh install of Feisty but no go.

What graphics card do you have? The Restricted Driver Manager should work for most graphics cards that can have proprietary drivers (i.e. not Intel, but ATI and Nvidia) unless they are very old or very new. If necessary (and assuming someone has not done so already), you should fill out a bug on Launchpad.

---

### Post by gar710 on 2007-09-19
I'm glad I found this thread.  I've been wondering how the XPS 410n was working out for those who bought it.  

I've been using  Pclinuxos for about a month now in a dual boot with XP.  I'm finding no good reasons to even bother with XP anymore.  I have a multi partitioned disc, which I have room for another Linux version.   I tried Ubuntu,Kubuntu, Linux Mint and Freespire , none of them could give me the correct resolution of my Dell 2407 (1920x1200) out of the box. I activated the  ATI restricted drivers for my old Radeon 9500PRO card, but it never did work. From the forums, I see I'm not alone in resolution issues with Ubuntu.

   It seems even the Dell Ubuntu versions may have the same problem. I don't get this at all. It is very discouraging for someone newish to Ubuntu to install it , and it can't even give you the correct resolution.  The Ubuntu based distros are the only ones of the versions I've tried (Mepis, Pclos, SamLinux and Mandriva) that don't give the correct resolution without tinkering at all.  To buy  a Dell Ubuntu pc and not have it give you your resolution would be even more discouraging.  

Why can't Ubuntu get the resolution right OTB for so many pc's ?

Another thing to remember about buying a Dell, there's no reason you can't buy any of their pc's with any or no OS , re-format the drive to your liking and install what you like.  From the review here, it's obvious Dell has done nothing Linux specific to their Ubuntu based pc's,  so you may as well do as you wish with any of their offerings. That way you may be able to get a better deal or components you -do- want.  Just a thought.

-cheers

---

