---
title: "[SOLVED] KDE has taken over!"
date: 2007-07-28
forum: Desktop Environments
---

### Post by iflanery on 2007-07-28
I've had this problem for quite a few months, but it came to a head last night when I decided I wanted to go back to Ubuntu (I'm using Kubuntu right now). For some reason, I can't get my initial log-in screen back to the GDM, and KDE seems to have permanently messed up my installation of GNOME (much slower boot-up times, Gtk theme manager crashing, leaving me with nothing but a desktop background). Xfce doesn't even boot up. At all. 

I don't want rid myself of KDE completely (especially not amaroK and akregator); I simply want GNOME to be the default window manager. How can I go about accomplishing this?

More info will about my situation will be given by request; this is simply the best I could summarize my problem.

I'm using Kubuntu 6.10, b/w.

---

### Post by t0nedef on 2007-07-28
I had this exact same problem.... so this is what i did to get it all back and working again.... there is prolly an easier way, but it works

while logged in KDE *you don't want to try this in gnome, fun things will happen*

```
sudo apt-get remove alacarte app-install-data-commercial apport-gtk at-spi binfmt-support bittorrent brltty-x11 bug-buddy capplets-data cdrecord cli-common compiz compiz-core compiz-gnome compiz-gtk compiz-plugins contact-lookup-applet dbus-1-utils dcraw deskbar-applet desktop-effects diveintopython doc-base docbook-xml ekiga eog esound espeak espeak-data evince evolution evolution-common evolution-data-server evolution-data-server-common evolution-exchange evolution-plugins evolution-webcal example-content f-spot feisty-gdm-themes feisty-session-splashes feisty-wallpapers file-roller firefox firefox-gnome-support gaim gaim-data gamin gcalctool gcc-3.3-base gconf-editor gconf2 gdebi gdebi-core gdm gedit gedit-common gimp gimp-data gimp-print gimp-python gksu gnome-about gnome-accessibility-themes gnome-app-install gnome-applets gnome-applets-data gnome-btdownload gnome-cards-data gnome-control-center gnome-cups-manager gnome-desktop-data gnome-doc-utils gnome-games gnome-games-data gnome-icon-theme gnome-keyring gnome-keyring-manager gnome-mag gnome-media gnome-media-common gnome-menus gnome-mime-data gnome-mount gnome-netstatus-applet gnome-nettool gnome-orca gnome-panel gnome-panel-data gnome-pilot gnome-pilot-conduits gnome-power-manager gnome-screensaver gnome-session gnome-spell gnome-system-monitor gnome-system-tools gnome-terminal gnome-terminal-data gnome-themes gnome-user-guide gnome-utils gnome-volume-manager gstreamer0.10-alsa gstreamer0.10-esd gstreamer0.10-gnomevfs gstreamer0.10-plugins-base gstreamer0.10-plugins-base-apps gstreamer0.10-plugins-good gstreamer0.10-tools gstreamer0.10-x gthumb gtk2-engines gtk2-engines-pixbuf gtk2-engines-ubuntulooks gtkhtml3.14 gucharmap guile-1.6-libs hal-device-manager human-cursors-theme human-icon-theme human-theme hwdb-client-gnome language-selector libaa1 libatspi1.0-0 libavahi-glib1 libavc1394-0 libbeagle0 libbonobo2-0 libbonobo2-common libbonoboui2-0 libbonoboui2-common libbrlapi1 libcaca0 libcairo-perl libcamel1.2-10 libcdio6 libcroco3 libcucul0 libdecoration0 libdjvulibre15 libdv4 libebook1.2-9 libecal1.2-7 libedata-book1.2-2 libedata-cal1.2-6 libedataserver1.2-9 libedataserverui1.2-8 libeel2-2 libeel2-data libegroupwise1.2-13 libenchant1c2a libespeak1 libexchange-storage1.2-3 libgail-common libgail-gnome-module libgail18 libgamin0 libgconf2.0-cil libgda2-3 libgda2-common libgdiplus libgdl-1-0 libgdl-1-common libgimp2.0 libgksu1.2-1 libgksu2-0 libgksuui1.0-1 libglade2.0-cil libglew1 libglib-perl libglib2.0-cil libgmime-2.0-2 libgmime2.2-cil libgnome-desktop-2 libgnome-keyring0 libgnome-mag2 libgnome-media0 libgnome-menu2 libgnome-pilot2 libgnome-speech3 libgnome-window-settings1 libgnome2-0 libgnome2-canvas-perl libgnome2-common libgnome2-perl libgnome2-vfs-perl libgnome2.0-cil libgnomecanvas2-0 libgnomecanvas2-common libgnomecups1.0-1 libgnomecupsui1.0-1c2a libgnomekbd-common libgnomekbd1 libgnomekbdui1 libgnomeprint2.2-0 libgnomeprint2.2-data libgnomeprintui2.2-0 libgnomeprintui2.2-common libgnomeui-0 libgnomeui-common libgnomevfs2-0 libgnomevfs2-bin libgnomevfs2-common libgnomevfs2-extra libgsf-1-114 libgsf-1-common libgtk2-perl libgtk2.0-cil libgtkhtml2-0 libgtkhtml3.14-19 libgtksourceview-common libgtksourceview1.0-0 libgtkspell0 libgtop2-7 libgtop2-common libgucharmap6 libguile-ltdl-1 libgutenprintui2-1 libhsqldb-java libhtml-parser-perl libhtml-tagset-perl libhtml-tree-perl libiec61883-0 libkpathsea4 liblaunchpad-integration0 liblircclient0 liblpint-bonobo0 libmdbtools libmetacity0 libmono-cairo1.0-cil libmono-corlib1.0-cil libmono-corlib2.0-cil libmono-data-tds2.0-cil libmono-security2.0-cil libmono-sharpzip2.84-cil libmono-sqlite2.0-cil libmono-system-data2.0-cil libmono-system-web2.0-cil libmono-system1.0-cil libmono-system2.0-cil libmono0 libmono2.0-cil libnautilus-burn4 libnautilus-extension1 libndesk-dbus-glib1.0-cil libndesk-dbus1.0-cil libnet-dbus-perl libnm-glib0 libnotify1 libnspr4 libnss3 liboil0.3 liboobs-1-3 libopal-2.2.0 libpanel-applet2-0 libpisock9 libpisync0 libpoppler1-glib libpt-1.10.0 libpt-plugins-alsa libpt-plugins-v4l libpt-plugins-v4l2 libqthreads-12 librsvg2-2 librsvg2-common libscrollkeeper0 libservlet2.3-java libsexy2 libshout3 libslab0 libsoup2.2-8 libstdc++5 libtotem-plparser1 liburi-perl libvte-common libvte9 libwmf0.2-7 libwnck-common libwnck18 libwww-perl libxevie1 libxklavier11 libxml-parser-perl libxml-twig-perl libxml2-utils libxres1 metacity metacity-common mkisofs mono-common mono-gac mono-jit mono-runtime nautilus nautilus-cd-burner nautilus-data nautilus-sendto network-manager-gnome notification-daemon onboard openoffice.org openoffice.org-base openoffice.org-evolution openoffice.org-filter-mobiledev openoffice.org-gnome openoffice.org-gtk pkg-config python-at-spi python-bittorrent python-cairo python-gconf python-gdbm python-glade2 python-gmenu python-gnome2 python-gnome2-desktop python-gnome2-extras python-gnomecanvas python-gobject python-gst0.10 python-gtk2 python-gtkhtml2 python-launchpad-integration python-libxml2 python-notify python-numeric python-orca-brlapi python-pyorbit python-virtkey python-vte python-xml rdesktop restricted-manager rhythmbox rss-glx scim scim-gtk2-immodule scim-modules-socket scim-modules-table scim-tables-additional screensaver-default-images scrollkeeper serpentine sgml-data shared-mime-info software-properties-gtk sound-juicer ssh-askpass-gnome synaptic system-tools-backends tangerine-icon-theme tango-icon-theme tango-icon-theme-common tomboy totem totem-gstreamer totem-mozilla tsclient ubuntu-artwork ubuntu-desktop ubuntu-docs ubuntu-sounds update-manager update-notifier usplash-theme-ubuntu vino vnc-common whois xsane xsane-common xscreensaver-data xscreensaver-gl xsltproc xvncviewer yelp zenity
```

