---
title: "Ubuntu Customisation Kit [UCK] error. Please help."
date: 2010-12-07
forum: Development CD/DVD Image Testing
---

### Post by ProcuratorIncendia on 2010-12-07
I was hoping to create a custom ubuntu distro. [I like flavour instead of distro]
...using the Ubuntu Customisation Kit. I tried twice and both times I got an error.
```
Ubuntu Customization Kit 2.2.1
Starting CD remastering on  Tue Dec 7 18:33:04 GMT 2010
Customization dir=/home/user/tmp/customization-scripts
Mounting ISO image...
Unpacking ISO image...
Unmounting ISO image...
Mounting SquashFS image...
Unpacking SquashFS image...
Unmounting SquashFS image...
Creating apt cache...
Creating root home...
Mounting /proc
Mounting /sys
Mounting /dev/pts
Mounting /var/run
Mounting /tmp
Mounting /home/user/tmp/remaster-root-home
Mounting /home/user/tmp/remaster-apt-cache
Mounting /home/user/tmp/customization-scripts
Copying resolv.conf...
Creating DBUS uuid...
Get:1 http://security.ubuntu.com maverick-security Release.gpg [198B]
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en
Get:2 http://archive.ubuntu.com maverick Release.gpg [198B]
Ign http://archive.ubuntu.com/ubuntu/ maverick/main Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en
Get:3 http://security.ubuntu.com maverick-security Release [27.2kB]
Get:4 http://archive.ubuntu.com maverick-updates Release.gpg [198B]
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en
Get:5 http://archive.ubuntu.com maverick Release [39.8kB]
Get:6 http://archive.ubuntu.com maverick-updates Release [31.4kB]
Get:7 http://archive.ubuntu.com maverick/main Sources [829kB]
Get:8 http://security.ubuntu.com maverick-security/main Sources [15.5kB]
Get:9 http://security.ubuntu.com maverick-security/restricted Sources [14B]
Get:10 http://security.ubuntu.com maverick-security/main i386 Packages [48.0kB]
Get:11 http://security.ubuntu.com maverick-security/restricted i386 Packages [14B]
Get:12 http://archive.ubuntu.com maverick/restricted Sources [4370B]
Get:13 http://archive.ubuntu.com maverick/main i386 Packages [1492kB]
Get:14 http://archive.ubuntu.com maverick/restricted i386 Packages [5992B]
Get:15 http://archive.ubuntu.com maverick-updates/main Sources [47.6kB]
Get:16 http://archive.ubuntu.com maverick-updates/restricted Sources [14B]
Get:17 http://archive.ubuntu.com maverick-updates/main i386 Packages [125kB]
Get:18 http://archive.ubuntu.com maverick-updates/restricted i386 Packages [14B]
Fetched 2667kB in 3s (686kB/s)
Reading package lists...
Installing language packs (en)...
Reading package lists...
Building dependency tree...
Reading state information...
language-pack-en is already the newest version.
language-pack-en-base is already the newest version.
language-pack-gnome-en is already the newest version.
language-pack-gnome-en-base is already the newest version.
language-support-en is already the newest version.
language-support-writing-en is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 186 not upgraded.
Removing unnecessary language packages...
Reading package lists...
Building dependency tree...
Reading state information...
The following packages will be REMOVED:
  language-pack-bn* language-pack-bn-base* language-pack-de*
  language-pack-de-base* language-pack-es* language-pack-es-base*
  language-pack-gnome-bn* language-pack-gnome-bn-base* language-pack-gnome-de*
  language-pack-gnome-de-base* language-pack-gnome-es*
  language-pack-gnome-es-base* language-pack-gnome-pt*
  language-pack-gnome-pt-base* language-pack-gnome-xh*
  language-pack-gnome-xh-base* language-pack-gnome-zh-hans*
  language-pack-gnome-zh-hans-base* language-pack-pt* language-pack-pt-base*
  language-pack-xh* language-pack-xh-base* language-pack-zh-hans*
  language-pack-zh-hans-base*
0 upgraded, 0 newly installed, 24 to remove and 186 not upgraded.
After this operation, 138MB disk space will be freed.
(Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 124413 files and directories currently installed.)
Removing language-pack-gnome-es-base ...
Purging configuration files for language-pack-gnome-es-base ...
Removing language-pack-gnome-es ...
Removing language-pack-es-base ...
Purging configuration files for language-pack-es-base ...
Removing language-pack-gnome-pt-base ...
Purging configuration files for language-pack-gnome-pt-base ...
Removing language-pack-gnome-xh-base ...
Purging configuration files for language-pack-gnome-xh-base ...
Removing language-pack-gnome-zh-hans-base ...
Purging configuration files for language-pack-gnome-zh-hans-base ...
Removing language-pack-gnome-bn-base ...
Purging configuration files for language-pack-gnome-bn-base ...
Removing language-pack-gnome-bn ...
Removing language-pack-bn-base ...
Purging configuration files for language-pack-bn-base ...
Removing language-pack-gnome-de-base ...
Purging configuration files for language-pack-gnome-de-base ...
Removing language-pack-gnome-de ...
Removing language-pack-de-base ...
Purging configuration files for language-pack-de-base ...
Removing language-pack-es ...
Removing language-pack-gnome-pt ...
Removing language-pack-gnome-xh ...
Removing language-pack-gnome-zh-hans ...
Removing language-pack-pt-base ...
Purging configuration files for language-pack-pt-base ...
Removing language-pack-xh-base ...
Purging configuration files for language-pack-xh-base ...
Removing language-pack-zh-hans-base ...
Purging configuration files for language-pack-zh-hans-base ...
Removing language-pack-bn ...
Removing language-pack-de ...
Removing language-pack-pt ...
Removing language-pack-xh ...
Removing language-pack-zh-hans ...
Processing triggers for software-center ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.C.cache...
Processing triggers for python-central ...
Processing triggers for python-support ...
CHOICE='Continue building'
Done
Removing generated machine uuid...
Removing generated resolv.conf...
Unmounting /home/user/tmp/remaster-root/tmp/customization-scripts...
Unmounting /home/user/tmp/remaster-root/var/cache/apt...
Unmounting /home/user/tmp/remaster-root/root...
Unmounting /home/user/tmp/remaster-root/tmp...
Unmounting /home/user/tmp/remaster-root/var/run...
Unmounting /home/user/tmp/remaster-root/dev/pts...
Unmounting /home/user/tmp/remaster-root/sys...
Unmounting /home/user/tmp/remaster-root/proc...
Cleaning up temporary directories...
Running ISO customization script /home/user/tmp/customization-scripts/customize_iso...
--2010-12-07 18:43:32--  http://archive.ubuntu.com/ubuntu/pool/main/g/gfxboot-theme-ubuntu/gfxboot-theme-ubuntu_0.10.2.tar.gz
Resolving archive.ubuntu.com... 91.189.92.169, 91.189.92.170, 91.189.92.171, ...
Connecting to archive.ubuntu.com|91.189.92.169|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 199953 (195K) [application/x-gzip]
Saving to: `gfxboot-theme-ubuntu_0.10.2.tar.gz'

     0K .......... .......... .......... .......... .......... 25%  623K 0s
    50K .......... .......... .......... .......... .......... 51% 1.18M 0s
   100K .......... .......... .......... .......... .......... 76% 1.35M 0s
   150K .......... .......... .......... .......... .....     100% 1.36M=0.2s

