---
title: "Plextor SCSI CD lockup"
date: 2009-04-22
forum: General Help
---

### Post by Prof.Arronax on 2009-04-22
Greetings.

This machine has 1 IDE DVD/CDRW drive and 1 SCSI based Plextor PX-W1210S type drive. It can sometimes read a *data* CDROM, but hard-locks the machine (turn off the power switch - down to hardware level lockup) whenever an audio or mixed media disc is inserted.  The IDE drive suffers no such problems.  Using SysInfo,I find no mention of the SCSI controller card (Initio INI-9100U/UW) in its Storage listings.  SysInfo however *does* show the presence of the Plextor drive as SCSI device scsi0.  It goes on to list the IDE type hard disk and the DVD/CDRW drive as SCSI devices as well (???), namely scsi1 and scsi2 in that order.  

A prior version of Ubuntu (I believe 7.xx or 6.xx) did recognise and utilise the Plextor drive properly, without any intervention on my part.  Does this current version not have the detection capability for the SCSI controller and its attached devices?  If not, what must I install/uninstall to finally use this drive?

T.I.A.

---

### Post by christophevr on 2009-05-14
Hello,

Over here just the same problem. ubuntu Jaunty 9.04 . Yess it's a very old machine (2 pentium II 400 processors). 2 hardisk Ultra2 scsi, 2 plextor drives one only reader ultraplex 40 scsi2 one plexwriter 8/2/20 (they are all 13 year old -:)) . Harddisk connected on ultra2 white corect cable and Ultra2/Lvd se terminator. Cdrom's connected to the wide connector it's the adaptec chipset 7880 chipset white the extra aic3860 (to be able using ultra2 at 16 bits and wide 8 bits devices. At full performance. with debian up to lenny everything run's fine. But whit ubuntu when inserting audio cd into plextor system lock-up. After a very very long time +- 5 minutes. message unable to mount audio cdrom appears. Data cdrom's are mounted perfectly. On this pc I also have a DVD writer connected to the ide bus. There I can mount an audio cd but it's going orfully slow to rip a cd. 
Mb is asus P2B-DS. acutally 512 MB pc100 sdram non-ecc,2 processors PII 400 , 2 Hd 18 GB IBM Ultra 2 10000 rpm,One hd 250 GB IDE maxtor.Ubuntu installed one IBM HD1 Home on IBM HD2 . Maxtor only used to keep big data like dvd iso's and music library.

Is there maybe a driver which has to be changed ? It's seems something like that. White debian(lenny) problem does not occur.

Also IDE devices seems to be detected as scsi devices, but do work very slow (but that's more cause it's and old ide bus max ultraDMA/33) 

I noticed that ubuntu does have problems to make difference between ide,scsi and also sata. But never was able to find out why.:-k

---

### Post by christophevr on 2009-05-14
Hello Again, I dunno if one off the specialist do sometimes see dis message. But I thaught Maybe put some more info. I just installed scsi list device program whit synaptic. (to use lsscsi) This is the output. I put some comments to it.
[0:0:0:0]    disk    ATA      MAXTOR STM325082 3.AA  /dev/sda 
my comment: hd maxtor located on ide 1 primary
[1:0:0:0]    cd/dvd  _NEC     DVD_RW ND-3540A  1.04  /dev/sr0 
my comment: DVD RW optiarc located in ide2 primary
[2:0:0:0]    disk    IBM      DDYS-T18350N     SA2A  /dev/sdb 
my comment: HD 1 located ultra2 connector scsi adress 0
[2:0:1:0]    disk    IBM      DDYS-T18350N     SA2A  /dev/sdc 
my comment: Hd 2 located on ultra2 connector scsi adres 1
[2:0:3:0]    cd/dvd  PLEXTOR  CD-ROM PX-40TS   1.10  /dev/sr1 
my comment:Cd-rom reader located on uw scsi connector scsi adress 3
[2:0:4:0]    cd/dvd  PLEXTOR  CD-R   PX-W8220T 1.05  /dev/sr2 
my comment:Cd-rom reader/writer located on uw scsi connector scsi adress 4

p;s. Terminations and bios configuration of scsi is correct. It does work under debian.

maybe solution or work around can be found using sdparm or one off the scsi tools ?? Since it does mount perfectly a Data cd But not an audio cd. Actually mounting an audio cd lock's the system up. Giving at the end (after I removed the cd ) Could not mount audio cd, Dbus error. ?? 

Audio cd can well be mounted into the ide dvd writer . But on this pc performance from ide is very very very slow. 

Ter info it's the first time i couldn't find a solution or work around into linux I'm using debian now for 5 years but are brand new on ubuntu. But since debian and ubuntu are very similar except that ubuntu is much more advanced whit kernel I think there must be somewhere a solution, I even think a very small work around, but those can take long to find :-) :-k

greetings christophe

---

