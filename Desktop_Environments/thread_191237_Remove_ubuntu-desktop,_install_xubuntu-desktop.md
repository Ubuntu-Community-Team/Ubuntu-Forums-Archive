---
title: "Remove ubuntu-desktop, install xubuntu-desktop"
date: 2006-06-07
forum: Desktop Environments
---

### Post by Laurent247 on 2006-06-07
I've got Dapper Drake install and operational. I want to remove the standard gnome-based Ubuntu desktop and replace it with Xubuntu-desktop instead.

Every documentation/information that I have found thus far indicates how to install it from a "server" install of Ubuntu, which has no desktop at all.

Of course I tried "sudo apt-get install xubuntu-desktop". It changed my logon screen, but after that I boot into the same desktop as before.

Furthermore, I'd appreciate if the procedure could also remove unnecessary packages from my previous ubuntu-desktop installation.

I understand it's a meta package merely selecting a bunch of other packages, but I am not faint-hearted, I can manually apt-get remove 50 packages if such is required.

Obviously, if it's too complicated and the sane choice falls back to "backup your data and reinstall", then i'll do that. But I'd rather do it the package-managed way.

Thanks in advance for all inputs and comments.

---

### Post by glotz on 2006-06-07
This applies to Dapper:

You'll need to first uninstall GNOME and then install Xfce. Here are the commands. (source [http://www.psychocats.net/ubuntu/purekde](http://www.psychocats.net/ubuntu/purekde) )

