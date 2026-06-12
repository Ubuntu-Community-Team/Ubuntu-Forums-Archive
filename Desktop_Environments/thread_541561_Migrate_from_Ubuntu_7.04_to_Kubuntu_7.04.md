---
title: "Migrate from Ubuntu 7.04 to Kubuntu 7.04"
date: 2007-09-03
forum: Desktop Environments
---

### Post by gtdaqua on 2007-09-03
Ok, I have a doubt here.

In a nutshell: Installed Ubuntu on my other machine - didnt like it much and want to go to Kubuntu 7.04 (i love this one!). 

So what I have done is went to synaptic and selected some kubuntu components like kubuntu-desktop, splash, some grub compo etc (which again selected some more components) and about 190MB is being downloaded as I type. I dont want to use GNOME. Ever. I just want to stick to KDE. 

So i think after i have this kubuntu-desktop installed do i just have to type

"apt-get remove gnome-desktop"

to get rid of KDE (and all its apps of course like totem, photo organizer)? I want to be able to use the ones that come with KDE (Amarok, K3b, Kaffeine, KMix, KTorrent, Kopit).

I saw [this]("http://ubuntuforums.org/showthread.php?t=482815") and I guess this would be simple.

Any thoughts, ubuntu lovers?

---

### Post by the yawner on 2007-09-03
While I'm relatively new myself, I'd wager that's the correct way to do it. Just to be sure though, you could also do the following if you think something might be missed out.

