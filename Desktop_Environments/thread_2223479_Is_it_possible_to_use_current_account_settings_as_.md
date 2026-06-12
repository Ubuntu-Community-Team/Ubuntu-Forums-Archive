---
title: "Is it possible to use current account settings as default for new users?"
date: 2014-05-11
forum: Desktop Environments
---

### Post by Juhele on 2014-05-11
hi,
I created a preconfigured account in Lubuntu 14.04 and would like to use all the changes as default for all new accounts - including cursor, theme, wallpaper and also configs for particular programs. Is it possible? I am doing this because many users request the same scheme but they are often just BFUs... :KS  The account I created does not contain any personal information and was created directly for the remaster so no problem there. Is there any way? 

thanks

PS: I found [this ]("http://askubuntu.com/questions/62927/how-do-i-set-the-default-icon-set-and-wallpaper-for-new-users")but the .gconf folder is empty in my case so it probably does not work for Lubuntu... :confused:

---

### Post by sudodus on 2014-05-11
Try putting what is stored in your home directory it into the directory **/etc/skel** (usually changes in the current hidden files there, as well as other hidden files).

```
ls -la /etc/skel
```

-o-

Are you talking about new users in the same computer or new computers?

---

### Post by Juhele on 2014-05-11
Hi,
thanks for reply. I currently have it installed on Vbox and need to change this for new users using my remastered Lubuntu. so, for new computers. :-)

---

### Post by sudodus on 2014-05-11
The tip in #2 might be enough for new users in the same computer. But you mentioned the word 'remastered', and you need something like that for new computers.

If you plan to deliver many almost identical computers, you can make an [OEM installation]("https://help.ubuntu.com/community/Ubuntu_OEM_Installer_Overview") and clone it, for example with [Clonezilla]("http://clonezilla.org/").

To install into different sized drives, you need something else, for example the [One Button Installer]("https://help.ubuntu.com/community/OBI"), and make your own tarball. As long as you do not install any proprietary drivers, you can install working systems from that tarball. This is due to the portability of Ubuntu and Ubuntu flavours and re-spins. An alternative is [fsarchiver]("http://www.fsarchiver.org/Main_Page").

The most advanced method is to make a re-spin alias remaster the code and make an own iso file. Then you have 'your own' linux re-spin or distro.

---

### Post by Juhele on 2014-05-11
I successfully used Remastersys to create both my personal backups and also those "remastered" versions - my own generated ISO files which worked both as Live DVD (or live usb when used Unetbootin) and also as installation media. I created such ISO some time ago for one of my relatives and made it available to download some time later. As it was preconfigured and looked similarly to Win XP, people started to ask new version after 14.04 was out. So I am working on it now.

I do not think cloning would be good solution for this case. And targed computers are not much similar - I started with testing on old Eee 901 netbook and also installed on few Pentium 4 desktops, but some users install it even on relatively new laptops. I do not have experience with solutions you mentioned but as I know the remastered ISO installs my preconfigured account in the same way as I have it on my testing machine. So maybe I am wrong and your solution for the same computer would be enough. So I will look on your solution with etc/skel :-)

---

### Post by sudodus on 2014-05-11
You master Remastersys :KS

Then just go ahead and use it! It will give you the highest degree of freedom to do what you want.

By the way, did you use Remastersys for 12.04 LTS based systems or also for 14.04 LTS? Please share your results :-)

---

### Post by Juhele on 2014-07-14
Hi,
although my reply is a little bit delayed I think it can be also useful for others. First, I must say that even in Lubuntu and Kubuntu 14.04. Trusty Tahr I still use Remastersys from
```
http://www.remastersys.com/ubuntu quantal main
```

I faced one minor issue when one of my remasters was missing the installer so I had to manually add Ubiquity via Synaptic and next remaster was OK. I am often using Remaster to produce my remaster called [Lubuntu W7 Professional]("http://juhele.blogspot.cz/2014/05/lubuntu-w7-1404-professional-vydano.html?view=classic") aimed on ex-XP beginner users with old machines (the first one was only made for one of my relatives for his old PC but after sharing the ISO went popular and I was asked to create updated version :p ).

I am also posting here a complete Remastersys log for my last remaster:

