---
title: "I mistakenly purged gsettings-desktop-schemas; how can I recover?"
date: 2016-06-29
forum: Desktop Environments
---

### Post by watchpocket on 2016-06-29
Here's how things went from bad to worse:

I wanted to remove an item (an icon) on the Unity-greeter top panel. (The greeter is the only Unity thing I use).  So I made some changes in one of the Unity-greeter config files, or lightdm config files (I forget which).  This left me in low-graphics mode.

Then, I stupidly and quite mistakenly ran this command:

```
sudo apt-get purge gsettings-desktop-schemas && apt-get install gsettings-desktop-schemas
```

Then I watched tons of things being purged.  Then I had no online connectivity, and still don't, from my Ubuntu Mate 14.04 drive.  I (also stupidly) appear to have no backup of my 14.04.

I *can* -- from my Ubuntu Mate 16.04 disk --  mount the drive that has 14.04 on it and access it that way.  My question:

[I][B]How can I:

 (a) get back online; 

(b) recover gsettings-desktop-schemas; 

and (c) get lightdm/unity-greeter running back in graphics mode?
[/B][/I]
Would it make any sense for me to try to copy my 16.04 (or 12.04) "gsettings-desktop-schemas" over to the 14.04 system?  (though I don't know where to look for it).

I really seem to have wandered into no-man's-land, & need to get on the right path.  *Any help appreciated*.

---

### Post by CantankRus on 2016-06-29
Wow,
Just simulated uninstalling gsettings-desktop-schemas....
```
The following packages will be REMOVED:
  a11y-profile-manager-indicator activity-log-manager adwaita-icon-theme aisleriot altyo apport-gtk apturl arc-theme-solid ardesia audio-recorder bamfdaemon baobab bluez-obexd
  boot-repair boot-sav boot-sav-extra cairo-dock cairo-dock-core cairo-dock-plug-ins cairo-dock-plug-ins-dbus-interface-python cairo-dock-plug-ins-integration checkbox-converged
  checkbox-gui cheese clementine compiz compiz-gnome dconf-editor deja-dup easystroke easytag eog evince evince-common evolution-data-server-online-accounts file-roller firefox
  fwupd gcr gdebi gedit gedit-dev gedit-plugins geoclue-2.0 geoclue-ubuntu-geoip gir1.2-appindicator3-0.1 gir1.2-clutter-1.0 gir1.2-geocodeglib-1.0 gir1.2-gnomedesktop-3.0
  gir1.2-gtk-3.0 gir1.2-gtkclutter-1.0 gir1.2-gtksource-3.0 gir1.2-gucharmap-2.90 gir1.2-gweather-3.0 gir1.2-nautilus-3.0 gir1.2-nemo-3.0 gir1.2-panelapplet-5.0 gir1.2-peas-1.0
  gir1.2-rb-3.0 gir1.2-soup-2.4 gir1.2-vte-2.91 gir1.2-webkit-3.0 gir1.2-webkit2-4.0 gir1.2-wnck-3.0 gjs gkbd-capplet glade2script glib-networking gloobus-preview gnome-applets
  gnome-bluetooth gnome-calculator gnome-calendar gnome-disk-utility gnome-flashback gnome-font-viewer gnome-icon-theme gnome-keyring gnome-mahjongg gnome-mines gnome-orca
  gnome-panel gnome-power-manager gnome-screensaver gnome-screenshot gnome-session gnome-session-bin gnome-session-canberra gnome-session-flashback gnome-settings-daemon
  gnome-software gnome-sudoku gnome-system-log gnome-system-monitor gnome-terminal gnome-themes-standard gnome-themes-standard-data gnome-user-guide gnome-user-share
  gnome-video-effects gnome-weather gnote grilo-plugins-0.2-base gsettings-desktop-schemas gsettings-desktop-schemas-dev gstreamer0.10-plugins-good gstreamer1.0-clutter-3.0
  gstreamer1.0-plugins-bad gstreamer1.0-plugins-good gthumb gtk-redshift gtk-theme-config gucharmap gvfs-backends humanity-icon-theme ibus ibus-gtk3 ibus-table
  indicator-application indicator-appmenu indicator-bluetooth indicator-datetime indicator-keyboard indicator-printers indicator-session language-selector-gnome
  libaccount-plugin-1.0-0 libaccount-plugin-generic-oauth libaccount-plugin-google libappindicator3-1 libappstream-glib8 libavahi-ui-gtk3-0 libcanberra-gtk3-0
  libcanberra-gtk3-module libcheese-gtk25 libcheese8 libclutter-1.0-0 libclutter-gst-3.0-0 libclutter-gtk-1.0-0 libcryptui0a libdmapsharing-3.0-2 libebackend-1.2-10
  libebook-1.2-16 libebook-contacts-1.2-2 libecal-1.2-19 libedata-book-1.2-25 libedataserver-1.2-21 libedataserverui-1.2-1 libevdocument3-4 libevview3-3 libgail-3-0 libgcr-ui-3-1
  libgdata22 libgeocode-glib0 libgjs0e libgldi3 libgnome-bluetooth13 libgnome-desktop-3-12 libgnomekbd8 libgrilo-0.2-1 libgtk-3-0 libgtk-3-bin libgtk-3-common libgtk-3-dev
  libgtkmm-3.0-1v5 libgtkmm-3.0-dev libgtksourceview-3.0-1 libgtksourceview-3.0-dev libgtkspell3-3-0 libgucharmap-2-90-7 libgucharmap-2-90-dev libgweather-3-6 libido3-0.1-0
  libindicator3-7 libmetacity-private3a libnautilus-extension1a libnemo-extension1 libnm-gtk0 libnma0 libpanel-applet0 libpeas-1.0-0 libpeas-1.0-0-python3loader libpeas-dev
  libreoffice-avmedia-backend-gstreamer librest-0.7-0 librhythmbox-core9 libsoup-gnome2.4-1 libsoup2.4-1 libtimezonemap1 libtotem-plparser18 libtotem0 libunity-control-center1
  libunity-core-6.0-9 libunity-gtk3-parser0 libunity-misc4 libunity-settings-daemon1 libunity-webapps0 libvte-2.91-0 libvte-2.91-dev libwebkit2gtk-4.0-37 libwebkit2gtk-4.0-37-gtk2
  libwebkitgtk-3.0-0 libwnck-3-0 libyelp0 light-themes mediterraneannight-gtk-theme metacity mousetweaks nautilus nautilus-admin nautilus-sendto nautilus-share nemo nemo-audio-tab
  nemo-emblems nemo-filename-repairer nemo-fileroller nemo-gloobus-sushi nemo-gtkhash nemo-image-converter nemo-seahorse nemo-share network-manager network-manager-gnome
  network-manager-pptp-gnome notify-osd nvidia-settings obconf onboard onboard-data opera pavucontrol pinentry-gnome3 plainbox-provider-checkbox plainbox-provider-resource-generic
  policykit-1-gnome python-nautilus python-nemo python3-aptdaemon.gtk3widgets redshift-gtk remmina remmina-plugin-rdp remmina-plugin-vnc rhythmbox rhythmbox-plugin-zeitgeist
  rhythmbox-plugins screen-resolution-extra seahorse seahorse-daemon session-shortcuts sessioninstaller shotwell simple-scan software-properties-gtk synaptic
  system-config-printer-gnome totem transmission-gtk ubuntu-artwork ubuntu-docs ubuntu-mono ubuntu-release-upgrader-gtk ubuntu-session ubuntu-software unity unity-asset-pool
  unity-control-center unity-control-center-signon unity-greeter unity-gtk3-module unity-launcher-folders unity-mail unity-reboot unity-scope-home unity-services
  unity-settings-daemon unity-tweak-tool unity-webapps-common unity-webapps-service update-manager update-notifier usb-creator-gtk variety variety-slideshow vino xdg-user-dirs-gtk
  xdiagnose yad yelp zeitgeist-datahub zenity
```
If it was me I would backup $HOME and reinstall.

---

### Post by watchpocket on 2016-06-29
Thanks for posting that simulation -- it'll give me a good idea of all the stuff I lost.  

Still contemplating what action to take.  I did get this response on askubuntu:


[LIST=1]
[*]Boot to your damaged Mate 14.04, connect it using network cable.
[*]When you reach low graphic message, switch to virtual console tty1 using Ctrl+Alt+F1.
[*]Login then run ifconfig check you network interface name.
  ~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr f2:11:df:ff:59:0c  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Memory:f7e00000-f7e20000 
  Use the name you got to auto configure it using DHCP.
  sudo dhclient eth0

[*]To check connection
  ~$ ping google.com
PING google.com (216.58.208.238) 56(84) bytes of data.
64 bytes from par10s22-in-f14.1e100.net (216.58.208.238): icmp_seq=1 ttl=54 time=57.5 ms
64 bytes from par10s22-in-f14.1e100.net (216.58.208.238): icmp_seq=2 ttl=54 time=59.8 ms

[*]Fix the desktop by reinstall all missing packages
  sudo apt-get install mate-desktop

[*]Reboot
[/LIST]

---

### Post by watchpocket on 2016-06-29
Does anyone know which log will show me exactly what was deleted when I ran the purge command?  Thanks.

---

### Post by yetimon_64 on 2016-06-29
> **watchpocket said:**
> Does anyone know which log will show me exactly what was deleted when I ran the purge command?  Thanks.

Try checking /var/log/apt/history.log, it may hold some details. I am not sure if it will list all, like in          CantankRus' simulation, or just the package you removed. Hopefully that file will show some useful detail.

---

### Post by watchpocket on 2016-06-29
> * I would backup $HOME and reinstall. 				*

When you say "reinstall" -- you mean reinstall the large group of programs that were purged, correct?  Or do you mean reinstall a fresh Ubuntu Mate 14.04?

---

### Post by CantankRus on 2016-06-30
> **watchpocket said:**
> > * I would backup $HOME and reinstall. 				*

When you say "reinstall" -- you mean reinstall the large group of programs that were purged, correct?  Or do you mean reinstall a fresh Ubuntu Mate 14.04?
You can reinstall while keeping your home partition data.
Choose not to format in the installer.
Note your login name,computer name and login password and use the same when reinstalling.
The terminal prompt shows this.
eg 
```
**glen**@**Xenial**:~$
```
username=**glen ** (home folder name)
computername=**Xenial**
If you cant boot at all you you can check this from a live usb/cd as described [**_[COLOR="#B22222"]HERE[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=2057342&p=13319348#post13319348").

[**_[COLOR="#B22222"]UbuntuReinstallation[/COLOR]_**]("https://help.ubuntu.com/community/UbuntuReinstallation")

---

### Post by fdrake on 2016-06-30
if you experience problem reinstalling from oyur terminal, i suggest you something chrooting your partition:
get a live cd  and chroot your partition with it and try to reinstall then the purged programs back.
how to chroot ([https://theguyonthe3rdfloor.wordpress.com/](https://theguyonthe3rdfloor.wordpress.com/)   search for :" Method #2 &#8211; WITH live cd")

---

### Post by watchpocket on 2016-07-02
So for anyone else who might accidentally do what I did here, I got things back under control this way:

After I'd entered the command that you should ***never* **invoke ( *sudo purge gsettings-desktop-schemas* ), 

I got out of a black screen and onto the raw busybox command-prompt with *<CTRL><ALT>  <F1>*. I logged in with username & password, then issued the following commands: ```
ifconfig -a
sudo dhclient eth0
```
That got my network connection working again.  Then:
```
sudo apt-get install gsettings-desktop-schemas
``` The latter command installed most, but not all, of what I needed.

So I opened ***/var/log/dpkg.log***, weeded through it and found every single app, applet and library that had been purged, and painstakingly re-installed them all one by one.  

Though most of them got installed with the *sudo apt-get install gsettings-desktop-schemas* command, I had no way of knowing which did or didn't until I went to install them individually. Several important apps that I'd lost were only restored with the command to install that particular item.  When I re-booted, I was more or less back to normal.  

This all took about two-and-a-half hours. 

[I][B]Oh mother, tell your children 
not to do what I have done[/B]
[/I]
Thanks everyone who helped.

---

