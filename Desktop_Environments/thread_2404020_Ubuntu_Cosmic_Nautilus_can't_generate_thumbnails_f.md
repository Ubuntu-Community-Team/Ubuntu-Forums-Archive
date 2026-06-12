---
title: "Ubuntu Cosmic: Nautilus can't generate thumbnails for any file"
date: 2018-10-18
forum: Desktop Environments
---

### Post by manmath on 2018-10-18
Nautilus can't create thumbnails for images, pdfs, videos, etc. I installed Cosmic with minimal cd image and then installed necessary applications with "--no-install-recommends" option. So, I guess it's missing some packages. Also, I checked nautilus preferences. It's set to always show thumbnail for files below 4GB. Please have a look at all my installed packages (Here is the list of packages:  [ATTACH]281389[/ATTACH] and suggest if it's missing a package related to thumbnail generation.

Update:

Out of curiosity I ran nautilus as the root user, surprising nautilus showed thumbnails of all the files. But with normal user privileges nautilus can't display thumbnails.

---

### Post by dino99 on 2018-10-19
check that libgdk-pixbuf2.0-bin is installed

---

### Post by manmath on 2018-10-19
Yes, it's been installed. Please have a look at the list of packages:  [ATTACH]281389[/ATTACH], and suggest me if I'm missing any other packages.

Update:

Out of curiosity I ran nautilus as the root user, surprising nautilus showed thumbnails of all the files. But with normal user privileges nautilus can't display thumbnails.

---

### Post by Claus7 on 2018-10-19
Hello,

I'm checking nautilus under lubuntu. The packages compared are those named: nautilus, Files. The number of your packages exceeds mine. Could you please check the permissions you have in your home folder?

Regards!

---

### Post by manmath on 2018-10-19
> **Claus7 said:**
> Hello,

Could you please check the permissions you have in your home folder?

Regards!

Thank you, but how do I do that? Please suggest.

Update:
Out of curiosity I ran nautilus as the root user, surprising nautilus showed thumbnails of all the files. But with normal user privileges nautilus can't display thumbnails.

---

### Post by Claus7 on 2018-10-19
Hello,