```
System Backup Mode Selected
Enabling remastersys-firstboot
Checking filesystem type of the Working Folder
/home/remastersys/remastersys is on a ext4 filesystem
Making sure popularity contest is not installed
Installing the Ubiquity GTK frontend
Checking if the /home/remastersys/remastersys folder has been created
Creating /home/remastersys/remastersys folder tree
Creating /home/remastersys/remastersys/ISOTMP folder tree
Copying /var and /etc to temp area and excluding extra files  ... this will take a while so be patient
Cleaning up files not needed for the live in /home/remastersys/remastersys/dummysys
Making sure adduser and autologin functions of casper are set properly
Copying memtest86+ for the live system
Creating isolinux setup for the live system
Checking the ARCH of the system and setting the README.diskdefines file
Creating filesystem.manifest and filesystem.manifest-desktop
Excluding folder from the backup that will cause issues
Copying the install icon to the desktop of flynn
Creating the casper.conf file.
Checking and setting user-setup-apply for the live system
Setting up casper and ubiquity options for backup mode
Creating a new initial ramdisk for the live system
Copying your kernel and initrd for the livecd
Creating filesystem.squashfs   ... this will take a while so be patient
------------------------------------------------------
Mount information
/dev/sda1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
none on /sys/fs/pstore type pstore (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=flynn)
XX_Lubuntu_W7_share on /media/sf_XX_Lubuntu_W7_share type vboxsf (gid=999,rw)
/dev/sr0 on /media/flynn/VBOXADDITIONS_4.3.12_93733 type iso9660 (ro,nosuid,nodev,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500,uhelper=udisks2)
------------------------------------------------------
Disk size information
Souborový systém    Velikost Užito Volno Uži% P&#345;ipojeno do
/dev/sda1                15G  6,2G  7,2G  46% /
none                    4,0K     0  4,0K   0% /sys/fs/cgroup
udev                    488M   12K  488M   1% /dev
tmpfs                   101M  1,1M  100M   2% /run
none                    5,0M     0  5,0M   0% /run/lock
none                    501M     0  501M   0% /run/shm
none                    100M   16K  100M   1% /run/user
XX_Lubuntu_W7_share      94G   90G  4,0G  96% /media/sf_XX_Lubuntu_W7_share
/dev/sr0                 62M   62M     0 100% /media/flynn/VBOXADDITIONS_4.3.12_93733
------------------------------------------------------
Casper Script info
celkem 144
-rwxr-xr-x 1 root root  297 dub  9 20:33 01integrity_check
-rwxr-xr-x 1 root root  467 dub  9 20:33 05mountpoints
-rwxr-xr-x 1 root root  680 dub  9 20:33 07remove_oem_config
-rwxr-xr-x 1 root root  400 dub  9 20:33 12fstab
-rwxr-xr-x 1 root root  831 dub  9 20:33 13swap
-rwxr-xr-x 1 root root 1221 dub  9 20:33 14locales
-rw-r--r-- 1 root root 2454 dub  9 20:33 15autologin
-rwxr-xr-x 1 root root 1169 dub  9 20:33 16gdmnopasswd
-rwxr-xr-x 1 root root  577 dub  9 20:33 18hostname
-rwxr-xr-x 1 root root 9106 dub  9 20:33 19keyboard
-rwxr-xr-x 1 root root  546 dub  9 20:33 20xconfig
-rwxr-xr-x 1 root root 1775 dub  9 20:33 22desktop_settings
-rwxr-xr-x 1 root root  410 dub  9 20:33 22sslcert
-rwxr-xr-x 1 root root 3814 dub  9 20:33 23networking
-rwxr-xr-x 1 root root 2280 dub  9 20:33 24preseed
-rw-r--r-- 1 root root 4329 dub  9 20:33 25adduser
-rwxr-xr-x 1 root root 1996 dub  9 20:33 25configure_init
-rwxr-xr-x 1 root root  577 dub  9 20:33 26serialtty
-rwxr-xr-x 1 root root 2250 dub  9 20:33 30accessibility
-rwxr-xr-x 1 root root 1188 dub  9 20:33 31disable_update_notifier
-rwxr-xr-x 1 root root  463 dub  9 20:33 32disable_hibernation
-rwxr-xr-x 1 root root  650 dub  9 20:33 33enable_apport_crashes
-rwxr-xr-x 1 root root  928 dub  9 20:33 34disable_kde_services
-rwxr-xr-x 1 root root  636 dub  9 20:33 35fix_language_selector
-rwxr-xr-x 1 root root  407 dub  9 20:33 36disable_trackerd
-rwxr-xr-x 1 root root  908 dub  9 20:33 40install_driver_updates
-rwxr-xr-x 1 root root  650 dub  9 20:33 41apt_cdrom
-rwxr-xr-x 1 root root  997 dub  9 20:33 43disable_updateinitramfs
-rwxr-xr-x 1 root root  658 dub  9 20:33 44pk_allow_ubuntu
-rwxr-xr-x 1 root root  594 dub  9 20:33 45jackd2
-rwxr-xr-x 1 root root  215 dub  9 20:33 48kubuntu_disable_restart_notifications
-rwxr-xr-x 1 root root  169 dub  9 20:33 49kubuntu_mobile_session
-rwxr-xr-x 1 root root  346 dub  9 20:33 50ubiquity-bluetooth-agent
------------------------------------------------------
/etc/remastersys.conf info
#Remastersys Global Configuration File


# This is the temporary working directory and won't be included on the cd/dvd
WORKDIR="/home/remastersys"


# Here you can add any other files or directories to be excluded from the live filesystem
# Separate each entry with a space
EXCLUDES="/media/sf_XX_Lubuntu_W7_share"


# Here you can change the livecd/dvd username
LIVEUSER="custom"


# Here you can change the name of the livecd/dvd label
LIVECDLABEL="Lubuntu W7 14.04 Professional r4"


# Here you can change the name of the ISO file that is created
CUSTOMISO="Lubuntu_W7_14.04_Pro_r4.iso"


# Here you can change the mksquashfs options
SQUASHFSOPTS="-no-recovery -always-use-fragments -b 1M -no-duplicates"


# Here you can prevent the Install icon from showing up on the desktop in backup mode. 0 - to not show 1 - to show
BACKUPSHOWINSTALL="1"


# Here you can change the url for the usb-creator info
LIVECDURL="http://www.remastersys.com"

------------------------------------------------------
/etc/casper.conf info
# This file should go in /etc/casper.conf
# Supported variables are:
# USERNAME, USERFULLNAME, HOST, BUILD_SYSTEM

export USERNAME="flynn"
export USERFULLNAME="Live session user"
export HOST="flynn"
export BUILD_SYSTEM="Ubuntu"
export FLAVOUR="flynn"
------------------------------------------------------
/etc/passwd info
root:x:0:0:root:/root:/bin/bash
daemon:x:1:1:daemon:/usr/sbin:/usr/sbin/nologin
bin:x:2:2:bin:/bin:/usr/sbin/nologin
sys:x:3:3:sys:/dev:/usr/sbin/nologin
sync:x:4:65534:sync:/bin:/bin/sync
games:x:5:60:games:/usr/games:/usr/sbin/nologin
man:x:6:12:man:/var/cache/man:/usr/sbin/nologin
lp:x:7:7:lp:/var/spool/lpd:/usr/sbin/nologin
mail:x:8:8:mail:/var/mail:/usr/sbin/nologin
news:x:9:9:news:/var/spool/news:/usr/sbin/nologin
uucp:x:10:10:uucp:/var/spool/uucp:/usr/sbin/nologin
proxy:x:13:13:proxy:/bin:/usr/sbin/nologin
www-data:x:33:33:www-data:/var/www:/usr/sbin/nologin
backup:x:34:34:backup:/var/backups:/usr/sbin/nologin
list:x:38:38:Mailing List Manager:/var/list:/usr/sbin/nologin
irc:x:39:39:ircd:/var/run/ircd:/usr/sbin/nologin
gnats:x:41:41:Gnats Bug-Reporting System (admin):/var/lib/gnats:/usr/sbin/nologin
nobody:x:65534:65534:nobody:/nonexistent:/usr/sbin/nologin
libuuid:x:100:101::/var/lib/libuuid:
syslog:x:101:104::/home/syslog:/bin/false
messagebus:x:102:106::/var/run/dbus:/bin/false
usbmux:x:103:46:usbmux daemon,,,:/home/usbmux:/bin/false
dnsmasq:x:104:65534:dnsmasq,,,:/var/lib/misc:/bin/false
ntp:x:105:110::/home/ntp:/bin/false
whoopsie:x:106:114::/nonexistent:/bin/false
lightdm:x:107:115:Light Display Manager:/var/lib/lightdm:/bin/false
flynn:x:1000:1000:Kevin Flynn,,,:/home/flynn:/bin/bash
vboxadd:x:999:1::/var/run/vboxadd:/bin/false
------------------------------------------------------
/etc/group info
root:x:0:
daemon:x:1:
bin:x:2:
sys:x:3:
adm:x:4:syslog,flynn
tty:x:5:
disk:x:6:
lp:x:7:
mail:x:8:
news:x:9:
uucp:x:10:
man:x:12:
proxy:x:13:
kmem:x:15:
dialout:x:20:
fax:x:21:
voice:x:22:
cdrom:x:24:flynn
floppy:x:25:
tape:x:26:
sudo:x:27:flynn
audio:x:29:
dip:x:30:flynn
www-data:x:33:
backup:x:34:
operator:x:37:
list:x:38:
irc:x:39:
src:x:40:
gnats:x:41:
shadow:x:42:
utmp:x:43:
video:x:44:
sasl:x:45:
plugdev:x:46:flynn
staff:x:50:
games:x:60:
users:x:100:
nogroup:x:65534:
libuuid:x:101:
netdev:x:102:
crontab:x:103:
syslog:x:104:
fuse:x:105:
messagebus:x:106:
ssl-cert:x:107:
lpadmin:x:108:flynn
scanner:x:109:
ntp:x:110:
mlocate:x:111:
ssh:x:112:
utempter:x:113:
whoopsie:x:114:
lightdm:x:115:
nopasswdlogin:x:116:
bluetooth:x:117:
flynn:x:1000:
sambashare:x:118:flynn
vboxsf:x:999:
winbindd_priv:x:119:
------------------------------------------------------
/etc/X11/default-display-manager info
/usr/sbin/lightdm
------------------------------------------------------
/etc/skel info
/etc/skel
/etc/skel/.local
/etc/skel/.local/share
/etc/skel/.local/share/recently-used.xbel
/etc/skel/.gconf
/etc/skel/.config
/etc/skel/.config/pcmanfm
/etc/skel/.config/pcmanfm/lubuntu
/etc/skel/.config/pcmanfm/lubuntu/pcmanfm.conf
/etc/skel/.config/pcmanfm/lubuntu/desktop-items-0.conf
/etc/skel/.config/compiz-1
/etc/skel/.config/compiz-1/compizconfig
/etc/skel/.config/compiz-1/compizconfig/Default.ini
/etc/skel/.config/compiz-1/compizconfig/config
/etc/skel/.config/compiz-1/compizconfig/done_upgrades
/etc/skel/.config/upstart
/etc/skel/.config/gweled.conf
/etc/skel/.config/openbox
/etc/skel/.config/openbox/lubuntu-rc.xml
/etc/skel/.config/dconf
/etc/skel/.config/dconf/user
/etc/skel/.config/xfce4
/etc/skel/.config/xfce4/xfconf
/etc/skel/.config/xfce4/xfconf/xfce-perchannel-xml
/etc/skel/.config/pulse
/etc/skel/.config/pulse/cookie
/etc/skel/.config/teamviewer9
/etc/skel/.config/teamviewer9/drive_c
/etc/skel/.config/teamviewer9/drive_c/users
/etc/skel/.config/teamviewer9/drive_c/users/Public
/etc/skel/.config/teamviewer9/drive_c/users/Public/Favorites
/etc/skel/.config/teamviewer9/drive_c/users/Public/Templates
/etc/skel/.config/teamviewer9/drive_c/users/Public/Pictures
/etc/skel/.config/teamviewer9/drive_c/users/Public/Videos
/etc/skel/.config/teamviewer9/drive_c/users/Public/Music
/etc/skel/.config/teamviewer9/drive_c/users/Public/Start Menu
/etc/skel/.config/teamviewer9/drive_c/users/Public/Start Menu/Programs
/etc/skel/.config/teamviewer9/drive_c/users/Public/Start Menu/Programs/StartUp
/etc/skel/.config/teamviewer9/drive_c/users/Public/Start Menu/Programs/Administrative Tools
/etc/skel/.config/teamviewer9/drive_c/users/Public/Desktop
/etc/skel/.config/teamviewer9/drive_c/users/Public/Documents
/etc/skel/.config/teamviewer9/drive_c/users/Public/Application Data
/etc/skel/.config/teamviewer9/drive_c/users/Public/Application Data/Microsoft
/etc/skel/.config/teamviewer9/drive_c/windows
/etc/skel/.config/teamviewer9/drive_c/windows/temp
/etc/skel/.config/teamviewer9/drive_c/windows/notepad.exe
/etc/skel/.config/teamviewer9/drive_c/windows/logs
/etc/skel/.config/teamviewer9/drive_c/windows/regedit.exe
/etc/skel/.config/teamviewer9/drive_c/windows/hh.exe
/etc/skel/.config/teamviewer9/drive_c/windows/command
/etc/skel/.config/teamviewer9/drive_c/windows/command/start.exe
/etc/skel/.config/teamviewer9/drive_c/windows/rundll.exe
/etc/skel/.config/teamviewer9/drive_c/windows/twain.dll
/etc/skel/.config/teamviewer9/drive_c/windows/system32
/etc/skel/.config/teamviewer9/drive_c/windows/system32/dosx.exe
/etc/skel/.config/teamviewer9/drive_c/windows/system32/msxml.dll
/etc/skel/.config/teamviewer9/drive_c/windows/system32/msxml3.dll
/etc/skel/.config/teamviewer9/drive_c/windows/system32/drivers
/etc/skel/.config/teamviewer9/drive_c/windows/system32/drivers/mountmgr.sys
/etc/skel/.config/teamviewer9/drive_c/windows/system32/winemenubuilder.exe
/etc/skel/.config/teamviewer9/drive_c/windows/system32/notepad.exe
/etc/skel/.config/teamviewer9/drive_c/windows/system32/wbem
/etc/skel/.config/teamviewer9/drive_c/windows/system32/wbem/mofcomp.exe
/etc/skel/.config/teamviewer9/drive_c/windows/system32/wbem/wbemprox.dll
/etc/skel/.config/teamviewer9/drive_c/windows/system32/wbem/wmic.exe
/etc/skel/.config/teamviewer9/drive_c/windows/system32/wbem/wmiutils.dll
/etc/skel/.config/teamviewer9/drive_c/windows/system32/msxml2.dll
/etc/skel/.config/teamviewer9/drive_c/windows/system32/ddhelp.exe
/etc/skel/.config/teamviewer9/drive_c/windows/system32/dsound.vxd
/etc/skel/.config/teamviewer9/drive_c/windows/system32/msxml6.dll
/etc/skel/.config/teamviewer9/drive_c/windows/system32/msxml4.dll
/etc/skel/.config/teamviewer9/drive_c/windows/system32/gecko
/etc/skel/.config/teamviewer9/drive_c/windows/system32/gecko/plugin
/etc/skel/.config/teamviewer9/drive_c/windows/system32/gecko/plugin/npmshtml.dll
/etc/skel/.config/teamviewer9/drive_c/windows/system32/mui
/etc/skel/.config/teamviewer9/drive_c/windows/system32/spool
/etc/skel/.config/teamviewer9/drive_c/windows/system32/spool/drivers
/etc/skel/.config/teamviewer9/drive_c/windows/system32/spool/drivers/color
/etc/skel/.config/teamviewer9/drive_c/windows/system32/spool/printers
/etc/skel/.config/teamviewer9/drive_c/windows/system32/l_intl.nls
/etc/skel/.config/teamviewer9/drive_c/windows/system32/shdocvw.dll
/etc/skel/.config/teamviewer9/drive_c/windows/system32/iexplore.exe
/etc/skel/.config/teamviewer9/drive_c/windows/system32/rsabase.dll
/etc/skel/.config/teamviewer9/drive_c/windows/system32/rsaenh.dll
/etc/skel/.config/teamviewer9/drive_c/windows/system32/winhlp32.exe
/etc/skel/.config/teamviewer9/drive_c/windows/system32/explorer.exe
/etc/skel/.config/teamviewer9/drive_c/windows/help
/etc/skel/.config/teamviewer9/drive_c/windows/system
/etc/skel/.config/teamviewer9/drive_c/windows/system/ddeml.dll
/etc/skel/.config/teamviewer9/drive_c/windows/system/mmsystem.dll
/etc/skel/.config/teamviewer9/drive_c/windows/system.ini
/etc/skel/.config/teamviewer9/drive_c/windows/Fonts
/etc/skel/.config/teamviewer9/drive_c/windows/inf
/etc/skel/.config/teamviewer9/drive_c/windows/winhelp.exe
/etc/skel/.config/teamviewer9/drive_c/windows/win.ini
/etc/skel/.config/teamviewer9/drive_c/windows/twain_32.dll
/etc/skel/.config/teamviewer9/drive_c/windows/winhlp32.exe
/etc/skel/.config/teamviewer9/drive_c/windows/explorer.exe
/etc/skel/.config/teamviewer9/drive_c/Program Files
/etc/skel/.config/teamviewer9/drive_c/Program Files/Internet Explorer
/etc/skel/.config/teamviewer9/drive_c/Program Files/Internet Explorer/iexplore.exe
/etc/skel/.config/teamviewer9/drive_c/Program Files/Common Files
/etc/skel/.config/teamviewer9/drive_c/Program Files/Common Files/System
/etc/skel/.config/teamviewer9/drive_c/Program Files/Common Files/System/OLE DB
/etc/skel/.config/teamviewer9/drive_c/Program Files/Common Files/System/OLE DB/oledb32.dll
/etc/skel/.config/teamviewer9/drive_c/Program Files/Common Files/System/OLE DB/msdaps.dll
/etc/skel/.config/teamviewer9/drive_c/TeamViewer
/etc/skel/.config/teamviewer9/drive_c/TeamViewer/TeamViewer_Resource_es.dll
/etc/skel/.config/teamviewer9/drive_c/TeamViewer/TeamViewer_Resource_uk.dll
/etc/skel/.config/teamviewer9/drive_c/TeamViewer/TeamViewer_Resource_ru.dll
/etc/skel/.config/teamviewer9/drive_c/TeamViewer/TeamViewer_Resource_da.dll
/etc/skel/.config/teamviewer9/drive_c/TeamViewer/TeamViewer_Resource_no.dll
/etc/skel/.config/teamviewer9/drive_c/TeamViewer/TeamViewer_Resource_fr.dll
/etc/skel/.config/teamviewer9/drive_c/TeamViewer/TeamViewer_Resource_nl.dll
/etc/skel/.config/teamviewer9/drive_c/TeamViewer/Lizenz.txt
/etc/skel/.config/teamviewer9/drive_c/TeamViewer/TeamViewer_Resource_pt.dll
/etc/skel/.config/teamviewer9/drive_c/TeamViewer/License.txt
/etc/skel/.config/teamviewer9/drive_c/TeamViewer/TeamViewer_Resource_fi.dll
/etc/skel/.config/teamviewer9/drive_c/TeamViewer/TeamViewer_Resource_lt.dll
/etc/skel/.config/teamviewer9/drive_c/TeamViewer/TeamViewer_Resource_ro.dll
/etc/skel/.config/teamviewer9/drive_c/TeamViewer/TeamViewer_Resource_en.dll
/etc/skel/.config/teamviewer9/drive_c/TeamViewer/TeamViewer_Resource_cs.dll
/etc/skel/.config/teamviewer9/drive_c/TeamViewer/TeamViewer.exe
/etc/skel/.config/teamviewer9/drive_c/TeamViewer/libtvextension.so
/etc/skel/.config/teamviewer9/drive_c/TeamViewer/TeamViewer_Resource_id.dll
/etc/skel/.config/teamviewer9/drive_c/TeamViewer/TeamViewer_Resource_hr.dll
/etc/skel/.config/teamviewer9/drive_c/TeamViewer/TeamViewer_Resource_sr.dll
/etc/skel/.config/teamviewer9/drive_c/TeamViewer/TeamViewer_Resource_sk.dll
/etc/skel/.config/teamviewer9/drive_c/TeamViewer/TeamViewer_Resource_it.dll
/etc/skel/.config/teamviewer9/drive_c/TeamViewer/TeamViewer_Resource_pl.dll
/etc/skel/.config/teamviewer9/drive_c/TeamViewer/TeamViewer_Resource_bg.dll
/etc/skel/.config/teamviewer9/drive_c/TeamViewer/TeamViewer_Resource_de.dll
/etc/skel/.config/teamviewer9/drive_c/TeamViewer/TeamViewer_Resource_hu.dll
/etc/skel/.config/teamviewer9/drive_c/TeamViewer/TeamViewer_Resource_tr.dll
/etc/skel/.config/teamviewer9/drive_c/TeamViewer/TeamViewer_Resource_sv.dll
/etc/skel/.config/teamviewer9/drive_c/TeamViewer/TeamViewer_StaticRes.dll
/etc/skel/.config/teamviewer9/drive_c/TeamViewer/tvwine.dll.so
/etc/skel/.config/teamviewer9/logfiles
/etc/skel/.config/teamviewer9/logfiles/TeamViewer9_Logfile.log
/etc/skel/.config/teamviewer9/logfiles/startup.log
/etc/skel/.config/teamviewer9/logfiles/winelog
/etc/skel/.config/teamviewer9/config
/etc/skel/.config/teamviewer9/config/client.conf
/etc/skel/.config/teamviewer9/.tweak
/etc/skel/.config/teamviewer9/.tweak/no_xrandr
/etc/skel/.config/teamviewer9/.tweak/no_fileassocs
/etc/skel/.config/teamviewer9/.tweak/fontsmooth_rgb
/etc/skel/.config/teamviewer9/.tweak/no_xvidmodeext
/etc/skel/.config/teamviewer9/user.reg
/etc/skel/.config/teamviewer9/dosdevices
/etc/skel/.config/teamviewer9/dosdevices/c:
/etc/skel/.config/teamviewer9/dosdevices/z:
/etc/skel/.config/teamviewer9/.update-timestamp
/etc/skel/.config/teamviewer9/userdef.reg
/etc/skel/.config/teamviewer9/system.reg
/etc/skel/.config/enchant
/etc/skel/.config/enchant/cs_CZ.exc
/etc/skel/.config/enchant/cs_CZ.dic
/etc/skel/.config/ubuntu-tweak
/etc/skel/.config/ubuntu-tweak/temp
/etc/skel/.config/ubuntu-tweak/ubuntu-tweak.log
/etc/skel/.config/ubuntu-tweak/tweaks
/etc/skel/.config/ubuntu-tweak/tweaks/__init__.py
/etc/skel/.config/ubuntu-tweak/admins
/etc/skel/.config/ubuntu-tweak/admins/__init__.py
/etc/skel/.config/ubuntu-tweak/clips
/etc/skel/.config/ubuntu-tweak/clips/__init__.py
/etc/skel/.config/ubuntu-tweak/janitor
/etc/skel/.config/ubuntu-tweak/janitor/__init__.py
/etc/skel/.config/ubuntu-tweak/appcenter
/etc/skel/.config/gtk-2.0
/etc/skel/.config/gtk-2.0/gtkfilechooser.ini
/etc/skel/.config/lxterminal
/etc/skel/.config/lxterminal/lxterminal.conf
/etc/skel/.config/Trolltech.conf
/etc/skel/.config/libreoffice
/etc/skel/.config/libreoffice/4
/etc/skel/.config/libreoffice/4/user
/etc/skel/.config/libreoffice/4/user/database
/etc/skel/.config/libreoffice/4/user/database/biblio.odb
/etc/skel/.config/libreoffice/4/user/database/evolocal.odb
/etc/skel/.config/libreoffice/4/user/database/biblio
/etc/skel/.config/libreoffice/4/user/database/biblio/biblio.dbf
/etc/skel/.config/libreoffice/4/user/database/biblio/biblio.dbt
/etc/skel/.config/libreoffice/4/user/gallery
/etc/skel/.config/libreoffice/4/user/gallery/sg30.sdv
/etc/skel/.config/libreoffice/4/user/gallery/sg30.thm
/etc/skel/.config/libreoffice/4/user/psprint
/etc/skel/.config/libreoffice/4/user/config
/etc/skel/.config/libreoffice/4/user/config/classic.sog
/etc/skel/.config/libreoffice/4/user/config/standard.sob
/etc/skel/.config/libreoffice/4/user/config/tango.soc
/etc/skel/.config/libreoffice/4/user/config/standard.soh
/etc/skel/.config/libreoffice/4/user/config/gallery.soc
/etc/skel/.config/libreoffice/4/user/config/libreoffice.soc
/etc/skel/.config/libreoffice/4/user/config/cmyk.soc
/etc/skel/.config/libreoffice/4/user/config/html.soc
/etc/skel/.config/libreoffice/4/user/config/standard.soc
/etc/skel/.config/libreoffice/4/user/config/standard.sod
/etc/skel/.config/libreoffice/4/user/config/standard.soe
/etc/skel/.config/libreoffice/4/user/config/styles.sod
/etc/skel/.config/libreoffice/4/user/config/scribus.soc
/etc/skel/.config/libreoffice/4/user/config/web.soc
/etc/skel/.config/libreoffice/4/user/config/arrowhd.soe
/etc/skel/.config/libreoffice/4/user/config/autotbl.fmt
/etc/skel/.config/libreoffice/4/user/config/javasettings_Linux_x86.xml
/etc/skel/.config/libreoffice/4/user/config/soffice.cfg
/etc/skel/.config/libreoffice/4/user/config/soffice.cfg/modules
/etc/skel/.config/libreoffice/4/user/config/soffice.cfg/modules/swriter
/etc/skel/.config/libreoffice/4/user/config/soffice.cfg/modules/swriter/statusbar
/etc/skel/.config/libreoffice/4/user/config/soffice.cfg/modules/swriter/toolbar
/etc/skel/.config/libreoffice/4/user/config/soffice.cfg/modules/swriter/menubar
/etc/skel/.config/libreoffice/4/user/config/soffice.cfg/modules/swriter/images
/etc/skel/.config/libreoffice/4/user/config/soffice.cfg/modules/swriter/images/Bitmaps
/etc/skel/.config/libreoffice/4/user/config/standard.sog
/etc/skel/.config/libreoffice/4/user/config/hatching.soh
/etc/skel/.config/libreoffice/4/user/config/palette.soc
/etc/skel/.config/libreoffice/4/user/config/modern.sog
/etc/skel/.config/libreoffice/4/user/registrymodifications.xcu
/etc/skel/.config/libreoffice/4/user/extensions
/etc/skel/.config/libreoffice/4/user/extensions/tmp
/etc/skel/.config/libreoffice/4/user/extensions/tmp/registry
/etc/skel/.config/libreoffice/4/user/extensions/tmp/registry/com.sun.star.comp.deployment.help.PackageRegistryBackend
/etc/skel/.config/libreoffice/4/user/extensions/tmp/registry/com.sun.star.comp.deployment.help.PackageRegistryBackend/backenddb.xml
/etc/skel/.config/libreoffice/4/user/extensions/tmp/registry/com.sun.star.comp.deployment.script.PackageRegistryBackend
/etc/skel/.config/libreoffice/4/user/extensions/tmp/registry/com.sun.star.comp.deployment.executable.PackageRegistryBackend
/etc/skel/.config/libreoffice/4/user/extensions/tmp/registry/com.sun.star.comp.deployment.sfwk.PackageRegistryBackend
/etc/skel/.config/libreoffice/4/user/extensions/tmp/registry/com.sun.star.comp.deployment.component.PackageRegistryBackend
/etc/skel/.config/libreoffice/4/user/extensions/tmp/registry/com.sun.star.comp.deployment.configuration.PackageRegistryBackend
/etc/skel/.config/libreoffice/4/user/extensions/tmp/registry/com.sun.star.comp.deployment.configuration.PackageRegistryBackend/backenddb.xml
/etc/skel/.config/libreoffice/4/user/extensions/tmp/registry/com.sun.star.comp.deployment.bundle.PackageRegistryBackend
/etc/skel/.config/libreoffice/4/user/extensions/tmp/extensions
/etc/skel/.config/libreoffice/4/user/extensions/bundled
/etc/skel/.config/libreoffice/4/user/extensions/bundled/registry
/etc/skel/.config/libreoffice/4/user/extensions/bundled/registry/com.sun.star.comp.deployment.help.PackageRegistryBackend
/etc/skel/.config/libreoffice/4/user/extensions/bundled/registry/com.sun.star.comp.deployment.help.PackageRegistryBackend/backenddb.xml
/etc/skel/.config/libreoffice/4/user/extensions/bundled/registry/com.sun.star.comp.deployment.script.PackageRegistryBackend
/etc/skel/.config/libreoffice/4/user/extensions/bundled/registry/com.sun.star.comp.deployment.executable.PackageRegistryBackend
/etc/skel/.config/libreoffice/4/user/extensions/bundled/registry/com.sun.star.comp.deployment.sfwk.PackageRegistryBackend
/etc/skel/.config/libreoffice/4/user/extensions/bundled/registry/com.sun.star.comp.deployment.component.PackageRegistryBackend
/etc/skel/.config/libreoffice/4/user/extensions/bundled/registry/com.sun.star.comp.deployment.configuration.PackageRegistryBackend
/etc/skel/.config/libreoffice/4/user/extensions/bundled/registry/com.sun.star.comp.deployment.configuration.PackageRegistryBackend/backenddb.xml
/etc/skel/.config/libreoffice/4/user/extensions/bundled/registry/com.sun.star.comp.deployment.bundle.PackageRegistryBackend
/etc/skel/.config/libreoffice/4/user/extensions/bundled/lastsynchronized
/etc/skel/.config/libreoffice/4/user/extensions/shared
/etc/skel/.config/libreoffice/4/user/extensions/shared/registry
/etc/skel/.config/libreoffice/4/user/extensions/shared/registry/com.sun.star.comp.deployment.help.PackageRegistryBackend
/etc/skel/.config/libreoffice/4/user/extensions/shared/registry/com.sun.star.comp.deployment.help.PackageRegistryBackend/backenddb.xml
/etc/skel/.config/libreoffice/4/user/extensions/shared/registry/com.sun.star.comp.deployment.script.PackageRegistryBackend
/etc/skel/.config/libreoffice/4/user/extensions/shared/registry/com.sun.star.comp.deployment.executable.PackageRegistryBackend
/etc/skel/.config/libreoffice/4/user/extensions/shared/registry/com.sun.star.comp.deployment.sfwk.PackageRegistryBackend
/etc/skel/.config/libreoffice/4/user/extensions/shared/registry/com.sun.star.comp.deployment.component.PackageRegistryBackend
/etc/skel/.config/libreoffice/4/user/extensions/shared/registry/com.sun.star.comp.deployment.configuration.PackageRegistryBackend
/etc/skel/.config/libreoffice/4/user/extensions/shared/registry/com.sun.star.comp.deployment.configuration.PackageRegistryBackend/backenddb.xml
/etc/skel/.config/libreoffice/4/user/extensions/shared/registry/com.sun.star.comp.deployment.bundle.PackageRegistryBackend
/etc/skel/.config/libreoffice/4/user/extensions/shared/lastsynchronized
/etc/skel/.config/libreoffice/4/user/extensions/buildid
/etc/skel/.config/libreoffice/4/user/autocorr
/etc/skel/.config/libreoffice/4/user/uno_packages
/etc/skel/.config/libreoffice/4/user/basic
/etc/skel/.config/libreoffice/4/user/basic/script.xlc
/etc/skel/.config/libreoffice/4/user/basic/dialog.xlc
/etc/skel/.config/libreoffice/4/user/basic/Standard
/etc/skel/.config/libreoffice/4/user/basic/Standard/Module1.xba
/etc/skel/.config/libreoffice/4/user/basic/Standard/dialog.xlb
/etc/skel/.config/libreoffice/4/user/basic/Standard/script.xlb
/etc/skel/.config/libreoffice/4/user/autotext
/etc/skel/.config/libreoffice/4/user/autotext/mytexts.bau
/etc/skel/.config/leafpad
/etc/skel/.config/leafpad/leafpadrc
/etc/skel/.config/lxsession
/etc/skel/.config/lxsession/Lubuntu
/etc/skel/.config/lxsession/Lubuntu/desktop.conf
/etc/skel/.config/lxsession/Lubuntu/autostart
/etc/skel/.config/libfm
/etc/skel/.config/libfm/libfm.conf
/etc/skel/.config/libfm/dir-settings.conf
/etc/skel/.config/lxpanel
/etc/skel/.config/lxpanel/Lubuntu
/etc/skel/.config/lxpanel/Lubuntu/config
/etc/skel/.config/lxpanel/Lubuntu/panels
/etc/skel/.config/lxpanel/Lubuntu/panels/panel
/etc/skel/.config/gpicview
/etc/skel/.config/gpicview/gpicview.conf
/etc/skel/.config/doublecmd
/etc/skel/.config/doublecmd/doublecmd.xml
/etc/skel/.config/doublecmd/pixmaps.txt
/etc/skel/.config/doublecmd/session.ini
/etc/skel/.config/doublecmd/pwd.ini
/etc/skel/.config/doublecmd/doublecmd.ext.example
/etc/skel/.config/doublecmd/doublecmd.ext
/etc/skel/.config/doublecmd/multiarc.ini
/etc/skel/.config/doublecmd/shortcuts.scf
/etc/skel/.config/doublecmd/history.xml
/etc/skel/.config/ibus
/etc/skel/.config/ibus/bus
/etc/skel/.config/ibus/bus/06fc92f9624996d4078a496e5363e1aa-unix-0
/etc/skel/.bashrc
/etc/skel/.profile
/etc/skel/Plocha
/etc/skel/Plocha/skype.desktop
/etc/skel/Plocha/pcmanfm3L75EX.desktop
/etc/skel/Plocha/home.desktop
/etc/skel/Plocha/pidgin.desktop
/etc/skel/Plocha/firefox.desktop
/etc/skel/Plocha/teamviewer-teamviewer9.desktop
/etc/skel/Plocha/libreoffice-calc.desktop
/etc/skel/Plocha/libreoffice-writer.desktop
/etc/skel/Plocha/Servis
/etc/skel/Plocha/Servis/lxterminal.desktop
/etc/skel/Plocha/Servis/install_double_cmd.desktop
/etc/skel/Plocha/Servis/synaptic.desktop
/etc/skel/Plocha/Servis/install_chromium.desktop
/etc/skel/Plocha/Servis/pcmanfm.desktop
/etc/skel/.bash_logout
/etc/skel/.xscreensaver
------------------------------------------------------
lsb-release info
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=14.04
DISTRIB_CODENAME=trusty
DISTRIB_DESCRIPTION="Ubuntu 14.04 LTS"
------------------------------------------------------
remastersys version info
REMASTERSYSVERSION="3.0.4-2"
 
------------------------------------------------------
ISOTMP info
/home/remastersys/remastersys/ISOTMP:
celkem 20
drwxr-xr-x 2 root root 4096 &#269;ec 13 15:20 casper
drwxr-xr-x 2 root root 4096 &#269;ec 13 15:20 install
drwxr-xr-x 2 root root 4096 &#269;ec 13 15:20 isolinux
drwxr-xr-x 2 root root 4096 &#269;ec 13 15:20 preseed
-rw-r--r-- 1 root root  213 &#269;ec 13 15:20 README.diskdefines

/home/remastersys/remastersys/ISOTMP/casper:
celkem 1520296
-rw-r--r-- 1 root root      45380 &#269;ec 13 15:20 filesystem.manifest
-rw-r--r-- 1 root root      45318 &#269;ec 13 15:20 filesystem.manifest-desktop
-rw-r--r-- 1 root root 1522864128 &#269;ec 13 15:28 filesystem.squashfs
-rw-r--r-- 1 root root   27994701 &#269;ec 13 15:20 initrd.gz
-rw-r--r-- 1 root root        213 &#269;ec 13 15:20 README.diskdefines
-rw------- 1 root root    5813328 &#269;ec 13 15:20 vmlinuz

/home/remastersys/remastersys/ISOTMP/install:
celkem 176
-rw-r--r-- 1 root root 176500 &#269;ec 13 15:20 memtest

/home/remastersys/remastersys/ISOTMP/isolinux:
celkem 488
-rw-r--r-- 1 root root  24576 &#269;ec 13 15:20 isolinux.bin
-rw-r--r-- 1 root root    914 &#269;ec 13 15:20 isolinux.cfg
-rwxr-xr-x 1 root root 313101 &#269;ec 13 15:20 splash.png
-rw-r--r-- 1 root root 152976 &#269;ec 13 15:20 vesamenu.c32

/home/remastersys/remastersys/ISOTMP/preseed:
celkem 4
-rwxr-xr-x 1 root root 212 &#269;ec 13 15:20 custom.seed
------------------------------------------------------
/home/remastersys/remastersys/tmpusers info
------------------------------------------------------
Command-line options = backup
------------------------------------------------------
Cleaning up the install icon from the user desktops
Removing the ubiquity frontend as it has been included and is not needed on the normal system
Calculating the installed filesystem size for the installer
Removing remastersys-firstboot from system startup
Making disk compatible with Ubuntu Startup Disk Creator.
Creating md5sum.txt for the livecd/dvd
Creating Lubuntu_W7_14.04_Pro_r4.iso in /home/remastersys/remastersys
Making Lubuntu_W7_14.04_Pro_r4.iso a hybrid iso
Creating Lubuntu_W7_14.04_Pro_r4.iso.md5 in /home/remastersys/remastersys
/home/remastersys/remastersys/Lubuntu_W7_14.04_Pro_r4.iso which is 1,5G in size is ready to be burned or tested in a virtual machine.

```

