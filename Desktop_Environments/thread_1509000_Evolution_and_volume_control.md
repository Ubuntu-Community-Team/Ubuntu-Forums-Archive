---
title: "Evolution and volume control"
date: 2010-06-13
forum: Desktop Environments
---

### Post by slash86 on 2010-06-13
Is it possible to remove evolution notification icon and stay only with volume control?

I appreciate the effort made to integrate everything in 10.04, but it is not a really nice feature to me, since i do not like empathy and i hate evolution. I think ubuntu should put more effort in freedom and less effort in making people all obliged to use the same apps.

---

### Post by bigsmitty64 on 2010-06-13
Ya that does stink huh? Unfortunately the only fix I have found is to remove that set up from the panel, then go to system/preferences/sound, and drag that (sound) to the panel. It works fine for me. When you click it, you get the whole sound properties box,Hope this helps at all :)

---

### Post by slash86 on 2010-06-13
Yeah, this is an option... To me:

integration == less freedom

they are kind of forcing us to use their favorite or sponsored software. i really don't think it is nice.

---

### Post by garvinrick4 on 2010-06-13
```
Here is what comes with evolution: Better to just ignore it I imagine.

rick@rick-laptop:~$ aptitude show evolution
Package: evolution
State: installed
Automatically installed: no
Version: 2.30.1.2-3ubuntu1
Priority: optional
Section: gnome
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 1,278k
Depends: libart-2.0-2 (>= 2.3.18), libatk1.0-0 (>= 1.29.3), libc6 (>= 2.7),
         libcairo2 (>= 1.2.4), libcamel1.2-14 (>= 2.30.1), libcamel1.2-14 (<
         2.31), libcanberra-gtk0 (>= 0.2), libcanberra0 (>= 0.2), libdbus-1-3
         (>= 1.0.2), libdbus-glib-1-2 (>= 0.78), libebackend1.2-0 (>= 2.30.1),
         libebook1.2-9 (>= 2.30.1), libecal1.2-7 (>= 2.30.1),
         libedataserver1.2-11 (>= 2.30.1), libedataserverui1.2-8 (>= 2.30.1),
         libegroupwise1.2-13 (>= 2.30.1), libenchant1c2a (>= 1.6), libevolution
         (>= 2.30.1.2), libfontconfig1 (>= 2.8.0), libfreetype6 (>= 2.2.1),
         libgconf2-4 (>= 2.27.0), libgdata-google1.2-1 (>= 2.30.1),
         libgdata1.2-1 (>= 2.30.1), libglib2.0-0 (>= 2.22.0),
         libgnome-desktop-2-17 (>= 1:2.29.92), libgnomecanvas2-0 (>= 2.11.1),
         libgtk2.0-0 (>= 2.20.0), libgtkhtml-editor0 (>= 1:3.30.1),
         libgtkhtml-editor0 (< 1:3.31), libgtkhtml3.14-19 (>= 1:3.30.1),
         libgtkhtml3.14-19 (< 1:3.31), libgweather1 (>= 2.28.0), libical0 (>=
         0.42), libice6 (>= 1:1.0.0), liblaunchpad-integration1 (>= 0.1.17),
         libnotify1 (>= 0.4.5), libnotify1-gtk2.10, libnspr4-0d (>=
         4.7.3-0ubuntu1~), libnss3-1d (>= 3.12.2~rc1), libpango1.0-0 (>=
         1.14.0), libsm6, libsoup2.4-1 (>= 2.24.3), libsqlite3-0 (>= 3.6.23.1),
         libstartup-notification0 (>= 0.10), libunique-1.0-0 (>= 1.0.0), libxml2
         (>= 2.7.4), zlib1g (>= 1:1.1.4), gconf2 (>= 2.28.1-2), evolution-common
         (= 2.30.1.2-3ubuntu1), evolution-data-server (>= 2.30.1),
         evolution-data-server (< 2.31), gnome-icon-theme (>= 2.19.92), dbus
Recommends: gnome-desktop-data, evolution-plugins, evolution-webcal, yelp,
            bogofilter | spamassassin
Suggests: bug-buddy, gnupg, network-manager, evolution-exchange, evolution-dbg,
          evolution-plugins-experimental
Provides: imap-client, mail-reader
Description: groupware suite with mail client and organizer
 Evolution is a groupware suite which integrates mail, calendar, address book,
 to-do list and memo tools. 
 
 Additional features include integration with Exchange and Groupwise servers,
 newsgroup client, LDAP support, web calendars and synchronization with Palm
 devices. 
 
 Evolution is a graphical application that is part of GNOME, and is distributed
 by Novell, Inc. 
 
 See http://www.novell.com/products/evolution/ for more information. 
 
 The following plugins belonging to the "base" set are included. 
 * calendar-file 
 * calendar-http 
 * calendar-weather 
 * email-custom-headers 
 * itip-formatter 
 * plugin-manager 
 * python 
 * default-source 
 * addressbook-file 
 * startup-wizard 
 * mark-all-read 
 * groupwise-features 
 * groupwise-account-setup 
 * mail-account-disable 
 * publish-calendar 
 * caldav 
 * imap-features 
 * google-account-setup 
 * sa-junk-plugin 
 * bogo-junk-plugin 
 * mono 
 * webdav-account-setup
Homepage: http://www.gnome.org/projects/evolution/

```
rick@rick-laptop:~$

---

### Post by slash86 on 2010-06-13
evolution depends on everything you pasted...
i do not see any reason to obligue users to use it, adding it as default in gnome user interface...

---