open a terminal ([https://linuxconfig.org/how-to-open-a-terminal-on-ubuntu-bionic-beaver-18-04-linux](https://linuxconfig.org/how-to-open-a-terminal-on-ubuntu-bionic-beaver-18-04-linux)) and then type:
cd ../

and then post the output of:
ls -l

Regards!

---

### Post by manmath on 2018-10-19
Here's the list of permissions in my home folder:

> 
manmath@manmath-H61M-DS2:/home$ ls -al
total 28
drwxr-xr-x  4 root    root     4096 Oct 14 04:49 .
drwxr-xr-x 23 root    root     4096 Oct 14 08:03 ..
drwx------  2 root    root    16384 Sep 11 15:28 lost+found
drwxr-xr-x 18 manmath manmath  4096 Oct 19 14:43 manmath
manmath@manmath-H61M-DS2:/home$ cd manmath/
manmath@manmath-H61M-DS2:~$ ls -al
total 120
drwxr-xr-x 18 manmath manmath  4096 Oct 19 14:43 .
drwxr-xr-x  4 root    root     4096 Oct 14 04:49 ..
-rw-r--r--  1 manmath manmath   220 Oct 14 03:01 .bash_logout
-rw-r--r--  1 manmath manmath  3771 Oct 14 03:01 .bashrc
drwxr-xr-x 16 manmath manmath  4096 Oct 19 11:22 .cache
drwx------ 27 manmath manmath  4096 Oct 19 14:34 .config
drwxr-xr-x  2 manmath manmath  4096 Oct 14 05:24 Desktop
-rw-r--r--  1 manmath manmath    43 Oct 18 12:15 .dmrc
drwxr-xr-x  5 manmath manmath  4096 Oct 18 12:18 Documents
drwxr-xr-x  5 manmath manmath  4096 Oct 19 14:58 Downloads
drwx------  3 manmath manmath  4096 Oct 14 03:07 .gnupg
-rw-------  1 manmath manmath 16674 Oct 19 13:23 .ICEauthority
drwxrwxr-x  2 manmath manmath  4096 Oct 14 05:35 .icons
drwxr-xr-x  2 manmath manmath  4096 Oct 19 07:18 ielt
drwxrwxr-x  4 manmath manmath  4096 Oct 14 04:51 .kingsoft
drwx------  3 manmath manmath  4096 Oct 14 03:07 .local
drwx------  5 manmath manmath  4096 Sep 11 11:41 .mozilla
drwxr-xr-x 22 manmath manmath  4096 Oct 14 05:58 Music
drwxr-xr-x  5 manmath manmath  4096 Oct 18 15:43 Pictures
drwx------  3 manmath manmath  4096 Oct 14 07:13 .pki
-rw-r--r--  1 manmath manmath   807 Oct 14 03:01 .profile
-rw-r--r--  1 manmath manmath     0 Oct 14 03:13 .sudo_as_admin_successful
drwxrwxr-x  2 manmath manmath  4096 Oct 14 05:35 .themes
drwxr-xr-x  5 manmath manmath  4096 Oct 19 08:49 Videos
-rw-------  1 manmath manmath    61 Oct 19 13:23 .Xauthority
-rw-rw-r--  1 manmath manmath   131 Oct 14 06:44 .xinputrc

The username is manmath

Update:
Out of curiosity I ran nautilus as the root user, surprising nautilus showed thumbnails of all the files. But with normal user privileges nautilus can't display thumbnails.

---

### Post by Claus7 on 2018-10-19
Hello,

your permissions seem fine. Could you try also this:
[https://askubuntu.com/questions/211843/why-i-cant-see-the-thumbnails-in-nautilus](https://askubuntu.com/questions/211843/why-i-cant-see-the-thumbnails-in-nautilus)

Regards!

---

### Post by manmath on 2018-10-19
Tried, did not work in my case.

Here's some more info that may help you figure out what might have gone wrong:

Installed packages related to thumbnail generation:

gir1.2-gdkpixbuf-2.0
libgdk-pixbuf2.0-0
libgdk-pixbuf2.0-bin
libgdk-pixbuf2.0-common
chromium-codecs-ffmpeg-extra
ffmpeg
ffmpegthumbnailer
libffmpegthumbnailer4v5
gir1.2-nautilus-3.0
libnautilus-extension1a
nautilus
nautilus-data
gir1.2-gstreamer-1.0
gstreamer1.0-alsa
gstreamer1.0-clutter-3.0
gstreamer1.0-gl
gstreamer1.0-gtk3
gstreamer1.0-libav
gstreamer1.0-plugins-base
gstreamer1.0-plugins-good
gstreamer1.0-plugins-ugly
gstreamer1.0-pulseaudio
gstreamer1.0-tools
gstreamer1.0-x
libgstreamer-gl1.0-0
libgstreamer-plugins-base1.0-0
libgstreamer-plugins-good1.0-0
libgstreamer1.0-0
gir1.2-gnomedesktop-3.0
gnome-calculator
gnome-control-center
gnome-control-center-data
gnome-desktop3-data
gnome-disk-utility
gnome-flashback
gnome-flashback-common
gnome-menus
gnome-mpv
gnome-panel
gnome-panel-data
gnome-screensaver
gnome-screenshot
gnome-session-bin
gnome-session-canberra
gnome-session-common
gnome-session-flashback
gnome-settings-daemon
gnome-settings-daemon-schemas
gnome-sound-recorder
gnome-startup-applications
gnome-terminal
gnome-terminal-data
gnome-video-effects
language-selector-gnome
libgnome-autoar-0-0
libgnome-bluetooth13
libgnome-desktop-3-17
libgnome-menu-3-0
libsoup-gnome2.4-1
network-manager-gnome
pinentry-gnome3
policykit-1-gnome
ubuntu-gnome-default-settings

Thumbnail configuration files:

manmath@manmath-H61M-DS2:/usr/share/thumbnailers$ ls
evince.thumbnailer  ffmpegthumbnailer.thumbnailer  gdk-pixbuf-thumbnailer.thumbnailer  librsvg.thumbnailer  totem.thumbnailer
manmath@manmath-H61M-DS2:/usr/share/thumbnailers$ cat *
[Thumbnailer Entry]
TryExec=evince-thumbnailer
Exec=evince-thumbnailer -s %s %u %o
MimeType=application/pdf;application/x-bzpdf;application/x-gzpdf;application/x-xzpdf;application/x-ext-pdf;application/postscript;application/x-bzpostscript;application/x-gzpostscript;image/x-eps;image/x-bzeps;image/x-gzeps;application/x-ext-ps;application/x-ext-eps;application/illustrator;application/x-dvi;application/x-bzdvi;application/x-gzdvi;application/x-ext-dvi;image/vnd.djvu+multipage;application/x-ext-djv;application/x-ext-djvu;image/tiff;application/x-cbr;application/x-cbz;application/x-cb7;application/x-cbt;application/x-ext-cbr;application/x-ext-cbz;application/x-ext-cb7;application/x-ext-cbt;application/vnd.comicbook+zip;application/vnd.comicbook-rar;application/oxps;application/vnd.ms-xpsdocument
[Thumbnailer Entry]
TryExec=ffmpegthumbnailer
Exec=ffmpegthumbnailer -i %i -o %o -s %s -f
MimeType=video/jpeg;video/mp4;video/mpeg;video/quicktime;video/x-ms-asf;video/x-ms-wm;video/x-ms-wmv;video/x-msvideo;video/x-flv;video/x-matroska;video/webm;video/mp2t;
[Thumbnailer Entry]
TryExec=/usr/bin/gdk-pixbuf-thumbnailer
Exec=/usr/bin/gdk-pixbuf-thumbnailer -s %s %u %o
MimeType=image/png;image/bmp;image/x-bmp;image/x-MS-bmp;image/gif;image/x-icon;image/x-ico;image/x-win-bitmap;image/vnd.microsoft.icon;application/ico;image/ico;image/icon;text/ico;application/x-navi-animation;image/jpeg;image/x-portable-anymap;image/x-portable-bitmap;image/x-portable-graymap;image/x-portable-pixmap;image/tiff;image/x-xpixmap;image/x-xbitmap;image/x-tga;image/x-icns;image/x-quicktime;image/qtif;
[Thumbnailer Entry]
TryExec=/usr/bin/gdk-pixbuf-thumbnailer
Exec=/usr/bin/gdk-pixbuf-thumbnailer -s %s %u %o
MimeType=image/svg+xml;image/svg+xml-compressed;
[Thumbnailer Entry]
TryExec=/usr/bin/totem-video-thumbnailer
Exec=/usr/bin/totem-video-thumbnailer -s %s %u %o
MimeType=application/mxf;application/ogg;application/ram;application/sdp;application/vnd.apple.mpegurl;application/vnd.ms-asf;application/vnd.ms-wpl;application/vnd.rn-realmedia;application/vnd.rn-realmedia-vbr;application/x-extension-m4a;application/x-extension-mp4;application/x-flash-video;application/x-matroska;application/x-netshow-channel;application/x-ogg;application/x-quicktimeplayer;application/x-shorten;image/vnd.rn-realpix;image/x-pict;misc/ultravox;text/x-google-video-pointer;video/3gp;video/3gpp;video/3gpp2;video/dv;video/divx;video/fli;video/flv;video/mp2t;video/mp4;video/mp4v-es;video/mpeg;video/mpeg-system;video/msvideo;video/ogg;video/quicktime;video/vivo;video/vnd.divx;video/vnd.mpegurl;video/vnd.rn-realvideo;video/vnd.vivo;video/webm;video/x-anim;video/x-avi;video/x-flc;video/x-fli;video/x-flic;video/x-flv;video/x-m4v;video/x-matroska;video/x-mjpeg;video/x-mpeg;video/x-mpeg2;video/x-ms-asf;video/x-ms-asf-plugin;video/x-ms-asx;video/x-msvideo;video/x-ms-wm;video/x-ms-wmv;video/x-ms-wmx;video/x-ms-wvx;video/x-nsv;video/x-ogm+ogg;video/x-theora;video/x-theora+ogg;video/x-totem-stream;audio/x-pn-realaudio;audio/3gpp;audio/3gpp2;audio/aac;audio/ac3;audio/AMR;audio/AMR-WB;audio/basic;audio/dv;audio/eac3;audio/flac;audio/m4a;audio/midi;audio/mp1;audio/mp2;audio/mp3;audio/mp4;audio/mpeg;audio/mpg;audio/ogg;audio/opus;audio/prs.sid;audio/scpls;audio/vnd.rn-realaudio;audio/wav;audio/webm;audio/x-aac;audio/x-aiff;audio/x-ape;audio/x-flac;audio/x-gsm;audio/x-it;audio/x-m4a;audio/x-m4b;audio/x-matroska;audio/x-mod;audio/x-mp1;audio/x-mp2;audio/x-mp3;audio/x-mpg;audio/x-mpeg;audio/x-ms-asf;audio/x-ms-asx;audio/x-ms-wax;audio/x-ms-wma;audio/x-musepack;audio/x-opus+ogg;audio/x-pn-aiff;audio/x-pn-au;audio/x-pn-wav;audio/x-pn-windows-acm;audio/x-realaudio;audio/x-real-audio;audio/x-s3m;audio/x-sbc;audio/x-shorten;audio/x-speex;audio/x-stm;audio/x-tta;audio/x-wav;audio/x-wavpack;audio/x-vorbis;audio/x-vorbis+ogg;audio/x-xm;application/x-flac;

Startup applications:
 - Files
 - Gnome settings daemon's media-keys plugin
 - Gnome settings daemon's xsettings plugin
 - Indicator messages
 - Network (Gnome Flashback)
 - Pulseaudio sound system
 - Screensaver (Gnome Flashback)

Thumbnail cache directory permissions:

manmath@manmath-H61M-DS2:~$ cd .cache/
[email]manmath@manmath-H61M-DS2:~/.cache[/email]$ ls -l
total 76
drwx------  2 manmath manmath  4096 Oct 17 08:46 babl
drwx------  3 manmath manmath  4096 Oct 14 07:13 chromium
-rw-r--r--  1 manmath manmath  8192 Oct 18 15:26 event-sound-cache.tdb.5b12201269264fbfb202ebc52060a981.x86_64-pc-linux-gnu
drwx------  8 manmath manmath  4096 Oct 18 12:15 evolution
drwxr-xr-x  2 manmath manmath 12288 Oct 18 12:18 fontconfig
drwx------  3 manmath manmath  4096 Oct 14 04:51 gegl-0.4
drwxr-xr-x  2 manmath manmath  4096 Oct 17 22:02 gnome-calculator
drwx------  3 manmath manmath  4096 Oct 16 18:02 gnome-control-center
drwx------  2 manmath manmath  4096 Oct 19 16:15 gnome-screenshot
drwxrwxr-x  2 manmath manmath  4096 Oct 19 16:14 gstreamer-1.0
drwxr-xr-x 15 manmath manmath  4096 Oct 18 07:07 mesa_shader_cache
drwxrwxr-x  3 manmath manmath  4096 Oct 14 04:20 mozilla
drwx------  3 manmath manmath  4096 Oct 19 11:22 thumbnails
drwxrwxr-x  2 manmath manmath  4096 Oct 14 03:16 update-manager-core
drwx------  2 manmath manmath  4096 Oct 17 08:48 wallpaper
drwxrwxr-x  3 manmath manmath  4096 Oct 15 21:55 youtube-dl
[email]manmath@manmath-H61M-DS2:~/.cache[/email]$ cd thumbnails/
[email]manmath@manmath-H61M-DS2:~/.cache[/email]/thumbnails$ ls -l
total 4
drwx------ 3 manmath manmath 4096 Oct 19 11:22 fail
[email]manmath@manmath-H61M-DS2:~/.cache[/email]/thumbnails$ cd fail/
[email]manmath@manmath-H61M-DS2:~/.cache[/email]/thumbnails/fail$ ls -l
total 4
drwx------ 2 manmath manmath 4096 Oct 19 16:26 gnome-thumbnail-factory

System info and nautilus preview settings:
[ATTACH=CONFIG]281386[/ATTACH]

Update:
Out of curiosity I ran nautilus as the root user, surprising nautilus showed thumbnails of all the files. But with normal user privileges nautilus can't display thumbnails.

---

### Post by Claus7 on 2018-10-19
Hello,

just to mention that I'm comparing your output with files under lubuntu 18.04.

So,
> **manmath said:**
> Tried, did not work in my case.

Here's some more info that may help you figure out what might have gone wrong:

Installed packages related to thumbnail generation:...

we have differences, yet just a question here: how to you know that these are the only files that are related with thumbnails and how were you able to isolate them?

> **manmath said:**
> 
Thumbnail configuration files:

...
with a quick look things are ok here.

> **manmath said:**
> 
Startup applications:
 - Files
 - Gnome settings daemon's media-keys plugin
 - Gnome settings daemon's xsettings plugin
 - Indicator messages
 - Network (Gnome Flashback)
 - Pulseaudio sound system
 - Screensaver (Gnome Flashback)

why do you have under startup applications all these?

> **manmath said:**
> 
Thumbnail cache directory permissions:

manmath@manmath-H61M-DS2:~$ cd .cache/
[email]manmath@manmath-H61M-DS2:~/.cache[/email]$ ls -l
total 76
drwx------  2 manmath manmath  4096 Oct 17 08:46 babl
drwx------  3 manmath manmath  4096 Oct 14 07:13 chromium
-rw-r--r--  1 manmath manmath  8192 Oct 18 15:26 event-sound-cache.tdb.5b12201269264fbfb202ebc52060a981.x86_64-pc-linux-gnu
drwx------  8 manmath manmath  4096 Oct 18 12:15 evolution
drwxr-xr-x  2 manmath manmath 12288 Oct 18 12:18 fontconfig
drwx------  3 manmath manmath  4096 Oct 14 04:51 gegl-0.4
drwxr-xr-x  2 manmath manmath  4096 Oct 17 22:02 gnome-calculator
drwx------  3 manmath manmath  4096 Oct 16 18:02 gnome-control-center
drwx------  2 manmath manmath  4096 Oct 19 16:15 gnome-screenshot
drwxrwxr-x  2 manmath manmath  4096 Oct 19 16:14 gstreamer-1.0
drwxr-xr-x 15 manmath manmath  4096 Oct 18 07:07 mesa_shader_cache
drwxrwxr-x  3 manmath manmath  4096 Oct 14 04:20 mozilla
drwx------  3 manmath manmath  4096 Oct 19 11:22 thumbnails
drwxrwxr-x  2 manmath manmath  4096 Oct 14 03:16 update-manager-core
drwx------  2 manmath manmath  4096 Oct 17 08:48 wallpaper
drwxrwxr-x  3 manmath manmath  4096 Oct 15 21:55 youtube-dl
[email]manmath@manmath-H61M-DS2:~/.cache[/email]$ cd thumbnails/
[B][email]manmath@manmath-H61M-DS2:~/.cache[/email]/thumbnails$ ls -l
total 4[/B]
drwx------ 3 manmath manmath 4096 Oct 19 11:22 fail
[email]manmath@manmath-H61M-DS2:~/.cache[/email]/thumbnails$ cd fail/
[email]manmath@manmath-H61M-DS2:~/.cache[/email]/thumbnails/fail$ ls -l
total 4
drwx------ 2 manmath manmath 4096 Oct 19 16:26 gnome-thumbnail-factory

System info and nautilus preview settings:
[ATTACH=CONFIG]281386[/ATTACH]

All the same more or less until the bold line: here my total is 8 and the folders are large and normal: what if backing up those folders with different name, removing the original and rebooting?

Regards!

---

### Post by mc4man on 2018-10-19
For videos nautilus would use the totem thumbnailer though thumbnails would only be produced for files totem can play (decode) 
Do you have the gstreamer bad, ugly & libav plugins installed? If so or after installing them delete the .config/thumbnails folder & try again.
```
sudo apt install gstreamer1.0-libav gstreamer1.0-plugins-bad gstreamer1.0-plugins-ugly
```
Images are handled by the pixbuf thumbnailer which you seem to have, may also benefit from deleting that folder..

---

### Post by manmath on 2018-10-19
Yes, they are all installed.

Update:
Out of curiosity I ran nautilus as the root user, surprising nautilus showed thumbnails of all the files. But with normal user privileges nautilus can't display thumbnails.

> **Claus7 said:**
> How to you know that these are the only files that are related with thumbnails and how were you able to isolate them?
[B]
I don't know, but I presumed.[/B]
All the same more or less until the bold line: here my total is 8 and the folders are large and normal: what if backing up those folders with different name, removing the original and rebooting?
** I'm Sorry, I could not get it.**


I don't know how to explain except that the problem is real. I've also posted the entire list of packages installed on my system. Also, it's not a normal installation. I installed from a minimal CD and then  built with the minimal possible packages.

Update:
Out of curiosity I ran nautilus as the root user, surprising nautilus showed thumbnails of all the files. But with normal user privileges nautilus can't display thumbnails.

> **mc4man said:**
> Do you have the gstreamer bad, ugly & libav plugins installed? If so or after installing them delete the .config/thumbnails folder & try again.
They are all installed. And I did remove the configuration files, even created a new user, meaning a clean slate, yet the problem persists.

Update:
Out of curiosity I ran nautilus as the root user, surprising nautilus showed thumbnails of all the files. But with normal user privileges nautilus can't display thumbnails.

---

### Post by mc4man on 2018-10-19
Actually I meant to say is delete the .cache/thumbnails folder, may or may not have any positive effect. 
What does this report? (longshot
```
gsettings get org.gnome.nautilus.preferences show-image-thumbnails
```

You could post the results of this, maybe some package jumps out..
```
sudo apt -s install ubuntu-desktop
```

---

### Post by manmath on 2018-10-19
```
manmath@manmath-H61M-DS2:~$ gsettings get org.gnome.nautilus.preferences show-image-thumbnails
'always'
manmath@manmath-H61M-DS2:~$ sudo apt -s install ubuntu-desktop
[sudo] password for manmath: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  anacron bc cpp cpp-8 evolution-data-server foomatic-db-compressed-ppds gdm3
  gir1.2-accountsservice-1.0 gir1.2-gck-1 gir1.2-gcr-3 gir1.2-gdm-1.0
  gir1.2-geoclue-2.0 gir1.2-gnomebluetooth-1.0 gir1.2-gweather-3.0
  gir1.2-ibus-1.0 gir1.2-json-1.0 gir1.2-mutter-3 gir1.2-nm-1.0 gir1.2-nma-1.0
  gir1.2-upowerglib-1.0 gnome-keyring gnome-shell gnome-shell-common
  gnome-shell-extension-appindicator gnome-shell-extension-ubuntu-dock
  gstreamer1.0-packagekit gstreamer1.0-plugins-base-apps gvfs-bin inputattach
  libappstream4 libboost-system1.67.0 libboost-thread1.67.0
  libcairo-gobject-perl libcairo-perl libebackend-1.2-10 libebook-1.2-19
  libebook-contacts-1.2-2 libedata-book-1.2-25 libedata-cal-1.2-29
  libedataserverui-1.2-2 libglib-object-introspection-perl libglib-perl
  libgtk3-perl libisl19 libmutter-3-0 libphonenumber7 libprotobuf10
  libu2f-udev libxcb-res0 libxcb-xkb1 libxkbcommon-x11-0 libyaml-0-2 libyelp0
  mutter mutter-common openprinting-ppds p11-kit p11-kit-modules packagekit
  patch perl printer-driver-pnm2ppa python3-debconf python3-debian
  python3-software-properties python3-yaml software-properties-common
  software-properties-gtk spice-vdagent ubuntu-drivers-common
  ubuntu-release-upgrader-gtk ubuntu-session ubuntu-wallpapers
  ubuntu-wallpapers-cosmic update-manager update-notifier
  update-notifier-common x11-apps x11-session-utils x11-xserver-utils
  xfonts-base xfonts-utils xorg xorg-docs-core xwayland yaru-theme-gnome-shell
  yelp yelp-xsl
Suggested packages:
  default-mta | mail-transport-agent cpp-doc gcc-8-locales evolution hplip
  hplip-cups cups-filters printer-driver-all libpam-gnome-keyring gnome-orca
  chrome-gnome-shell gir1.2-telepathyglib-0.12 gnome-themes-standard-data
  gnome-backgrounds gir1.2-telepathylogger-0.2 libfont-freetype-perl
  libxml-libxml-perl hpijs-ppds appstream ed diffutils-doc perl-doc
  libterm-readline-gnu-perl | libterm-readline-perl-perl make magicfilter
  | apsfilter python3-aptdaemon.pkcompat ubuntu-wallpapers-karmic
  ubuntu-wallpapers-lucid ubuntu-wallpapers-maverick ubuntu-wallpapers-natty
  ubuntu-wallpapers-oneiric ubuntu-wallpapers-precise
  ubuntu-wallpapers-quantal ubuntu-wallpapers-raring ubuntu-wallpapers-saucy
  ubuntu-wallpapers-trusty ubuntu-wallpapers-utopic ubuntu-wallpapers-vivid
  ubuntu-wallpapers-wily ubuntu-wallpapers-xenial ubuntu-wallpapers-yakkety
  ubuntu-wallpapers-zesty ubuntu-wallpapers-artful ubuntu-wallpapers-bionic
  gir1.2-unity-5.0 nickle cairo-5c xorg-docs xfonts-100dpi xfonts-75dpi
  x11-xfs-utils
Recommended packages:
  rsyslog | system-log-daemon cups-filters | foomatic-filters cups cups-client
  libpam-fprintd xserver-xephyr libpam-gnome-keyring gnome-keyring-pkcs11 bolt
  gkbd-capplet gnome-user-docs iio-sensor-proxy switcheroo-control
  xserver-xorg-legacy gnome-software | apper packagekit-tools
  unattended-upgrades aisleriot app-install-data-partner apport-gtk
  avahi-autoipd avahi-daemon baobab bluez bluez-cups branding-ubuntu brltty
  cups-bsd cups-filters deja-dup example-content fonts-indic fonts-kacst-one
  fonts-khmeros-core fonts-lao fonts-lklug-sinhala fonts-noto-cjk
  fonts-sil-abyssinica fonts-sil-padauk fonts-thai-tlwg fonts-tibetan-machine
  fwupd fwupd-signed gir1.2-gmenu-3.0 gnome-accessibility-themes
  gnome-bluetooth gnome-calendar gnome-font-viewer gnome-getting-started-docs
  gnome-initial-setup gnome-mahjongg gnome-mines gnome-power-manager
  gnome-software-plugin-snap gnome-sudoku gnome-todo gpg-agent hplip ibus
  ibus-gtk ibus-gtk3 ibus-table kerneloops laptop-detect libnss-mdns
  libproxy1-plugin-gsettings libproxy1-plugin-networkmanager libreoffice-calc
  libreoffice-gnome libreoffice-impress libreoffice-math libreoffice-ogltrans
  libreoffice-pdfimport libreoffice-style-breeze libreoffice-writer memtest86+
  mousetweaks nautilus-sendto nautilus-share
  network-manager-config-connectivity-ubuntu network-manager-openvpn-gnome
  network-manager-pptp-gnome orca pcmciautils plymouth-theme-ubuntu-logo ppp
  pppconfig pppoeconf printer-driver-brlaser printer-driver-c2esp
  printer-driver-foo2zjs printer-driver-m2300w printer-driver-min12xxw
  printer-driver-ptouch printer-driver-pxljr printer-driver-sag-gdi
  printer-driver-splix pulseaudio-module-bluetooth remmina rhythmbox seahorse
  shotwell simple-scan snapd speech-dispatcher thunderbird
  thunderbird-gnome-support transmission-gtk ubuntu-docs ubuntu-report
  ubuntu-software ubuntu-web-launchers usb-creator-gtk vino whoopsie
  xcursor-themes xdg-desktop-portal-gtk xul-ext-ubufox yaru-theme-gtk
  yaru-theme-icon yaru-theme-sound python3-launchpadlib xbitmaps
  xfonts-scalable
The following NEW packages will be installed:
  anacron bc cpp cpp-8 evolution-data-server foomatic-db-compressed-ppds gdm3
  gir1.2-accountsservice-1.0 gir1.2-gck-1 gir1.2-gcr-3 gir1.2-gdm-1.0
  gir1.2-geoclue-2.0 gir1.2-gnomebluetooth-1.0 gir1.2-gweather-3.0
  gir1.2-ibus-1.0 gir1.2-json-1.0 gir1.2-mutter-3 gir1.2-nm-1.0 gir1.2-nma-1.0
  gir1.2-upowerglib-1.0 gnome-keyring gnome-shell gnome-shell-common
  gnome-shell-extension-appindicator gnome-shell-extension-ubuntu-dock
  gstreamer1.0-packagekit gstreamer1.0-plugins-base-apps gvfs-bin inputattach
  libappstream4 libboost-system1.67.0 libboost-thread1.67.0
  libcairo-gobject-perl libcairo-perl libebackend-1.2-10 libebook-1.2-19
  libebook-contacts-1.2-2 libedata-book-1.2-25 libedata-cal-1.2-29
  libedataserverui-1.2-2 libglib-object-introspection-perl libglib-perl
  libgtk3-perl libisl19 libmutter-3-0 libphonenumber7 libprotobuf10
  libu2f-udev libxcb-res0 libxcb-xkb1 libxkbcommon-x11-0 libyaml-0-2 libyelp0
  mutter mutter-common openprinting-ppds p11-kit p11-kit-modules packagekit
  patch perl printer-driver-pnm2ppa python3-debconf python3-debian
  python3-software-properties python3-yaml software-properties-common
  software-properties-gtk spice-vdagent ubuntu-desktop ubuntu-drivers-common
  ubuntu-release-upgrader-gtk ubuntu-session ubuntu-wallpapers
  ubuntu-wallpapers-cosmic update-manager update-notifier
  update-notifier-common x11-apps x11-session-utils x11-xserver-utils
  xfonts-base xfonts-utils xorg xorg-docs-core xwayland yaru-theme-gnome-shell
  yelp yelp-xsl
0 upgraded, 89 newly installed, 0 to remove and 0 not upgraded.
Inst perl (5.26.2-7 Ubuntu:18.10/cosmic [amd64])
Inst ubuntu-drivers-common (1:0.5.5 Ubuntu:18.10/cosmic [amd64])
Inst python3-debian (0.1.33 Ubuntu:18.10/cosmic [all])
Inst python3-debconf (1.5.69 Ubuntu:18.10/cosmic [all])
Inst patch (2.7.6-3 Ubuntu:18.10/cosmic [amd64])
Inst update-notifier-common (3.192.7 Ubuntu:18.10/cosmic [all])
Inst libyaml-0-2 (0.2.1-1 Ubuntu:18.10/cosmic [amd64])
Inst python3-yaml (3.12-1build3 Ubuntu:18.10/cosmic [amd64])
Inst anacron (2.3-24 Ubuntu:18.10/cosmic [amd64])
Inst bc (1.07.1-2 Ubuntu:18.10/cosmic [amd64])
Inst libisl19 (0.20-2 Ubuntu:18.10/cosmic [amd64])
Inst cpp-8 (8.2.0-7ubuntu1 Ubuntu:18.10/cosmic [amd64])
Inst cpp (4:8.2.0-1ubuntu1 Ubuntu:18.10/cosmic [amd64])
Inst libebackend-1.2-10 (3.30.1-1build1 Ubuntu:18.10/cosmic [amd64])
Inst libboost-system1.67.0 (1.67.0-7 Ubuntu:18.10/cosmic [amd64])
Inst libboost-thread1.67.0 (1.67.0-7 Ubuntu:18.10/cosmic [amd64])
Inst libprotobuf10 (3.0.0-9.1ubuntu3 Ubuntu:18.10/cosmic [amd64])
Inst libphonenumber7 (7.1.0-5ubuntu6 Ubuntu:18.10/cosmic [amd64])
Inst libebook-contacts-1.2-2 (3.30.1-1build1 Ubuntu:18.10/cosmic [amd64])
Inst libedata-book-1.2-25 (3.30.1-1build1 Ubuntu:18.10/cosmic [amd64])
Inst libebook-1.2-19 (3.30.1-1build1 Ubuntu:18.10/cosmic [amd64])
Inst libedata-cal-1.2-29 (3.30.1-1build1 Ubuntu:18.10/cosmic [amd64])
Inst libedataserverui-1.2-2 (3.30.1-1build1 Ubuntu:18.10/cosmic [amd64])
Inst p11-kit-modules (0.23.14-2 Ubuntu:18.10/cosmic [amd64])
Inst p11-kit (0.23.14-2 Ubuntu:18.10/cosmic [amd64])
Inst gnome-keyring (3.28.2-0ubuntu1 Ubuntu:18.10/cosmic [amd64])
Inst evolution-data-server (3.30.1-1build1 Ubuntu:18.10/cosmic [amd64])
Inst foomatic-db-compressed-ppds (20180917-1 Ubuntu:18.10/cosmic [all])
Inst gir1.2-gdm-1.0 (3.30.1-1ubuntu5 Ubuntu:18.10/cosmic [amd64])
Inst gir1.2-accountsservice-1.0 (0.6.45-1ubuntu1 Ubuntu:18.10/cosmic [amd64])
Inst gir1.2-gck-1 (3.28.0-1 Ubuntu:18.10/cosmic [amd64])
Inst gir1.2-gcr-3 (3.28.0-1 Ubuntu:18.10/cosmic [amd64])
Inst gir1.2-geoclue-2.0 (2.4.12-2ubuntu1 Ubuntu:18.10/cosmic [amd64])
Inst gir1.2-gnomebluetooth-1.0 (3.28.2-2 Ubuntu:18.10/cosmic [amd64])
Inst gir1.2-gweather-3.0 (3.28.2-1 Ubuntu:18.10/cosmic [amd64])
Inst gir1.2-ibus-1.0 (1.5.19-1ubuntu1 Ubuntu:18.10/cosmic [amd64])
Inst mutter-common (3.30.1-1 Ubuntu:18.10/cosmic [all])
Inst libxcb-res0 (1.13.1-1 Ubuntu:18.10/cosmic [amd64])
Inst libxcb-xkb1 (1.13.1-1 Ubuntu:18.10/cosmic [amd64])
Inst libxkbcommon-x11-0 (0.8.2-1 Ubuntu:18.10/cosmic [amd64])
Inst libmutter-3-0 (3.30.1-1 Ubuntu:18.10/cosmic [amd64])
Inst gir1.2-json-1.0 (1.4.4-1 Ubuntu:18.10/cosmic [amd64])
Inst gir1.2-mutter-3 (3.30.1-1 Ubuntu:18.10/cosmic [amd64])
Inst gir1.2-nm-1.0 (1.12.4-1ubuntu1 Ubuntu:18.10/cosmic [amd64])
Inst gir1.2-nma-1.0 (1.8.18-2ubuntu2 Ubuntu:18.10/cosmic [amd64])
Inst gir1.2-upowerglib-1.0 (0.99.8-2 Ubuntu:18.10/cosmic [amd64])
Inst gnome-shell-common (3.30.1-2ubuntu1 Ubuntu:18.10/cosmic [all])
Inst ubuntu-wallpapers-cosmic (18.10.2-0ubuntu1 Ubuntu:18.10/cosmic [all])
Inst ubuntu-wallpapers (18.10.2-0ubuntu1 Ubuntu:18.10/cosmic [all])
Inst mutter (3.30.1-1 Ubuntu:18.10/cosmic [amd64])
Inst gnome-shell (3.30.1-2ubuntu1 Ubuntu:18.10/cosmic [amd64])
Inst xwayland (2:1.20.1-3ubuntu2 Ubuntu:18.10/cosmic [amd64])
Inst yaru-theme-gnome-shell (18.10.6 Ubuntu:18.10/cosmic [all])
Inst ubuntu-session (3.30.0-0ubuntu4 Ubuntu:18.10/cosmic [all])
Inst x11-xserver-utils (7.7+8 Ubuntu:18.10/cosmic [amd64])
Inst gdm3 (3.30.1-1ubuntu5 Ubuntu:18.10/cosmic [amd64])
Inst gnome-shell-extension-appindicator (22-1 Ubuntu:18.10/cosmic [all])
Inst gnome-shell-extension-ubuntu-dock (63ubuntu1 Ubuntu:18.10/cosmic [all])
Inst libappstream4 (0.12.2-2 Ubuntu:18.10/cosmic [amd64])
Inst packagekit (1.1.10-1ubuntu7 Ubuntu:18.10/cosmic [amd64])
Inst gstreamer1.0-packagekit (1.1.10-1ubuntu7 Ubuntu:18.10/cosmic [amd64])
Inst gstreamer1.0-plugins-base-apps (1.14.4-1ubuntu1 Ubuntu:18.10/cosmic [amd64])
Inst gvfs-bin (1.38.0-2ubuntu2 Ubuntu:18.10/cosmic [amd64])
Inst libcairo-perl (1.106-2build2 Ubuntu:18.10/cosmic [amd64])
Inst libglib-perl (3:1.327-1 Ubuntu:18.10/cosmic [amd64])
Inst libcairo-gobject-perl (1.004-2build3 Ubuntu:18.10/cosmic [amd64])
Inst libglib-object-introspection-perl (0.045-1 Ubuntu:18.10/cosmic [amd64])
Inst libgtk3-perl (0.034-2 Ubuntu:18.10/cosmic [all])
Inst libu2f-udev (1.1.6-1 Ubuntu:18.10/cosmic [all])
Inst libyelp0 (3.30.0-1build1 Ubuntu:18.10/cosmic [amd64])
Inst openprinting-ppds (20180917-1 Ubuntu:18.10/cosmic [all])
Inst printer-driver-pnm2ppa (1.13+nondbs-0ubuntu6 Ubuntu:18.10/cosmic [amd64])
Inst python3-software-properties (0.96.27 Ubuntu:18.10/cosmic [all])
Inst software-properties-common (0.96.27 Ubuntu:18.10/cosmic [all])
Inst software-properties-gtk (0.96.27 Ubuntu:18.10/cosmic [all])
Inst spice-vdagent (0.17.0-1ubuntu2 Ubuntu:18.10/cosmic [amd64])
Inst inputattach (1:1.6.0-2 Ubuntu:18.10/cosmic [amd64])
Inst update-notifier (3.192.7 Ubuntu:18.10/cosmic [amd64]) []
Inst update-manager (1:18.10.10 Ubuntu:18.10/cosmic [all]) []
Inst ubuntu-release-upgrader-gtk (1:18.10.11 Ubuntu:18.10/cosmic [all])
Inst xfonts-utils (1:7.7+6 Ubuntu:18.10/cosmic [amd64])
Inst xfonts-base (1:1.0.4+nmu1 Ubuntu:18.10/cosmic [all])
Inst x11-apps (7.7+7 Ubuntu:18.10/cosmic [amd64])
Inst x11-session-utils (7.7+3 Ubuntu:18.10/cosmic [amd64])
Inst xorg-docs-core (1:1.7.1-1.1 Ubuntu:18.10/cosmic [all])
Inst xorg (1:7.7+19ubuntu8 Ubuntu:18.10/cosmic [amd64])
Inst yelp-xsl (3.30.1-1 Ubuntu:18.10/cosmic [all])
Inst yelp (3.30.0-1build1 Ubuntu:18.10/cosmic [amd64])
Inst ubuntu-desktop (1.425 Ubuntu:18.10/cosmic [amd64])
Conf perl (5.26.2-7 Ubuntu:18.10/cosmic [amd64])
Conf ubuntu-drivers-common (1:0.5.5 Ubuntu:18.10/cosmic [amd64])
Conf python3-debian (0.1.33 Ubuntu:18.10/cosmic [all])
Conf python3-debconf (1.5.69 Ubuntu:18.10/cosmic [all])
Conf patch (2.7.6-3 Ubuntu:18.10/cosmic [amd64])
Conf update-notifier-common (3.192.7 Ubuntu:18.10/cosmic [all])
Conf libyaml-0-2 (0.2.1-1 Ubuntu:18.10/cosmic [amd64])
Conf python3-yaml (3.12-1build3 Ubuntu:18.10/cosmic [amd64])
Conf anacron (2.3-24 Ubuntu:18.10/cosmic [amd64])
Conf bc (1.07.1-2 Ubuntu:18.10/cosmic [amd64])
Conf libisl19 (0.20-2 Ubuntu:18.10/cosmic [amd64])
Conf cpp-8 (8.2.0-7ubuntu1 Ubuntu:18.10/cosmic [amd64])
Conf cpp (4:8.2.0-1ubuntu1 Ubuntu:18.10/cosmic [amd64])
Conf libebackend-1.2-10 (3.30.1-1build1 Ubuntu:18.10/cosmic [amd64])
Conf libboost-system1.67.0 (1.67.0-7 Ubuntu:18.10/cosmic [amd64])
Conf libboost-thread1.67.0 (1.67.0-7 Ubuntu:18.10/cosmic [amd64])
Conf libprotobuf10 (3.0.0-9.1ubuntu3 Ubuntu:18.10/cosmic [amd64])
Conf libphonenumber7 (7.1.0-5ubuntu6 Ubuntu:18.10/cosmic [amd64])
Conf libebook-contacts-1.2-2 (3.30.1-1build1 Ubuntu:18.10/cosmic [amd64])
Conf libedata-book-1.2-25 (3.30.1-1build1 Ubuntu:18.10/cosmic [amd64])
Conf libebook-1.2-19 (3.30.1-1build1 Ubuntu:18.10/cosmic [amd64])
Conf libedata-cal-1.2-29 (3.30.1-1build1 Ubuntu:18.10/cosmic [amd64])
Conf libedataserverui-1.2-2 (3.30.1-1build1 Ubuntu:18.10/cosmic [amd64])
Conf p11-kit-modules (0.23.14-2 Ubuntu:18.10/cosmic [amd64])
Conf p11-kit (0.23.14-2 Ubuntu:18.10/cosmic [amd64])
Conf gnome-keyring (3.28.2-0ubuntu1 Ubuntu:18.10/cosmic [amd64])
Conf evolution-data-server (3.30.1-1build1 Ubuntu:18.10/cosmic [amd64])
Conf foomatic-db-compressed-ppds (20180917-1 Ubuntu:18.10/cosmic [all])
Conf gir1.2-gdm-1.0 (3.30.1-1ubuntu5 Ubuntu:18.10/cosmic [amd64])
Conf gir1.2-accountsservice-1.0 (0.6.45-1ubuntu1 Ubuntu:18.10/cosmic [amd64])
Conf gir1.2-gck-1 (3.28.0-1 Ubuntu:18.10/cosmic [amd64])
Conf gir1.2-gcr-3 (3.28.0-1 Ubuntu:18.10/cosmic [amd64])
Conf gir1.2-geoclue-2.0 (2.4.12-2ubuntu1 Ubuntu:18.10/cosmic [amd64])
Conf gir1.2-gnomebluetooth-1.0 (3.28.2-2 Ubuntu:18.10/cosmic [amd64])
Conf gir1.2-gweather-3.0 (3.28.2-1 Ubuntu:18.10/cosmic [amd64])
Conf gir1.2-ibus-1.0 (1.5.19-1ubuntu1 Ubuntu:18.10/cosmic [amd64])
Conf mutter-common (3.30.1-1 Ubuntu:18.10/cosmic [all])
Conf libxcb-res0 (1.13.1-1 Ubuntu:18.10/cosmic [amd64])
Conf libxcb-xkb1 (1.13.1-1 Ubuntu:18.10/cosmic [amd64])
Conf libxkbcommon-x11-0 (0.8.2-1 Ubuntu:18.10/cosmic [amd64])
Conf libmutter-3-0 (3.30.1-1 Ubuntu:18.10/cosmic [amd64])
Conf gir1.2-json-1.0 (1.4.4-1 Ubuntu:18.10/cosmic [amd64])
Conf gir1.2-mutter-3 (3.30.1-1 Ubuntu:18.10/cosmic [amd64])
Conf gir1.2-nm-1.0 (1.12.4-1ubuntu1 Ubuntu:18.10/cosmic [amd64])
Conf gir1.2-nma-1.0 (1.8.18-2ubuntu2 Ubuntu:18.10/cosmic [amd64])
Conf gir1.2-upowerglib-1.0 (0.99.8-2 Ubuntu:18.10/cosmic [amd64])
Conf gnome-shell-common (3.30.1-2ubuntu1 Ubuntu:18.10/cosmic [all])
Conf ubuntu-wallpapers-cosmic (18.10.2-0ubuntu1 Ubuntu:18.10/cosmic [all])
Conf ubuntu-wallpapers (18.10.2-0ubuntu1 Ubuntu:18.10/cosmic [all])
Conf mutter (3.30.1-1 Ubuntu:18.10/cosmic [amd64])
Conf gnome-shell (3.30.1-2ubuntu1 Ubuntu:18.10/cosmic [amd64])
Conf xwayland (2:1.20.1-3ubuntu2 Ubuntu:18.10/cosmic [amd64])
Conf yaru-theme-gnome-shell (18.10.6 Ubuntu:18.10/cosmic [all])
Conf ubuntu-session (3.30.0-0ubuntu4 Ubuntu:18.10/cosmic [all])
Conf x11-xserver-utils (7.7+8 Ubuntu:18.10/cosmic [amd64])
Conf gdm3 (3.30.1-1ubuntu5 Ubuntu:18.10/cosmic [amd64])
Conf gnome-shell-extension-appindicator (22-1 Ubuntu:18.10/cosmic [all])
Conf gnome-shell-extension-ubuntu-dock (63ubuntu1 Ubuntu:18.10/cosmic [all])
Conf libappstream4 (0.12.2-2 Ubuntu:18.10/cosmic [amd64])
Conf packagekit (1.1.10-1ubuntu7 Ubuntu:18.10/cosmic [amd64])
Conf gstreamer1.0-packagekit (1.1.10-1ubuntu7 Ubuntu:18.10/cosmic [amd64])
Conf gstreamer1.0-plugins-base-apps (1.14.4-1ubuntu1 Ubuntu:18.10/cosmic [amd64])
Conf gvfs-bin (1.38.0-2ubuntu2 Ubuntu:18.10/cosmic [amd64])
Conf libcairo-perl (1.106-2build2 Ubuntu:18.10/cosmic [amd64])
Conf libglib-perl (3:1.327-1 Ubuntu:18.10/cosmic [amd64])
Conf libcairo-gobject-perl (1.004-2build3 Ubuntu:18.10/cosmic [amd64])
Conf libglib-object-introspection-perl (0.045-1 Ubuntu:18.10/cosmic [amd64])
Conf libgtk3-perl (0.034-2 Ubuntu:18.10/cosmic [all])
Conf libu2f-udev (1.1.6-1 Ubuntu:18.10/cosmic [all])
Conf libyelp0 (3.30.0-1build1 Ubuntu:18.10/cosmic [amd64])
Conf openprinting-ppds (20180917-1 Ubuntu:18.10/cosmic [all])
Conf printer-driver-pnm2ppa (1.13+nondbs-0ubuntu6 Ubuntu:18.10/cosmic [amd64])
Conf python3-software-properties (0.96.27 Ubuntu:18.10/cosmic [all])
Conf software-properties-common (0.96.27 Ubuntu:18.10/cosmic [all])
Conf software-properties-gtk (0.96.27 Ubuntu:18.10/cosmic [all])
Conf spice-vdagent (0.17.0-1ubuntu2 Ubuntu:18.10/cosmic [amd64])
Conf inputattach (1:1.6.0-2 Ubuntu:18.10/cosmic [amd64])
Conf update-notifier (3.192.7 Ubuntu:18.10/cosmic [amd64])
Conf update-manager (1:18.10.10 Ubuntu:18.10/cosmic [all])
Conf ubuntu-release-upgrader-gtk (1:18.10.11 Ubuntu:18.10/cosmic [all])
Conf xfonts-utils (1:7.7+6 Ubuntu:18.10/cosmic [amd64])
Conf xfonts-base (1:1.0.4+nmu1 Ubuntu:18.10/cosmic [all])
Conf x11-apps (7.7+7 Ubuntu:18.10/cosmic [amd64])
Conf x11-session-utils (7.7+3 Ubuntu:18.10/cosmic [amd64])
Conf xorg-docs-core (1:1.7.1-1.1 Ubuntu:18.10/cosmic [all])
Conf xorg (1:7.7+19ubuntu8 Ubuntu:18.10/cosmic [amd64])
Conf yelp-xsl (3.30.1-1 Ubuntu:18.10/cosmic [all])
Conf yelp (3.30.0-1build1 Ubuntu:18.10/cosmic [amd64])
Conf ubuntu-desktop (1.425 Ubuntu:18.10/cosmic [amd64])
```

Update:
Out of curiosity I ran nautilus as the root user, surprising nautilus showed thumbnails of all the files. But with normal user privileges nautilus can't display thumbnails.

---

### Post by Claus7 on 2018-10-19
Hello,

this is really a big list of packages! Have you done a proper installation? I mean, it seems that many cosmic packages are missing here. You could wait also for a response from *mc4man*, yet I would suggest you the following commands:
sudo apt update
sudo apt upgrade

so any missing packages from your system will be installed.

Regards!

---

### Post by manmath on 2018-10-19
I've done proper installation using mini cd ([http://archive.ubuntu.com/ubuntu/dists/cosmic/main/installer-amd64/current/images/netboot/mini.iso](http://archive.ubuntu.com/ubuntu/dists/cosmic/main/installer-amd64/current/images/netboot/mini.iso)). However, from the very beginning I pulled only the necessary packages to build a gnome-flashback-session. The good part is the entire installation footprint is just 2.4GB, it boots in ~10sec on a shoddy 54rpm mechanical drive and consumes just ~230mb memory. So, I don't want to go for a full installation. I've put too much effort into making the system nimble. The experience has been cosmic (figuratively and literally) except for this annoying thumbnail creation problem. It's puzzling what can be the issue with thumbnails. Yes, my system has been fully updated.

manmath@manmath-H61M-DS2:~$ su
root@manmath-H61M-DS2:/home/manmath# apt update && apt upgrade && apt full-upgrade && apt dist-upgrade
Hit:1 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) cosmic-security InRelease           
Get:2 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) cosmic InRelease [242 kB]         
Get:3 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) cosmic-updates InRelease [83.2 kB]
Fetched 325 kB in 5s (61.7 kB/s)    
Reading package lists... Done
Building dependency tree       
Reading state information... Done
All packages are up to date.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  acpi-support acpid cheese dconf-cli ethtool fonts-noto-color-emoji fonts-ubuntu gir1.2-dbusmenu-glib-0.4 gir1.2-dee-1.0 gir1.2-gdesktopenums-3.0 gir1.2-gnomedesktop-3.0 gir1.2-goa-1.0 gnome-video-effects
  gtk2-engines ifupdown inxi iputils-tracepath irqbalance libgutenprint-common libgutenprint9 libplist-utils linux-base media-player-info menu menu-xdg mtools nano pm-utils policykit-desktop-privileges
  python3-distro python3-psutil python3-setproctitle python3-xapp tree update-manager-core xfonts-encodings xinit xinput
Use 'apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  acpi-support acpid cheese dconf-cli ethtool fonts-noto-color-emoji fonts-ubuntu gir1.2-dbusmenu-glib-0.4 gir1.2-dee-1.0 gir1.2-gdesktopenums-3.0 gir1.2-gnomedesktop-3.0 gir1.2-goa-1.0 gnome-video-effects
  gtk2-engines ifupdown inxi iputils-tracepath irqbalance libgutenprint-common libgutenprint9 libplist-utils linux-base media-player-info menu menu-xdg mtools nano pm-utils policykit-desktop-privileges
  python3-distro python3-psutil python3-setproctitle python3-xapp tree update-manager-core xfonts-encodings xinit xinput
Use 'apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  acpi-support acpid cheese dconf-cli ethtool fonts-noto-color-emoji fonts-ubuntu gir1.2-dbusmenu-glib-0.4 gir1.2-dee-1.0 gir1.2-gdesktopenums-3.0 gir1.2-gnomedesktop-3.0 gir1.2-goa-1.0 gnome-video-effects
  gtk2-engines ifupdown inxi iputils-tracepath irqbalance libgutenprint-common libgutenprint9 libplist-utils linux-base media-player-info menu menu-xdg mtools nano pm-utils policykit-desktop-privileges
  python3-distro python3-psutil python3-setproctitle python3-xapp tree update-manager-core xfonts-encodings xinit xinput
Use 'apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Update:
Out of curiosity I ran nautilus as the root user, surprising nautilus showed thumbnails of all the files. But with normal user privileges nautilus can't display thumbnails.

---

### Post by dino99 on 2018-10-20
You clearly miss a dependency; but which one ? that's the question  :confused:   Try installing xfonts-base which seems mandatory anyway.
and clean the room:>  sudo apt-get autoremove

---

### Post by manmath on 2018-10-20
Did that followed by "apt install -f". It installed all those packages over again. Thereafter apt doesn't suggest to autoremove. It's good. Thanks for the response. Please suggest what could possibly have gone wrong with thumbnail creation. I'm ready to spend sometime and do what ever you suggest (except for a complete OS install).

Now, apt update and upgrade is error-free:

root@manmath-H61M-DS2:/home/manmath# apt update && apt upgrade && apt full-upgrade
Get:1 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) cosmic InRelease [242 kB]
Hit:2 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) cosmic-security InRelease
Get:3 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) cosmic-updates InRelease [83.2 kB]
Fetched 325 kB in 4s (73.3 kB/s)    
Reading package lists... Done
Building dependency tree       
Reading state information... Done
All packages are up to date.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