I did it that way because it wouldn't let me just remove and reinstall gdm because of dependancy on ubuntu-desktop, and when its done with all that

```
sudo aptitude install ubuntu-desktop
```

when it gets to the part when its reinstalling gdm it will ask you if you want to use gdm or kdm, select the one you want. It worked for me, i don't promise it will work for you. that second command reinstalls everything we just uninstalled, i doublechecked it myself... but i don't know if you used apt-get or aptitude to install your gnome in the first place, but if you decide you change your mind later and want to remove gnome again, just type 

```
sudo aptitude remove gnome
```

and since you used aptitude this time, it should do the exact same thing. that of course only works if you originally installed it with aptitude.

---

### Post by iflanery on 2007-07-28
Luckily I didn't do this while logged into Gnome. I had the foresight to do it while logged into Window Maker, but either way I ****** it up pretty badly. I managed to get rid of KDE alright, but my computer decided to take the login manager down along with it. I chose not to kill the current session, but when I logged out, I saw just a blank screen with a black cursor. ](*,) So, I'm pretty much back to square one. Using sudo aptitude install ubuntu-desktop didn't work, as it said it was already installed. Same with GDM. So I just said **** it. For the time being, though, my computer is basically an expensive paperweight, which explains why I'm currently downloading an image of version 7.04.

