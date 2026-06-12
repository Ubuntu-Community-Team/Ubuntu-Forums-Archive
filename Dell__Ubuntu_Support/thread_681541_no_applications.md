---
title: "no applications"
date: 2008-01-29
forum: Dell  Ubuntu Support
---

### Post by shrimants on 2008-01-29
So i really like ubuntu and how stable it is now on my computer (dell vostro 1500, c2d 2.2 ghz, nvidia 8600m gt, 2 gigs ram, ipw3945, 1680x1050 screen).

what i absolutely hate is the fact that it comes with every single application that i will and will not ever use. i cant stand that at all. is there any way i can remove every single application it comes with so i can start from "scratch"? like all i need is possibly package manager but probably only terminal and Gnome. and obviously the kernel and drivers. i dont need things like sticky notes or tomboy or that fish or doctor something's eyes that follow you around the screen. i dont need evolution or ekiga or half the audio video stuff.

i want to switch to linux because unlike windows, it doesnt need to come with a dedicated something or the other for everything. i want to choose my own applications based on my needs. basically, office, pidgin, mozilla, some universal media player is more or less all i need. that and like the calender/time thing and sound etc. and codecs i guess, but i can get those myself too.

any help?

---

### Post by drsaamah on 2008-01-29
have you tried simply removing them?  if you go to the the applications tab->add/remove applications, you can select to view only the applications already installed on ur system.  from there just remove what you don't want.
the only problem is going to be removing applications that contain libraries other applications are dependent on.  you can remove those using synaptics package manager.  be careful doing that though.  when i first started using linux i tried doing that and accidently deleted xorg.

---