To uninstall GNOME: **sudo apt-get remove alacarte app-install-data-commercial at-spi avahi-daemon bittorrent bluez-pin brltty-x11 bug-buddy capplets-data contact-lookup-applet dbus-1-utils deskbar-applet desktop-base desktop-file-utils ekiga eog esound evince evolution evolution-data-server evolution-exchange evolution-plugins evolution-webcal festival festlex-cmu festlex-poslex festvox-kallpc16k file-roller firefox firefox-gnome-support fping gaim gaim-data gcalctool gconf-editor gconf2 gconf2-common gdb gdebi gdm gedit gedit-common gimp gimp-data gimp-print gimp-python gksu gnome-about gnome-accessibility-themes gnome-app-install gnome-applets gnome-applets-data gnome-btdownload gnome-control-center gnome-cups-manager gnome-desktop-data gnome-doc-utils gnome-games gnome-games-data gnome-icon-theme gnome-keyring gnome-mag gnome-media gnome-menus gnome-mime-data gnome-netstatus-applet gnome-nettool gnome-panel gnome-panel-data gnome-pilot gnome-pilot-conduits gnome-power-manager gnome-screensaver gnome-session gnome-spell gnome-system-monitor gnome-system-tools gnome-terminal gnome-terminal-data gnome-themes gnome-utils gnome-volume-manager gnome2-user-guide gnopernicus gok gstreamer0.10-alsa gstreamer0.10-esd gstreamer0.10-gnomevfs gstreamer0.10-plugins-base gstreamer0.10-plugins-base-apps gstreamer0.10-plugins-good gstreamer0.10-tools gstreamer0.10-x gthumb gtk2-engines-clearlooks gtk2-engines-crux gtk2-engines-highcontrast gtk2-engines-industrial gtk2-engines-lighthouseblue gtk2-engines-mist gtk2-engines-pixbuf gtk2-engines-redmond95 gtk2-engines-smooth gtk2-engines-thinice gtk2-engines-ubuntulooks gtkhtml3.8 gucharmap guile-1.6-libs hal-device-manager hwdb-client im-switch language-selector launchpad-integration libaa1 libatk1.0-0 libatspi1.0-0 libavahi-core4 libavahi-glib1 libavc1394-0 libbeagle0 libbeecrypt6 libbonobo2-0 libbonobo2-common libbonoboui2-0 libbonoboui2-common libbtctl2 libcamel1.2-8 libcdio6 libcompfaceg1 libcroco3 libdaemon0 libdjvulibre15 libdv4 libebook1.2-5 libecal1.2-3 libedata-book1.2-2 libedata-cal1.2-1 libedataserver1.2-7 libedataserverui1.2-6 libeel2-2 libeel2-data libegroupwise1.2-9 libestools1.2 libexchange-storage1.2-1 libgail-common libgail-gnome-module libgail17 libgconf2-4 libgda2-3 libgda2-common libgdl-1-0 libgdl-1-common libgimp2.0 libgksu1.2-1 libgksuui1.0-1 libglade2-0 libglew1 libglib-perl libglib2.0-data libgnome-desktop-2 libgnome-keyring0 libgnome-mag2 libgnome-menu2 libgnome-pilot2 libgnome-speech3 libgnome2-0 libgnome2-canvas-perl libgnome2-common libgnome2-perl libgnome2-vfs-perl libgnomebt0 libgnomecanvas2-0 libgnomecanvas2-common libgnomecups1.0-1 libgnomecupsui1.0-1c2a libgnomeprint2.2-0 libgnomeprint2.2-data libgnomeprintui2.2-0 libgnomeprintui2.2-common libgnomeui-0 libgnomeui-common libgnomevfs2-0 libgnomevfs2-bin libgnomevfs2-common libgnomevfs2-extra libgpod0 libgsf-1-113 libgsf-1-common libgtk2-perl libgtk2.0-0 libgtk2.0-bin libgtk2.0-common libgtkhtml2-0 libgtkhtml3.8-15 libgtksourceview-common libgtksourceview1.0-0 libgtkspell0 libgtop2-7 libgucharmap4 libguile-ltdl-1 libgutenprintui2-1 libkpathsea4 liblaunchpad-integration0 liblircclient0 liblpint-bonobo0 libmetacity0 libnautilus-burn3 libnautilus-extension1 libnotify1 liboil0.3 libopal-2.2.0 libpanel-applet2-0 libpango1.0-0 libpango1.0-common libpisync0 libpoppler1-glib libpt-1.10.0 libpt-plugins-alsa libpt-plugins-v4l libpt-plugins-v4l2 libqthreads-12 librpm4 librsvg2-2 librsvg2-common libsdl1.2debian libsdl1.2debian-alsa libsexy2 libshout3 libsoup2.2-8 libtotem-plparser1 libvte-common libvte4 libwmf0.2-7 libwnck-common libwnck18 libxklavier10 libxml2-utils libxres1 metacity nautilus nautilus-cd-burner nautilus-data nautilus-sendto notification-daemon openoffice.org-evolution openoffice.org-gnome openoffice.org-gtk pkg-config python-glade2 python-gmenu python-gnome2 python-gnome2-desktop python-gnome2-extras python-gst0.10 python-gtk2 python-launchpad-integration python-libxml2 python-vte python2.4-cairo python2.4-glade2 python2.4-gnome2 python2.4-gnome2-desktop python2.4-gnome2-extras python2.4-gobject python2.4-gtk2 rdesktop rhythmbox rpm rss-glx scim scim-gtk2-immodule scim-modules-socket screensaver-default-images serpentine shared-mime-info sharutils sound-juicer ssh-askpass-gnome synaptic system-tools-backends tangerine-icon-theme tango-icon-theme tango-icon-theme-common totem totem-gstreamer tsclient ttf-arphic-ukai ubuntu-artwork ubuntu-desktop ubuntu-docs ubuntu-sounds unattended-upgrades update-manager update-notifier vino vnc-common whois xsane xsane-common xscreensaver xscreensaver-data xscreensaver-gl xsltproc xvncviewer yelp zenity**

To install Xfce **sudo aptitude install xubuntu-desktop**

You'll need to do it in that order.

---

### Post by Cirrocco on 2006-06-07
i recommend copy and paste...lol

---

### Post by bbarrons on 2006-06-07
if you have the space why not leave ubuntu and log into xubuntu. I find that some things are better in gdm than xfce so I bounce between both. You should be able to select which session from the login screen.

