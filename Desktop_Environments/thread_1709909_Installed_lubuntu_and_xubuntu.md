---
title: "Installed lubuntu and xubuntu"
date: 2011-03-19
forum: Desktop Environments
---

### Post by TNAFan on 2011-03-19
The whole story is, I could not create a Xubuntu 10.04 CD for some reason or another it would continually fail.  So I made a Lubuntu 10.04 CD and installed, then installed Xubuntu 10.04 on the side.  Now, how would I go about removing Lubuntu 10.04?

---

### Post by SteveDee on 2011-03-19
> **TNAFan said:**
> ....Now, how would I go about removing Lubuntu 10.04?

Try this: [http://www.psychocats.net/ubuntu/purexfce](http://www.psychocats.net/ubuntu/purexfce)

---

### Post by Krytarik on 2011-03-19
> **SteveDee said:**
> Try this: [http://www.psychocats.net/ubuntu/purexfce](http://www.psychocats.net/ubuntu/purexfce)
This may work. However, if you installed xubuntu by the meta-package "xubuntu-desktop", you would have to use this command, note the "--reinstall" option at the end:
```
sudo apt-get remove ace-of-penguins aqualung arj cheese cheese-common chromium-browser chromium-browser-inspector chromium-browser-l10n chromium-codecs-ffmpeg esound-clients esound-common galculator giblib1 gnome-bluetooth gnome-disk-utility gnome-mplayer gnome-power-manager gpicview hardinfo leafpad libaudio2 libaudiofile0 libavcodec52 libavformat52 libavutil50 libcddb2 libcompfaceg1 libdca0 libdirectfb-1.2-9 libdiscid0 libdvdnav4 libdvdread4 libenca0 libesd0 libfm-gtk0 libfm0 libgdu-gtk0 libgif4 libgpgme11 libgringotts2 libgsm1 libical0 libid3tag0 libifp4 libimlib2 liblircclient0 liblrdf0 liblzo2-2 libmad0 libmcrypt4 libmenu-cache1 libmhash2 libmodplug1 libmp3lame0 libmpcdec6 libmusicbrainz3-6 libneon27-gnutls libobparser21 libobrender21 liboggz2 libonig2 libopenal1 libpisock9 libpostproc51 libpth20 libraptor1 librpm1 librpmbuild1 librpmio1 libschroedinger-1.0-0 libsdl1.2debian libsdl1.2debian-alsa libsvga1 libswscale0 libtar libts-0.0-0 libuniconf4.6 libva1 libvdpau1 libvpx0 libwvstreams4.6-base libwvstreams4.6-extras libx264-98 libxvidcore4 lubuntu-artwork lubuntu-core lubuntu-default-settings lubuntu-desktop lubuntu-icon-theme lxappearance lxde-common lxde-core lxdm lxinput lxlauncher lxmenu-data lxpanel lxpanel-indicator-applet-plugin lxrandr lxsession lxsession-edit lxshortcut lxtask lxterminal mplayer mtpaint ntp obconf obexd-client openbox openbox-themes osmo p7zip-full pcmanfm plymouth-theme-lubuntu-logo powernowd rpm rpm-common rpm2cpio scrot sylpheed sylpheed-i18n transmission transmission-cli tsconf wvdial xarchiver xpad && sudo apt-get install --reinstall xubuntu-desktop
```
Greetings.

---

### Post by TNAFan on 2011-03-19
TY Krytarik!

---

