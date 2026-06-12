---
title: "notify-osd corners"
date: 2010-08-30
forum: Desktop Environments
---

### Post by gnrathon on 2010-08-30
I have a strange little problem with the notification system.
It used to look perfectly normal, but now all the corners except for the top left are sharp instead of rounded.... is there any way i can get it back to normal? 

I will post a picture so you can see it better.

---

### Post by gnrathon on 2010-08-30
bump

---

### Post by Elfy on 2010-08-30
Please do not bump so soon.

---

### Post by gnrathon on 2010-08-30
okay, im sorry

---

### Post by Gaygerbil on 2010-08-31
I do believe you're using NotifyOSD config since you're testing how you're notifications look like, if so there's something called Corner Radius it should be in the bottom right corner of your bubble config, turn that one up and tell me if there's a difference.

---

### Post by gnrathon on 2010-08-31
> **Gaygerbil said:**
> I do believe you're using NotifyOSD config since you're testing how you're notifications look like, if so there's something called Corner Radius it should be in the bottom right corner of your bubble config, turn that one up and tell me if there's a difference.

Yes I am using NotifyOSD and no it didn't do anything.

---

### Post by hhh on 2010-08-31
Delete the file .notify-osd in your /home/USER_NAME folder (it's hidden) and start over. If that doesn't work, copy/paste the sample .notify-osd file from this post...
[http://www.webupd8.org/2010/05/finally-easy-way-to-customize-notify.html](http://www.webupd8.org/2010/05/finally-easy-way-to-customize-notify.html)

As you can see from that file, the corner-radius (and, oddly, the drop shadow) is determined by 2 numbers, but I can't figure out which does what.

HTH.

---

### Post by gnrathon on 2010-08-31
> **hhh said:**
> Delete the file .notify-osd in your /home/USER_NAME folder (it's hidden) and start over. If that doesn't work, copy/paste the sample .notify-osd file from this post...
[http://www.webupd8.org/2010/05/finally-easy-way-to-customize-notify.html](http://www.webupd8.org/2010/05/finally-easy-way-to-customize-notify.html)

As you can see from that file, the corner-radius (and, oddly, the drop shadow) is determined by 2 numbers, but I can't figure out which does what.

HTH.

Tried both, no success. It seems that (if you look at the photo) that the shadows are cut off from the corners.

---

### Post by hhh on 2010-09-01
What about purging notify osd (and deleting that configuration file again) and reinstalling? You'll need to remove the repositories for the updated notify osd first, then...

```
sudo apt-get purge notify-osd
```
Delete .notify-osd
```
sudo apt-get install notify-osd
```
Then you can update notify osd again if everything is back to normal first.

Webupd8 (among other places) has instructions on completely removing PPAs. You might try leaving a comment in one of the notify osd threads there, Andrew is very helpful.

---

### Post by Giraffro on 2010-09-08
I have this problem too.

> **hhh said:**
> What about purging notify osd (and deleting that configuration file again) and reinstalling? You'll need to remove the repositories for the updated notify osd first, then...

```
sudo apt-get purge notify-osd
```
Delete .notify-osd
```
sudo apt-get install notify-osd
```
Then you can update notify osd again if everything is back to normal first.

I've tried this and it's still broken. In fact, there was no configuration file before I uninstalled. I've also tried updating notify-osd to 0.9.29-0ubuntu3 and it's still broken.

---

### Post by Gaygerbil on 2010-09-09
Just a thought if you haven't tried this already open up Synaptic and search notify and libnotify I'd completely remove notify-osd, libnotify, pythonnotify, libnotify-bin, and notify-osd-icons, log out then reinstall em'. 

Also try delete your notify-osd config file while you do that.

---

### Post by Giraffro on 2010-09-09
> **Gaygerbil said:**
> Just a thought if you haven't tried this already open up Synaptic and search notify and libnotify I'd completely remove notify-osd, libnotify, pythonnotify, libnotify-bin, and notify-osd-icons, log out then reinstall em'. 

Also try delete your notify-osd config file while you do that.

Still broken. For anyone willing to try this, selecting 'Complete removal' in Synaptic will remove gnome-desktop (edit: and Déjà Dup). Not too much of a problem, just run the following command after logging in through terminal (e.g. booting into recovery mode):

```
sudo apt-get install gnome-desktop
```

Also, if you're having trouble finding packages in Synaptic, I had libnotify1 and python-notify instead of libnotify and pythonnotify respectively (running Lucid).

---

### Post by Milos_SD on 2010-09-09
You are using xorg-edgers ppa, do you? If you do, then the updated libpixman package is a problem.

---

### Post by Giraffro on 2010-09-09
> **Milos_SD said:**
> You are using xorg-edgers ppa, do you? If you do, then the updated libpixman package is a problem.

libpixman was causing the issues. Fixed now. Thanks!

---

### Post by mejs on 2010-09-13
hi, how can you roll back libpixman package without uninstalling it, because it requires removal of a lot of other stuff?

---

### Post by joey.slb on 2010-09-23
*sudo apt-get install libpixman-1-0**=**VERSION_TO_INSTALL*

To see the versions available:
*apt-cache show libpixman-1-0*

---

### Post by mejs on 2010-10-09
that will still require removal of around 1.5 GB of packages, basically removing half of the system...

```
~$ sudo apt-get install libpixman-1-0=0.16.4-1ubuntu2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  python-docky menu libmono-getoptions2.0-cil libbluetooth-dev libbabl-0.0-0
  libxcb-keysyms1 xchat-common most libsdl-gfx1.2-4 libvamp-hostsdk3 fatresize
  libglew1.5 libxmlrpc-core-c3 libxmlrpc-c3 qemu cheese-common audacity-data
  libflac++6 xdotool libcddb2 libparted0 libdvbpsi5 python-utidylib
  cairo-dock-data cryptsetup libtre5 libvlc2 libtidy-0.99-0 gettext
  libboost-signals1.40.0 vlc-nox cvs python-compizconfig wmctrl libwxbase2.8-0
  python-feedparser libenet0debian1 liblzo2-2 tcl libiso9660-7 fuseiso
  libxdg-basedir1 liblua5.1-0 libdb4.7 vlc-plugin-pulse xsel vlc-data
  libboost-filesystem1.40.0 libtar cairo-dock-plug-ins-data gimp-data
  python-chardet libvlccore2 libvcdinfo0 libebml0 libboost-system1.40.0
  libetpan13 libmatroska0 libdevil1c2 libsdl-image1.2
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  0ad 0ad-data adobe-flashplugin adobeair aisleriot alacarte apport-gtk apturl
  at-spi audacity basilisk2 boxee brasero brltty-x11 cairo-dock-core
  cairo-dock-plug-ins cairo-dock-plug-ins-integration checkbox-gtk cheese
  chromium-browser chromium-browser-inspector chromium-codecs-ffmpeg
  clicompanion compiz compiz-fusion-plugins-extra compiz-fusion-plugins-main
  compiz-gnome compiz-plugins compizconfig-settings-manager
  computer-janitor-gtk couchdb-bin default-jre desktopcouch docky empathy eog
  evince evolution evolution-couchdb evolution-data-server evolution-exchange
  evolution-indicator evolution-plugins evolution-webcal f-spot file-roller
  firefox firefox-branding firefox-gnome-support frostwire gbrainy gcalctool
  gconf-editor gdebi gdm gdm-guest-session gedit gimp gksu gnome-about
  gnome-accessibility-themes gnome-applets gnome-bluetooth gnome-codec-install
  gnome-control-center gnome-disk-utility gnome-games-common gnome-icon-theme
  gnome-keyring gnome-mag gnome-mahjongg gnome-media gnome-menus gnome-nettool
  gnome-orca gnome-panel gnome-power-manager gnome-raw-thumbnailer
  gnome-schedule gnome-screensaver gnome-session gnome-session-bin
  gnome-session-canberra gnome-settings-daemon gnome-sudoku
  gnome-system-monitor gnome-system-tools gnome-terminal gnome-themes-selected
  gnome-themes-ubuntu gnome-user-guide gnome-user-share gnome-utils gnomine
  gparted gstreamer0.10-plugins-bad gstreamer0.10-plugins-good gstreamer0.10-x
  gsynaptics gtk2-engines gtk2-engines-murrine gtk2-engines-pixbuf gtkdialog
  gucharmap gvfs gvfs-backends gvfs-bin gvfs-fuse gwibber gwibber-service
  humanity-icon-theme ibus ibus-gtk ibus-m17n ibus-table icedtea6-plugin
  indicator-applet indicator-applet-session indicator-application indicator-me
  indicator-messages indicator-session indicator-sound indicator-usb
  jockey-gtk language-selector libaccess-bridge-java libaccess-bridge-java-jni
  libappindicator0 libatspi1.0-0 libavahi-ui0 libbonoboui2-0 libbrasero-media0
  libcairo-perl libcairo2 libcairomm-1.0-1 libcanberra-gtk-module
  libcanberra-gtk0 libcheese-gtk18 libclutter-1.0-0 libclutter-gtk-0.10-0
  libcryptui0 libdbusmenu-gtk1 libedataserverui1.2-8 libevdocument2 libevview2
  libexchange-storage1.2-3 libflickrnet2.2-cil libgail-common
  libgail-gnome-module libgail18 libgcr0 libgdict-1.0-6 libgdiplus libgdu-gtk0
  libgegl-0.0-0 libgimp2.0 libgksu2-0 libglade2-0 libglade2.0-cil
  libgnome-bluetooth7 libgnome-desktop-2-17 libgnome-media0 libgnome-pilot2
  libgnome-window-settings1 libgnome2-0 libgnome2-canvas-perl libgnome2-perl
  libgnome2.24-cil libgnomecanvas2-0 libgnomedesktop2.20-cil libgnomekbd4
  libgnomepanel2.24-cil libgnomeui-0 libgoocanvas3 libgpod-common libgpod4
  libgraphviz4 libgstfarsight0.10-0 libgtk-vnc-1.0-0 libgtk2-perl libgtk2.0-0
  libgtk2.0-bin libgtk2.0-cil libgtkglext1 libgtkhtml-editor0
  libgtkhtml3.14-19 libgtkmm-2.4-1c2a libgtksourceview2.0-0 libgtkspell0
  libgucharmap7 libgweather1 libido-0.1-0 libindicate-gtk2 libindicator0
  liblaunchpad-integration1 liblaunchpad-integration1.0-cil liblpint-bonobo0
  libmagickcore2-extra libmetacity-private0 libmono-addins-gui0.2-cil
  libmono-cairo2.0-cil libmono-system-runtime2.0-cil libmono-system-web2.0-cil
  libmono2.0-cil libmoon libnautilus-extension1 libnotify-bin libnotify0.4-cil
  libnotify1 libnunit2.4-cil libpanel-applet2-0 libpango-perl libpango1.0-0
  libpangomm-1.4-1 libpolkit-gtk-1-0 libpoppler-glib4 libpurple0 librsvg2-2
  librsvg2-2.18-cil librsvg2-common libsexy2 libtelepathy-farsight0
  libubuntuone-1.0-1 libunique-1.0-0 libvte9 libwebkit-1.0-2 libwmf0.2-7-gtk
  libwnck2.20-cil libwnck22 libwxgtk2.8-0 light-themes metacity
  moonlight-plugin-core mousetweaks multiboot mupen64plus nautilus
  nautilus-sendto nautilus-sendto-empathy nautilus-share network-manager-gnome
  network-manager-pptp-gnome notify-osd onboard openjdk-6-jre
  openoffice.org-base-core openoffice.org-calc openoffice.org-common
  openoffice.org-core openoffice.org-draw openoffice.org-emailmerge
  openoffice.org-gnome openoffice.org-gtk openoffice.org-help-en-us
  openoffice.org-impress openoffice.org-math openoffice.org-style-human
  openoffice.org-writer
  org.bcdef.antenna.43fd862ecbf25eb623fc234ef1704635b78e3ab6.1 pitivi
  plymouth-label plymouth-theme-ubuntu-logo plymouth-x11 policykit-1-gnome
  pysdm python-appindicator python-aptdaemon-gtk python-cairo
  python-desktopcouch python-desktopcouch-records python-evolution
  python-farsight python-glade2 python-gmenu python-gnome2 python-gnomeapplet
  python-gnomecanvas python-gnomekeyring python-gtk2 python-gtkmozembed
  python-gtksourceview2 python-gtkspell python-ibus python-indicate
  python-launchpad-integration python-notify python-papyon python-pyatspi
  python-pygoocanvas python-rsvg python-traitsbackendwx python-ubuntuone
  python-ubuntuone-client python-uno python-virtkey python-vte python-webkit
  python-wnck python-wxgtk2.8 python-wxversion quadrapassel rhythmbox
  rhythmbox-plugin-cdrecorder rhythmbox-plugins
  rhythmbox-ubuntuone-music-store screenlets screensaver-default-images
  seahorse simple-ccsm simple-scan software-center software-properties-gtk
  ssh-askpass-gnome startupmanager synaptic system-config-printer-gnome
  telepathy-butterfly telepathy-haze tomboy totem totem-mozilla totem-plugins
  transmission-gtk tsclient
  tweetdeckfast.fff259dc0ce2657847bbb4aff0e62062efc56543.1 ubufox
  ubuntu-artwork ubuntu-desktop ubuntu-docs ubuntu-mono ubuntu-tweak
  ubuntuone-client ubuntuone-client-gnome update-manager update-notifier
  usb-creator-gtk vinagre vino vlc xchat xdg-user-dirs-gtk xscreensaver-data
  xscreensaver-gl xulrunner-1.9.2 yelp zenity
The following packages will be DOWNGRADED:
  libpixman-1-0
0 upgraded, 0 newly installed, 1 downgraded, 347 to remove and 7 not upgraded.
Need to get 236kB of archives.
After this operation, 1,596MB disk space will be freed.

```

---

### Post by libihero on 2010-12-10
> **Giraffro said:**
> libpixman was causing the issues. Fixed now. Thanks!


how were you able to fix it??

---

### Post by Giraffro on 2010-12-10
> **libihero said:**
> how were you able to fix it??

It's been a while, but I think there was the libpixman build in xorg-edgers that was the problem. I would've thought the build included in 10.10 would fix this, so try updating / upgrading.

---

### Post by ram0s on 2010-12-15
I'm sorry to be reviving this thread, but I don't think it is necessary to open a new one for this question...

My notifications just vanished. I wasn't even trying to configure anything on them, I was happy the way they were. I just noticed they vanished: Nothing appears: no updates on IM's no volume info, no media player info, nothing. I've tried reinstalling notify-osd, but didn't do anything. 

I'm using avant window manager, and if I activate the notification daemon applet, they work, but when removing it again, the standard NotifyOSD (which is the one I like -.-) doesn't show anything. The process is running and everything seems to be in order. It just vanished. Any help?

Cheers.

---

