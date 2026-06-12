---
title: "[Ubuntu 13.04] Problems reinstalling Unity after uninstalling Gnome"
date: 2013-07-05
forum: Desktop Environments
---

### Post by mslinn on 2013-07-05
I originally installed the default Ubuntu 13.04 desktop with Unity. Later I installed the complete Gnome package. Because this installation runs under Vmware Workstation, I found loads > 5 were common, so I want to go back to Unity. Here is an edited version of the history. For a while, upon bootup, I first saw only a blue square for a second then I only saw a black screen after that. I could log in via ssh. After some fussing I restored Gnome. How can I go back to Unity?

  404  sudo apt-get install --reinstall unity-services ubuntu-desktop dconf-tools unity
  405  sudo apt-get install gdm
  407  sudo apt-get install dconf-tools
  408  setsid unity
  409  sudo /usr/lib/nux/unity_support_test -p
  410  sudo apt-get install lightdm lightdm-greeter-example-gtk
  415  sudo reboot
  418  sudo apt-get uninstall gnome-shell
  419  sudo apt-get remove gnome-shell
  420  sudo dpkg-reconfigure lightdm
  421  sudo reboot
  422  sudo apt-get uninstall gnome
  423  sudo apt-get remove gnome
  424  sudo apt-get remove gnome-*
  425  sudo apt-get remove gnome-common
  426  sudo apt-get remove full-gnome3-experience
  427  sudo apt-get remove full-gnome-desktop
  428  sudo dpkg-reconfigure
  429  sudo apt-get install ubuntu-settings
  430  sudo apt-get autoremove
  431  sudo apt-get remove gnome-documents
  432  sudo apt-get remove gnome-boxes
  433  sudo apt-get install overlay-scrollbar*
  434  sudo apt-get install unity
  440  sudo apt-get install unity-reset
  441  sudo apt-get update
  442  dconf reset -f /org/compiz/
  443  sudo apt-get install dconf-tools
  444  dconf reset -f /org/compiz/
  445  sudo unity --reset-icons
  451  sudo unity --reset-icons &disown
  452  sudo reboot
  453  sudo apt-get install --reinstall unity-services
  454  sudo apt-get install ubuntu-desktop
  455  sudo apt-get autoremove
  456  sudo apt-get install dconf-tools
  457  dconf reset -f /org/compiz/
  460  sudo unity --reset-icons
  461  unity --reset-icons
  462  sudo apt-get install dconf-tools
  467  sudo apt-get update && sudo apt-get upgrade
  468  sudo apt-get autoremove
  469  sudo reboot
  472  sudo apt-get remove unity
  473  sudo apt-get install ubuntu-desktop unity
  477  sudo dpkg-reconfigure
  478  sudo dpkg-reconfigure gdm
  480  sudo gdm&
  481  sudo apt-get remove compizconfig-settings-manager
  482  sudo apt-get remove compiz-fusion-plugins-extra
  483  sudo apt-get remove compiz-plugins-extra
  484  sudo apt-get purge compiz*
  485  sudo apt-get install unity-2d
  486  sudo apt-get install ubuntu-desktop
  487  sudo apt-get install ubuntu-desktop-2d
  488  sudo apt-get install ubuntu-desktop-2d
  489  sudo apt-get install compizconfig-settings-manager
  490  sudo apt-get install xserver-xgl
  491  sudo apt-get install emerald
  492  sudo apt-get install compiz-fusion-plugins-extra
  493  sudo apt-get install git compiz-plugins-extra
  494  sudo apt-get install compiz-plugins-extra
  495  sudo apt-get install unity
  496  gconftool-2 --recursive-unset /apps/compiz-1
  497  gconftool-2 --recursive-unset /apps/compizconfig-1
  498  unity --reset
  499  unity --reset-icons


Here is how I restored Gnome:

  490  sudo aptitude update
  491  sudo apt-get install aptitude
  492  sudo apt-get install dselect
  493  sudo dselect access
  494  sudo dselect update
  495  sudo apt-get dselect-upgrade
  496  sudo apt-get dselect-update
  497  sudo aptitude upgrade
  498  sudo apt-get autoremove
  499  sudo apt-get autoclean
  500  sudo reboot

Is there a way forward?

---

### Post by dino99 on 2013-07-05
unity needs gnome by the way; so what you are doing make no sense.

---

### Post by mslinn on 2013-07-05
If you know how to restore Unity, then you would be more helpful if you offered a suggestion.

---

