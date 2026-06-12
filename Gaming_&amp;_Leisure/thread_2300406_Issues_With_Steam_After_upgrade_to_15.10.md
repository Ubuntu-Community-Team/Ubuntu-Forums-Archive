---
title: "Issues With Steam After upgrade to 15.10"
date: 2015-10-25
forum: Gaming &amp; Leisure
---

### Post by Urgazhi on 2015-10-25
I upgraded my desktop to 15.10 today, and had a few issues.

The upgrade uninstalled steam, libgl1-mesa-dri:i386, and libgl1-mesa-glx:i386

Attempting to reinstall those packages results in the requirement for libdrm-amdgpu1:i386.

Trying install those results in the following...
```

sudo apt-get install libgl1-mesa-dri:i386 libgl1-mesa-glx:i386 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libgl1-mesa-dri:i386 : Depends: libdrm-amdgpu1:i386 (>= 2.4.63) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

Which results in...

urgazhi@urgazhi-Aurora:~$ sudo apt-get install libgl1-mesa-dri:i386 libgl1-mesa-glx:i386 libdrm-amdgpu1:i386 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  bluez-obexd brasero-common cheese-common dvd+rw-tools growisofs gstreamer1.0-pulseaudio libabw-0.1-1v5 libarmadillo5 libarpack2 libbasicusageenvironment0
  libcamel-1.2-52 libcddb2 libchromaprint0 libctemplate2v5 libdap17v5 libdapclient6v5 libdvbpsi10 libe-book-0.1-1 libebml4v5 libebook-contacts-1.2-1
  libedataserver-1.2-20 libepsilon1 libetonyek-0.1-1 libfreerdp-cache1.1 libfreerdp-client1.1 libfreerdp-codec1.1 libfreerdp-common1.1.0 libfreerdp-core1.1
  libfreerdp-crypto1.1 libfreerdp-gdi1.1 libfreerdp-locale1.1 libfreerdp-primitives1.1 libfreerdp-utils1.1 libfreexl1 libgdal1i libgeos-3.5.0 libgeos-c1v5
  libgif4 libgles1-mesa libgles2-mesa libgmime-2.6-0 libgroupsock1 libgtkmm-2.4-1v5 libgtksourceview-3.0-common libhdf4-0-alt libhdf5-10 libinput10
  libiso9660-8 libkmlbase1 libkmldom1 libkmlengine1 liblircclient0 liblivemedia23 liblwgeom-2.1.8 libmatroska6v5 libminiupnpc10 libminizip1 libmwaw-0.3-3v5
  libmysqlcppconn7v5 libnetcdf7 libodbc1 libodfgen-0.1-1v5 libogdi3.2 libopenjp2-7 liborcus-0.10-0v5 libpcre16-3 libpcrecpp0v5 libpostproc-ffmpeg53 libpq5
  libproj9 libproxy-tools libqqwing2v5 libqt5core5a libqt5dbus5 libquvi-scripts libquvi7 libresid-builder0c2a libsidplay2v5 libspatialite7 libssh2-1
  libsuperlu4 libtinyxml2.6.2v5 libtotem-plparser-common libtotem-plparser18 libupnp6 liburiparser1 libusageenvironment1 libva-drm1 libva-x11-1 libvcdinfo0
  libvlc5 libvlccore8 libvncclient1 libvsqlitepp3v5 libwinpr-crt0.1 libwinpr-dsparse0.1 libwinpr-environment0.1 libwinpr-file0.1 libwinpr-handle0.1
  libwinpr-heap0.1 libwinpr-input0.1 libwinpr-interlocked0.1 libwinpr-library0.1 libwinpr-path0.1 libwinpr-pool0.1 libwinpr-registry0.1 libwinpr-rpc0.1
  libwinpr-sspi0.1 libwinpr-synch0.1 libwinpr-sysinfo0.1 libwinpr-thread0.1 libwinpr-utils0.1 libwpd-0.10-10 libwpd-0.10-10v5 libwpg-0.3-3 libwps-0.4-4
  libxcb-composite0 libxcb-icccm4 libxcb-image0 libxcb-keysyms1 libxcb-randr0 libxcb-render-util0 libxcb-xkb1 libxcb-xv0 libxerces-c3.1 libxkbcommon-x11-0
  libzip4 mysql-utilities mysql-workbench-data ocl-icd-libopencl1 odbcinst odbcinst1debian2 proj-bin proj-data python-mysql.connector python-pyodbc
  python-pysqlite2 python3-bs4 python3-html5lib python3-lxml qttranslations5-l10n vlc-data vlc-nox vlc-plugin-notify vlc-plugin-samba
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libbsd0:i386 libdrm-intel1:i386 libdrm-nouveau2:i386 libdrm-radeon1:i386 libdrm2:i386 libedit2:i386 libelf1:i386 libexpat1:i386 libffi6:i386
  libglapi-mesa:i386 libllvm3.6v5:i386 libpciaccess0:i386 libstdc++6:i386 libtxc-dxtn-s2tc0:i386 libx11-6:i386 libx11-xcb1:i386 libxau6:i386 libxcb-dri2-0:i386
  libxcb-dri3-0:i386 libxcb-glx0:i386 libxcb-present0:i386 libxcb-sync1:i386 libxcb1:i386 libxdamage1:i386 libxdmcp6:i386 libxext6:i386 libxfixes3:i386
  libxshmfence1:i386 libxxf86vm1:i386
The following packages will be REMOVED:
  abiword abiword-plugin-grammar adwaita-icon-theme apport-gtk blueman brasero brasero-cdrkit catfish evince file-roller gcr gir1.2-appindicator3-0.1
  gir1.2-cheese-3.0 gir1.2-clutter-1.0 gir1.2-cogl-1.0 gir1.2-coglpango-1.0 gir1.2-gtk-3.0 gir1.2-gtkclutter-1.0 gir1.2-vte-2.90 gir1.2-vte-2.91
  gir1.2-webkit-3.0 gir1.2-wnck-3.0 gnome-calculator gnome-icon-theme gnome-icon-theme-full gnome-icon-theme-symbolic gnome-keyring gnome-mines gnome-sudoku
  gnome-system-tools gnome-themes-standard gnome-themes-standard-data gnome-user-guide gnomine gnumeric gnumeric-doc gstreamer1.0-clutter
  gstreamer1.0-plugins-bad-videoparsers gtk-theme-config gucharmap gvfs gvfs-backends gvfs-daemons gvfs-fuse humanity-icon-theme indicator-application
  language-selector-gnome libabiword-3.0 libappindicator3-1 libbrasero-media3-1 libcanberra-gtk3-0 libcanberra-gtk3-module libchamplain-0.12-0
  libchamplain-gtk-0.12-0 libcheese7 libclutter-1.0-0 libclutter-gst-2.0-0 libclutter-gtk-1.0-0 libcogl-pango20 libcogl-path20 libcogl20 libdrm-amdgpu1
  libegl1-mesa libevdocument3-4 libevview3-3 libgail-3-0 libgbm1 libgcr-ui-3-1 libgl1-mesa-dri libgl1-mesa-glx libglew1.10 libglu1-mesa libgnome-desktop-3-10
  libgoffice-0.10-10 libgrip0 libgstreamer-plugins-bad1.0-0 libgtk-3-0 libgtk-3-bin libgtk-3-common libgtkmm-3.0-1v5 libgtksourceview-3.0-1 libgucharmap-2-90-7
  libido3-0.1-0 libindicator3-7 libnautilus-extension1a libnm-gtk0 libqt5gui5 libqt5widgets5 libqt5x11extras5 libreoffice-base-core libreoffice-calc
  libreoffice-core libreoffice-gtk libreoffice-math libreoffice-writer libvisual-0.4-plugins libvte-2.90-9 libvte-2.91-0 libwayland-egl1-mesa
  libwebkitgtk-1.0-0 libwebkitgtk-3.0-0 libwnck-3-0 libxfce4panel-2.0-4 libxfce4ui-2-0 libyelp0 light-locker light-locker-settings lightdm-gtk-greeter
  lightdm-gtk-greeter-settings menulibre mesa-utils mesa-vdpau-drivers mousepad mugshot mysql-workbench network-manager-gnome network-manager-pptp-gnome
  onboard onboard-data oneconf parole pavucontrol policykit-1-gnome python-aptdaemon.gtk3widgets python-ubuntu-sso-client python3-aptdaemon.gtk3widgets
  python3-uno sessioninstaller simple-scan software-center software-properties-gtk system-config-printer-gnome transmission-gtk ubuntu-mono
  ubuntu-release-upgrader-gtk ubuntu-sso-client update-manager update-notifier usb-creator-gtk va-driver-all vdpau-va-driver vlc x11-utils xdg-user-dirs-gtk
  xfce4-indicator-plugin xfpanel-switch xorg xserver-xorg xserver-xorg-core xserver-xorg-input-all xserver-xorg-input-evdev xserver-xorg-input-mouse
  xserver-xorg-input-synaptics xserver-xorg-input-vmmouse xserver-xorg-input-wacom xserver-xorg-video-ati xserver-xorg-video-cirrus xserver-xorg-video-fbdev
  xserver-xorg-video-intel xserver-xorg-video-mach64 xserver-xorg-video-mga xserver-xorg-video-neomagic xserver-xorg-video-nouveau
  xserver-xorg-video-openchrome xserver-xorg-video-qxl xserver-xorg-video-r128 xserver-xorg-video-radeon xserver-xorg-video-s3 xserver-xorg-video-savage
  xserver-xorg-video-siliconmotion xserver-xorg-video-sisusb xserver-xorg-video-tdfx xserver-xorg-video-trident xserver-xorg-video-vesa
  xserver-xorg-video-vmware xubuntu-core xubuntu-default-settings xubuntu-desktop yelp zenity
The following NEW packages will be installed:
  libbsd0:i386 libdrm-amdgpu1:i386 libdrm-intel1:i386 libdrm-nouveau2:i386 libdrm-radeon1:i386 libdrm2:i386 libedit2:i386 libelf1:i386 libexpat1:i386
  libffi6:i386 libgl1-mesa-dri:i386 libgl1-mesa-glx:i386 libglapi-mesa:i386 libllvm3.6v5:i386 libpciaccess0:i386 libstdc++6:i386 libtxc-dxtn-s2tc0:i386
  libx11-6:i386 libx11-xcb1:i386 libxau6:i386 libxcb-dri2-0:i386 libxcb-dri3-0:i386 libxcb-glx0:i386 libxcb-present0:i386 libxcb-sync1:i386 libxcb1:i386
  libxdamage1:i386 libxdmcp6:i386 libxext6:i386 libxfixes3:i386 libxshmfence1:i386 libxxf86vm1:i386
0 upgraded, 32 newly installed, 180 to remove and 0 not upgraded.
Need to get 4,870 kB/15.4 MB of archives.
After this operation, 612 MB disk space will be freed.
Do you want to continue? [Y/n] 

```