Works good for me so I am going to continue using it. :-)

---

### Post by sudodus on 2014-07-14
Thanks for sharing :-)

---

### Post by Gobugs on 2014-08-04
I would like to use skel,  but with 14.04,  I don't find the xml config files.  Where are they?
$H/.gconf  .config are basically empty => which I guessing means their location has changed to somewhere else.
Where did they go ??  :)   thanks.

---

### Post by ping-wu on 2014-08-04
"Remastersys . . ."

I have successfully used Remastersys on Ubuntu through Ubuntu 14.04.

The problem is, a Remastersys-remastered ISO does not boot on  UEFI systems.

---

### Post by Juhele on 2014-11-29
Hi,
I was contacted by the users that the installer completely ignores user settings set (username, language etc.) during installation and uses the live user name + settings instead. Is there something I put in the **/etc/skel **causing this? I would like to use the live user settings as default to keep the theme and other system settings and configuration but I would also like to give them the freedom to set username, language etc.

thanks

---

### Post by sudodus on 2014-11-29
Are you using the [OEM installation]("https://help.ubuntu.com/community/Ubuntu_OEM_Installer_Overview") feature?

---

### Post by Juhele on 2014-11-29
I do not think so even in case of the other users. I think the users just click Install Ubuntu and use the default mode. I did not intentionally change anything in it. I tried it with another machine in default mode and I really got almost clone of the system on my "developer" VM which I use as source for the remasters.

---

### Post by sudodus on 2014-11-29
Maybe you can try if the OEM installation feature can help you solve the problem.

---

