---
title: "installing dvd-rw"
date: 2006-01-20
forum: Desktop Environments
---

### Post by bonbon64 on 2006-01-20
i need help installing a dvd-rw, someone on an irc channel tryed to help me the final conclusion was that i need to rebuild the dvd-rw but i am not sure how to do this and was wondering if anyone knew where i could find a good HOWTO

this is what was said:

gogogog54 hello
Svetlana hello gogogog54
gogogog54 i got a bit of a problem
gogogog54 its probly something quite simply cos i only started useing linux a couple of months ago
gogogog54 i cant seem  to burn dvds
gogogog54 this is the error it gives me in gnomebaker -
gogogog54 :-[ RESERVE TRACK failed with SK=5h/ASC=30h/ACQ=05h]: Wrong medium type
gogogog54 /dev/hda: "Current Write Speed" is 1.0x1385KBps.
gogogog54 :-[ WRITE@LBA=0h failed with SK=5h/ASC=30h/ACQ=05h]: Wrong medium type
gogogog54 :-( media is not formatted or unsupported.
gogogog54 :-( write failed: Wrong medium type
gogogog54 i have set up my hardware weird so the cd drive is actually hda
gogogog54 any idea
gogogog54 or any idea how i could get a better error report
gogogog54 nop!
gogogog54 no onje seem to want to help me 
gogogog54 HELP
siplex hi gogogog54
siplex what do you to burn dvds?
siplex use to burn
gogogog54 [http://www.cdrinfo.com/Sections/Reviews/Specific.aspx?ArticleId=10711](http://www.cdrinfo.com/Sections/Reviews/Specific.aspx?ArticleId=10711)
gogogog54 the meduim is and i bought 16x memorex dvd-r
siplex maybe you should try with another software
siplex xcdroast for exemple
gogogog54 i tryed k3b
gogogog54 exact same error
siplex have you the same problem?
gogogog54 yeah
siplex is there anything strange in the system logs?
gogogog54 and i cant seem to find anything on any fourms about it
gogogog54 i dont really know what i am looking for
siplex i have already seen similar message (Wrong medium type)  with bad DVDs
siplex have you try different DVDs or CDs?
gogogog54 mmhh
gogogog54 i dont have any other dvds 
gogogog54 cd's work fine
siplex have you try burning with anoher OS?
gogogog54 i found this in the logs, i dont know if its relivant 
gogogog54 [4380708.714000] cdrom: This disc doesn't have any tracks I recognize!
gogogog54 no
siplex which type of disc was in the drive where this message was print?
gogogog54 dvd-r
gogogog54 the only kind i have had in it all day
siplex i don't think it is a related-hardware problem
siplex i 'd rather think you encounter softare problems
gogogog54 i could take the dvd drive out and test it in the windows machine but its a bit of a hassel
Svetlana ... avec Linux vous avez un noyau ... avec windows, des pepins ...
siplex can you read dvds?
gogogog54 mount: block device /dev/hda is write-protected, mounting read-only
gogogog54 mount: wrong fs type, bad option, bad superblock on /dev/hda,
gogogog54        missing codepage or other error
gogogog54        In some cases useful info is found in syslog - try
gogogog54        dmesg | tail  or so
gogogog54 Error: could not execute pmount
gogogog54 nop
siplex :(
siplex what command line you used?
gogogog54 not useing command line i am still learning
gogogog54 =newbie
siplex :)
siplex there is a problem with the mount
siplex maybe in /etc/fstab
gogogog54 is it because i set them up weird in bois
siplex bios?
gogogog54 yeah
siplex i don't think
siplex have done special change in the bios?
gogogog54 well the cd drives are set to primary master and slave
gogogog54 thats why its says hda instead of hdc
gogogog54 what would i need to change in fstab
siplex can you paste somewhere fstab?
siplex and give the read device name of the dvd?
gogogog54 i dont understand
siplex paste the content of your file /etc/fstab
gogogog54 so i change cd -/dev/hda        /media/cdrom1
gogogog54 to - /dev/hda        /media/dvd1
gogogog54 ?
siplex good
siplex try: mount -t iso9660 /dev/hda /media/dvd1
gogogog54 mount: mount point /media/dvd1 does not exist
gogogog54 Error: could not execute pmount
siplex mkdir /media/dvd1
siplex :-\
gogogog54 yeah...
gogogog54 does dvd writer have diffrent permissions
siplex you should check in /etc/passwd if there a special user
gogogog54 i tryed the mount -t - mount: block device /dev/hda is write-protected, mounting read-only
gogogog54 mount: wrong fs type, bad option, bad superblock on /dev/hda,
gogogog54        missing codepage or other error
gogogog54        In some cases useful info is found in syslog - try
gogogog54        dmesg | tail  or so
siplex dmesg|grep /dev/hda
gogogog54 i think its working it says blank dvd
siplex ok
siplex you must check with a already burned dvd
gogogog54 yea it burnt cd didnt work
gogogog54 same error
gogogog54 and theres now an extra cd drive in nautils
gogogog54 or dvdrw
siplex you should read tutorials about burning and restart from scratch
siplex your configuration seem to be strange
gogogog54 mmhh ok
gogogog54 its all a learning procces
gogogog54 fick sake
gogogog54 i really apprecate the help thanks
gogogog54 you are the only one that would give me the time of day, trying to fix this
siplex it is a very basic problem and boring to fix :)
gogogog54 do you know where i could find a good tutorial - or do you think i could change the dvd back into hdc or would i lose the mount points
gogogog54 would it be easyer to sort than building a new dvd divice which i know nothing about
siplex which distro you have?
gogogog54 ubuntu
gogogog54 5.10


any help would be good 

ben

---

### Post by bonbon64 on 2006-01-20
i really need some ANYONE just a link or something, no one seems to will to help anywhere!

---

### Post by soulestream on 2006-01-20
you might wanna give us some information

output of "sudo fdisk -l"
/etc/fstab

so we can make sure its actually hda

have you tried burning as root?

if that works it just a permission problem.

does the bios detect the drive?


soule

---

### Post by Ocxic on 2006-01-20
make sure you have the right disc DVD+RW and DVD-RW are two diffrent discs, and your burner may not support one of those types. try with a DVD-R/+R and see what happens.

---

### Post by bonbon64 on 2006-01-23
thanks for the help heres what "sudo fdisk -l" came up with

Disk /dev/hdc: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1       14215   114181956   83  Linux
/dev/hdc2           14216       14593     3036285    5  Extended
/dev/hdc5           14216       14593     3036253+  82  Linux swap / Solaris

Disk /dev/hdd: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *           1       14593   117218241   8e  Linux LVM
bon@ubuntu:~$


this is what my dvd burner suports:-

DVD-ROM, DVD-R, DVD-RW, DVD+R, DVD+RW, DVD-Video, CD-ROM, CD-ROM XA, CD-Audio, CD Extra, CD Text, CD-IReady, CD-Bridge, Photo-CD, VideoCD, Hybrid CD

this is what i bought : [http://www.ebuyer.com/customer/products/index.html?rb=15485551814&action=c2hvd19wcm9kdWN0X292ZXJ2aWV3&product_uid=99323](http://www.ebuyer.com/customer/products/index.html?rb=15485551814&action=c2hvd19wcm9kdWN0X292ZXJ2aWV3&product_uid=99323)

this is my dvd burner : [http://www.cdrinfo.com/Sections/Revi...rticleId=10711](http://www.cdrinfo.com/Sections/Revi...rticleId=10711)

thank for the help 

ben

---

### Post by bonbon64 on 2006-01-23
oh and this is how fstab is setup

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdc1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdc5       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by Ocxic on 2006-01-24
check and see if you have dvdrtools and dvd+rw-tools installed from synaptic and try again.

---

### Post by bonbon64 on 2006-01-24
didnt have have one of them installed but installed it and i still get the same error this is the error:

Executing 'mkisofs -V a-apex icaare -p bon -iso-level 3 -l -R -hide-rr-moved -J -joliet-long -gui -graft-points 01_1973_Bruce_Springsteen_The_Wild,_the_ Innocent,_and_the_ E_Street_Shuffle_mp3_192_catarulas_[GRuPoKuÃ‘aoRi=/home/bon/Desktop/Music/01_1973_Bruce_Springsteen_The_Wild,_the_ Innocent,_and_the_ E_Street_Shuffle_mp3_192_catarulas_[GRuPoKuÃ‘aoRi 1998 - Prolonging The Magic=/home/bon/Desktop/Music/1998 - Prolonging The Magic 2 unlimited=/home/bon/Desktop/Music/2 unlimited 2005 odyssey=/home/bon/Desktop/Music/2005 odyssey 24 7=/home/bon/Desktop/Music/24 7 60s=/home/bon/Desktop/Music/60s 808 State=/home/bon/Desktop/Music/808 State 808 state - don solaris=/home/bon/Desktop/Music/808 state - don solaris [ mas... ]=/home/bon/Desktop/Music/[ mas... ] abba=/home/bon/Desktop/Music/abba abdominal & dj fase - flowtation device=/home/bon/Desktop/Music/abdominal & dj fase - flowtation device AC DC - Back In Black=/home/bon/Desktop/Music/AC DC - Back In Black acoustic alchemy - 1989 - blue chip=/home/bon/Desktop/Music/acoustic alchemy - 1989 - blue chip Adam Sandler=/home/bon/Desktop/Music/Adam Sandler Addicted to bass=/home/bon/Desktop/Music/Addicted to bass Adventures Beyond The Ultraworld (CD1)=/home/bon/Desktop/Music/Adventures Beyond The Ultraworld (CD1) Aim - Fabriclive 17 (FLAC - CUE - EAC)=/home/bon/Desktop/Music/Aim - Fabriclive 17 (FLAC - CUE - EAC) Alias - The Other Side Of The Looking Glass=/home/bon/Desktop/Music/Alias - The Other Side Of The Looking Glass alien dream time=/home/bon/Desktop/Music/alien dream time aphex twin (afx) - analord 01=/home/bon/Desktop/Music/aphex twin (afx) - analord 01 aphex twin i care because you do=/home/bon/Desktop/Music/aphex twin i care because you do | builtin_dd of=/dev/hda obs=32k seek=0'
INFO:	UTF-8 character encoding detected by locale settings.
	Assuming UTF-8 encoded filenames on source filesystem,
	use -input-charset to override.
Using BRUCE_SPRINGSTEEN_THE_WI000.JPG;1 for  01_1973_Bruce_Springsteen_The_Wild,_the_ Innocent,_and_the_ E_Street_Shuffle_mp3_192_catarulas_[GRuPoKuÃ‘aoRi/Bruce_Springsteen-The_Wild,_The%20innocent_And_The_E_Street_Shuffle-Trasera.jpg (Bruce_Springsteen-The_Wild,_The%20innocent_And_The_E_Street_Shuffle-Frontal.jpg)
Using AUNTIE_AUBREY_S_EXCURSIONS_B000 for  01_1973_Bruce_Springsteen_The_Wild,_the_ Innocent,_and_the_ E_Street_Shuffle_mp3_192_catarulas_[GRuPoKuÃ‘aoRi/Auntie Aubrey's Excursions Beyond The Call Of Duty (Disc 2) (Auntie Aubrey's Excursions Beyond The Call Of Duty (Disc 1))
Using JAMIE_LIDELL___WARP_ROUT000.MP3;1 for  /home/bon/Desktop/Music/01_1973_Bruce_Springsteen_The_Wild,_the_ Innocent,_and_the_ E_Street_Shuffle_mp3_192_catarulas_[GRuPoKuÃ‘aoRi/amon torin/Jamie Lidell - WARP-ROUTINE - 11 - Daddy's Car.mp3 (Jamie Lidell - WARP-ROUTINE - 05 - Entroscooper.mp3)
Using ALBUMART__5E09D4D8_6ACC_000.JPG;1 for  /home/bon/Desktop/Music/01_1973_Bruce_Springsteen_The_Wild,_the_ Innocent,_and_the_ E_Street_Shuffle_mp3_192_catarulas_[GRuPoKuÃ‘aoRi/jimi tenor live kid bob/salvia/AlbumArt_{5E09D4D8-6ACC-4356-9245-FB61AF328380}_Small.jpg (AlbumArt_{5E09D4D8-6ACC-4356-9245-FB61AF328380}_Large.jpg)
Using ALBUMART__499D51C9_6EC3_000.JPG;1 for  /home/bon/Desktop/Music/01_1973_Bruce_Springsteen_The_Wild,_the_ Innocent,_and_the_ E_Street_Shuffle_mp3_192_catarulas_[GRuPoKuÃ‘aoRi/jimi tenor live kid bob/salvia/AlbumArt_{499D51C9-6EC3-4510-B213-AD578CDC83A8}_Small.jpg (AlbumArt_{499D51C9-6EC3-4510-B213-AD578CDC83A8}_Large.jpg)
Using ALBUMART__2B86A946_01AE_000.JPG;1 for  /home/bon/Desktop/Music/01_1973_Bruce_Springsteen_The_Wild,_the_ Innocent,_and_the_ E_Street_Shuffle_mp3_192_catarulas_[GRuPoKuÃ‘aoRi/jimi tenor live kid bob/salvia/AlbumArt_{2B86A946-01AE-433C-9F7C-28CC26299A01}_Small.jpg (AlbumArt_{2B86A946-01AE-433C-9F7C-28CC26299A01}_Large.jpg)
Using THE_MATTHEW_HERBERT_BIG_000.MP3;1 for  /home/bon/Desktop/Music/01_1973_Bruce_Springsteen_The_Wild,_the_ Innocent,_and_the_ E_Street_Shuffle_mp3_192_catarulas_[GRuPoKuÃ‘aoRi/mathew herbet/the matthew herbert big band - misprints.mp3 (the matthew herbert big band - 03 - fiction.mp3)
Using MATTHEW_HERBERT___LET_S_000.MP3;1 for  /home/bon/Desktop/Music/01_1973_Bruce_Springsteen_The_Wild,_the_ Innocent,_and_the_ E_Street_Shuffle_mp3_192_catarulas_[GRuPoKuÃ‘aoRi/mathew herbet/Matthew Herbert - let's all make mistakes - 03 - isolÃ©e - r.mp3 (Matthew Herbert - let's all make mistakes - 01 - lost weigh.mp3)
Using MATTHEW_HERBERT___IT_S_O000.MP3;1 for  /home/bon/Desktop/Music/01_1973_Bruce_Springsteen_The_Wild,_the_ Innocent,_and_the_ E_Street_Shuffle_mp3_192_catarulas_[GRuPoKuÃ‘aoRi/mathew herbet/Matthew Herbert - It's only.mp3 (Matthew Herbert - It's only a reprise.mp3)
Using RADIOHEAD___HAIL_TO_THE_000.MP3;1 for  /home/bon/Desktop/Music/01_1973_Bruce_Springsteen_The_Wild,_the_ Innocent,_and_the_ E_Street_Shuffle_mp3_192_catarulas_[GRuPoKuÃ‘aoRi/mathew herbet/Hail To The Thief/Radiohead - Hail To The Thief - 15 - Screaming Backwards.mp3 (Radiohead - Hail To The Thief - 14 - A Wolf At the Door.mp3)
Using RADIOHEAD___HAIL_TO_THE_001.MP3;1 for  /home/bon/Desktop/Music/01_1973_Bruce_Springsteen_The_Wild,_the_ Innocent,_and_the_ E_Street_Shuffle_mp3_192_catarulas_[GRuPoKuÃ‘aoRi/mathew herbet/Hail To The Thief/Radiohead - Hail To The Thief - 14 - A Wolf At the Door.mp3 (Radiohead - Hail To The Thief - 13 - Scatterbrain.mp3)
Using RADIOHEAD___HAIL_TO_THE_002.MP3;1 for  /home/bon/Desktop/Music/01_1973_Bruce_Springsteen_The_Wild,_the_ Innocent,_and_the_ E_Street_Shuffle_mp3_192_catarulas_[GRuPoKuÃ‘aoRi/mathew herbet/Hail To The Thief/Radiohead - Hail To The Thief - 13 - Scatterbrain.mp3 (Radiohead - Hail To The Thief - 12 - Myxamatosis.mp3)
Using RADIOHEAD___HAIL_TO_THE_003.MP3;1 for  /home/bon/Desktop/Music/01_1973_Bruce_Springsteen_The_Wild,_the_ Innocent,_and_the_ E_Street_Shuffle_mp3_192_catarulas_[GRuPoKuÃ‘aoRi/mathew herbet/Hail To The Thief/Radiohead - Hail To The Thief - 12 - Myxamatosis.mp3 (Radiohead - Hail To The Thief - 11 - Punch Up At A Wedding.mp3)
Using RADIOHEAD___HAIL_TO_THE_004.MP3;1 for  /home/bon/Desktop/Music/01_1973_Bruce_Springsteen_The_Wild,_the_ Innocent,_and_the_ E_Street_Shuffle_mp3_192_catarulas_[GRuPoKuÃ‘aoRi/mathew herbet/Hail To The Thief/Radiohead - Hail To The Thief - 11 - Punch Up At A Wedding.mp3 (Radiohead - Hail To The Thief - 10 - I Will.mp3)
Using RADIOHEAD___HAIL_TO_THE_005.MP3;1 for  /home/bon/Desktop/Music/01_1973_Bruce_Springsteen_The_Wild,_the_ Innocent,_and_the_ E_Street_Shuffle_mp3_192_catarulas_[GRuPoKuÃ‘aoRi/mathew herbet/Hail To The Thief/Radiohead - Hail To The Thief - 10 - I Will.mp3 (Radiohead - Hail To The Thief - 09 - There There.mp3)
Using RADIOHEAD___HAIL_TO_THE_006.MP3;1 for  /home/bon/Desktop/Music/01_1973_Bruce_Springsteen_The_Wild,_the_ Innocent,_and_the_ E_Street_Shuffle_mp3_192_catarulas_[GRuPoKuÃ‘aoRi/mathew herbet/Hail To The Thief/Radiohead - Hail To The Thief - 09 - There There.mp3 (Radiohead - Hail To The Thief - 08 - The Gloaming.mp3)
Using RADIOHEAD___HAIL_TO_THE_007.MP3;1 for  /home/bon/Desktop/Music/01_1973_Bruce_Springsteen_The_Wild,_the_ Innocent,_and_the_ E_Street_Shuffle_mp3_192_catarulas_[GRuPoKuÃ‘aoRi/mathew herbet/Hail To The Thief/Radiohead - Hail To The Thief - 08 - The Gloaming.mp3 (Radiohead - Hail To The Thief - 07 - We Suck Young Blood.mp3)
Using RADIOHEAD___HAIL_TO_THE_008.MP3;1 for  /home/bon/Desktop/Music/01_1973_Bruce_Springsteen_The_Wild,_the_ Innocent,_and_the_ E_Street_Shuffle_mp3_192_catarulas_[GRuPoKuÃ‘aoRi/mathew herbet/Hail To The Thief/Radiohead - Hail To The Thief - 07 - We Suck Young Blood.mp3 (Radiohead - Hail To The Thief - 06 - Where I End and You Begin.mp3)
Using RADIOHEAD___HAIL_TO_THE_009.MP3;1 for  /home/bon/Desktop/Music/01_1973_Bruce_Springsteen_The_Wild,_the_ Innocent,_and_the_ E_Street_Shuffle_mp3_192_catarulas_[GRuPoKuÃ‘aoRi/mathew herbet/Hail To The Thief/Radiohead - Hail To The Thief - 06 - Where I End and You Begin.mp3 (Radiohead - Hail To The Thief - 05 - Go To Sleep.mp3)
Using RADIOHEAD___HAIL_TO_THE_00A.MP3;1 for  /home/bon/Desktop/Music/01_1973_Bruce_Springsteen_The_Wild,_the_ Innocent,_and_the_ E_Street_Shuffle_mp3_192_catarulas_[GRuPoKuÃ‘aoRi/mathew herbet/Hail To The Thief/Radiohead - Hail To The Thief - 05 - Go To Sleep.mp3 (Radiohead - Hail To The Thief - 04 - Backdrifts.mp3)
Using RADIOHEAD___HAIL_TO_THE_00B.MP3;1 for  /home/bon/Desktop/Music/01_1973_Bruce_Springsteen_The_Wild,_the_ Innocent,_and_the_ E_Street_Shuffle_mp3_192_catarulas_[GRuPoKuÃ‘aoRi/mathew herbet/Hail To The Thief/Radiohead - Hail To The Thief - 04 - Backdrifts.mp3 (Radiohead - Hail To The Thief - 03 - Sail To The Moon.mp3)
Using RADIOHEAD___HAIL_TO_THE_00C.MP3;1 for  /home/bon/Desktop/Music/01_1973_Bruce_Springsteen_The_Wild,_the_ Innocent,_and_the_ E_Street_Shuffle_mp3_192_catarulas_[GRuPoKuÃ‘aoRi/mathew herbet/Hail To The Thief/Radiohead - Hail To The Thief - 03 - Sail To The Moon.mp3 (Radiohead - Hail To The Thief - 02 - Sit Down Stand Up.mp3)
Using RADIOHEAD___HAIL_TO_THE_00D.MP3;1 for  /home/bon/Desktop/Music/01_1973_Bruce_Springsteen_The_Wild,_the_ Innocent,_and_the_ E_Street_Shuffle_mp3_192_catarulas_[GRuPoKuÃ‘aoRi/mathew herbet/Hail To The Thief/Radiohead - Hail To The Thief - 02 - Sit Down Stand Up.mp3 (Radiohead - Hail To The Thief - 01 - 2+2=5.mp3)
Using TERENCE_MC_KENNA___SPACE000.MP3;1 for  alien dream time/terence mc kenna - spacetime continuum - alien dream time - 05 of 06 - aero.mp3 (terence mc kenna - spacetime continuum - alien dream time - 04 of 06 - spea.mp3)
Using TERENCE_MC_KENNA___SPACE001.MP3;1 for  alien dream time/terence mc kenna - spacetime continuum - alien dream time - 04 of 06 - spea.mp3 (terence mc kenna - spacetime continuum - alien dream time - 03 of 06 - alie.mp3)
Using TERENCE_MC_KENNA___SPACE002.MP3;1 for  alien dream time/terence mc kenna - spacetime continuum - alien dream time - 03 of 06 - alie.mp3 (terence mc kenna - spacetime continuum - alien dream time - 02 of 06 - tran.mp3)
Using APHEX_TWIN___ANALORD_10_000.MP3;1 for  /home/bon/Desktop/Music/aphex twin (afx) - analord 01/afx - analord/analord 10/Aphex Twin - Analord 10 - 02 - Xmd5a.mp3 (Aphex Twin - Analord 10 - 01 - fenixfunk.mp3)
Using ALBUMART__B4624149_4A67_000.JPG;1 for  aphex twin i care because you do/albumart_{b4624149-4a67-4441-ab77-77f50327769e}_small.jpg (albumart_{b4624149-4a67-4441-ab77-77f50327769e}_large.jpg)
/dev/hda: engaging DVD-R DAO upon user request...
/dev/hda: reserving 2247120 blocks
:-[ RESERVE TRACK failed with SK=5h/ASC=30h/ACQ=05h]: Wrong medium type
/dev/hda: "Current Write Speed" is 1.0x1385KBps.
:-[ WRITE@LBA=0h failed with SK=5h/ASC=30h/ACQ=05h]: Wrong medium type
:-( media is not formatted or unsupported.
:-( write failed: Wrong medium type

---

