---
title: "Installing vim-full without Gnome"
date: 2009-05-18
forum: General Help
---

### Post by dmccarney on 2009-05-18
Hello,

I'm running a headless server (i.e. X and a window manager are not installed.) and I would like to install the vim-full package. 

It seems to be the only way I can get the *:syntax* feature for syntax highlighting to work.

Unfortunately, when I install vim-full it also includes the GUI frontend for Vim and thus a TON of Gnome/GUI related packages that I don't want.

Is there an easier way to do this?

Thanks,

- Dan

```
The following NEW packages will be installed:
  aspell aspell-en busybox console-common console-data dbus dbus-x11 dictionaries-common eject
  esound-clients esound-common gconf2 gconf2-common gnome-keyring gnome-mime-data gnome-mount
  hal hal-info hicolor-icon-theme initramfs-tools kbd klibc-utils libart-2.0-2 libaspell15
  libatk1.0-0 libatk1.0-data libaudiofile0 libavahi-client3 libavahi-common-data
  libavahi-common3 libavahi-glib1 libbonobo2-0 libbonobo2-common libbonoboui2-0
  libbonoboui2-common libcups2 libdbus-1-3 libdbus-glib-1-2 libdirectfb-extra libeel2-2.20
  libeel2-data libenchant1c2a libesd0 libgail-common libgail18 libgconf2-4 libglade2-0
  libgnome-keyring0 libgnome-menu2 libgnome2-0 libgnome2-common libgnomecanvas2-0
  libgnomecanvas2-common libgnomeui-0 libgnomeui-common libgnomevfs2-0 libgnomevfs2-common
  libgnomevfs2-extra libgpm2 libgtk2.0-0 libgtk2.0-bin libgtk2.0-common libhal-storage1 libhal1
  libhunspell-1.2-0 libice6 libidl0 libjpeg62 libklibc libmalaga7 libnautilus-extension1
  libnotify1 liborbit2 libpam-gnome-keyring libpci3 libperl5.10 libruby1.8 libsexy2 libsm6
  libsmbclient libsmbios-bin libsmbios2 libsplashy1 libstartup-notification0 libtalloc1 libtiff4
  libvoikko1 libvolume-id0 libwbclient0 libwnck-common libwnck22 libx86-1 libxcomposite1
  libxcursor1 libxdamage1 libxfixes3 libxi6 libxinerama1 libxrandr2 libxres1 libxt6
  myspell-en-us notification-daemon pciutils pm-utils powermgmt-base radeontool shared-mime-info
  tcl8.4 udev usbutils uswsusp vbetool vim-full vim-gnome vim-gui-common
```

---

### Post by jcampbell1 on 2009-06-10
I am having the same issue.  I just ended up install all of that crap on my server.  Doesn't seem to cause any major issues.  It would be nice if there was a vim-full-server package.

---

### Post by Brandon Williams on 2009-06-10
I think that the package you want is vim-nox. The description of vim-full in Jaunty indicates that it is just a transitional package from the old name vim-full to the new name vim-gnome. The vim-nox package has all the scripting support without the GUI.

---

### Post by sdennie on 2009-06-10
The only thing you need to get syntax highlighting to work is the vim package (as opposed to the default vim-tiny):

```

sudo apt-get install vim

```

That will also grab vim-runtime and after that, ":syntax on" should work fine and you won't need all the gnome dependencies.

---

### Post by bodhi.zazen on 2009-06-10
> **sdennie said:**
> The only thing you need to get syntax highlighting to work is the vim package (as opposed to the default vim-tiny):

```

sudo apt-get install vim

```That will also grab vim-runtime and after that, ":syntax on" should work fine and you won't need all the gnome dependencies.

I fully support this information.

---

### Post by ibuclaw on 2009-06-10
Don't forget to put:
```
syntax on
```
In your **~/.vimrc** file if you don't want to have to input it ever time you open a new file. ;)

---

### Post by bodhi.zazen on 2009-06-10
Shhh , don't tell tinivole ...

apt-get install vim automagically turns on syntax highlighting.

---

### Post by ikislav on 2009-11-16
Hello... I'm completely new to Linux and Ubuntu so I need someone to hold my hand :)
My question is: If I install Vim with "sudo apt-get install vim", will the old vim-tiny remain on the system, or will it be upgraded, or will it be deleted? My main concern here is if that operation will make some junk on my system.

---

### Post by bodhi.zazen on 2009-11-16
I believe it will leave it.

As the old adage goes, Linux is not Windows and we do not have as many problems with "junk".

If you wish, see :

[http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html](http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html)

---