Thanks for the advice, though. Much appreciated.

---

### Post by pbcartwright on 2007-07-29
not sure how your partitions are setup, but if you have a separate /home partition ( recommended) you can use teh CD and reinstall Ubuntu and have all your settings back. If you didn't create a separate /home, you should copy  your /home folder somewhere as backup, or at least /home/USER_NAME/.kde and .gnome
I reinstall Linux all the time, and still have my mail folders and firefox bookmarks intact.

---

### Post by snkiz on 2007-07-29
> **pbcartwright said:**
> 
I reinstall Linux all the time, and still have my mail folders and firefox bookmarks intact.

Exactly how do you do that?

---

### Post by jim_p on 2007-07-29
> **snkiz said:**
> Exactly how do you do that?

I think he has set his /home folder to a whole other partition. The firefox bookmarks must be lying somewhere in there

---

### Post by Happy_Man on 2007-07-29
> **iflanery said:**
> Luckily I didn't do this while logged into Gnome. I had the foresight to do it while logged into Window Maker, but either way I ****** it up pretty badly. I managed to get rid of KDE alright, but my computer decided to take the login manager down along with it. I chose not to kill the current session, but when I logged out, I saw just a blank screen with a black cursor. ](*,) So, I'm pretty much back to square one. Using sudo aptitude install ubuntu-desktop didn't work, as it said it was already installed. Same with GDM. So I just said **** it. For the time being, though, my computer is basically an expensive paperweight, which explains why I'm currently downloading an image of version 7.04.

Thanks for the advice, though. Much appreciated.
There is an easier way. Upgrading is good and all, but if you still want to keep everything, here's a good way to do it. Do a hard reboot, and then boot the recovery mode. Log in, and use the command ```
sudo aptitude install ubuntu-desktop
```

---

### Post by iflanery on 2007-07-29
> **pbcartwright said:**
> not sure how your partitions are setup, but if you have a separate /home partition ( recommended) you can use teh CD and reinstall Ubuntu and have all your settings back. If you didn't create a separate /home, you should copy  your /home folder somewhere as backup, or at least /home/USER_NAME/.kde and .gnome
I reinstall Linux all the time, and still have my mail folders and firefox bookmarks intact.

For one thing, I didn't have any separate partitions; when I installed Ubuntu on my computer, I had to give my entire hard drive to it because Windows XP Pro--which I was using at the time--refused to cooperate with the partitioner. I would think that simply using a back up of my /home/ directory would simply bring me back in the very situation from which I seek to get away.

In any event, I performed a clean install, with the latest version of Ubuntu, and things have been working pretty smoothly.

---

### Post by strabes on 2007-08-11
In order to get GDM to be the default, do ```
sudo dpkg-reconfigure kdm
sudo dpkg-reconfigure gdm
``` and select gdm both times. If you installed kubuntu-desktop using aptitude then you won't have any problems removing it:```
sudo aptitude remove kubuntu-desktop
```You said you wanted amarok still so just reinstall it; your settings will be saved in your home folder and won't be removed with the above command unless you use the -purge flag.

---

### Post by iflanery on 2007-08-11
Thanks for the help and advice, everyone (I really should've waited before doing another clean install, lemme tell ya), but I've pretty much had this problem solved for a couple weeks.

---

