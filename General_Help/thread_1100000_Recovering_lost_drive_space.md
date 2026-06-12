---
title: "Recovering lost drive space"
date: 2009-03-18
forum: General Help
---

### Post by pd1944 on 2009-03-18
I've tried all the suggestions that I have found...empty trash (including e-mail), empty temp folders (rm -rf /tmp/*), deleting package files (apt-get clean and apt-get autoclean). and running localepurge.  All of them help to some extent...but I am now at a point where I keep losing space and am not able to recover it.

I am running Ubuntu on a Dell Mini 9, and I don't use the internal drive to store anything with the exception of a few e-mail messages...but I regularly clean this up and get back a few megs.  I'm travelling in New Zealand and what I mostly do is transfer .jpg files from a compact flash card (via USB) to an external hard drive (also via USB). A week ago I had 240mb of free space after running localepurge.  Since then I've transferred maybe 900mb of .jpg files as described above, and I'm down to 165mb of free space.

I've tried all of the above and I am unable to recover any space...any suggestions welcome...but please be gentle as I am not a unix/ubuntu wizard...but I am trying to learn.

Thanks.

Paul Donovan

---

### Post by taurus on 2009-03-18
Post the outputs of these commands from a terminal.

```
df -h
sudo du -h /var
```

---

### Post by pd1944 on 2009-03-18
pdonovan@pdonovan:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2             3.4G  3.1G  165M  96% /
varrun                247M  100K  247M   1% /var/run
varlock               247M     0  247M   0% /var/lock
udev                  247M   52K  247M   1% /dev
devshm                247M   12K  247M   1% /dev/shm
lrm                   247M  1.5M  246M   1% /lib/modules/2.6.24-19-lpia/volatile
gvfs-fuse-daemon      3.4G  3.1G  165M  96% /home/pdonovan/.gvfs
/dev/mmcblk0p1        7.4G   65M  7.4G   1% /media/disk
pdonovan@pdonovan:~$ sudo du -h /var
[sudo] password for pdonovan: 
4.0K	/var/cache/hwtest
4.0K	/var/cache/cups/ppd
4.0K	/var/cache/cups/rss
20K	/var/cache/cups
36K	/var/cache/dictionaries-common
5.7M	/var/cache/debconf
5.1M	/var/cache/app-install
924K	/var/cache/hald
4.0K	/var/cache/samba
4.0K	/var/cache/gnome-system-tools/backup
8.0K	/var/cache/gnome-system-tools
4.0K	/var/cache/apt/archives/partial
24K	/var/cache/apt/archives
24M	/var/cache/apt
20K	/var/cache/man/tr
4.0K	/var/cache/man/fsstnd
20K	/var/cache/man/fr.UTF-8
20K	/var/cache/man/ja
20K	/var/cache/man/pt_BR
20K	/var/cache/man/pl
20K	/var/cache/man/hu
20K	/var/cache/man/fr.ISO8859-1
20K	/var/cache/man/es
4.0K	/var/cache/man/cat4
20K	/var/cache/man/ru.KOI8-R
4.0K	/var/cache/man/X11R6
20K	/var/cache/man/it.UTF-8
4.0K	/var/cache/man/opt
20K	/var/cache/man/zh_TW
4.0K	/var/cache/man/cat6
20K	/var/cache/man/de
20K	/var/cache/man/ru
4.0K	/var/cache/man/local
20K	/var/cache/man/fi
4.0K	/var/cache/man/cat8
4.0K	/var/cache/man/oldlocal
20K	/var/cache/man/ru.UTF-8
20K	/var/cache/man/ko
4.0K	/var/cache/man/cat7
20K	/var/cache/man/sv
20K	/var/cache/man/pl.ISO8859-2
4.0K	/var/cache/man/cat1
20K	/var/cache/man/zh_CN
20K	/var/cache/man/it.ISO8859-1
20K	/var/cache/man/pa
4.0K	/var/cache/man/cat5
20K	/var/cache/man/fr
20K	/var/cache/man/gl
20K	/var/cache/man/pl.UTF-8
20K	/var/cache/man/id
20K	/var/cache/man/it
20K	/var/cache/man/cs
4.0K	/var/cache/man/cat3
864K	/var/cache/man
4.0K	/var/cache/jockey
312K	/var/cache/fontconfig
5.9M	/var/cache/flashplugin-nonfree
48K	/var/cache/ldconfig
28K	/var/cache/system-tools-backends/backup/5/etc
32K	/var/cache/system-tools-backends/backup/5
8.0K	/var/cache/system-tools-backends/backup/1/etc
12K	/var/cache/system-tools-backends/backup/1
8.0K	/var/cache/system-tools-backends/backup/6/var/cache/system-tools-backends
12K	/var/cache/system-tools-backends/backup/6/var/cache
16K	/var/cache/system-tools-backends/backup/6/var
20K	/var/cache/system-tools-backends/backup/6
8.0K	/var/cache/system-tools-backends/backup/7/etc
12K	/var/cache/system-tools-backends/backup/7
8.0K	/var/cache/system-tools-backends/backup/First/var/cache/system-tools-backends
12K	/var/cache/system-tools-backends/backup/First/var/cache
16K	/var/cache/system-tools-backends/backup/First/var
20K	/var/cache/system-tools-backends/backup/First
8.0K	/var/cache/system-tools-backends/backup/3/var/cache/system-tools-backends
12K	/var/cache/system-tools-backends/backup/3/var/cache
16K	/var/cache/system-tools-backends/backup/3/var
20K	/var/cache/system-tools-backends/backup/3
8.0K	/var/cache/system-tools-backends/backup/2/var/cache/system-tools-backends
12K	/var/cache/system-tools-backends/backup/2/var/cache
16K	/var/cache/system-tools-backends/backup/2/var
20K	/var/cache/system-tools-backends/backup/2
8.0K	/var/cache/system-tools-backends/backup/4/etc
12K	/var/cache/system-tools-backends/backup/4
152K	/var/cache/system-tools-backends/backup
160K	/var/cache/system-tools-backends
20K	/var/cache/localepurge
43M	/var/cache
48K	/var/log/cups
4.0K	/var/log/news
4.0K	/var/log/samba
280K	/var/log/apt
12K	/var/log/fsck
24K	/var/log/gdm
4.0K	/var/log/dist-upgrade
4.0K	/var/log/unattended-upgrades
4.0K	/var/log/ntpstats
5.2M	/var/log
412K	/var/tmp/kdecache-pdonovan
416K	/var/tmp
0	/var/lock
4.0K	/var/crash
4.0K	/var/spool/cups/tmp
140K	/var/spool/cups
16K	/var/spool/anacron
4.0K	/var/spool/openoffice/uno_packages/cache
8.0K	/var/spool/openoffice/uno_packages
12K	/var/spool/openoffice
4.0K	/var/spool/cups-pdf/SPOOL
4.0K	/var/spool/cups-pdf/ANONYMOUS
12K	/var/spool/cups-pdf
184K	/var/spool
4.0K	/var/opt
0	/var/run/sudo/pdonovan
0	/var/run/sudo
0	/var/run/wpa_supplicant0
4.0K	/var/run/cups/certs
12K	/var/run/cups
8.0K	/var/run/NetworkManager
0	/var/run/console
8.0K	/var/run/hald
8.0K	/var/run/avahi-daemon
4.0K	/var/run/dbus
8.0K	/var/run/klogd
0	/var/run/PolicyKit
0	/var/run/screen
4.0K	/var/run/network
0	/var/run/sendsigs.omit.d
100K	/var/run
4.0K	/var/local
4.0K	/var/games
4.0K	/var/mail
8.0K	/var/backups
4.0K	/var/lib/guidance-backends
28K	/var/lib/python-support/python2.5/gdata/docs
52K	/var/lib/python-support/python2.5/gdata/spreadsheet
76K	/var/lib/python-support/python2.5/gdata/calendar
44K	/var/lib/python-support/python2.5/gdata/apps
48K	/var/lib/python-support/python2.5/gdata/base
416K	/var/lib/python-support/python2.5/gdata
16K	/var/lib/python-support/python2.5/dbus/mainloop
180K	/var/lib/python-support/python2.5/dbus
68K	/var/lib/python-support/python2.5/atom
92K	/var/lib/python-support/python2.5/glchess/ggz
88K	/var/lib/python-support/python2.5/glchess/chess/fics
196K	/var/lib/python-support/python2.5/glchess/chess
36K	/var/lib/python-support/python2.5/glchess/ui
140K	/var/lib/python-support/python2.5/glchess/gtkui
200K	/var/lib/python-support/python2.5/glchess/scene/opengl
56K	/var/lib/python-support/python2.5/glchess/scene/cairo
284K	/var/lib/python-support/python2.5/glchess/scene
944K	/var/lib/python-support/python2.5/glchess
376K	/var/lib/python-support/python2.5/orca/scripts
1.6M	/var/lib/python-support/python2.5/orca
20K	/var/lib/python-support/python2.5/gtk-2.0/gnomevfs
20K	/var/lib/python-support/python2.5/gtk-2.0/gnomeprint
16K	/var/lib/python-support/python2.5/gtk-2.0/pynotify
24K	/var/lib/python-support/python2.5/gtk-2.0/gtk/gdkgl
52K	/var/lib/python-support/python2.5/gtk-2.0/gtk/gtkgl
164K	/var/lib/python-support/python2.5/gtk-2.0/gtk
16K	/var/lib/python-support/python2.5/gtk-2.0/gnomedesktop
60K	/var/lib/python-support/python2.5/gtk-2.0/gobject
24K	/var/lib/python-support/python2.5/gtk-2.0/bonobo
16K	/var/lib/python-support/python2.5/gtk-2.0/totem
44K	/var/lib/python-support/python2.5/gtk-2.0/gnome
20K	/var/lib/python-support/python2.5/gtk-2.0/evolution
504K	/var/lib/python-support/python2.5/gtk-2.0
156K	/var/lib/python-support/python2.5/xdg
100K	/var/lib/python-support/python2.5/gnome_sudoku/gtk_goodies
448K	/var/lib/python-support/python2.5/gnome_sudoku
88K	/var/lib/python-support/python2.5/invest
5.2M	/var/lib/python-support/python2.5
5.2M	/var/lib/python-support
12K	/var/lib/dictionaries-common/ispell
8.0K	/var/lib/dictionaries-common/aspell
12K	/var/lib/dictionaries-common/wordlist
36K	/var/lib/dictionaries-common
176K	/var/lib/misc
58M	/var/lib/gconf/defaults
92K	/var/lib/gconf/debian.defaults
58M	/var/lib/gconf
8.0K	/var/lib/initramfs-tools
8.0K	/var/lib/dbus
4.0K	/var/lib/hal
52K	/var/lib/belocs
4.0K	/var/lib/vim/addons
8.0K	/var/lib/vim
4.0K	/var/lib/xkb
12K	/var/lib/PolicyKit
32M	/var/lib/dpkg/info
4.0K	/var/lib/dpkg/parts
304K	/var/lib/dpkg/alternatives
16K	/var/lib/dpkg/triggers
4.0K	/var/lib/dpkg/updates
37M	/var/lib/dpkg
4.0K	/var/lib/sgml-base
4.0K	/var/lib/gnome-session
8.0K	/var/lib/alsa
4.0K	/var/lib/synaptic
1.5M	/var/lib/defoma/psfontmgr.d
4.0K	/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID
228K	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
236K	/var/lib/defoma/x-ttcidfont-conf.d/dirs
624K	/var/lib/defoma/x-ttcidfont-conf.d
152K	/var/lib/defoma/libwmf0.2-7.d
4.0K	/var/lib/defoma/gs.d/dirs/CMap
128K	/var/lib/defoma/gs.d/dirs/fonts
136K	/var/lib/defoma/gs.d/dirs
248K	/var/lib/defoma/gs.d
148K	/var/lib/defoma/pango.d
84K	/var/lib/defoma/scripts
128K	/var/lib/defoma/fontconfig.d
3.3M	/var/lib/defoma
8.0K	/var/lib/locales/supported.d
12K	/var/lib/locales
4.0K	/var/lib/displayconfig-gtk/locations
8.0K	/var/lib/displayconfig-gtk
4.0K	/var/lib/apt/mirrors/partial
8.0K	/var/lib/apt/mirrors
4.0K	/var/lib/apt/periodic
76K	/var/lib/apt/keyrings
220K	/var/lib/apt/lists/partial
42M	/var/lib/apt/lists
42M	/var/lib/apt
12K	/var/lib/update-notifier/user.d
16K	/var/lib/update-notifier
24K	/var/lib/ucf/cache
72K	/var/lib/ucf
148K	/var/lib/scrollkeeper/en_GB
68K	/var/lib/scrollkeeper/tr
68K	/var/lib/scrollkeeper/nb
116K	/var/lib/scrollkeeper/ja
60K	/var/lib/scrollkeeper/nn
168K	/var/lib/scrollkeeper/pt_BR
80K	/var/lib/scrollkeeper/pl
60K	/var/lib/scrollkeeper/hr
116K	/var/lib/scrollkeeper/hu
60K	/var/lib/scrollkeeper/my
60K	/var/lib/scrollkeeper/as
60K	/var/lib/scrollkeeper/ky
68K	/var/lib/scrollkeeper/kn
72K	/var/lib/scrollkeeper/da
272K	/var/lib/scrollkeeper/es
60K	/var/lib/scrollkeeper/af
60K	/var/lib/scrollkeeper/si
120K	/var/lib/scrollkeeper/bg
60K	/var/lib/scrollkeeper/hy
60K	/var/lib/scrollkeeper/tl
60K	/var/lib/scrollkeeper/se
144K	/var/lib/scrollkeeper/el
144K	/var/lib/scrollkeeper/uk
60K	/var/lib/scrollkeeper/sq
60K	/var/lib/scrollkeeper/ta
60K	/var/lib/scrollkeeper/am
60K	/var/lib/scrollkeeper/lg
104K	/var/lib/scrollkeeper/zh_TW
64K	/var/lib/scrollkeeper/et
60K	/var/lib/scrollkeeper/fo
72K	/var/lib/scrollkeeper/is
60K	/var/lib/scrollkeeper/tg
60K	/var/lib/scrollkeeper/rm
60K	/var/lib/scrollkeeper/lo
64K	/var/lib/scrollkeeper/lt
60K	/var/lib/scrollkeeper/bn
132K	/var/lib/scrollkeeper/de
60K	/var/lib/scrollkeeper/te
60K	/var/lib/scrollkeeper/ga
200K	/var/lib/scrollkeeper/ru
148K	/var/lib/scrollkeeper/ca
60K	/var/lib/scrollkeeper/mr
108K	/var/lib/scrollkeeper/nl
60K	/var/lib/scrollkeeper/kk
60K	/var/lib/scrollkeeper/cy
60K	/var/lib/scrollkeeper/rw
60K	/var/lib/scrollkeeper/mg
136K	/var/lib/scrollkeeper/fi
96K	/var/lib/scrollkeeper/ro
60K	/var/lib/scrollkeeper/ka
60K	/var/lib/scrollkeeper/co
160K	/var/lib/scrollkeeper/ko
76K	/var/lib/scrollkeeper/ar
60K	/var/lib/scrollkeeper/lb
68K	/var/lib/scrollkeeper/he
64K	/var/lib/scrollkeeper/ms
60K	/var/lib/scrollkeeper/th
60K	/var/lib/scrollkeeper/ia
252K	/var/lib/scrollkeeper/sv
72K	/var/lib/scrollkeeper/sr
60K	/var/lib/scrollkeeper/li
68K	/var/lib/scrollkeeper/be
60K	/var/lib/scrollkeeper/sr@Latn
5.2M	/var/lib/scrollkeeper/index
264K	/var/lib/scrollkeeper/C
156K	/var/lib/scrollkeeper/zh_CN
60K	/var/lib/scrollkeeper/or
76K	/var/lib/scrollkeeper/vi
60K	/var/lib/scrollkeeper/sw
60K	/var/lib/scrollkeeper/mn
60K	/var/lib/scrollkeeper/sl
60K	/var/lib/scrollkeeper/yo
60K	/var/lib/scrollkeeper/ku
124K	/var/lib/scrollkeeper/pa
60K	/var/lib/scrollkeeper/bs
60K	/var/lib/scrollkeeper/ur
60K	/var/lib/scrollkeeper/mi
200K	/var/lib/scrollkeeper/oc
260K	/var/lib/scrollkeeper/fr
60K	/var/lib/scrollkeeper/wa
72K	/var/lib/scrollkeeper/gl
72K	/var/lib/scrollkeeper/en
72K	/var/lib/scrollkeeper/id
60K	/var/lib/scrollkeeper/yi
60K	/var/lib/scrollkeeper/gu
60K	/var/lib/scrollkeeper/uz
64K	/var/lib/scrollkeeper/lv
120K	/var/lib/scrollkeeper/pt
5.9M	/var/lib/scrollkeeper/TOC
60K	/var/lib/scrollkeeper/fa
200K	/var/lib/scrollkeeper/it
92K	/var/lib/scrollkeeper/sk
60K	/var/lib/scrollkeeper/wo
60K	/var/lib/scrollkeeper/ml
60K	/var/lib/scrollkeeper/ne
60K	/var/lib/scrollkeeper/no
60K	/var/lib/scrollkeeper/tk
60K	/var/lib/scrollkeeper/ug
60K	/var/lib/scrollkeeper/zu
104K	/var/lib/scrollkeeper/eu
92K	/var/lib/scrollkeeper/cs
60K	/var/lib/scrollkeeper/an
60K	/var/lib/scrollkeeper/eo
60K	/var/lib/scrollkeeper/xh
60K	/var/lib/scrollkeeper/br
60K	/var/lib/scrollkeeper/az
21M	/var/lib/scrollkeeper
8.0K	/var/lib/ntp
68K	/var/lib/doc-base/info
8.0K	/var/lib/doc-base/omf/pnm2ppa-calibrate
8.0K	/var/lib/doc-base/omf/diveintopython
8.0K	/var/lib/doc-base/omf/gnupginterface
8.0K	/var/lib/doc-base/omf/dc
8.0K	/var/lib/doc-base/omf/install-docs-man
8.0K	/var/lib/doc-base/omf/ispell-manual
8.0K	/var/lib/doc-base/omf/java-policy
8.0K	/var/lib/doc-base/omf/man-db
8.0K	/var/lib/doc-base/omf/doc-base
8.0K	/var/lib/doc-base/omf/pnm2ppa-ppa_networking
8.0K	/var/lib/doc-base/omf/debian-java-faq
8.0K	/var/lib/doc-base/omf/pnm2ppa-color
8.0K	/var/lib/doc-base/omf/gimp-help-en
108K	/var/lib/doc-base/omf
68K	/var/lib/doc-base/documents
248K	/var/lib/doc-base
16K	/var/lib/gdm
4.0K	/var/lib/libuuid
28K	/var/lib/acpi-support
32K	/var/lib/xml-core
4.0K	/var/lib/flashplugin-nonfree
12K	/var/lib/dhcp3
4.0K	/var/lib/NetworkManager
4.0K	/var/lib/update-manager
4.0K	/var/lib/snmp
12K	/var/lib/avahi-autoipd
3.5M	/var/lib/aspell
8.0K	/var/lib/thunderbird/extensions.d
12K	/var/lib/thunderbird
24K	/var/lib/x11
8.0K	/var/lib/PolicyKit-public
4.0K	/var/lib/initscripts
4.0K	/var/lib/aptitude
8.0K	/var/lib/urandom
169M	/var/lib
217M	/var
pdonovan@pdonovan:~$

