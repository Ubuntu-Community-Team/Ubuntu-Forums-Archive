---
title: "xubuntu questions, oh my gnome..."
date: 2008-03-29
forum: Desktop Environments
---

### Post by kforum on 2008-03-29
alright first thing, xubuntu installs teh bloody gnome too right?

can i remove that 'crap' or do i have to keep, it... i really dont like gnome, even just being in the background.

and also, is there a way to edit mouse options to disable the click funtion on the laptop's mousepad, i really dont like how linux generally doesnt separate regular mouse options from laptop ones...

also, i diddnt find how to change the menu styles(in order to make the menus look something like zenwalk, in design ;) ).

any other tweaks and hits would be lovely too.

i tried searching around in the forums, but everything regarding xubuntu is clumsy and bogus, in my opinion, not to mention scattered. someone should really gather all these questions into stickies.

anyhow, thanks in advanced.

---

### Post by mali2297 on 2008-03-30
> **kforum said:**
> 
can i remove that 'crap' or do i have to keep, it... i really dont like gnome, even just being in the background.

You can remove most things. If you use Synaptic, it will tell which apps that will be removed together with a certain gnome library. Beware so that you don't remove **gksu** or **synaptic**.

> 
and also, is there a way to edit mouse options to disable the click funtion on the laptop's mousepad, i really dont like how linux generally doesnt separate regular mouse options from laptop ones...


You can make the touchpad act as a generic mouse (that is, without double-tap  actions etc) by editing the file /etc/X11/xorg.conf. This is not an ideal solution and might not work for you, but you can try it if you want. 

In the terminal, open the file with the command
```

sudo nano /etc/X11/xorg.conf

```
Look for lines similar to
```

       InputDevice     "Configured Mouse"
       InputDevice     "Synaptics Touchpad"
 
```
in the section "ServerLayout". Comment out the *touchpad* line, that is, put a # in front of it.
```

      InputDevice     "Configured Mouse"
#       InputDevice     "Synaptics Touchpad"

```
Save, quit and restart X.

> 
i tried searching around in the forums, but everything regarding xubuntu is clumsy and bogus, in my opinion, not to mention scattered. someone should really gather all these questions into stickies.

You are welcome to contribute. When you have gathered some useful tweaks, you can for example make a tutorial in the *Tutorials & Tips* forum.

---