I clearly don't want to do that...  

According to this site ([http://www.ubuntuupdates.org/package/core/wily/multiverse/proposed/steam](http://www.ubuntuupdates.org/package/core/wily/multiverse/proposed/steam)) Steam isn't even supposed to be in the repository...

Thoughts?

---

### Post by oldrocker99 on 2015-10-26
I just installed 15.10 (MATE) and the Steam install went without a hitch. Did you upgrade or was it a new installation? Upgrades are notoriously hinky.

---

### Post by Urgazhi on 2015-10-26
It was an upgrade.  I just find it odd that those packages were uninstalled, and attempting to install them wants to cause a rollback on just about every program installed during the upgrade.

According to dpkg --list  Those packages were all set to rc (removed with configuration files left behind) but purging them did not help at all.

I have an AMD card in there, and installing the propitiatory drivers before steam does not work (though nvidia ships with the 32 bit libGL file, I think?)
lshw -c Display shows the following.
```

*-display               
       description: VGA compatible controller
       product: Barts PRO [Radeon HD 6850]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:08:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:29 memory:d0000000-dfffffff memory:fbfc0000-fbfdffff ioport:e000(size=256) memory:fbfa0000-fbfbffff

```

Alright

So I figured out what the issue was.

I had the [https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers](https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers) PPA installed

I ran their purge PPA and thought it had downgraded everything, but it didn't.

So when I attempted to run 

```

urgazhi@urgazhi-Aurora:~$ sudo aptitude install steam
Note: selecting "steam:i386" instead of the
      virtual package "steam"
The following NEW packages will be installed:
  libbsd0:i386{a} libdrm-amdgpu1:i386{ab} libdrm-intel1:i386{a} libdrm-nouveau2:i386{a} libdrm-radeon1:i386{a} libdrm2:i386{a} libedit2:i386{a} 
  libelf1:i386{a} libexpat1:i386{a} libffi6:i386{a} libgl1-mesa-dri:i386{a} libgl1-mesa-glx:i386{a} libglapi-mesa:i386{a} libllvm3.6v5:i386{a} 
  libpciaccess0:i386{a} libstdc++6:i386{a} libtxc-dxtn-s2tc0:i386{a} libx11-6:i386{a} libx11-xcb1:i386{a} libxau6:i386{a} libxcb-dri2-0:i386{a} 
  libxcb-dri3-0:i386{a} libxcb-glx0:i386{a} libxcb-present0:i386{a} libxcb-sync1:i386{a} libxcb1:i386{a} libxdamage1:i386{a} libxdmcp6:i386{a} 
  libxext6:i386{a} libxfixes3:i386{a} libxinerama1:i386{a} libxshmfence1:i386{a} libxxf86vm1:i386{a} steam:i386 
0 packages upgraded, 34 newly installed, 0 to remove and 0 not upgraded.
Need to get 5,752 kB/16.3 MB of archives. After unpacking 144 MB will be used.
The following packages have unmet dependencies:
 libdrm-amdgpu1 : Breaks: libdrm-amdgpu1:i386 (!= 2.4.65+git1510161830.304552~gd~v) but 2.4.64-1 is to be installed.
 libdrm-amdgpu1:i386 : Breaks: libdrm-amdgpu1 (!= 2.4.64-1) but 2.4.65+git1510161830.304552~gd~v is installed.
The following actions will resolve these dependencies:

     Keep the following packages at their current version:
1)     libdrm-amdgpu1:i386 [Not Installed]                
2)     libgl1-mesa-dri:i386 [Not Installed]               
3)     libgl1-mesa-glx:i386 [Not Installed]               
4)     steam:i386 [Not Installed]                         



Accept this solution? [Y/n/q/?] y
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B of archives. After unpacking 0 B will be used.

```

I noticed the GIT versions...

```

sudo add-apt-repository ppa:oibaf/graphics-drivers

```

and then 
```

urgazhi@urgazhi-Aurora:~$ sudo apt-get install steam
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libbsd0:i386 libdrm-amdgpu1:i386 libdrm-intel1:i386 libdrm-nouveau2:i386 libdrm-radeon1:i386 libdrm2:i386 libedit2:i386 libelf1:i386 libexpat1:i386
  libffi6:i386 libgl1-mesa-dri:i386 libgl1-mesa-glx:i386 libglapi-mesa:i386 libllvm3.6v5:i386 libnettle6:i386 libpciaccess0:i386 libstdc++6:i386
  libtxc-dxtn-s2tc0:i386 libx11-6:i386 libx11-xcb1:i386 libxau6:i386 libxcb-dri2-0:i386 libxcb-dri3-0:i386 libxcb-glx0:i386 libxcb-present0:i386
  libxcb-sync1:i386 libxcb1:i386 libxdamage1:i386 libxdmcp6:i386 libxext6:i386 libxfixes3:i386 libxinerama1:i386 libxshmfence1:i386 libxxf86vm1:i386
The following NEW packages will be installed:
  libbsd0:i386 libdrm-amdgpu1:i386 libdrm-intel1:i386 libdrm-nouveau2:i386 libdrm-radeon1:i386 libdrm2:i386 libedit2:i386 libelf1:i386 libexpat1:i386
  libffi6:i386 libgl1-mesa-dri:i386 libgl1-mesa-glx:i386 libglapi-mesa:i386 libllvm3.6v5:i386 libnettle6:i386 libpciaccess0:i386 libstdc++6:i386
  libtxc-dxtn-s2tc0:i386 libx11-6:i386 libx11-xcb1:i386 libxau6:i386 libxcb-dri2-0:i386 libxcb-dri3-0:i386 libxcb-glx0:i386 libxcb-present0:i386
  libxcb-sync1:i386 libxcb1:i386 libxdamage1:i386 libxdmcp6:i386 libxext6:i386 libxfixes3:i386 libxinerama1:i386 libxshmfence1:i386 libxxf86vm1:i386 steam:i386
0 upgraded, 35 newly installed, 0 to remove and 0 not upgraded.
Need to get 8,244 kB/18.7 MB of archives.
After this operation, 182 MB of additional disk space will be used.

```

Then it worked!

---

### Post by Bashing-om on 2015-10-26
Urgazhi; Hello;

Currently with FGLRX and steam, we are left high and dry by AMD in release 15.10.
See the release notes for 15.10:
[https://wiki.ubuntu.com/WilyWerewolf/ReleaseNotes](https://wiki.ubuntu.com/WilyWerewolf/ReleaseNotes)
and the bug report there in respect to your situation.
Please add your voice to the report.

Keep in mind that the FGLRX driver is proprietary to AMD, we in the open source world have no control over their software. We have to await on what AMD can do and will do .

[INDENT][INDENT]not good
[INDENT][INDENT][INDENT]just the way it is
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Urgazhi on 2015-10-26
Thankfully I was not using the fglrx driver when I upgraded.  I switched to the open source driver because the fglrx driver had issues with dragging windows between my multi-monitor setup.

I would like to see openGL 4.0 support for the HD6850, which would allow most people to get away from the proprietary drivers, in my opinion.

Thank you for your input!

---

