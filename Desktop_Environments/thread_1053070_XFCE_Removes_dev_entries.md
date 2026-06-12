---
title: "XFCE Removes /dev/ entries"
date: 2009-01-28
forum: Desktop Environments
---

### Post by Nunim on 2009-01-28
I've recently setup a Ubuntu VPS (8.04) and everything works well until I try to install a desktop environment(in this case XFCE4).  I used the command apt-get install xfce4 and it appears to work, however upon reboot many entries are removed from /dev/ including random, unrandom and null. This results in the OpenSSH-Server being unable to start so I am more or less limited on my interaction with the VPS after this point since I am forced to rely upon a web interface to issue commands. Why is this happening and is there an easy way to restore all devices?

>  acl busybox-initramfs consolekit dbus dbus-x11 desktop-file-utils fontconfig
  fortune-mod fortunes-min gamin gconf2-common gtk2-engines-xfce hal hal-info
  hicolor-icon-theme initramfs-tools libatk1.0-0 libcairo2 libcupsys2
  libdatrie0 libdbus-glib-1-2 libexif12 libexo-0.3-0 libgamin0 libgconf2-4
  libglib2.0-0 libgtk2.0-0 libgtk2.0-common libhal-storage1 libidl0 libnotify1
  liborbit2 libpango1.0-0 libpango1.0-common libpcre3 libpolkit-dbus2
  libpolkit-grant2 libpolkit2 librecode0 libsmbios1 libstartup-notification0
  libthai-data libthai0 libthunar-vfs-1-2 libtiff4 liburi-perl libvolume-id0
  libxfce4mcs-client3 libxfce4mcs-manager3 libxfce4util4 libxfcegui4-4
  libxklavier12 libxml2 module-init-tools pciutils pm-utils policykit
  powermgmt-base shared-mime-info thunar thunar-data udev usbutils xfce4
  xfce4-icon-theme xfce4-mcs-manager xfce4-mcs-plugins xfce4-panel
  xfce4-session xfce4-utils xfdesktop4 xfdesktop4-data xfwm4


After those packages are installed and I reboot the container, the dev entries are removed so OpenSSH-Server, among other things, fails to work properly.  I've tried using the command mknod /dev/random c 1 9, and others to recreate some of the missing files but these are also deleted after a system reboot.

---

