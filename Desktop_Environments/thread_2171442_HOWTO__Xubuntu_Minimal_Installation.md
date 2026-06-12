---
title: "HOWTO:  Xubuntu Minimal Installation"
date: 2013-08-30
forum: Desktop Environments
---

### Post by fredbird67 on 2013-08-30
I'm in the process of creating a Linux distribution in my spare time.  Xfce is my personal favorite desktop environments, but I don't like how Canonical insists on bloating it up in Xubuntu.  As a result, Xubuntu has destroyed Xfce's reputation of being a lightweight desktop environment thanks to its bloat.  But I'm here to show y'all how to create a TRULY lightweight yet fully functional Xfce desktop.  Here's how:

1) Go grab yourself a copy of Ubuntu Mini Remix at [http://www.ubuntu-mini-remix.org]("http://www.ubuntu-mini-remix.org/") and install it.  NOTE -- Ubuntu Mini Remix WILL need to be burned to a CD and CANNOT be installed from a USB.

2) Install Ubuntu Mini Remix.  When you get close to the end of the installation, you will be presented with a list of pre-defined packages you can install, such as Ubuntu Server, Mail Server, Ubuntu, Kubuntu, Lubuntu, Xubuntu, Mythbuntu, and...well, there are some three dozen or so choices, one of which is for a Lubuntu Minimal Installation (but not one for Xubuntu, which is why I'm doing this).  But don't install ANY of these.  Instead, just skip this step entirely.

3) Once you have finished installing, removed the CD, rebooted, and logged in, run the following command:

```
sudo apt-get install acpi-support alsa-base alsa-utils anacron apport-gtk avahi-daemon ca-certificates dbus-x11 desktop-base desktop-file-utils desktopnova-module-xfce dmz-cursor-theme eject fonts-liberation foomatic-db-compressed-ppds foomatic-filters genisoimage ghostscript-x gnome-disk-utility gnome-keyring gvfs-backends gvfs-fuse hardinfo ibus kerneloops-daemon inputattach laptop-detect libnss-mdns libpam-ck-connector libsasl2-modules libxp6 lightdm lightdm-gtk-greeter lubuntu-software-center mobile-broadband-provider-info modemmanager ntp nvidia-common pavucontrol pcmciautils policykit-desktop-privileges pulseaudio rfkill software-properties-gtk synaptic thunar ttf-dejavu-core ttf-freefont ttf-ubuntu-font-family ubuntu-extras-keyring usb-modeswitch unzip wget wicd wicd-gtk wireless-tools wpasupplicant xfce-keyboard-shortcuts xfce4-mixer xfce4-notifyd xfce4-panel xfce4-power-manager xfce4-screenshooter xfce4-session xfce4-settings xfce4-terminal xfce4-utils xfce4-volumed xfconf xfwm4 xkb-data xorg 
```

Once you've done that, then reboot, and you'll be greeted by LightDM, and once you log in, you'll be at your brand-new Xfce desktop.

Keep in mind that this is VERY bare-bones, as it does not include much of anything else at all.  Also, you'll be presented with a rather ugly-looking desktop with stock Xfce wallpaper, the GNOME icon theme, and the Raleigh GTK theme (the latter two being quite ugly, IMHO) plus you will be asked if you want the default panel layout (across the top AND bottom) or just one empty panel that you can place anywhere to your own personal tastes (I prefer having it along the bottom).  But hey, at least you'll have a completely functional desktop, and you can arrange it and theme it to your heart's content.

---

### Post by GMartin735 on 2013-09-06
How will this handle the PAE issue with older computers.  I was looking at xubuntu 12.0.4 LTS as an upgrade from Ubuntu 11 but wireless driver installs hangs me up.

---

### Post by vasa1 on 2013-09-06
> **fredbird67 said:**
> I'm in the process of creating a Linux distribution in my spare time.  Xfce is my personal favorite desktop environments, but I don't like how **Canonical insists on bloating it up in Xubuntu**.  As a result, Xubuntu has destroyed Xfce's reputation of being a lightweight desktop environment thanks to its bloat.  ....
I suggest you fix the part in bold. Xubuntu is a community distro. If things are misrepresented, it may devalue the rest.

---