After the package transaction, this is the list of packages currently installed on my system:  [ATTACH]281389[/ATTACH]. Please have a look and suggest me if I'm missing any package related to thumbnail generation.

Update:
Out of curiosity I ran nautilus as the root user, surprising nautilus showed thumbnails of all the files. But with normal user privileges nautilus can't display thumbnails.

Till we solve this problem, I'm interested to know if there is any other way to setup a gnome flashback session without adding much bloat (gnome shell stuff)?

Update:
Out of curiosity I ran nautilus as the root user, surprising nautilus showed thumbnails of all the files. But with normal user privileges nautilus can't display thumbnails.

---

### Post by wildmanne39 on 2018-10-20
Please do not make duplicate posts.

Thanks

---

### Post by manmath on 2018-10-20
Sorry, it was by mistake.

Update:
Out of curiosity I ran nautilus as the root user, surprising nautilus showed thumbnails of all the files. But with normal user privileges nautilus can't display thumbnails.

---

### Post by Claus7 on 2018-10-20
Hello,

> **manmath said:**
> Is there any way I can manually create thumbnails for all files?

I do not know if there is such a way yet:

in my box when I type under synaptic thumbnails I get the following packages:
libgdk-pixbuf2.0-bin (you already have it)
tumbler-common (you don't have it)
libtumbler-1-0 (you don't have it)
tumbler (you don't have it)

so you could start from here and install those packages.

Regards!

---

### Post by manmath on 2018-10-20
IMO, tumbler is for thunar. I don't know what is for nautilus.

Here are the nautilus bits in apps and xdg:
root@manmath-H61M-DS2:/# find -name "nautilus*.desktop"
./etc/xdg/autostart/nautilus-autostart.desktop
./usr/share/applications/nautilus-autorun-software.desktop
./usr/share/applications/nautilus-classic.desktop

Though nautilus is installed, I can't find nautilus.desktop, only nautilus-classic.desktop that you see above this line. Is there something wrong here?

Update:
Out of curiosity I ran nautilus as the root user, surprising nautilus showed thumbnails of all the files. But with normal user privileges nautilus can't display thumbnails.

Ok. Seems it's difficult to solve the problem. Life is too short to waste a week for thumbnail generation. I've been using linux for over 15 years and lo, I'm clueless. So, let me mark it solved (though it's not), so that you and I can move on to better stuff. Thank you all for contributing your ideas.

Update:

A ray hope. Out of curiosity I ran nautilus as the root user, surprising nautilus showed thumbnails of all the files. But with normal user privileges nautilus can't display thumbnails.

---

### Post by vanadium on 2018-10-21
Bad idea to mark a post solved if it is not solved. Nothing so disappointing as to find a solved post about your problem just to find out there is no solution at all. If you want to move on, just ignore the post (=unsubscribe).

---

### Post by oldos2er on 2018-10-21
Removed the "Solved" tag. As vanadium says, it's not fair to others seeking help to mark a thread "Solved" when there's no solution.

---

### Post by manmath on 2018-10-22
Can we mark it "Unsolved" so that it can save time of those looking for a solution?

---

### Post by maingmeong on 2018-10-22
Try this one.
[https://imgur.com/a/cNjFQEc](https://imgur.com/a/cNjFQEc)

---

### Post by manmath on 2018-10-22
Tried. Did not help.

Update:
A ray of hope. Out of curiosity I ran nautilus as the root user, surprising nautilus showed thumbnails of all the files. But with normal user privileges nautilus can't display thumbnails.

---

### Post by maingmeong on 2018-10-23
> **manmath said:**
> Tried. Did not help.

Can you give screenshoot of your nautilus thumbnails look like?

---

### Post by manmath on 2018-10-23
Sure, please have a look.[ATTACH=CONFIG]281413[/ATTACH]

Update:
A ray of hope. Out of curiosity I ran nautilus as the root user, surprising nautilus showed thumbnails of all the files. But with normal user privileges nautilus can't display thumbnails.

---

### Post by maingmeong on 2018-10-23
> **manmath said:**
> Sure, please have a look.[ATTACH=CONFIG]281413[/ATTACH]

Are you sure you updated to Ubuntu Cosmic 18.10? Your icons and stuff looks like 18.04.  Can you give me your screenshoot of your About.

---

### Post by manmath on 2018-10-23
I did not upgrade. I had built system from mini cd. Here's the screenshot of About This Computer:[ATTACH=CONFIG]281416[/ATTACH]

Update:
A ray of hope. Out of curiosity I ran nautilus as the root user, surprising nautilus showed thumbnails of all the files. But with normal user privileges nautilus can't display thumbnails. Please suggest me what to do.

---

### Post by Claus7 on 2018-10-23
Hello,

just an update:
1) Have you entered .cache folder (when you open a terminal, type cd .cache). Then have you removed anything from there by typing:
rm * ?
After that, have you rebooted to see what happened? 
Be careful with the command above, since you do not want to remove anything sensitive. 
It would be easier to open nautilus, and then from options to show hidden files and remove them as usual to trash.
I repeat this, since I saw an edited message of yours earlier and it was not clear to me whether you attempted to delete those folders or not.
Also, if you delete the files via nautilus, they will go to trash, which means that you will be able to restore them if needed (this was my initial proposal, to keep a backup first of this folders and files).

2) If nautilus is not displaying things normally, can you see the thumbnails if you install thunar for example? You could check, so as to isolate the problem either for nautilus or for every files manager.

Just a couple of more ideas,
Regards!

---

### Post by manmath on 2018-10-23
Mine is a prestine gnome flashback 18.10 from the get go. And took all care that you've mentioned. Yeah, it's the same with xfce thunar, I'm unable to see thumbnail for any file at all either on thunar or nautilus.

Update:
A ray of hope. Out of curiosity I ran nautilus as the root user, surprising nautilus showed thumbnails of all the files. But with normal user privileges nautilus can't display thumbnails. Please suggest me what to do.

---

### Post by Claus7 on 2018-10-24
Hello,

so, it is system related. Now:
1)do you have dconf or gconf editor with the version (pristine 18.10) you are using? I suppose that you have dconf since gconf is obsolete. If you open dconf and type thumbnails, what are the results that you are getting? Do you have any option related with enable/disable thumbnails? 
2)I was able to see that maybe it is also mime related, so in the above search, check if there are any related results with mime name disabled, so you can enable them back.