(taken from [http://www.psychocats.net/ubuntu/purekde]("http://www.psychocats.net/ubuntu/purekde")
> sudo apt-get remove alacarte app-install-data-commercial apport-gtk at-spi binfmt-support bittorrent brltty-x11 bug-buddy capplets-data cdrecord cli-common compiz compiz-core compiz-gnome compiz-gtk compiz-plugins contact-lookup-applet dbus-1-utils dcraw deskbar-applet desktop-effects diveintopython doc-base docbook-xml ekiga eog esound espeak espeak-data evince evolution evolution-common evolution-data-server evolution-data-server-common evolution-exchange evolution-plugins evolution-webcal example-content f-spot feisty-gdm-themes feisty-session-splashes feisty-wallpapers file-roller firefox firefox-gnome-support gaim gaim-data gamin gcalctool gcc-3.3-base gconf-editor gconf2 gdebi gdebi-core gdm gedit gedit-common gimp gimp-data gimp-print gimp-python gksu gnome-about gnome-accessibility-themes gnome-app-install gnome-applets gnome-applets-data gnome-btdownload gnome-cards-data gnome-control-center gnome-cups-manager gnome-desktop-data gnome-doc-utils gnome-games gnome-games-data gnome-icon-theme gnome-keyring gnome-keyring-manager gnome-mag gnome-media gnome-media-common gnome-menus gnome-mime-data gnome-mount gnome-netstatus-applet gnome-nettool gnome-orca gnome-panel gnome-panel-data gnome-pilot gnome-pilot-conduits gnome-power-manager gnome-screensaver gnome-session gnome-spell gnome-system-monitor gnome-system-tools gnome-terminal gnome-terminal-data gnome-themes gnome-user-guide gnome-utils gnome-volume-manager gstreamer0.10-alsa gstreamer0.10-esd gstreamer0.10-gnomevfs gstreamer0.10-plugins-base gstreamer0.10-plugins-base-apps gstreamer0.10-plugins-good gstreamer0.10-tools gstreamer0.10-x gthumb gtk2-engines gtk2-engines-pixbuf gtk2-engines-ubuntulooks gtkhtml3.14 gucharmap guile-1.6-libs hal-device-manager human-cursors-theme human-icon-theme human-theme hwdb-client-gnome language-selector libaa1 libatspi1.0-0 libavahi-glib1 libavc1394-0 libbeagle0 libbonobo2-0 libbonobo2-common libbonoboui2-0 libbonoboui2-common libbrlapi1 libcaca0 libcairo-perl libcamel1.2-10 libcdio6 libcroco3 libcucul0 libdecoration0 libdjvulibre15 libdv4 libebook1.2-9 libecal1.2-7 libedata-book1.2-2 libedata-cal1.2-6 libedataserver1.2-9 libedataserverui1.2-8 libeel2-2 libeel2-data libegroupwise1.2-13 libenchant1c2a libespeak1 libexchange-storage1.2-3 libgail-common libgail-gnome-module libgail18 libgamin0 libgconf2.0-cil libgda2-3 libgda2-common libgdiplus libgdl-1-0 libgdl-1-common libgimp2.0 libgksu1.2-1 libgksu2-0 libgksuui1.0-1 libglade2.0-cil libglew1 libglib-perl libglib2.0-cil libgmime-2.0-2 libgmime2.2-cil libgnome-desktop-2 libgnome-keyring0 libgnome-mag2 libgnome-media0 libgnome-menu2 libgnome-pilot2 libgnome-speech3 libgnome-window-settings1 libgnome2-0 libgnome2-canvas-perl libgnome2-common libgnome2-perl libgnome2-vfs-perl libgnome2.0-cil libgnomecanvas2-0 libgnomecanvas2-common libgnomecups1.0-1 libgnomecupsui1.0-1c2a libgnomekbd-common libgnomekbd1 libgnomekbdui1 libgnomeprint2.2-0 libgnomeprint2.2-data libgnomeprintui2.2-0 libgnomeprintui2.2-common libgnomeui-0 libgnomeui-common libgnomevfs2-0 libgnomevfs2-bin libgnomevfs2-common libgnomevfs2-extra libgsf-1-114 libgsf-1-common libgtk2-perl libgtk2.0-cil libgtkhtml2-0 libgtkhtml3.14-19 libgtksourceview-common libgtksourceview1.0-0 libgtkspell0 libgtop2-7 libgtop2-common libgucharmap6 libguile-ltdl-1 libgutenprintui2-1 libhsqldb-java libhtml-parser-perl libhtml-tagset-perl libhtml-tree-perl libiec61883-0 libkpathsea4 liblaunchpad-integration0 liblircclient0 liblpint-bonobo0 libmdbtools libmetacity0 libmono-cairo1.0-cil libmono-corlib1.0-cil libmono-corlib2.0-cil libmono-data-tds2.0-cil libmono-security2.0-cil libmono-sharpzip2.84-cil libmono-sqlite2.0-cil libmono-system-data2.0-cil libmono-system-web2.0-cil libmono-system1.0-cil libmono-system2.0-cil libmono0 libmono2.0-cil libnautilus-burn4 libnautilus-extension1 libndesk-dbus-glib1.0-cil libndesk-dbus1.0-cil libnet-dbus-perl libnm-glib0 libnotify1 libnspr4 libnss3 liboil0.3 liboobs-1-3 libopal-2.2.0 libpanel-applet2-0 libpisock9 libpisync0 libpoppler1-glib libpt-1.10.0 libpt-plugins-alsa libpt-plugins-v4l libpt-plugins-v4l2 libqthreads-12 librsvg2-2 librsvg2-common libscrollkeeper0 libservlet2.3-java libsexy2 libshout3 libslab0 libsoup2.2-8 libstdc++5 libtotem-plparser1 liburi-perl libvte-common libvte9 libwmf0.2-7 libwnck-common libwnck18 libwww-perl libxevie1 libxklavier11 libxml-parser-perl libxml-twig-perl libxml2-utils libxres1 metacity metacity-common mkisofs mono-common mono-gac mono-jit mono-runtime nautilus nautilus-cd-burner nautilus-data nautilus-sendto network-manager-gnome notification-daemon onboard openoffice.org openoffice.org-base openoffice.org-evolution openoffice.org-filter-mobiledev openoffice.org-gnome openoffice.org-gtk pkg-config python-at-spi python-bittorrent python-cairo python-gconf python-gdbm python-glade2 python-gmenu python-gnome2 python-gnome2-desktop python-gnome2-extras python-gnomecanvas python-gobject python-gst0.10 python-gtk2 python-gtkhtml2 python-launchpad-integration python-libxml2 python-notify python-numeric python-orca-brlapi python-pyorbit python-virtkey python-vte python-xml rdesktop restricted-manager rhythmbox rss-glx scim scim-gtk2-immodule scim-modules-socket scim-modules-table scim-tables-additional screensaver-default-images scrollkeeper serpentine sgml-data shared-mime-info software-properties-gtk sound-juicer ssh-askpass-gnome synaptic system-tools-backends tangerine-icon-theme tango-icon-theme tango-icon-theme-common tomboy totem totem-gstreamer totem-mozilla tsclient ubuntu-artwork ubuntu-desktop ubuntu-docs ubuntu-sounds update-manager update-notifier usplash-theme-ubuntu vino vnc-common whois xsane xsane-common xscreensaver-data xscreensaver-gl xsltproc xvncviewer yelp zenity && sudo apt-get install kubuntu-desktop



---

### Post by swisscow on 2007-09-03
Best and simplest in my humble opinion, if you have your docs backed up and haven't invested too much special effort in ubuntu, download and burn the kubuntu cd and do a fresh install.

I've migrated from gnome to kde in the past and it just doesn't seem to go as smoothly as a fresh install. Why - I have no idea.l

---

### Post by gtdaqua on 2007-09-03
Thanks swisscow! 
Yawner, thank you! wonder where u got  that thing anyway!!!

Ok, the only reason why I dont want a fresh install because, I have XP running on it. 
XP was the primary OS. And without any modificaitions, I installed Ubuntu 7.04 on a unused partition and Ubuntu automatically brought my XP Pro on the boot menu! 

So I dont want to play again and lose XP (for now. later I will spank it!)

---

### Post by Azzco on 2007-09-03
The boot menu will still be the same with kubuntu. Kubuntu is a derivate of ubuntu and most is the same except for the desktop enviroment and programmes. just reinstall over your ubuntu partition and you should be okay. ;)

---

### Post by gtdaqua on 2007-09-03
Swisscow!

when you say it doesnt go "as smoothly" - what are the issues that would come?

Would it all disappear if we followed that big fat code from Yawner (thanks again, Yawner! I think I will do this just to be sure)

how  about "apt-get autoremove" ?

---

### Post by gtdaqua on 2007-09-03
So the boot menu won't remove XP? I currently have the following in the boot choice list

Ubuntu 
Ubuntu (Recovery)
Ubuntu Memtest
XP Pro

So if i do fresh install of Kubuntu after deleting the Linux partition, you say that XP will remain. Right?

---

### Post by the yawner on 2007-09-03
Forgot to mention that the big fat code installs kubuntu-desktop as well. Anyway, got it from this site: [http://www.psychocats.net/ubuntu/]("http://www.psychocats.net/ubuntu/")

=====

As for re-installation, you shouldn't have any problems. Just select the partition option to manual. Check the format checkbox on the ubuntu partition and edit the mount back to just / (I think it's now set to /media~ when you're going for a reinstall) and leave swap as it is.

Glad to be of help. Cheers. :)

---

### Post by gtdaqua on 2007-09-03
Cheers Guys!

So now that two of you confirmed I think I will just take the Kubuntu CD and install it. I previously did manual partitioning to specify "/" drive and swap. 4.5GB for "/" and 2GB for swap.

Will let you guys know tomorrow (this is for my home PC) how it all went!

---

### Post by swisscow on 2007-09-03
> **gtdaqua said:**
> Swisscow!

when you say it doesnt go "as smoothly" - what are the issues that would come?

Would it all disappear if we followed that big fat code from Yawner (thanks again, Yawner! I think I will do this just to be sure)

how  about "apt-get autoremove" ?

Just things haven't gone so well. Like I said, I don't know why but wireless networking didn't work without some effort, menus seemed screwed up - still had gnome stuff in there. Reading further down this thread it seems you're going for the fresh install. Good choice.

---

### Post by gtdaqua on 2007-09-03
yes. I will do a fresh install - although I prefer a lot of tweaks before doing the standard thing. 

I was a little reluctant on fresh install but all my data is safe inside the HDD. Even if XP doesnt boot up, I think I can manage and fully migrate and start using Kubuntu. Its an Intel P4 - ugliest ever made and XP just takes way too long to respond! So I might probably be happy if XP doesnt boot at all!

---

### Post by gtdaqua on 2007-09-04
ALL CLEAR NOW!

Installed Fresh Kubuntu Feisty 32bit on the desktop and XP is intact! Success

Thank you everyone!

---

### Post by misfitpierce on 2007-09-04
Indeed I would fresh install a Kubuntu disc if you plan on removing gnome anyways. Safest and surest way to get Kubuntu which I also love and did :)

---

