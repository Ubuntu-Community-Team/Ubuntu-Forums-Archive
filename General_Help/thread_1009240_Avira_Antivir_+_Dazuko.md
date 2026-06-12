---
title: "Avira Antivir + Dazuko"
date: 2008-12-12
forum: General Help
---

### Post by lord_lethris on 2008-12-12
**[CENTER][B][SIZE="5"]GRAVE DIGGING![/SIZE]**[/CENTER][/B]

Sorry to bring this up again.  I have searched the forum and found many entries on the subject... but no solutions!

And before I get flamed with "[COLOR="DarkOrange"]why do you need a virus checker with linux[/COLOR] :mad:".
Let me save your rant with "[COLOR="RoyalBlue"]I have My reasons - mainly mantanance[/COLOR] :p"

I have been here and done that.

[http://ubuntuforums.org/showthread.php?t=430920](http://ubuntuforums.org/showthread.php?t=430920)
[http://ubuntuforums.org/showthread.php?t=52385](http://ubuntuforums.org/showthread.php?t=52385)
[http://ubuntuforums.org/showthread.php?t=204501](http://ubuntuforums.org/showthread.php?t=204501)
[http://ubuntuforums.org/showthread.php?t=476486](http://ubuntuforums.org/showthread.php?t=476486)
[http://ubuntuforums.org/showthread.php?t=6085](http://ubuntuforums.org/showthread.php?t=6085)

The error im getting is at the Dazuko [COLOR="SeaGreen"]SUDO MAKE[/COLOR] stage. :-

```
make -C /lib/modules/2.6.27-9-generic/build SUBDIRS="/home/lethris/dazuko-2.3.5-pre1" modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-9-generic'
  CC [M]  /home/lethris/dazuko-2.3.5-pre1/dazuko_core.o
In file included from /home/lethris/dazuko-2.3.5-pre1/dazuko_platform.h:4,
                 from /home/lethris/dazuko-2.3.5-pre1/dazuko_core.c:36:
/home/lethris/dazuko-2.3.5-pre1/dazuko_linux26.h:27:27: error: asm/semaphore.h: No such file or directory
In file included from /home/lethris/dazuko-2.3.5-pre1/dazuko_platform.h:4,
                 from /home/lethris/dazuko-2.3.5-pre1/dazuko_core.c:36:
/home/lethris/dazuko-2.3.5-pre1/dazuko_linux26.h:50: error: field &#8216;mutex&#8217; has incomplete type
make[2]: *** [/home/lethris/dazuko-2.3.5-pre1/dazuko_core.o] Error 1
make[1]: *** [_module_/home/lethris/dazuko-2.3.5-pre1] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-9-generic'
make: *** [dummy_rule] Error 2
```

I have also tried most of theses - [http://www.dazuko.org/files/](http://www.dazuko.org/files/)

Any takers on a final [SOLVED] :D

And I know scanning windows drives you dont really need a stay resident scanner... but it would be nice to set it up, since "apparently" you can.

AAAAnd I know f-prot might be better, or clam.. But I use Avira on other windows PC's, and from a technical point of view, its easer to keep it in the family when VDF updates are involved.

---

### Post by lord_lethris on 2008-12-23
I guess no one knows then :(

---

### Post by lord_lethris on 2008-12-29
nope.  I guess so.

---

### Post by nickbrooker on 2009-01-30
Hi,

I'm trying the same thing.  I got a bit further though.

I got redirfs to compile ok.  Version 0.6 worked for me.

Then for dazuko got the same error. I'm not sure if it's correct but in the /usr/src/kernelversion/include/ there is an asm link to asm-x86 which does not have the semaphore.h file but include/linux does.  So either copying the file to asm or changing the link worked to get passed that error but then I get..

```
make -C /lib/modules/2.6.28-gentoo-r1/build SUBDIRS="/home/nick/Desktop/Downloads/antivir-workstation-pers-2.1.12-19/contrib/dazuko/dazuko-2.3.5-pre1" modules
make[1]: Entering directory `/usr/src/linux-2.6.28-gentoo-r1'
  CC [M]  /home/nick/Desktop/Downloads/antivir-workstation-pers-2.1.12-19/contrib/dazuko/dazuko-2.3.5-pre1/dazuko_core.o
  CC [M]  /home/nick/Desktop/Downloads/antivir-workstation-pers-2.1.12-19/contrib/dazuko/dazuko-2.3.5-pre1/dazuko_transport.o
  CC [M]  /home/nick/Desktop/Downloads/antivir-workstation-pers-2.1.12-19/contrib/dazuko/dazuko-2.3.5-pre1/dazuko_linux26_lsm.o
In file included from /home/nick/Desktop/Downloads/antivir-workstation-pers-2.1.12-19/contrib/dazuko/dazuko-2.3.5-pre1/dazuko_linux26_lsm.c:23:
/home/nick/Desktop/Downloads/antivir-workstation-pers-2.1.12-19/contrib/dazuko/dazuko-2.3.5-pre1/dazuko_linux26_lsm.h:653: error: unknown field 'register_security' specified in initializer
/home/nick/Desktop/Downloads/antivir-workstation-pers-2.1.12-19/contrib/dazuko/dazuko-2.3.5-pre1/dazuko_linux26_lsm.h:653: warning: missing braces around initializer
/home/nick/Desktop/Downloads/antivir-workstation-pers-2.1.12-19/contrib/dazuko/dazuko-2.3.5-pre1/dazuko_linux26_lsm.h:653: warning: (near initialization for 'dazuko_register_security_ops.name')
/home/nick/Desktop/Downloads/antivir-workstation-pers-2.1.12-19/contrib/dazuko/dazuko-2.3.5-pre1/dazuko_linux26_lsm.h:653: warning: initialization makes integer from pointer without a cast
/home/nick/Desktop/Downloads/antivir-workstation-pers-2.1.12-19/contrib/dazuko/dazuko-2.3.5-pre1/dazuko_linux26_lsm.h:653: error: initializer element is not computable at load time
/home/nick/Desktop/Downloads/antivir-workstation-pers-2.1.12-19/contrib/dazuko/dazuko-2.3.5-pre1/dazuko_linux26_lsm.h:653: error: (near initialization for 'dazuko_register_security_ops.name[0]')

```

The more observant will note I'm using Gentoo rather than Ubantu but I'm not finding much help on this one anywhere...

Any help from here?  This is more programmy than I do.:D

---

### Post by jaygeebuntu on 2009-02-01
You might find this link interesting/useful:

[http://allyourtech.com/content/articles/15_01_2006_installing_antivir_with_on_access_scanning_in_ubuntu_linux.php](http://allyourtech.com/content/articles/15_01_2006_installing_antivir_with_on_access_scanning_in_ubuntu_linux.php)

Also a new version of AntiVir for Unix is on its way according to:

[http://forum.avira.com/wbb/index.php?page=Thread&threadID=81395](http://forum.avira.com/wbb/index.php?page=Thread&threadID=81395)

---

### Post by tmsbrdrs on 2009-03-17
@jaygeebuntu

Your first link no longer works. I'm having the same troubles as have been posted.

I've done my research and so far have found no fixes or alternate installation procedures for Dazuko on the kernel used in Intrepid.

I've been wondering if there is a standalone antivirus app which does not use Dazuko for real-time antivirus scanning. 

Because my computer is connected to a Windows PC and because I routinely help friends with projects and papers, meaning I do lots of file transfers, I would prefer to have real-time antivirus scanning. Avira has a better heuristics engine than Avast! but I haven't found a way to have it quarantine what it finds yet. What would help most is the real-time scanning, but as I said, no Dazuko for the kernel used in Intrepid. 

What we need is one of two things. 

1) Instructions for a working installation of Dazuko in Intrepid. 

or

2) An antivirus solution which does not use Dazuko.

---

### Post by mb_webguy on 2009-03-17
I don't have any experience with Dazuko, but I have a few suggestions after a bit of Googling.

The Ubuntu community [Dazuku Troubleshooting]("https://help.ubuntu.com/community/DazukoTroubleshooting") page has a couple of methods of installing Dazuku.

Also, I'm assuming you've tried the instructions on the [Dazuku installation page]("http://dazuko.dnsalias.org/wiki/index.php/Installation_HOWTO").  If you have problems installing DazukuFS, you might want to try the [previous version]("http://dazuko.dnsalias.org/wiki/index.php/Installation_HOWTO_(Dazuko_2.x)").

Finally, you might want to use [checkinstall]("https://help.ubuntu.com/community/CheckInstall") when you get to the "sudo make install" stage.

---

### Post by jaygeebuntu on 2009-03-18
> **tmsbrdrs said:**
> @jaygeebuntu

Your first link no longer works...

Worked fine for me a couple of minutes ago.

BTW I've just made a post on the AV forum asking for a forecast availability date for the new AV for UNIX version. Will keep you posted.

---

### Post by jaygeebuntu on 2009-03-19
> **jaygeebuntu said:**
> 
BTW I've just made a post on the AV forum asking for a forecast availability date for the new AV for UNIX version. Will keep you posted.

According to Avira the new AV for UNIX version is in beta and is due for release later this month.

---

### Post by tmsbrdrs on 2009-04-02
I think it was just down when I tried it before. I checked it again a few minutes ago and it's working fine now. 

Does anyone know if Dazuko works with Jaunty?

---

### Post by jaygeebuntu on 2009-04-02
Here's the AntiVir for Linux link: [http://www.free-av.de/de/download/download_servers.php](http://www.free-av.de/de/download/download_servers.php)

The latest version is detailed in the first entry in the "Produkte" column.

HTH

---

### Post by tomcheng76 on 2009-05-08
Ubuntu Jaunty can install antivir avguard through this steps (test in AMD64 platform)
1. go [here]("http://www.free-av.com/en/download/download_servers.php") download Avira AntiVir Personal - FREE Antivirus for Linux / Solaris
2. Install it (DAZUKOFS install failed)
3. go [here]("http://dazuko.dnsalias.org/wiki/index.php/Downloads") and download dazukofs-3.0.0.tar.gz
4. install dazukofs using this [howto]("http://dazuko.dnsalias.org/wiki/index.php/Installation_HOWTO") (pleas apply patch patch-ubuntu-8.10)
5. In Step 4: Test DazukoFS, before executing showfiles, copy libdazukofs.so to /usr/lib, it should be in the dazukofs-3.0.0/test/lib directory.
6. After Step 5: Install DazukoFS, append a line
> dazukofs
to the end of /etc/modules 
7. reboot system

you can check avguard by following the step in antivir-workstation-pers-3.0.2-5/doc/avserver_en.pdf - 4.2 Testing Avira AntiVir Server

Here is the result
> $ cat /var/log/avguard.log
2009-05-09 02:02:25 bomber-C2D avguard.bin[3078]: AVGU: INFO Info: Using library for dazuko version 3 
2009-05-09 02:13:51 bomber-C2D avguard.bin[3080]: AVGU: ALERT AntiVir ALERT for file "/home/bomber/Download/eicar.com": Eicar-Test-Signature ; virus ; Contains code of the Eicar-Test-Signature virus
2009-05-09 02:13:51 bomber-C2D avguard.bin[3080]: AVGU: INFO Info: the alert in file /home/bomber/Download/eicar.com was handled. Action(s) taken: access denied, condition logged
2009-05-09 02:13:51 bomber-C2D avguard.bin[3080]: AVGU: INFO Info: automatically excluding /sys/ from scan (special fs)
2009-05-09 02:13:51 bomber-C2D avguard.bin[3080]: AVGU: INFO Info: automatically excluding /proc/ from scan (special fs)
2009-05-09 02:13:51 bomber-C2D avguard.bin[3080]: AVGU: INFO Info: automatically excluding /home/quarantine/ from scan (quarantine)
2009-05-09 02:13:51 bomber-C2D avguard.bin[3080]: AVGU: ALERT AntiVir ALERT for file "/home/bomber/Download/eicar.com": Eicar-Test-Signature ; virus ; Contains code of the Eicar-Test-Signature virus
2009-05-09 02:13:51 bomber-C2D avguard.bin[3080]: AVGU: INFO Info: the alert in file /home/bomber/Download/eicar.com was handled. Action(s) taken: access denied, condition logged
2009-05-09 02:14:49 bomber-C2D avguard.bin[3080]: AVGU: ALERT AntiVir ALERT for file "/home/bomber/Download/eicar.com": Eicar-Test-Signature ; virus ; Contains code of the Eicar-Test-Signature virus
2009-05-09 02:14:49 bomber-C2D avguard.bin[3080]: AVGU: INFO Info: the alert in file /home/bomber/Download/eicar.com was handled. Action(s) taken: access denied, condition logged

Hope it helps someone. :)

---

### Post by RT236 on 2009-05-27
> **tomcheng76 said:**
> Ubuntu Jaunty can install antivir avguard through this steps (test in AMD64 platform)
1. go [here]("http://www.free-av.com/en/download/download_servers.php") download Avira AntiVir Personal - FREE Antivirus for Linux / Solaris
2. Install it (DAZUKOFS install failed)
3. go [here]("http://dazuko.dnsalias.org/wiki/index.php/Downloads") and download dazukofs-3.0.0.tar.gz
4. install dazukofs using this [howto]("http://dazuko.dnsalias.org/wiki/index.php/Installation_HOWTO") (pleas apply patch patch-ubuntu-8.10)
5. In Step 4: Test DazukoFS, before executing showfiles, copy libdazukofs.so to /usr/lib, it should be in the dazukofs-3.0.0/test/lib directory.
6. After Step 5: Install DazukoFS, append a line

to the end of /etc/modules 
7. reboot system

you can check avguard by following the step in antivir-workstation-pers-3.0.2-5/doc/avserver_en.pdf - 4.2 Testing Avira AntiVir Server

Here is the result


Hope it helps someone. :)

This was excellent information.  I am able to successfully load dazuko into the kernel and use real-time scanning with AntiVir in Jaunty, although, I do find it slows down my system some.  Great info!  Thanks for posting!

**UPDATE:**  Although this was very successful for me in loading dazukofs as a kernel module I found AntiVir + dazukofs was slowing down my system.  I ended up removing AntiVir and also commented out dazukofs in fstab.  My system sped up significantly.  I went back to using KlamAV and setting a crontab for nightly scanning.  I used to use dazuko.ko as my kernel module with SuSE and Ubuntu until AppArmor, etc. prevented coexistence with dazuko.ko.  I have no idea why my system slowed down so much with dazukofs loaded as a kernel module.  Anyway, I'm really pleased you posted this information.  At minimal, I now know it's 100% possible to install Dazuko into Jaunty very successfully.  I just posted this in case someone else found their system slowed down.  I use a virus scanner for Windows reasons...

---

### Post by Erick001 on 2009-05-28
Ok, worked to me. But it didn't install Avira GUI. How can I do it?

---

### Post by RT236 on 2009-05-29
> **Erick001 said:**
> Ok, worked to me. But it didn't install Avira GUI. How can I do it?

Apparently the GUI was removed in the latest free version.  I believe the premium version is required.  This is a new change.  I used to use the GUI via antivir-gui but apparently it's disabled in the latest free version.

---

### Post by zolero on 2009-07-14
> **RT236 said:**
> Apparently the GUI was removed in the latest free version.  I believe the premium version is required.  This is a new change.  I used to use the GUI via antivir-gui but apparently it's disabled in the latest free version.

Look in your installer package's ../contrib/applet directory. There is an applet source to be compiled. I think that's some kind of GUI... anyway something graphical at least... :p

---