Hope problem will get solved,
Regards!

---

### Post by manmath on 2018-10-24
Here are the mime types related to thumbnail:

manmath@manmath-H61M-DS2:~$ cat /usr/share/thumbnailers/*
[Thumbnailer Entry]
TryExec=evince-thumbnailer
Exec=evince-thumbnailer -s %s %u %o
MimeType=application/pdf;application/x-bzpdf;application/x-gzpdf;application/x-xzpdf;application/x-ext-pdf;application/postscript;application/x-bzpostscript;application/x-gzpostscript;image/x-eps;image/x-bzeps;image/x-gzeps;application/x-ext-ps;application/x-ext-eps;application/illustrator;application/x-dvi;application/x-bzdvi;application/x-gzdvi;application/x-ext-dvi;image/vnd.djvu+multipage;application/x-ext-djv;application/x-ext-djvu;image/tiff;application/x-cbr;application/x-cbz;application/x-cb7;application/x-cbt;application/x-ext-cbr;application/x-ext-cbz;application/x-ext-cb7;application/x-ext-cbt;application/vnd.comicbook+zip;application/vnd.comicbook-rar;application/oxps;application/vnd.ms-xpsdocument
[Thumbnailer Entry]
TryExec=ffmpegthumbnailer
Exec=ffmpegthumbnailer -i %i -o %o -s %s -f
MimeType=video/jpeg;video/mp4;video/mpeg;video/quicktime;video/x-ms-asf;video/x-ms-wm;video/x-ms-wmv;video/x-msvideo;video/x-flv;video/x-matroska;video/webm;video/mp2t;
[Thumbnailer Entry]
TryExec=/usr/bin/gdk-pixbuf-thumbnailer
Exec=/usr/bin/gdk-pixbuf-thumbnailer -s %s %u %o
MimeType=image/png;image/bmp;image/x-bmp;image/x-MS-bmp;image/gif;image/x-icon;image/x-ico;image/x-win-bitmap;image/vnd.microsoft.icon;application/ico;image/ico;image/icon;text/ico;application/x-navi-animation;image/jpeg;image/x-portable-anymap;image/x-portable-bitmap;image/x-portable-graymap;image/x-portable-pixmap;image/tiff;image/x-xpixmap;image/x-xbitmap;image/x-tga;image/x-icns;image/x-quicktime;image/qtif;
[Thumbnailer Entry]
TryExec=/usr/bin/gdk-pixbuf-thumbnailer
Exec=/usr/bin/gdk-pixbuf-thumbnailer -s %s %u %o
MimeType=image/svg+xml;image/svg+xml-compressed;

And here's dconf setting: [ATTACH=CONFIG]281421[/ATTACH]

Update:
A ray of hope. Out of curiosity I ran nautilus as the root user, surprising nautilus showed thumbnails of all the files. But with normal user privileges nautilus can't display thumbnails. Please suggest me what to do.

Maybe I'm inching toward the solution. **Out of curiosity I ran nautilus as the root user, and lo, nautilus displayed thumbnails for all files.** Please help me what should I do now so that I can see thumbnails as a normal user.

[Here's a screencast]("https://www.youtube.com/watch?v=75OdYkt8HHM")

Should I create a separate thread as the issue is somewhat different than supposed earlier? Because nautilus, with root user privileges, does create thumbnails. But with normal user privileges it can't.

---

### Post by wildmanne39 on 2018-10-24
> **manmath said:**
> Should I create a separate thread as the issue is somewhat different than supposed earlier? Because nautilus, with root user privileges, does create thumbnails. But with normal user privileges it can't.

No, please continue in this thread.

Thanks

---

### Post by manmath on 2018-10-24
Ok.

Please have a look if there's anything unusual about my partition setup.

manmath@manmath-H61M-DS2:~$ cat /etc/fstab
# <file system>					<mount point>	<type>	<options>		<dump>	<pass>
UUID=90bd760a-afbc-4378-9ca6-e9431d637584	/		ext4	defaults,noatime	0	1
UUID=c586c909-4c88-4da2-8570-21510d17804f	/home		ext4	defaults,noatime	0	2

grub line:

GRUB_CMDLINE_LINUX_DEFAULT="quiet **rootfstype=ext4**" (I had made this change to suppress an error message)

menu entry in grub.cfg:

menuentry 'Ubuntu, with Linux 4.16.12' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.16.12-advanced-90bd760a-afbc-4378-9ca6-e9431d637584' {
	recordfail
	load_video
	gfxmode $linux_gfx_mode
	insmod gzio
	if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
	insmod part_msdos
	insmod ext2
	set root='hd0,msdos1'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  90bd760a-afbc-4378-9ca6-e9431d637584
	else
	  search --no-floppy --fs-uuid --set=root 90bd760a-afbc-4378-9ca6-e9431d637584
	fi
	echo	'Loading Linux 4.16.12 ...'
	linux	/boot/vmlinuz-4.16.12 root=**/dev/sda1** ro  quiet rootfstype=ext4  (I don't know why this, I suppose UUID should show here, I'm not sure though)
}