2010-12-07 18:43:32 (1.00 MB/s) - `gfxboot-theme-ubuntu_0.10.2.tar.gz' saved [199953/199953]

make -C po
make[1]: Entering directory `/tmp/tmp.QAn2MQc2Fk/gfxboot-theme-ubuntu/po'
bin/po2txt bootloader.pot >en.tr
bin/po2txt am.po >am.tr
bin/po2txt ar.po >ar.tr
bin/po2txt ast.po >ast.tr
bin/po2txt be.po >be.tr
bin/po2txt bg.po >bg.tr
bin/po2txt bn.po >bn.tr
bin/po2txt bs.po >bs.tr
bin/po2txt ca.po >ca.tr
bin/po2txt cs.po >cs.tr
bin/po2txt da.po >da.tr
bin/po2txt de.po >de.tr
bin/po2txt el.po >el.tr
bin/po2txt eo.po >eo.tr
bin/po2txt es.po >es.tr
bin/po2txt et.po >et.tr
bin/po2txt eu.po >eu.tr
bin/po2txt fi.po >fi.tr
bin/po2txt fr.po >fr.tr
bin/po2txt ga.po >ga.tr
bin/po2txt gl.po >gl.tr
bin/po2txt gu.po >gu.tr
bin/po2txt he.po >he.tr
bin/po2txt hi.po >hi.tr
bin/po2txt hr.po >hr.tr
bin/po2txt hu.po >hu.tr
bin/po2txt id.po >id.tr
bin/po2txt it.po >it.tr
bin/po2txt ja.po >ja.tr
bin/po2txt ka.po >ka.tr
bin/po2txt kk.po >kk.tr
bin/po2txt km.po >km.tr
bin/po2txt ko.po >ko.tr
bin/po2txt ku.po >ku.tr
bin/po2txt lt.po >lt.tr
bin/po2txt lv.po >lv.tr
bin/po2txt mk.po >mk.tr
bin/po2txt ml.po >ml.tr
bin/po2txt nb.po >nb.tr
bin/po2txt ne.po >ne.tr
bin/po2txt nl.po >nl.tr
bin/po2txt nn.po >nn.tr
bin/po2txt pl.po >pl.tr
bin/po2txt pt_BR.po >pt_BR.tr
bin/po2txt pt.po >pt.tr
bin/po2txt pt_PT.po >pt_PT.tr
bin/po2txt ro.po >ro.tr
bin/po2txt ru.po >ru.tr
bin/po2txt sk.po >sk.tr
bin/po2txt sl.po >sl.tr
bin/po2txt sq.po >sq.tr
bin/po2txt sr.po >sr.tr
bin/po2txt sv.po >sv.tr
bin/po2txt ta.po >ta.tr
bin/po2txt th.po >th.tr
bin/po2txt tl.po >tl.tr
bin/po2txt tr.po >tr.tr
bin/po2txt uk.po >uk.tr
bin/po2txt vi.po >vi.tr
bin/po2txt zh_CN.po >zh_CN.tr
bin/po2txt zh_TW.po >zh_TW.tr
make[1]: Leaving directory `/tmp/tmp.QAn2MQc2Fk/gfxboot-theme-ubuntu/po'
mkdir -p boot
mkbootmsg -O -v -L ../.. -l boot/log -c boot.config boot/init
make: mkbootmsg: Command not found
make: *** [bootdir] Error 127
Failed to build gfxboot theme
Ubuntu Customization Kit 2.2.1
Starting CD remastering on  Tue Dec 7 18:45:39 GMT 2010
Customization dir=/home/user/tmp/customization-scripts
Removing remastering root dir...
Removing ISO remastering dir...
Mounting ISO image...
Unpacking ISO image...
Unmounting ISO image...
Mounting SquashFS image...
Unpacking SquashFS image...
Unmounting SquashFS image...
Mounting /proc
Mounting /sys
Mounting /dev/pts
Mounting /var/run
Mounting /tmp
Mounting /home/user/tmp/remaster-root-home
Mounting /home/user/tmp/remaster-apt-cache
Mounting /home/user/tmp/customization-scripts
Copying resolv.conf...
Creating DBUS uuid...
Get:1 http://security.ubuntu.com maverick-security Release.gpg [198B]
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en
Get:2 http://archive.ubuntu.com maverick Release.gpg [198B]
Ign http://archive.ubuntu.com/ubuntu/ maverick/main Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en
Get:3 http://security.ubuntu.com maverick-security Release [27.2kB]
Get:4 http://archive.ubuntu.com maverick-updates Release.gpg [198B]
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en
Get:5 http://archive.ubuntu.com maverick Release [39.8kB]
Get:6 http://archive.ubuntu.com maverick-updates Release [31.4kB]
Get:7 http://security.ubuntu.com maverick-security/main Sources [15.5kB]
Get:8 http://archive.ubuntu.com maverick/main Sources [829kB]
Get:9 http://security.ubuntu.com maverick-security/restricted Sources [14B]
Get:10 http://security.ubuntu.com maverick-security/main i386 Packages [48.0kB]
Get:11 http://security.ubuntu.com maverick-security/restricted i386 Packages [14B]
Get:12 http://archive.ubuntu.com maverick/restricted Sources [4370B]
Get:13 http://archive.ubuntu.com maverick/main i386 Packages [1492kB]
Get:14 http://archive.ubuntu.com maverick/restricted i386 Packages [5992B]
Get:15 http://archive.ubuntu.com maverick-updates/main Sources [47.6kB]
Get:16 http://archive.ubuntu.com maverick-updates/restricted Sources [14B]
Get:17 http://archive.ubuntu.com maverick-updates/main i386 Packages [125kB]
Get:18 http://archive.ubuntu.com maverick-updates/restricted i386 Packages [14B]
Fetched 2667kB in 3s (714kB/s)
Reading package lists...
Installing language packs (en)...
Reading package lists...
Building dependency tree...
Reading state information...
language-pack-en is already the newest version.
language-pack-en-base is already the newest version.
language-pack-gnome-en is already the newest version.
language-pack-gnome-en-base is already the newest version.
language-support-en is already the newest version.
language-support-writing-en is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 186 not upgraded.
Removing unnecessary language packages...
Reading package lists...
Building dependency tree...
Reading state information...
The following packages will be REMOVED:
  language-pack-bn* language-pack-bn-base* language-pack-de*
  language-pack-de-base* language-pack-es* language-pack-es-base*
  language-pack-gnome-bn* language-pack-gnome-bn-base* language-pack-gnome-de*
  language-pack-gnome-de-base* language-pack-gnome-es*
  language-pack-gnome-es-base* language-pack-gnome-pt*
  language-pack-gnome-pt-base* language-pack-gnome-xh*
  language-pack-gnome-xh-base* language-pack-gnome-zh-hans*
  language-pack-gnome-zh-hans-base* language-pack-pt* language-pack-pt-base*
  language-pack-xh* language-pack-xh-base* language-pack-zh-hans*
  language-pack-zh-hans-base*
0 upgraded, 0 newly installed, 24 to remove and 186 not upgraded.
After this operation, 138MB disk space will be freed.
(Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 124413 files and directories currently installed.)
Removing language-pack-gnome-es-base ...
Purging configuration files for language-pack-gnome-es-base ...
Removing language-pack-gnome-es ...
Removing language-pack-es-base ...
Purging configuration files for language-pack-es-base ...
Removing language-pack-gnome-pt-base ...
Purging configuration files for language-pack-gnome-pt-base ...
Removing language-pack-gnome-xh-base ...
Purging configuration files for language-pack-gnome-xh-base ...
Removing language-pack-gnome-zh-hans-base ...
Purging configuration files for language-pack-gnome-zh-hans-base ...
Removing language-pack-gnome-bn-base ...
Purging configuration files for language-pack-gnome-bn-base ...
Removing language-pack-gnome-bn ...
Removing language-pack-bn-base ...
Purging configuration files for language-pack-bn-base ...
Removing language-pack-gnome-de-base ...
Purging configuration files for language-pack-gnome-de-base ...
Removing language-pack-gnome-de ...
Removing language-pack-de-base ...
Purging configuration files for language-pack-de-base ...
Removing language-pack-es ...
Removing language-pack-gnome-pt ...
Removing language-pack-gnome-xh ...
Removing language-pack-gnome-zh-hans ...
Removing language-pack-pt-base ...
Purging configuration files for language-pack-pt-base ...
Removing language-pack-xh-base ...
Purging configuration files for language-pack-xh-base ...
Removing language-pack-zh-hans-base ...
Purging configuration files for language-pack-zh-hans-base ...
Removing language-pack-bn ...
Removing language-pack-de ...
Removing language-pack-pt ...
Removing language-pack-xh ...
Removing language-pack-zh-hans ...
Processing triggers for software-center ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.C.cache...
Processing triggers for python-central ...
Processing triggers for python-support ...
CHOICE='Run console application'
Starting console application...
Running console application /usr/bin/gnome-terminal failed, trying the fallback xterm
CHOICE='Run package manager'
Starting package application...
WARNING: can not get name for '<gtk.TextBuffer object at 0xa54ec84 (GtkTextBuffer at 0xa21e948)>'
WARNING: can not get name for '<gtk.CellRendererText object at 0xa54ecac (GtkCellRendererText at 0xa221b10)>'
Exception in RPackageLister::xapianSearch():The revision being read has been discarded - you should call Xapian::Database::reopen() and retry the operation
Exception in RPackageLister::xapianSearch():The revision being read has been discarded - you should call Xapian::Database::reopen() and retry the operation
WARNING: can not get name for '<gtk.TextBuffer object at 0x907fd74 (GtkTextBuffer at 0x8d4e948)>'
WARNING: can not get name for '<gtk.CellRendererText object at 0x907fe64 (GtkCellRendererText at 0x8d51310)>'
WARNING: can not get name for '<gtk.CellRendererText object at 0x907f2ac (GtkCellRendererText at 0x9154270)>'
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv A4273F3D409BC60E6C51EF75A28BE6E4EF0A4C44
gpg: requesting key EF0A4C44 from hkp server keyserver.ubuntu.com
gpg: key EF0A4C44: public key "Launchpad CreBS stable" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
WARNING: can not get name for '<gtk.CellRendererText object at 0x907f284 (GtkCellRendererText at 0x9154308)>'
WARNING: can not get name for '<gtk.CellRendererText object at 0x909625c (GtkCellRendererText at 0x91543a0)>'
WARNING: can not get name for '<gtk.CellRendererText object at 0x9096a04 (GtkCellRendererText at 0x9154438)>'
WARNING: can not get name for '<gtk.CellRendererText object at 0x9096d4c (GtkCellRendererText at 0x91544d0)>'
WARNING: can not get name for '<gtk.CellRendererText object at 0x907f84c (GtkCellRendererText at 0x9154568)>'
WARNING: can not get name for '<gtk.CellRendererText object at 0x908461c (GtkCellRendererText at 0x9154600)>'
WARNING: can not get name for '<gtk.TextBuffer object at 0x9389f54 (GtkTextBuffer at 0x9056948)>'
WARNING: can not get name for '<gtk.CellRendererText object at 0x93892d4 (GtkCellRendererText at 0x9059310)>'
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv FBEF0D696DE1C72BA5A835FE5A9BF3BB4E5E17B5
gpg: requesting key 4E5E17B5 from hkp server keyserver.ubuntu.com
gpg: key 4E5E17B5: public key "Launchpad PPA for chromium-daily" imported
gpg: no ultimately trusted keys found
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv 7B2C3B0889BF5709A105D03AC2518248EEA14886
gpg: requesting key EEA14886 from hkp server keyserver.ubuntu.com
gpg: key EEA14886: public key "Launchpad VLC" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv 1640708104D2F866129B0E86A6804EA8EAE0D85C
gpg: requesting key EAE0D85C from hkp server keyserver.ubuntu.com
gpg: key EAE0D85C: public key "Launchpad PPA for Nate Muench" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
CHOICE='Continue building'
Done
Removing generated machine uuid...
Removing generated resolv.conf...
Unmounting /home/user/tmp/remaster-root/tmp/customization-scripts...
Unmounting /home/user/tmp/remaster-root/var/cache/apt...
Unmounting /home/user/tmp/remaster-root/root...
Unmounting /home/user/tmp/remaster-root/tmp...
Unmounting /home/user/tmp/remaster-root/var/run...
Unmounting /home/user/tmp/remaster-root/dev/pts...
Unmounting /home/user/tmp/remaster-root/sys...
Unmounting /home/user/tmp/remaster-root/proc...
Cleaning up temporary directories...
Running ISO customization script /home/user/tmp/customization-scripts/customize_iso...
--2010-12-07 19:44:38--  http://archive.ubuntu.com/ubuntu/pool/main/g/gfxboot-theme-ubuntu/gfxboot-theme-ubuntu_0.10.2.tar.gz
Resolving archive.ubuntu.com... 91.189.88.40, 91.189.88.45, 91.189.88.46, ...
Connecting to archive.ubuntu.com|91.189.88.40|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 199953 (195K) [application/x-gzip]
Saving to: `gfxboot-theme-ubuntu_0.10.2.tar.gz'

     0K .......... .......... .......... .......... .......... 25%  545K 0s
    50K .......... .......... .......... .......... .......... 51% 1.50M 0s
   100K .......... .......... .......... .......... .......... 76% 1.52M 0s
   150K .......... .......... .......... .......... .....     100% 1.52M=0.2s