---

### Post by Laurent247 on 2006-06-08
Thank you for your prompt and concise responses.

I can't beleive how obvious it was, and how I missed it. I used bbarrons' suggesetion of changing session at the logon screen, which I have never even checked before... :-\" 

Given that this small laptop will probably need the space very soon, I have bookmarked glotz's method for removing everything related to the ubuntu-desktop so that I can do it later on, once space constraints leave me no other choice.

Thank you all :D

---

### Post by aysiu on 2006-06-08
As the author of the Psychocats site, I thought I should mention that if you want to remove Gnome from XFCE and not KDE, you should use this link instead:

[http://www.psychocats.net/ubuntu/purexfce](http://www.psychocats.net/ubuntu/purexfce)

---

### Post by glotz on 2006-06-08
:oops: I was a lazy boy, gotta admit it. Nice going aysiu! I wonder if I can copy those instructions to Ubuntu wiki?

---

### Post by aysiu on 2006-06-08
[QUOTE=glotz]:oops: I was a lazy boy, gotta admit it. Nice going aysiu! I wonder if I can copy those instructions to Ubuntu wiki?[/QUOTE] Sure, go for it.

---

### Post by nightofnih on 2006-06-09
I am wondering if I could use the same command as posted by **glotz** to downgrade from a "Desktop" to a "Server". Here is some background why I want to do this.

I installed Ubuntu 4.10 (a loooong time ago) on my machine. I wanted to use that machine as a samba/FTP/web/TorrentFlux/CVS server, so I never used the desktop features. I had that box booting into the command-line rather than GDM. All worked great, then when Hoary came out, I upgrade to it (dist-upgrade), then upgraded to breezy, and finally to dapper recently (all without any problem). The upgrade notes for all of them insisted that I have ubuntu-desktop meta package installed before the upgrade so the upgrade would go fine. Well, now I am kind of running out of disk space and since I have no use for the X stuff on this box, I want to remove all GUI related things.

---

### Post by glotz on 2006-06-09
The command is from **aysiu** and I think it'd work just fine. On the other hand you might try running both uninstall commands, from [http://www.psychocats.net/ubuntu/purexfce](http://www.psychocats.net/ubuntu/purexfce) and from [http://www.psychocats.net/ubuntu/purekde](http://www.psychocats.net/ubuntu/purekde)

And then possibly get deborphan and remove any oprhaned packages it finds. Also, if you haven't cleared you package manager cache, that'll give you some breathing space!

---

### Post by aysiu on 2006-06-09
In Dapper, there's now a graphical frontend for *deborphan* called *gtkorphan*.

---

### Post by glotz on 2006-06-09
GUIs GUIs GUIs... :)

---

### Post by nightofnih on 2006-06-09
[QUOTE=glotz]The command is from **aysiu** and I think it'd work just fine. On the other hand you might try running both uninstall commands, from [http://www.psychocats.net/ubuntu/purexfce](http://www.psychocats.net/ubuntu/purexfce) and from [http://www.psychocats.net/ubuntu/purekde](http://www.psychocats.net/ubuntu/purekde)

And then possibly get deborphan and remove any oprhaned packages it finds. Also, if you haven't cleared you package manager cache, that'll give you some breathing space![/QUOTE]

Well thanks both to **glotz **and **aysiu **for posting the commands and links. I ran them and guess what - they worked - all gui related package are now gone ... I have gained ~1 GB. But along the way bunch of other packages are gone as well 8-[ - I think because they were probably dependencies of some of the packages that were meant to be removed. All of the php packages are gone (needed them for TorrentFlux). Also mysql clinet/server was uninstalled as well along with some SSL packages. Now I have to get all of them installed to get my stuff working.  I guess from now on - I'll probably only install stuff through aptitude as it seems to handle dependencies better.

---

### Post by glotz on 2006-06-09
That's a very good idea. Did you flush that packman cache and dump the orphans?

---

