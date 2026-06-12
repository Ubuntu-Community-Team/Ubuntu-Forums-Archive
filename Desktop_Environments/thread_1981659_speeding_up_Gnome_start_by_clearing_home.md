---
title: "speeding up Gnome start by clearing /home?"
date: 2012-05-17
forum: Desktop Environments
---

### Post by leopard86 on 2012-05-17
Dear forum users,
I want to solve an issue of mine and possibly share some information.

My laptop is running Ubuntu from more than 1 year without many changes besides upgrades from 10.10 to 11.04 and then 11.10 and then downgraded to 10.10 by a fresh install and then agin to 11.04. Each time it took only a few minutes as every configuration for gnome and its applications are on a separate partition mounting the /home folder. So far so good, the only problem is that each time I up/downgraded the system, Gnome start took longer and longer as - I guess - there are a lot of old hidden files in /home retaining formation that is not needed anymore or even increase the starting time by booting unuseful stuff and so on.

The machine is not very recent but at the first Ubuntu install  it was way faster. The boot time is ok, I also run several times bootchart and managed to gain some small extra time. The problem is when Gnome is started. I think there is a lot of trash that is not required anymore. I'm posting a list of my hidden folders in /home, maybe I can delete some of them right away that are not needed. Gnome is 2.31.1 (but the issue was there already with previous up/downgrades) and Ubuntu 11.04.

```
.
..
.AbiSuite
.adobe
.aFolder
.alsamodular
.aMule
.android
.appdata
.ardour2
.arduino
.ArobasMusic
.audacity-data
.autumn
.avm
.AwOkenrc
.bash_history
.bash_logout
.bashrc
.bazaar
.beast
.bserc
.byobu
.bzr.log
.cache
.chromium-bsu
.compiz
.compiz-1
.config
.crebs
.cups
.dbus
.desktopflickr
.dmrc
.dropbox
.dropbox-dist
.dropbox-dist-new
.dvdcss
.easystroke
.eclipse
.elements
.emerald
.esd_auth
.evolution
.face
.filezilla
.fontconfig
.fonts
.fretsonfire
.furiusisomount
.gconf
.gconfd
.gEDA
.gegl-0.0
.gervill
.gimp-2.6
.gksu.lock
.gnome2
.gnome2_private
.gnome-color-chooser
.gnupg
.gstreamer-0.10
.gtk-bookmarks
.gtkrc-2.0
.gtkrc-2.0-gnome-color-chooser
.gtkrc-2.0.save
.gvfs
.hgrc
.hplip
.hydrogen
.ICEauthority
.icedtea
.icedteaplugin
.icons
.idm
.jackbeat
.jackdrc
.jamin
.java
.kde
.kino-history
.kinorc
.launchy
.lesshst
.libreoffice
.local
.lyx
.lyxpipe.in
.lyxpipe.out
.macromedia
.matlab
.mc
.mhwaveedit
.mission-control
.moovida
.mozilla
.mplayer
.mtab.fuseiso
.musePrj
.nautilus
.netx
.ocrfeeder
.openoffice.org
.openshot
.orta
.patchagerc
.pdextended
.pki
.praat-dir
.printer-groups.xml
.processing
.profile
.pulse
.pulse.bak
.pulse-cookie
.python-eggs
.qt
.remmina
.rubberband.wisdom.d
.screenlets
.screenrc
.scribus
.shotwell
.Skype
.sooperlooper
.speech-dispatcher
.ssh
.subversion
.sudo_as_admin_successful
.supertux2
.synaptic
.teamviewer
.texmf-var
.themes
.thumbnails
.thunderbird
.torcs
.tortoisehg
.touchosc2pd
.tsclient
.tuxguitar-1.2
.tvplayer
.VirtualBox
.vkeybdmap
.vmware
.wally
.wine
.wine_backup
.wine_boh
.wine_ie6
.wine.old2
.wireshark
.x11vnc.log.lapleo:5900
.Xauthority
.xine
.xinput.d
.xscreensaver
.xscreensaver-getimage.cache
.xsession-errors
.xsession-errors.old

```

---

### Post by irw on 2012-05-17
I too have a separate home partition.

I have moved all of my home contents - hidden and visible files and folders - into a subdirectory and then moved back in stages what I wanted in my home. Sometimes it is quicker to re-create some settings than copy a folder with old and new stuff in it.

I last did this with a fresh install when I told the installer to ignore my home partition. I then mounted the home partition, moved everything into a new folder, then copied the contents of my new home folder across.
I then changed /etc/fstab to mount the original home partition.
Result: clean settings, ready to move back what I want or need bit by bit.

I'm tired - I think that make sense - if not ask for clarification!

---

### Post by leopard86 on 2012-05-17
Ok, that seems to be a good option... Did you get improvements in the system responseviness?

---

### Post by titaniumbones on 2012-10-07
Did anyone notice any particular speekdup with any of these dotfiles? about to try the same on my system, which has similar speed issues on boot.  Thanks!

---

