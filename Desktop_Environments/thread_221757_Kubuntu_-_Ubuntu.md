---
title: "Kubuntu - Ubuntu?"
date: 2006-07-24
forum: Desktop Environments
---

### Post by shane2peru on 2006-07-24
Ok, I did a base install some time ago of Ubuntu Dapper.  A clean installation.  I have played around with a few of the desktops and like the KDE programs a little better.  I was going to go pure KDE.  So I followed the directions in this link: [HOWTO: correctly install/remove desktops]("http://www.ubuntuforums.org/showthread.php?t=205002&highlight=ubuntu-desktop+packages") and it always ends up with a problem with installations.  I'm not able to install anything.  It always gives me an error of some scim thing, that I don't understand.  I have tried to completely remove ubuntu-desktop and afterwards I get the error.  I have to re-install ubuntu-desktop before I can do any other installations.  Help.  Do I have to do a complete reinstall with Kubuntu in order to get a true Ubuntu - KDE destop without using the space for Gnome to?  Thanks.

Shane

---

### Post by jISh on 2006-07-24
You can have both GNOME and KDE installed at the same time. You're going to have to tell us your error before you proceed any further.

---

### Post by brainformat on 2006-07-24
you can install it using synaptic.

---

### Post by aysiu on 2006-07-24
Can you post this "scim error"? What's the exact output (copy and paste the text) of this command? ```
sudo aptitude remove ubuntu-desktop
```

You may also want to take a look at this:
[http://www.psychocats.net/ubuntu/purekde](http://www.psychocats.net/ubuntu/purekde)

---

### Post by jrev on 2006-07-24
I cannot see the point to install two desktops on the same computer.
Unless you are looking for troubles.:confused:

---

### Post by aysiu on 2006-07-24
> **jrev said:**
> I cannot see the point to install two desktops on the same computer.
Unless you are looking for troubles.:confused:
I have three installed on one computer and no troubles at all.

---

### Post by shane2peru on 2006-07-24
> **aysiu said:**
> Can you post this "scim error"? What's the exact output (copy and paste the text) of this command? ```
sudo aptitude remove ubuntu-desktop
```

You may also want to take a look at this:
[http://www.psychocats.net/ubuntu/purekde](http://www.psychocats.net/ubuntu/purekde)

That is the link that got me into trouble.  I'm uninstalling ubuntu-desktop again for the 3rd time.  I will paste the error I get when I'm done.  By the way, I don't want 3 or 2 desktops, I just want KDE without having to re-install.  I don't like having 2 desktops because my menus are a mess, and I end up running Gnome apps in KDE and visa versa.  I don't know what goes with what most of the time, and I know they don't play well together.  There are always glitches, and programs crash/lock up.  I will post in a minute and let you know about the error.  Thanks for the feedback!

Shane

---

### Post by shane2peru on 2006-07-24
Ok, no errors now.  I kept trying to run this command:```
sudo apt-get remove alacarte app-install-data-commercial at-spi avahi-daemon bittorrent bluez-pin brltty-x11 bug-buddy capplets-data contact-lookup-applet dbus-1-utils deskbar-applet desktop-base desktop-file-utils ekiga eog esound evince evolution evolution-data-server evolution-exchange evolution-plugins evolution-webcal festival festlex-cmu festlex-poslex festvox-kallpc16k file-roller firefox firefox-gnome-support fping gaim gaim-data gcalctool gconf-editor gconf2 gconf2-common gdb gdebi gdm gedit gedit-common gimp gimp-data gimp-print gimp-python gksu gnome-about gnome-accessibility-themes gnome-app-install gnome-applets gnome-applets-data gnome-btdownload gnome-control-center gnome-cups-manager gnome-desktop-data gnome-doc-utils gnome-games gnome-games-data gnome-icon-theme gnome-keyring gnome-mag gnome-media gnome-menus gnome-mime-data gnome-netstatus-applet gnome-nettool gnome-panel gnome-panel-data gnome-pilot gnome-pilot-conduits gnome-power-manager gnome-screensaver gnome-session gnome-spell gnome-system-monitor gnome-system-tools gnome-terminal gnome-terminal-data gnome-themes gnome-utils gnome-volume-manager gnome2-user-guide gnopernicus gok gstreamer0.10-alsa gstreamer0.10-esd gstreamer0.10-gnomevfs gstreamer0.10-plugins-base gstreamer0.10-plugins-base-apps gstreamer0.10-plugins-good gstreamer0.10-tools gstreamer0.10-x gthumb gtk2-engines-clearlooks gtk2-engines-crux gtk2-engines-highcontrast gtk2-engines-industrial gtk2-engines-lighthouseblue gtk2-engines-mist gtk2-engines-pixbuf gtk2-engines-redmond95 gtk2-engines-smooth gtk2-engines-thinice gtk2-engines-ubuntulooks gtkhtml3.8 gucharmap guile-1.6-libs hal-device-manager hwdb-client im-switch language-selector launchpad-integration libaa1 libatk1.0-0 libatspi1.0-0 libavahi-core4 libavahi-glib1 libavc1394-0 libbeagle0 libbeecrypt6 libbonobo2-0 libbonobo2-common libbonoboui2-0 libbonoboui2-common libbtctl2 libcamel1.2-8 libcdio6 libcompfaceg1 libcroco3 libdaemon0 libdjvulibre15 libdv4 libebook1.2-5 libecal1.2-3 libedata-book1.2-2 libedata-cal1.2-1 libedataserver1.2-7 libedataserverui1.2-6 libeel2-2 libeel2-data libegroupwise1.2-9 libestools1.2 libexchange-storage1.2-1 libgail-common libgail-gnome-module libgail17 libgconf2-4 libgda2-3 libgda2-common libgdl-1-0 libgdl-1-common libgimp2.0 libgksu1.2-1 libgksuui1.0-1 libglade2-0 libglew1 libglib-perl libglib2.0-data libgnome-desktop-2 libgnome-keyring0 libgnome-mag2 libgnome-menu2 libgnome-pilot2 libgnome-speech3 libgnome2-0 libgnome2-canvas-perl libgnome2-common libgnome2-perl libgnome2-vfs-perl libgnomebt0 libgnomecanvas2-0 libgnomecanvas2-common libgnomecups1.0-1 libgnomecupsui1.0-1c2a libgnomeprint2.2-0 libgnomeprint2.2-data libgnomeprintui2.2-0 libgnomeprintui2.2-common libgnomeui-0 libgnomeui-common libgnomevfs2-0 libgnomevfs2-bin libgnomevfs2-common libgnomevfs2-extra libgpod0 libgsf-1-113 libgsf-1-common libgtk2-perl libgtk2.0-0 libgtk2.0-bin libgtk2.0-common libgtkhtml2-0 libgtkhtml3.8-15 libgtksourceview-common libgtksourceview1.0-0 libgtkspell0 libgtop2-7 libgucharmap4 libguile-ltdl-1 libgutenprintui2-1 libkpathsea4 liblaunchpad-integration0 liblircclient0 liblpint-bonobo0 libmetacity0 libnautilus-burn3 libnautilus-extension1 libnotify1 liboil0.3 libopal-2.2.0 libpanel-applet2-0 libpango1.0-0 libpango1.0-common libpisync0 libpoppler1-glib libpt-1.10.0 libpt-plugins-alsa libpt-plugins-v4l libpt-plugins-v4l2 libqthreads-12 librpm4 librsvg2-2 librsvg2-common libsdl1.2debian libsdl1.2debian-alsa libsexy2 libshout3 libsoup2.2-8 libtotem-plparser1 libvte-common libvte4 libwmf0.2-7 libwnck-common libwnck18 libxklavier10 libxml2-utils libxres1 metacity nautilus nautilus-cd-burner nautilus-data nautilus-sendto notification-daemon openoffice.org-evolution openoffice.org-gnome openoffice.org-gtk pkg-config python-glade2 python-gmenu python-gnome2 python-gnome2-desktop python-gnome2-extras python-gst0.10 python-gtk2 python-launchpad-integration python-libxml2 python-vte python2.4-cairo python2.4-glade2 python2.4-gnome2 python2.4-gnome2-desktop python2.4-gnome2-extras python2.4-gobject python2.4-gtk2 rdesktop rhythmbox rpm rss-glx scim scim-gtk2-immodule scim-modules-socket screensaver-default-images serpentine shared-mime-info sharutils sound-juicer ssh-askpass-gnome synaptic system-tools-backends tangerine-icon-theme tango-icon-theme tango-icon-theme-common totem totem-gstreamer tsclient ttf-arphic-ukai ubuntu-artwork ubuntu-desktop ubuntu-docs ubuntu-sounds unattended-upgrades update-manager update-notifier vino vnc-common whois xsane xsane-common xscreensaver xscreensaver-data xscreensaver-gl xsltproc xvncviewer yelp zenity
```  And that is what would bring up the error after I ran that, and tried to install something.  I was trying to save all the space I could save, that is what made me think that that was the command to use.  When I just used ```
sudo aptitude remove ubuntu-desktop
``` I don't get the error after running this command and then installing/uninstalling other things.  However some things are left there.  I noticed the a-la-carte menu editor was still installed (according to adept).  I would like to just run KDE, so I don't keep switching over to Gnome, and save all the space I can.

Shane

---

### Post by aysiu on 2006-07-24
What is the error you're getting? Can you copy and paste it here?

---

### Post by shane2peru on 2006-07-24
> **aysiu said:**
> What is the error you're getting? Can you copy and paste it here?

Sorry aysiu, I'm not getting the errors now.  It was when I ran that command that I refered to above.  It had to do with the scim package being broken.  It refused to install or uninstall anything but the ubuntu-desktop.  I had to re-install the ubuntu-desktop again to get it to work properly.  If you are really interested I could try and re-create the problem, and post the error, however it is rather time consuming since it takes about 30 minutes to run that command, - the very long one from the psycocats page - pure KDE.  If that is your page (or a friend of yours), and you are interested in the error, I will do it, let me know.  Thanks for all the help.

Shane

---

### Post by aysiu on 2006-07-24
If the problem is fixed, I don't need to know the error, but I'm curious as to why that command takes 30 minutes to run... don't you just copy and paste the text into the terminal? Please tell me you don't retype every single package name out by hand.

---

### Post by shane2peru on 2006-07-24
No, I don't type that fast! :D   It takes that long to completely install and uninstall ubuntu-desktop via apt, I'm wireless, and don't have the fastest DSL here in Peru!  Thanks for the help.

Shane

---

### Post by aysiu on 2006-07-24
Phew. That's good to know.

---

