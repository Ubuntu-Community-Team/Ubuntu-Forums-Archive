---
title: "LXDE autostarts Opera every time"
date: 2009-03-28
forum: Desktop Environments
---

### Post by n2stc on 2009-03-28
I can't figure out why.  I looked in the autostart folder and file: not there.  Anyone else have any ideas?

Thanks,
Stan

---

### Post by kerry_s on 2009-03-28
post the output of> ls -a

look in .xinitrc <most common
look in .xsession <possible

---

### Post by n2stc on 2009-03-29
> **kerry_s said:**
> post the output of> ls -a

look in .xinitrc <most common
look in .xsession <possible

I assume you meant of the home directory

```

--                      .klog
.                       .kompozer
..                      krc405-485-s305-385-3590.pdf
1-90s_country.ogg       kubuntu-8.10-desktop-i386.iso
ad.aup                  lexmark
ad_data                 .lftp
.adobe                  link-to-irextender.txt
.alltray                .local
.amsn                   .lpoptions
amsn_received           .macromedia
ARS 2008 programs.xls   .mcop
.aspell.en.prepl        .mcoprc
.aspell.en.pws          memo_file
.audacity1.2-stan       menu.lst
.audacity-data          menu.txt
banging head.txt        .metacity
.bash_history           Mom
.bash_logout            .mozilla
.bashrc                 .mozilla-thunderbird
.beagle                 .mplayer
bike for barter         Music
.cache                  My Documents
.camel_certs            MyPDA
.cddb                   My Received Files
clock                   myscripts
.config                 .nautilus
.conkyrc                nautilus-debug-log.txt
.conkyrc~               .netscape
Cron                    novena.odt
.d3lphinview            old address.csv
Dad.lnk                 .openoffice.org2
Dad's Pictures.lnk      .opera
.dbus                   opera6.adr
.dbus-keyrings          opera6.html
Desktop                 opera_9.62.2466.gcc4.qt3_i386.deb
desktop.ini             opera_9.63.2474.gcc4.qt3_i386.deb
.dmrc                   .orca
Documents               p1030217.jpg
downloaded              .pcmanfm
.esd_auth               Picture 056.jpg
.evolution              PIX
Examples                pn2stc_reduced.jpg
father_car0.odb         .profile
father-car-address.odt  Public
father_car.ods          .pulse-cookie
file:                   .purple
.filezilla              .qt
.fluxbox                QuickStart
.fontconfig             r_20080715_low.mp3
.fonts                  receipt.odt
.fonts.conf             .recently-used
.fr-5gzlkT              .recently-used.xbel
.fr-6kEEmu              Recipe.odb
.fr-afroy2              Recipes
.fr-CVM9iU              resume.doc
.fr-dqXRO2              .rhapsody
.fr-ES9dDP              .sane
.gcjwebplugin           .screem
.gconf                  .serpentine
.gconfd                 Shared Files
.gftp                   smb4k
.gimp-2.4               smb.conf
.gksu.lock              smb.conf~
.gnome                  .stellarium
.gnome2                 .strigi
.gnome2_private         .sudo_as_admin_successful
.gnomerc                .synaptic
.gnomerc~               Templates
.gnumericrc             .themes
.gnupg                  .thumbnails
.gpilotd                .tomboy
.gpilotd.pid            .tomboy.log
griffith.doc            To PIX_CD
griffith.html           to walmart
griffith.xml            .Trash
.gstreamer-0.10         --.unpacked
.gtk-bookmarks          .update-manager-core
.gtk_qt_engine_rc       .update-notifier
.gtkrc-1.2-gnome2       viewone
.gtkrc-2.0-kde          viewonecache
hello.c                 .vnc
hello.c~                .w3m
HELLO.C                 .wapi
.hplip                  .xaralx
.htoprc                 .XaraLXFilters
.hwdb                   .Xauthority
.ICEauthority           .xine
.icons                  .xinitrc
.ideskrc                .xsession
.idesktop               .xsession-errors
ij                      .xsession-errors-:1
images                  xsession.old
.java                   xsession.old1
.kde

```

Thanks!

---

### Post by kerry_s on 2009-03-29
let me see>
.xinitrc
.xsession
.config/openbox/startup

wow, i see your trying all kinds of things. :lolflag:

---

### Post by Mark76 on 2009-03-29
If I remember correctly LXDE has its own start up folder.

From what I can recall it's drag and drop, like the ROX one.

I think it's in /usr/share/

---

### Post by n2stc on 2009-04-02
Not in any of those places.
:mad:

---

### Post by features on 2009-04-02
try /home/$USER/.config/autostart 

That's where mine are with LXDE :)

($USER = your username :) )

---

