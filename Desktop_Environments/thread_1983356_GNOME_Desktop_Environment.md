---
title: "GNOME Desktop Environment"
date: 2012-05-20
forum: Desktop Environments
---

### Post by Pudwud on 2012-05-20
I installed the GNOME Desktop environment, with extra components and then deleted it but still get a Debian screen when I boot on my dual boot machine. Any idea on how I can get rid of it?

Thanks.

---

### Post by zombifier25 on 2012-05-20
Debian is an operating system. GNOME is merely a desktop environment for Debian.

---

### Post by lolpenguin on 2012-05-20
It is the GRUB theme. You can change it, but I don't know how.

---

### Post by kansasnoob on 2012-05-20
> **Pudwud said:**
> I installed the GNOME Desktop environment, with extra components and then deleted it but still get a Debian screen when I boot on my dual boot machine. Any idea on how I can get rid of it?

Thanks.

When you install a meta-package like 'gnome' it installs a lot of other dependencies. Like in my Ubuntu 12.04 if I were to install 'gnome' I'd be installing all of this:

> The following NEW packages will be installed:
  binfmt-support bogofilter bogofilter-bdb bogofilter-common
  browser-plugin-gnash cheese cheese-common cli-common ekiga epiphany-browser
  epiphany-browser-data epiphany-extensions evolution evolution-common
  evolution-plugins evolution-webcal fonts-cantarell gdm gedit-plugins gimp
  gimp-data gir1.2-accountsservice-1.0 gir1.2-caribou-1.0 gir1.2-clutter-1.0
  gir1.2-cogl-1.0 gir1.2-coglpango-1.0 gir1.2-folks-0.6
  gir1.2-gdesktopenums-3.0 gir1.2-gee-1.0 gir1.2-gjsdbus-1.0 gir1.2-gkbd-3.0
  gir1.2-gucharmap-2.90 gir1.2-json-1.0 gir1.2-mutter-3.0
  gir1.2-networkmanager-1.0 gir1.2-polkit-1.0 gir1.2-telepathyglib-0.12
  gir1.2-telepathylogger-0.2 gir1.2-upowerglib-1.0 gir1.2-xkl-1.0 gjs glchess
  glines gnash gnash-common gnect gnibbles gnobots2 gnome gnome-backgrounds
  gnome-contacts gnome-core gnome-dictionary gnome-games
  gnome-games-extra-data gnome-icon-theme-extras gnome-icon-theme-full
  gnome-js-common gnome-search-tool gnome-shell gnome-shell-common
  gnome-video-effects gnotravex gnotski gnuchess gnuchess-book gtali
  hamster-applet iagno imagemagick imagemagick-common inkscape
  libappindicator0.1-cil libbabl-0.0-0 libblas3gf libbonobo2-0
  libbonobo2-common libbonoboui2-0 libbonoboui2-common
  libboost-iostreams1.46.1 libboost-program-options1.46.1
  libboost-signals1.46.1 libboost-thread1.46.1 libcapi20-3 libcaribou-common
  libcaribou0 libcdt4 libcheese-gtk21 libcheese3 libclutter-1.0-0
  libclutter-1.0-common libclutter-gst-1.0-0 libclutter-gtk-1.0-0
  libclutter-imcontext-0.1-0 libcluttergesture-0.0.2-0 libcogl-common
  libcogl-pango0 libcogl9 libdbus-glib1.0-cil libdbus1.0-cil libevolution
  libgc1c2 libgconf2.0-cil libgdict-1.0-6 libgdict-common libgdiplus
  libgegl-0.0-0 libgfortran3 libgif4 libgimp2.0 libgjs0c libglade2-0
  libglib2.0-cil libgmime2.6-cil libgnome2-0 libgnomecanvas2-0
  libgnomecanvas2-common libgnomeui-0 libgnomeui-common libgnomevfs2-0
  libgnomevfs2-common libgnomevfs2-extra libgraph4 libgsl0ldbl
  libgtk-vnc-2.0-0 libgtk2.0-cil libgtkhtml-4.0-0 libgtkhtml-4.0-common
  libgtkhtml-editor-4.0-0 libgtkspell0 libgvc5 libgvnc-1.0-0 libilmbase6
  libjavascriptcoregtk-1.0-0 liblapack3gf liblaunchpad-integration1
  liblaunchpad-integration1.0-cil liblqr-1-0 libmagick++4 libmagickcore4
  libmagickcore4-extra libmagickwand4 libmono-addins-gui0.2-cil
  libmono-addins0.2-cil libmono-cairo4.0-cil libmono-corlib4.0-cil
  libmono-i18n-west4.0-cil libmono-i18n4.0-cil libmono-posix4.0-cil
  libmono-security4.0-cil libmono-sharpzip4.84-cil
  libmono-system-configuration4.0-cil libmono-system-core4.0-cil
  libmono-system-drawing4.0-cil libmono-system-security4.0-cil
  libmono-system-xml4.0-cil libmono-system4.0-cil libmozjs185-1.0
  libmusicbrainz4-3 libmutter0 libmx-1.0-2 libnetpbm10 libodbc1 libopal3.10.2
  libopenexr6 libpathplan4 libpst4 libpt2.10.2 libseed-gtk3-0 libunique-1.0-0
  libwebkitgtk-1.0-0 libwebkitgtk-1.0-common libwmf-bin liferea liferea-data
  lightsoff menu menu-xdg mono-4.0-gac mono-gac mono-runtime mutter-common
  netpbm notification-daemon odbcinst odbcinst1debian2 perlmagick
  python-gnome2 python-numpy python-pyorbit python-uniconvertor python-wnck
  quadrapassel rdesktop sound-juicer swell-foop tomboy unixodbc vinagre


But more specific to your question the Debian grub background is in 'desktop-base' so if you remove it:

```
sudo apt-get purge desktop-base
```

Then update the grub configuration:

```
sudo update-grub
```

That might fix that particular issue.

Note: 'desktop-base' doesn't show up in the packages to be installed on my machine if installing 'gnome' because I actually use some components included in that package so it's already installed.

I am curious why you installed 'gnome' :confused:

If we knew exactly what you're trying to achieve maybe we could be more helpful. We should also know exactly what version and flavor of Ubuntu you're running, whether it was an upgrade or a fresh install, etc :)

---

### Post by Pudwud on 2012-05-24
When I upgraded to 11.10 I was having a problem with right mouse functions and I thought that Unity might be the problem.  Things seem to be working better in 12.04.

Two questions:

1.  Can I just do the first step?

2.  I have a dual boot with Windows 7 - will in particular upgrading grub cause me a problem?

Thanks.

---

### Post by kansasnoob on 2012-05-24
Aha! Following up on a PM I now see what you meant.

You must run both commands for the change to take effect. In fact only running the first may make grub puke a bit looking for a nonexistent background image.

---

### Post by Pudwud on 2012-05-24
I trust that it will also not screw up my dual boot? I don't relish the idea of reinstalling Windows and Ubuntu!

Thanks.

Sorry to hear about the trees.

---

### Post by MadmanRB on 2012-05-24
Eh dont mess around with Grub, if it has the Debian theme leave it be, Ubuntu is based on Debian and Debian is one of the oldest and most reliable linux distros.
Its just a branding thing

---

### Post by Pudwud on 2012-05-24
The Debian screen is so ugly!!!

---

### Post by Pudwud on 2012-05-25
It worked!

Thanks.

---

