---
title: "[SOLVED] GNOME without all the extra software"
date: 2008-11-21
forum: Desktop Environments
---

### Post by djbushido on 2008-11-21
Is there a way to get GNOME desktop environment without all the extra software that I won't use? I'm not above recompiling myself by the way...

---

### Post by Linteg on 2008-11-21
Try uninstalling the individual apps in synaptic, gnome is rather modular. Just make sure that you don't remove anything needed by gnome itself.
Compiling something as big as gnome from source is not trivial and I would advise you not to.

---

### Post by rsambuca on 2008-11-21
You don't have to recompile anything, you can just use Synaptic to remove the programs you don't want.  Many of the gnome programs will be part of the meta-package called ubuntu-desktop.  Just keep in mind that you will have to re-install ubuntu-desktop prior to upgrading to a newer version of Ubuntu in the future.

---

### Post by kerry_s on 2008-11-21
> **djbushido said:**
> Is there a way to get GNOME desktop environment without all the extra software that I won't use? I'm not above recompiling myself by the way...

custom install:
[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

---

### Post by rsambuca on 2008-11-21
Definitely building up from a minimal installation would be best, if you are willing to start over.  My feeling is that if you are going to go that route, then perhaps there are other distros that would be better suited to your needs.

---

### Post by djbushido on 2008-11-22
I really like ubuntu as a distro (i actually use xubuntu, so that's why i have all of the extra software), but will look at setting up gnome and then taking out what i don't need. By the way, is the "gnome" in synaptic just a meta-package?

---

### Post by Linteg on 2008-11-22
> **djbushido said:**
> By the way, is the "gnome" in synaptic just a meta-package?
Yes

---

### Post by Bucky Ball on 2008-11-22
You install ubuntu server edition. It has nothing! (well, pretty much). Not even gnome. You can just load gnome from the terminal in a fresh server install and you are away. Create your blend. :)

---

### Post by armageddon08 on 2008-11-22
> **Bucky Ball said:**
> You install ubuntu server edition. It has nothing! (well, pretty much). Not even gnome. You can just load gnome from the terminal in a fresh server install and you are away. Create your blend. :)

After that I think this should help:
```
sudo aptitude install ubuntu-desktop --without-recommends
```

---

### Post by aysiu on 2008-11-22
If you already have standard Ubuntu installed and you want only the essential Gnome with nothing extra (and I mean *nothing* extra), paste this command into [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
sudo apt-get remove acpi acpid acpi-support alacarte alsa-base alsa-utils anacron apmd app-install-data-commercial apport-gtk avahi-autoipd avahi-daemon bc bluez-cups bluez-gnome bluez-utils bogofilter brasero brltty brltty-x11 ca-certificates cdparanoia compiz consolekit contact-lookup-applet cups cups-bsd cups-client cups-driver-gutenprint dc dcraw deskbar-applet desktop-file-utils doc-base dvd+rw-tools ekiga espeak evince evolution evolution-exchange evolution-plugins evolution-webcal example-content fast-user-switch-applet file-roller firefox firefox-gnome-support foo2zjs foomatic-db foomatic-db-engine foomatic-db-hpijs foomatic-filters fortune-mod f-spot gcalctool gcc gconf-editor gdebi gdm gdm-guest-session genisoimage ghostscript-x gimp gnome-about gnome-accessibility-themes gnome-app-install gnome-games gnome-mag gnome-media gnome-netstatus-applet gnome-nettool gnome-orca gnome-pilot-conduits gnome-power-manager gnome-screensaver gnome-spell gnome-system-monitor gnome-system-tools gnome-themes gnome-user-guide gnome-utils gstreamer0.10-alsa gstreamer0.10-plugins-base-apps gstreamer0.10-pulseaudio gstreamer0.10-schroedinger gtk2-engines gtk2-engines-pixbuf gucharmap gvfs-fuse hal hal-cups-utils hotkey-setup hplip hwtest-gtk im-switch inputattach jockey-gtk language-selector laptop-detect launchpad-integration lftp libcanberra-gnome libdeskbar-tracker libgl1-mesa-dri libgl1-mesa-glx libglut3 libgnome2-perl libgnomevfs2-bin libgnomevfs2-extra libnss-mdns libpam-ck-connector libpam-gnome-keyring libpt-1.10.10-plugins-v4l libpt-1.10.10-plugins-v4l2 libsasl2-modules libxp6 linux-headers-generic make min12xxw mousetweaks nautilus-cd-burner nautilus-sendto nautilus-share network-manager-gnome notification-daemon onboard openoffice.org-calc openoffice.org-gnome openoffice.org-impress openoffice.org-math openoffice.org-writer openprinting-ppds pcmciautils pidgin pidgin-otr pnm2ppa powermanagement-interface powernowd pulseaudio pulseaudio-esound-compat pulseaudio-module-gconf pulseaudio-module-hal pulseaudio-module-x11 pxljr readahead rhythmbox rss-glx scim scim-bridge-agent scim-bridge-client-gtk scim-gtk2-immodule screen screensaver-default-images seahorse smbclient software-properties-gtk splix ssh-askpass-gnome synaptic system-config-printer-gnome tangerine-icon-theme tomboy totem totem-mozilla tracker tracker-search-tool transmission-gtk tsclient ttf-arabeyes ttf-arphic-uming ttf-bitstream-vera ttf-dejavu-core ttf-freefont ttf-indic-fonts-core ttf-kochi-gothic ttf-kochi-mincho ttf-lao ttf-thai-tlwg ttf-unfonts-core ubufox ubuntu-artwork ubuntu-docs ubuntu-sounds unzip update-manager update-notifier usb-creator usplash usplash-theme-ubuntu vinagre vino wireless-tools wodim wpasupplicant wvdial xcursor-themes xdg-user-dirs xdg-user-dirs-gtk xdg-utils xkb-data xorg xsane xscreensaver-data xscreensaver-gl xterm x-ttcidfont-conf zenity zip && sudo apt-get install gnome-core
```

---

### Post by rsambuca on 2008-11-22
> **Bucky Ball said:**
> You install ubuntu server edition. It has nothing! (well, pretty much). Not even gnome. You can just load gnome from the terminal in a fresh server install and you are away. Create your blend. :)

If you are going to use this for a desktop pc, then I would suggest doing the command line installation from the alternate desktop CD rather than the server edition.  The server edition and the desktop edition have different kernels optimized for each particular use.  Both can be used, but you may as well use the one that is better tweaked for your system.  A command line installation is not necessarily the same as a server installation.

---

### Post by djbushido on 2008-11-22
I think I will try to uninstall most of the GNOME stuff and then just install ubuntu-desktop --without-recommends. However, the server edition would probably work, I just don't want to do another re-install - I have currently installed a variation of ubuntu ~7 times before I finally got one working, and I don't want to do that again.

---

