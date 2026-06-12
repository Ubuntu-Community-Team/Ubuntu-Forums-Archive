---
title: "User permission for poweroff, reboot, depends - LXDE"
date: 2011-06-12
forum: Desktop Environments
---

### Post by volkswagner on 2011-06-12
What is required for user to get available Logout Menu options for poweroff, restart, sleep, etc.?

I have a fresh install of 11.04 >minimal which I added LXDE using:

```
aptitude install --without-recommends xserver-xorg-video-geode xinit xauth x11-utils xfonts-base x11-xserver-utils
```

```
aptitude install --without-recommends lxde
```

Selected yes at the following output:

```
The following NEW packages will be installed:
  fontconfig{a} gpicview{a} gtk2-engines{a} leafpad{a} libasound2{a} libatk1.0-0{a} libatk1.0-data{a} libavahi-client3{a} libavahi-common-data{a} 
  libavahi-common3{a} libcups2{a} libdatrie1{a} libfm-gtk0{a} libfm0{a} libgdk-pixbuf2.0-0{a} libglade2-0{a} libgtk2.0-0{a} libgtk2.0-common{a} 
  libjasper1{a} libjpeg62{a} liblua5.1-0{a} libmenu-cache1{a} libobparser21{a} libobrender21{a} libpango1.0-0{a} libpython2.7{a} 
  libstartup-notification0{a} libthai-data{a} libthai0{a} libtiff4{a} libvte-common{a} libvte9{a} libxcb-aux0{a} libxcb-event1{a} lxappearance{a} lxde 
  lxde-common{a} lxde-core{a} lxde-icon-theme{a} lxinput{a} lxmenu-data{a} lxpanel{a} lxrandr{a} lxsession{a} lxsession-edit{a} lxshortcut{a} 
  lxterminal{a} obconf{a} openbox{a} pcmanfm{a} shared-mime-info{a} xarchiver{a} 
The following packages are RECOMMENDED but will NOT be installed:
  arj arora chimera2 chromium-browser edbrowse elinks elinks-lite elvis elvis-console epiphany-browser firefox galculator gdm gksu gvfs-backends 
  gvfs-fuse hicolor-icon-theme kdm konqueror libgtk2.0-bin lightdm links links2 lxdm lxmusic lynx-cur manpages-dev menu-xdg midori netrik netsurf 
  openbox-themes p7zip-full policykit-1-gnome rekonq rpm scrot seamonkey-browser slim unzip uzbl w3m wdm x-ttcidfont-conf xdg-utils xdm xemacs21-mule 
  xemacs21-mule-canna-wnn xemacs21-nomule xscreensaver xserver-xorg zip 
0 packages upgraded, 52 newly installed, 0 to remove and 0 not upgraded.
Need to get 14.4 MB of archives. After unpacking 47.9 MB will be used.
Do you want to continue? [Y/n/?] 
```


What stood out for me was... policykit-1-gnome.  I installed it and 
now root user gets the added options for shutdown and restart.

So how do I get regular user (with sudo priv. via admin group option) options for shutdown in LXDE?

Do any of the recommended packages look necessary for this?

I'm not sure yet how I will accomplish, since there still is no powerdev or any group created by adding
policykit.

I also added consolekit, but I'm not sure if that was necessary.

consolekit added messagebus group and policykit added no groups to /etc/group.

I have had this working with Debian without a login manager.  Is a login manager now required?

---

### Post by volkswagner on 2011-06-26
So so sad.  How can Ubuntu or any Linux distro become mainstream if internal workings are a mystery?

It seems from my limited knowledge that LXDM package is now required to get shutdown options.  I tried XDM and LightDM both of which did not grant user shutdown options in logout menu.

I don't see any package included in LXDM that allows this.

```
webdt@natty:~$ sudo aptitude install -s lxdm -R 
The following NEW packages will be installed:
  gtk2-engines-pixbuf{a} libcroco3{a} librsvg2-2{a} librsvg2-common{a} lxdm 
0 packages upgraded, 5 newly installed, 0 to remove and 0 not upgraded.
Need to get 428 kB of archives. After unpacking 2,716 kB will be used.
```

Why can't anyone on #ubunutu, #lxde, and UbuntuForums offer any incite?

If LXDM is required for shutdown shouldn't the dependency move from recommended to required?  

Shall I file a bug report on this?

---