2010-12-07 19:44:38 (1.03 MB/s) - `gfxboot-theme-ubuntu_0.10.2.tar.gz' saved [199953/199953]

make -C po
make[1]: Entering directory `/tmp/tmp.LAd2cPceJe/gfxboot-theme-ubuntu/po'
bin/po2txt bootloader.pot >en.tr
bin/po2txt am.po >am.tr
bin/po2txt ar.po >ar.tr
bin/po2txt ast.po >ast.tr
bin/po2txt be.po >be.tr
bin/po2txt bg.po >bg.tr
bin/po2txt bn.po >bn.tr
bin/po2txt bs.po >bs.tr
bin/po2txt ca.po >ca.tr
bin/po2txt cs.po >cs.tr
bin/po2txt da.po >da.tr
bin/po2txt de.po >de.tr
bin/po2txt el.po >el.tr
bin/po2txt eo.po >eo.tr
bin/po2txt es.po >es.tr
bin/po2txt et.po >et.tr
bin/po2txt eu.po >eu.tr
bin/po2txt fi.po >fi.tr
bin/po2txt fr.po >fr.tr
bin/po2txt ga.po >ga.tr
bin/po2txt gl.po >gl.tr
bin/po2txt gu.po >gu.tr
bin/po2txt he.po >he.tr
bin/po2txt hi.po >hi.tr
bin/po2txt hr.po >hr.tr
bin/po2txt hu.po >hu.tr
bin/po2txt id.po >id.tr
bin/po2txt it.po >it.tr
bin/po2txt ja.po >ja.tr
bin/po2txt ka.po >ka.tr
bin/po2txt kk.po >kk.tr
bin/po2txt km.po >km.tr
bin/po2txt ko.po >ko.tr
bin/po2txt ku.po >ku.tr
bin/po2txt lt.po >lt.tr
bin/po2txt lv.po >lv.tr
bin/po2txt mk.po >mk.tr
bin/po2txt ml.po >ml.tr
bin/po2txt nb.po >nb.tr
bin/po2txt ne.po >ne.tr
bin/po2txt nl.po >nl.tr
bin/po2txt nn.po >nn.tr
bin/po2txt pl.po >pl.tr
bin/po2txt pt_BR.po >pt_BR.tr
bin/po2txt pt.po >pt.tr
bin/po2txt pt_PT.po >pt_PT.tr
bin/po2txt ro.po >ro.tr
bin/po2txt ru.po >ru.tr
bin/po2txt sk.po >sk.tr
bin/po2txt sl.po >sl.tr
bin/po2txt sq.po >sq.tr
bin/po2txt sr.po >sr.tr
bin/po2txt sv.po >sv.tr
bin/po2txt ta.po >ta.tr
bin/po2txt th.po >th.tr
bin/po2txt tl.po >tl.tr
bin/po2txt tr.po >tr.tr
bin/po2txt uk.po >uk.tr
bin/po2txt vi.po >vi.tr
bin/po2txt zh_CN.po >zh_CN.tr
bin/po2txt zh_TW.po >zh_TW.tr
make[1]: Leaving directory `/tmp/tmp.LAd2cPceJe/gfxboot-theme-ubuntu/po'
mkdir -p boot
mkbootmsg -O -v -L ../.. -l boot/log -c boot.config boot/init
make: mkbootmsg: Command not found
make: *** [bootdir] Error 127
Failed to build gfxboot theme
```

Please tell me what I have done wrong. *This is the second log...the first time all I did was get UCK to delete some language packs and it also got a gfxboot theme error.*
...
Error solved: installed new UCK that was not available in Ubuntu.
For others with this problem the PPA is here: sudo add-apt-repository ppa:uck-team/uck-stable
Just check for updates in the update centre after typing that into terminal to get the newest UCK.

---