### Post by p_quarles on 2008-01-29
If you want maximum control over what is installed, and are willing to start from scratch, then I recommend this guide:
[http://www.psychocats.net/ubuntu/minimal#barebones](http://www.psychocats.net/ubuntu/minimal#barebones)

---

### Post by shrimants on 2008-01-29
the thing is, that i dont think that will install the drivers and whatnot that i need. for instance, i have the wireless card and lan card that need restricted drivers, and i also need the new nvidia drivers. im not sure if i use the restricted ones for an 8600m gt or if i use the nvidia-glx-new. also, theres no way that will work right away since the video drivers arent supported.

i know about the add/remove programs route to uninstall stuff, but ubuntu comes with so much useless crap that i have no idea what else is installed on there or what i actually need. like would it be a good idea to just install everything and then aptitude remove ubuntu-desktop? wouldnt that remove just about everything except drivers and gnome? or at the very least leave just a few things left over?

edit:> 
sudo apt-get remove alacarte aspell bittorrent bluez-cups bluez-gnome bluez-utils bogofilter bogofilter-bdb bogofilter-common brltty brltty-x11 bsh bug-buddy capplets-data cdrdao cli-common compiz compiz-core compiz-fusion-plugins-extra compiz-fusion-plugins-main compiz-gnome compiz-plugins consolekit contact-lookup-applet dcraw deskbar-applet dictionaries-common diveintopython ekiga eog espeak evince evolution evolution-common evolution-data-server evolution-data-server-common evolution-exchange evolution-plugins evolution-webcal f-spot fast-user-switch-applet firefox-gnome-support fping gcj-4.2-base gconf-editor gedit gedit-common gij gij-4.2 gimp-python gnome-about gnome-applets gnome-applets-data gnome-btdownload gnome-control-center gnome-desktop-data gnome-doc-utils gnome-keyring-manager gnome-media gnome-menus gnome-netstatus-applet gnome-nettool gnome-panel gnome-panel-data gnome-pilot gnome-pilot-conduits gnome-power-manager gnome-session gnome-spell gnome-terminal gnome-terminal-data gnome-user-guide gnome-utils gnome-volume-manager gstreamer0.10-alsa gstreamer0.10-esd gstreamer0.10-gnomevfs gstreamer0.10-plugins-base gstreamer0.10-plugins-base-apps gstreamer0.10-plugins-good gstreamer0.10-tools gstreamer0.10-x gthumb gtkhtml3.14 hal-device-manager hwdb-client-common hwdb-client-gnome libalut0 libao2 libart2.0-cil libavc1394-0 libbeagle0 libbluetooth2 libcaca0 libcamel1.2-10 libcdio6 libcompizconfig-backend-gconf libcompizconfig0 libcucul0 libdecoration0 libdeskbar-tracker libdv4 libebook1.2-9 libecal1.2-7 libedata-book1.2-2 libedata-cal1.2-6 libedataserver1.2-9 libedataserverui1.2-8 libeel2-2 libeel2-data libegroupwise1.2-13 libexchange-storage1.2-3 libgcj-bc libgcj-common libgcj8-1 libgconf2.0-cil libgda3-3 libgda3-common libgdl-1-0 libgdl-1-common libgdl-gnome-1-0 libgksu1.2-1 libgksuui1.0-1 libgl1-mesa-dri libglade2.0-cil libglew1.4 libglib2.0-cil libgmime-2.0-2 libgmime2.2-cil libgnome-pilot2 libgnome-vfs2.0-cil libgnome-window-settings1 libgnome2.0-cil libgnomevfs2-bin libgnomevfs2-extra libgpod2 libgsl0 libgtk2.0-cil libgtkhtml2.0-cil libgtkhtml3.14-19 libgtkhtml3.8-15 libgtksourceview2.0-0 libgtksourceview2.0-common libhsqldb-java libicu36 libiec61883-0 libjaxp1.3-java libjline-java liblpint-bonobo0 libmono-cairo1.0-cil libmono-corlib1.0-cil libmono-corlib2.0-cil libmono-data-tds2.0-cil libmono-security2.0-cil libmono-sharpzip2.84-cil libmono-sqlite2.0-cil libmono-system-data2.0-cil libmono-system-web2.0-cil libmono-system1.0-cil libmono-system2.0-cil libmono0 libmono2.0-cil libmtp6 libmusicbrainz4c2a libndesk-dbus-glib1.0-cil libndesk-dbus1.0-cil libneon26 liboil0.3 libopal-2.2 libopenal0a libpam-gnome-keyring libpisock9 libpisync0 libpt-1.10.0 libpt-plugins-alsa libpt-plugins-v4l libpt-plugins-v4l2 librarian0 libraw1394-8 librsvg2.0-cil libservlet2.4-java libshout3 libsndfile1 libsoup2.2-8 libsvg1 libtracker-gtk0 libtrackerclient0 libvisual-0.4-0 libvorbisenc2 libvorbisfile3 libwavpack1 libwpg-0.1-1 libwps-0.1-1 libxalan2-java libxerces2-java libxml2-utils mono-common mono-gac mono-jit mono-runtime nautilus nautilus-cd-burner nautilus-data nautilus-sendto o3read openoffice.org openoffice.org-base openoffice.org-calc openoffice.org-common openoffice.org-core openoffice.org-draw openoffice.org-evolution openoffice.org-gnome openoffice.org-gtk openoffice.org-hyphenation openoffice.org-impress openoffice.org-java-common openoffice.org-math openoffice.org-style-human openoffice.org-writer pkg-config python-bittorrent python-gmenu python-gnome2-extras python-pygtksourceview python-uno rdesktop rhythmbox rss-glx serpentine sound-juicer ssh-askpass-gnome tangerine-icon-theme tomboy totem-mozilla tracker tracker-search-tool tsclient ttf-opensymbol ubuntu-desktop ubuntu-docs ubuntu-sounds usplash-theme-ubuntu vino whois xdg-user-dirs xdg-user-dirs-gtk xsane xsane-common xsltproc yelp

would this command leave me with nothing but command line and drivers? or is this just a really bad idea... or should i use this as a guideline as to what to install/uninstall...so confused. i was thinking about trying puppy linux's iso maker script.

---