### Post by w0ng on 2008-03-30
If you're using Xubuntu Gutsy (7.10), run this command to get rid of all the default Ubuntu GNOME stuff:
```
sudo apt-get remove alacarte aspell bittorrent bluez-cups bluez-gnome bluez-utils bogofilter bogofilter-bdb bogofilter-common brltty brltty-x11 bsh bug-buddy capplets-data cdrdao cli-common compiz compiz-core compiz-fusion-plugins-extra compiz-fusion-plugins-main compiz-gnome compiz-plugins consolekit contact-lookup-applet dcraw deskbar-applet dictionaries-common diveintopython ekiga eog espeak evince evolution evolution-common evolution-data-server evolution-data-server-common evolution-exchange evolution-plugins evolution-webcal f-spot fast-user-switch-applet firefox-gnome-support fping gcj-4.2-base gconf-editor gedit gedit-common gij gij-4.2 gimp-python gnome-about gnome-applets gnome-applets-data gnome-btdownload gnome-control-center gnome-desktop-data gnome-doc-utils gnome-keyring-manager gnome-media gnome-menus gnome-netstatus-applet gnome-nettool gnome-panel gnome-panel-data gnome-pilot gnome-pilot-conduits gnome-power-manager gnome-session gnome-spell gnome-terminal gnome-terminal-data gnome-user-guide gnome-utils gnome-volume-manager gstreamer0.10-alsa gstreamer0.10-esd gstreamer0.10-gnomevfs gstreamer0.10-plugins-base gstreamer0.10-plugins-base-apps gstreamer0.10-plugins-good gstreamer0.10-tools gstreamer0.10-x gthumb gtkhtml3.14 hal-device-manager hwdb-client-common hwdb-client-gnome libalut0 libao2 libart2.0-cil libavc1394-0 libbeagle0 libbluetooth2 libcaca0 libcamel1.2-10 libcdio6 libcompizconfig-backend-gconf libcompizconfig0 libcucul0 libdecoration0 libdeskbar-tracker libdv4 libebook1.2-9 libecal1.2-7 libedata-book1.2-2 libedata-cal1.2-6 libedataserver1.2-9 libedataserverui1.2-8 libeel2-2 libeel2-data libegroupwise1.2-13 libexchange-storage1.2-3 libgcj-bc libgcj-common libgcj8-1 libgconf2.0-cil libgda3-3 libgda3-common libgdl-1-0 libgdl-1-common libgdl-gnome-1-0 libgksu1.2-1 libgksuui1.0-1 libgl1-mesa-dri libglade2.0-cil libglew1.4 libglib2.0-cil libgmime-2.0-2 libgmime2.2-cil libgnome-pilot2 libgnome-vfs2.0-cil libgnome-window-settings1 libgnome2.0-cil libgnomevfs2-bin libgnomevfs2-extra libgpod2 libgsl0 libgtk2.0-cil libgtkhtml2.0-cil libgtkhtml3.14-19 libgtkhtml3.8-15 libgtksourceview2.0-0 libgtksourceview2.0-common libhsqldb-java libicu36 libiec61883-0 libjaxp1.3-java libjline-java liblpint-bonobo0 libmono-cairo1.0-cil libmono-corlib1.0-cil libmono-corlib2.0-cil libmono-data-tds2.0-cil libmono-security2.0-cil libmono-sharpzip2.84-cil libmono-sqlite2.0-cil libmono-system-data2.0-cil libmono-system-web2.0-cil libmono-system1.0-cil libmono-system2.0-cil libmono0 libmono2.0-cil libmtp6 libmusicbrainz4c2a libndesk-dbus-glib1.0-cil libndesk-dbus1.0-cil libneon26 liboil0.3 libopal-2.2 libopenal0a libpam-gnome-keyring libpisock9 libpisync0 libpt-1.10.0 libpt-plugins-alsa libpt-plugins-v4l libpt-plugins-v4l2 librarian0 libraw1394-8 librsvg2.0-cil libservlet2.4-java libshout3 libsndfile1 libsoup2.2-8 libsvg1 libtracker-gtk0 libtrackerclient0 libvisual-0.4-0 libvorbisenc2 libvorbisfile3 libwavpack1 libwpg-0.1-1 libwps-0.1-1 libxalan2-java libxerces2-java libxml2-utils mono-common mono-gac mono-jit mono-runtime nautilus nautilus-cd-burner nautilus-data nautilus-sendto o3read openoffice.org openoffice.org-base openoffice.org-calc openoffice.org-common openoffice.org-core openoffice.org-draw openoffice.org-evolution openoffice.org-gnome openoffice.org-gtk openoffice.org-hyphenation openoffice.org-impress openoffice.org-java-common openoffice.org-math openoffice.org-style-human openoffice.org-writer pkg-config python-bittorrent python-gmenu python-gnome2-extras python-pygtksourceview python-uno rdesktop rhythmbox rss-glx serpentine sound-juicer ssh-askpass-gnome tangerine-icon-theme tomboy totem-mozilla tracker tracker-search-tool tsclient ttf-opensymbol ubuntu-desktop ubuntu-docs ubuntu-sounds usplash-theme-ubuntu vino whois xdg-user-dirs xdg-user-dirs-gtk xsane xsane-common xsltproc yelp && sudo apt-get install xubuntu-desktop
```

From [http://www.psychocats.net/ubuntu/purexfce](http://www.psychocats.net/ubuntu/purexfce)

These blogs have a few nice tips dedicated to xubuntu:
[http://xubuntublog.wordpress.com/](http://xubuntublog.wordpress.com/)
[http://xubuntu.wordpress.com/](http://xubuntu.wordpress.com/)

---

### Post by kforum on 2008-03-30
let me be more specific about something then... there is a gnome session'failsafe'  or whatnot... can i remove that, or change it to a xfce failsafe session?

Or am i always forced to have that bunutu* factor with my Xu?

ps: i ran that command... and it said all those things where -not installed...
its curious though that i do see it loading a gnome session before the xfce... maybe its that failsafe one? maybe...

---

