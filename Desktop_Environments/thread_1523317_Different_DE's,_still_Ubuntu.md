---
title: "Different DE's, still Ubuntu?"
date: 2010-07-03
forum: Desktop Environments
---

### Post by KdotJ on 2010-07-03
Okay so, I have a netbook with Ubuntu 10.04 installed on it, then I installed the netbook-launcher via synaptic. After a while, I then installed xfce4 from synaptic (not xubuntu-desktop).

So my question is, What's the difference, if any, between installing xubuntu, and installing ubuntu then installing xfce?
I know that the themes, splash, gdm theme, and default apps are different. But is that it? Is my system still effectively Ubuntu?

---

### Post by SmokeyThePanda on 2010-07-03
Well, in my opinion, even if you were to install Xubuntu, your computer is still Ubuntu. You just have the Xfce stuff instead of Gnome and the Xubuntu defaults instead of Ubuntu defaults. As I just installed a base Ubuntu system, then installed the Xfce defaults, without installing Xubuntu, there is quite a big difference. There are alot less files that are required for running a comfortable Xfce environment than with Xubuntu. Also, if you were to install Xubuntu and wanted to later remove Xfce, it would be highly difficult. Everything in the Xubuntu desktop is linked together by a meta package. So, if you wanted to remove Xfce, it would want to take out several other packages. 

In short, the difference is pretty massive. For convenience purposes, it's best to install the xfce window manager without installing Xubuntu-Desktop. I'm not sure that answered your question, but I tried. :p

---

### Post by KdotJ on 2010-07-03
Thanks for your reply, and yeah you answered it to an extent. I agree with you about the 'mess' of installing it. I found that out when I once installed kubuntu-desktop in ubuntu and ended up with a mash up of KDE apps and gnome apps and some funky configs.

I think I'll just leave it as it is, Ubuntu with Xfce installed on top. And to be fair, I kind of ended up making the Xfce look like gnome anyways...

---

### Post by SmokeyThePanda on 2010-07-03
Yeah. In all honesty, I prefer the gnome desktop over xfce. However, gnome is much more resource heavy, especially on my old computer with the small amount of RAM I have. >.< 

However, if you can get the hang of xfce, it's worth it. I currently have a linux mint theme on mine that I find quite beautiful. Not entirely sure how, but it defaulted onto my firefox as well and now firefox also looks great. xD

---

### Post by nothingspecial on 2010-07-03
```
$ sudo apt-get install xfce4
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  [COLOR=Red]aumix aumix-common desktop-base exo-utils fortune-mod fortunes-min
  gtk2-engines-xfce libexo-0.3-0 libexo-common librecode0 libthunar-vfs-1-2
  libxfce4menu-0.1-0 libxfce4util-bin libxfce4util-common libxfce4util4
  libxfcegui4-4 libxfconf-0-2 orage oss-compat tango-icon-theme thunar
  thunar-data thunar-volman xfce-keyboard-shortcuts xfce4-appfinder
  xfce4-mixer xfce4-panel xfce4-session xfce4-settings xfce4-utils xfconf
  xfdesktop4 xfdesktop4-data xfwm4 xfwm4-themes[/COLOR]
``````

$ sudo apt-get install xubuntu-desktop 
[sudo] password for rob: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:[COLOR=Red]
  a2ps app-install-data-commercial aumix aumix-common catfish exaile exo-utils
  fortune-mod fortunes-min gigolo gimp gimp-data gnumeric gnumeric-common
  gnumeric-doc gtk2-engines-xfce libbabl-0.0-0 libexo-0.3-0 libexo-common
  libgegl-0.0-0 libgimp2.0 libotr2 librecode0 libscim8c2a libsdl1.2debian-alsa
  libthunar-vfs-1-2 libxcb-keysyms1 libxfce4menu-0.1-0 libxfce4util-bin
  libxfce4util-common libxfce4util4 libxfcegui4-4 libxfconf-0-2 mousepad
  murrine-themes orage oss-compat pidgin pidgin-data pidgin-libnotify
  pidgin-otr psutils python-cddb python-mmkeys python-mutagen python-sexy
  ristretto scim scim-bridge-agent scim-bridge-client-gtk scim-gtk2-immodule
  scim-modules-socket tango-icon-theme tango-icon-theme-common tcl thunar
  thunar-archive-plugin thunar-data thunar-media-tags-plugin
  thunar-thumbnailers thunar-volman thunderbird vim-runtime wdiff xchat
  xchat-common xfce-keyboard-shortcuts xfce4-appfinder xfce4-clipman
  xfce4-clipman-plugin xfce4-cpugraph-plugin xfce4-dict xfce4-fsguard-plugin
  xfce4-mailwatch-plugin xfce4-mixer xfce4-mount-plugin xfce4-netload-plugin
  xfce4-notes xfce4-notes-plugin xfce4-panel xfce4-places-plugin
  xfce4-power-manager xfce4-power-manager-data xfce4-quicklauncher-plugin
  xfce4-screenshooter xfce4-session xfce4-settings xfce4-smartbookmark-plugin
  xfce4-systemload-plugin xfce4-terminal xfce4-utils xfce4-verve-plugin
  xfce4-volumed xfce4-weather-plugin xfce4-xkb-plugin xfconf xfdesktop4
  xfdesktop4-data xfprint4 xfswitch-plugin xfwm4 xfwm4-themes xscreensaver
  xubuntu-artwork xubuntu-default-settings xubuntu-docs xubuntu-gdm-theme
  xubuntu-icon-theme xubuntu-plymouth-theme xubuntu-wallpapers[/COLOR]

```The difference is in red.

And I already have abiword, feh ........ etc

---

### Post by KdotJ on 2010-07-03
I run Ubuntu on my laptop, but the issues I have with my netbook is battery life which is why I decided to have look at using Xfce to save resources. I just wish I would find a way to edit the items in the menu's. Some of them are soo long, and in ubuntu I could choose to hide the ones I didn't want.

---

### Post by SmokeyThePanda on 2010-07-03
Give this a try mate. 

[http://wiki.xfce.org/tips#how_to_add_or_remove_applications_in_the_system_menu](http://wiki.xfce.org/tips#how_to_add_or_remove_applications_in_the_system_menu)

---

### Post by KdotJ on 2010-07-03
> **SmokeyThePanda said:**
> Give this a try mate. 

[http://wiki.xfce.org/tips#how_to_add_or_remove_applications_in_the_system_menu](http://wiki.xfce.org/tips#how_to_add_or_remove_applications_in_the_system_menu)

Thanks for the link mate, I'll give it a try

---