Is it solvable? Or should I go for a reinstall (last resort)? Cos thumbnail creation is really necessary for me owing to thousands of videos, pictures and ebooks.

---

### Post by Claus7 on 2018-10-25
Hello,

> **manmath said:**
> 

And here's dconf setting: [ATTACH=CONFIG]281421[/ATTACH]

Update:
A ray of hope. Out of curiosity I ran nautilus as the root user, surprising nautilus showed thumbnails of all the files. But with normal user privileges nautilus can't display thumbnails. Please suggest me what to do.

my settings in dconf are different than yours, instead I have:
Use default value **ON**
Custom value 'local only' (yet it is grayed out).

Hope you are closer with this,
Regards!

---

### Post by manmath on 2018-10-25
Changed to default value. Still not working.

---

### Post by Claus7 on 2018-10-26
Hello,

1) could you please post a screenshot of the output of dconf when you type thumbnail? I get more options in general than the one you posted above.
2) how about creating a new user and check the thumbnails from there? If they are working for root and for a new user, then most probably something has to do with your original account.

Regards!

---

### Post by dino99 on 2018-10-26
As 'root' display the thumbnails, but not 'user', then the problem is narrowed down to 'apparmor privileges' 

Glance at the output of ' journalctl -b | grep apparmor'

You might find some diff when you are 'root' and when you are 'user'

---

### Post by manmath on 2018-10-26
Now I reinstalled the OS, and it's OK for now.

---

### Post by mc4man on 2018-10-27
> **manmath said:**
> Now I reinstalled the OS, and it's OK for now.
Seemed like best bet.
Does this new install also include the root user account like previous?

---

### Post by manmath on 2018-10-28
No. I sudo for admin tasks.

---