---

### Post by taurus on 2009-03-18
You don't give yourself a whole lot of disk space there with 3.4GB.  Maybe you should consider removing some apps that you don't really need.  If you don't use OpenOffice, should remove it.  And if you have two versions of kernels and only use the latest, remove the old one.  Go through your Applications menu and see what you can remove and try to remove it from synaptic.

```
ls -la /boot
```

---

### Post by pd1944 on 2009-03-18
I have stripped out all of the apps that I don't use...I do use Open Office and GIMP regularly, as well as Evolution and Bluefish...Part of the problem I have is that the Mini 9 came with very little drive space.

The thing that I do not understand is why space disappears when I copy a file from one external drive to another external drive...and I am not able to recover it once the copying is done...

Any ideas on that????

pd

---

### Post by Therion on 2009-03-18
Try using QuickStart's "House Cleaning" option.  It should free up some space.

Be SURE you read the install directions:  [http://www.quickstart.freeforums.org/quickstart-download-pics-t2.html](http://www.quickstart.freeforums.org/quickstart-download-pics-t2.html)

---

### Post by pd1944 on 2009-03-18
That worked!

Apparently when I copied the .jpg files, Ubuntu cached a copy of the thumbnail...there were over 400mb of thumbnails...and QuickStart removed them.

Thanks for the pointers...both of you, Taurus and Therion...

pd

---

