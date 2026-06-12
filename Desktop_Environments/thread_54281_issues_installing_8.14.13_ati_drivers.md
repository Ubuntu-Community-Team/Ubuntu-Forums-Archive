---
title: "issues installing 8.14.13 ati drivers?"
date: 2005-08-04
forum: Desktop Environments
---

### Post by holr on 2005-08-04
Hi!
Been reading the howto at [http://www.ubuntuforums.org/showthread.php?t=5356](http://www.ubuntuforums.org/showthread.php?t=5356) to try to get a better performance with the newer 8.14.13 drivers (rather than the ones you get with sudo apt-get install xorg-driver-fglrx). Running into some troubles and I dont know where im going wrong....

I have downloaded the kernel source (about 35mb) as a file called  linux-source-2.6.10.tar.bz2 , (through synaptic i think!) btw my uname -r brings "2.6.10-5-386" so i guess i have the right source, I unextracted it to /usr/src/linux-source-2.6.10.

Then created the symlink thing at /usr/src/linux ( sudo ln -s /usr/src/linux-source-2.6.10 /usr/src/linux)

I downloaded the latest xorg rpm from the ati website, alien'd it to a .deb and installed with  sudo dpkg -i --force-overwrite fglrx-6-8-0_8.14.13-2_i386.deb

However, when i try running the fglrx install, from the directory /lib/modules/fglrx/build_mod, with command sudo ./make.sh (I have chmod +x make.sh already) I get the following error:

ATI module generator V 2.0
==========================
initializing...
kernel includes at /usr/src/linux/include not found or incomplete
file: /usr/src/linux/include/linux/version.h

And fair enough, the version.h does not exist in the folder mentioned. I did a updatedb and then a "locate version.h" and got this:
/usr/include/linux/dvb/version.h
/usr/include/linux/version.h
/usr/include/gnu/libc-version.h
/usr/lib/perl5/Gnome2/Canvas/Install/gnomecanvasperl-version.h
/usr/lib/perl5/Gnome2/VFS/Install/vfs2perl-version.h
/usr/src/linux-source-2.6.10/arch/i386/math-emu/version.h
/usr/src/linux-source-2.6.10/drivers/net/sk98lin/h/skversion.h
/usr/src/linux-source-2.6.10/drivers/net/wireless/acx/version.h
/usr/src/linux-source-2.6.10/drivers/scsi/qla2xxx/qla_version.h
/usr/src/linux-source-2.6.10/fs/xfs/linux-2.6/xfs_version.h
/usr/src/linux-source-2.6.10/include/linux/dvb/version.h
/usr/src/linux-source-2.6.10/include/sound/version.h
/usr/src/linux-source-2.6.10/include/pcmcia/version.h
/usr/src/linux-source-2.6.10/include/wlan/version.h

Have I set up my symlink wrong? As there are plenty of version.h's about in the kernel-source!

Please help, I was enjoying a smooth game of doom 3 under fedora with the latest ati drivers (some reason doom  3 is much faster on linux than windows for me) but in all honesty I love ubuntu so much more. Its just that, on my year-old machine, the xorg-driver-fglrx doesnt cut the mustard with doom 3 for me, this is why I would like the latest drivers!

Thanks for any help! I can stop tearing my hair out then!

---

### Post by holr on 2005-08-04
[QUOTE=holr]Hi!
Been reading the howto at [http://www.ubuntuforums.org/showthread.php?t=5356](http://www.ubuntuforums.org/showthread.php?t=5356) to try to get a better performance with the newer 8.14.13 drivers (rather than the ones you get with sudo apt-get install xorg-driver-fglrx). Running into some troubles and I dont know where im going wrong....

I have downloaded the kernel source (about 35mb) as a file called  linux-source-2.6.10.tar.bz2 , (through synaptic i think!) btw my uname -r brings "2.6.10-5-386" so i guess i have the right source, I unextracted it to /usr/src/linux-source-2.6.10.

Then created the symlink thing at /usr/src/linux ( sudo ln -s /usr/src/linux-source-2.6.10 /usr/src/linux)

I downloaded the latest xorg rpm from the ati website, alien'd it to a .deb and installed with  sudo dpkg -i --force-overwrite fglrx-6-8-0_8.14.13-2_i386.deb

However, when i try running the fglrx install, from the directory /lib/modules/fglrx/build_mod, with command sudo ./make.sh (I have chmod +x make.sh already) I get the following error:

ATI module generator V 2.0
==========================
initializing...
kernel includes at /usr/src/linux/include not found or incomplete
file: /usr/src/linux/include/linux/version.h

And fair enough, the version.h does not exist in the folder mentioned. I did a updatedb and then a "locate version.h" and got this:
/usr/include/linux/dvb/version.h
/usr/include/linux/version.h
/usr/include/gnu/libc-version.h
/usr/lib/perl5/Gnome2/Canvas/Install/gnomecanvasperl-version.h
/usr/lib/perl5/Gnome2/VFS/Install/vfs2perl-version.h
/usr/src/linux-source-2.6.10/arch/i386/math-emu/version.h
/usr/src/linux-source-2.6.10/drivers/net/sk98lin/h/skversion.h
/usr/src/linux-source-2.6.10/drivers/net/wireless/acx/version.h
/usr/src/linux-source-2.6.10/drivers/scsi/qla2xxx/qla_version.h
/usr/src/linux-source-2.6.10/fs/xfs/linux-2.6/xfs_version.h
/usr/src/linux-source-2.6.10/include/linux/dvb/version.h
/usr/src/linux-source-2.6.10/include/sound/version.h
/usr/src/linux-source-2.6.10/include/pcmcia/version.h
/usr/src/linux-source-2.6.10/include/wlan/version.h

Have I set up my symlink wrong? As there are plenty of version.h's about in the kernel-source!

Please help, I was enjoying a smooth game of doom 3 under fedora with the latest ati drivers (some reason doom  3 is much faster on linux than windows for me) but in all honesty I love ubuntu so much more. Its just that, on my year-old machine, the xorg-driver-fglrx doesnt cut the mustard with doom 3 for me, this is why I would like the latest drivers!

Thanks for any help! I can stop tearing my hair out then![/QUOTE]
 any ideas?

---

### Post by holr on 2005-08-05
Managed to get it all working - had to install some linux-kernel headers and symlink those instead!

Great stuff - much better performance and doom 3 runs smooth ;-)

---

