---
title: "HELP-reinstallation, newbie...!!!"
date: 2009-03-10
forum: Dell Ubuntu Support (CLOSED)
---

### Post by vickoxy on 2009-03-10
Hi,
i found here how to install from grub mode Ubuntu. But when i hold ESC after dell logo showing up, came only line
MBR FV2... or something like that-and nothing. Is it possible to reinstall Ubuntu the way they say there (From hard drive (recommended): By using the GRUB menu at boot time)
[http://linux.dell.com/wiki/index.php...Reinstallation](http://linux.dell.com/wiki/index.php...Reinstallation)

Please help someone, because i desperately need dell, and now i have problems with my keyboard too..

Does anyone knows if grub functions in dell minis ubuntu? Or what to press to activate it?

---

### Post by upchucky on 2009-03-10
not much to go on here, need more info than help the newb.

machine specs, ubuntu version, grub eror, symptoms?

An educated guess tell me you had xp on this machine, the keypress seems to indicate that the Master boot record is messed up, and the way you posted seems to indicate that the ubuntu install did not even start.

if true then google xp fixmbr it should get xp rebooting again if indeed xp is the os and you did not mess it up. then install ubuntu by the conventional live cd method.

---

### Post by sirebral on 2009-03-10
You are using a DELL mini 9? I can help.

Do this.
[LIST]
[*]Open a Terminal: **Accessories > Terminal**
[*]Login to Nautilus: type **sudo nautilus** then your **password**
[*]Navigate to the grub folder: **/boot/grub/**
[*]Edit the **menu.lst**: **Right Click > Open in Text Editor**
[*]Change the **timeout** from **0** to **3**
[*]Reset
[*]When Grub Loader starts the countdown press **Esc**
[/LIST]

That should get you where you want to be.

---

### Post by vickoxy on 2009-03-10
> **upchucky said:**
> not much to go on here, need more info than help the newb.

machine specs, ubuntu version, grub eror, symptoms?

An educated guess tell me you had xp on this machine, the keypress seems to indicate that the Master boot record is messed up, and the way you posted seems to indicate that the ubuntu install did not even start.

if true then google xp fixmbr it should get xp rebooting again if indeed xp is the os and you did not mess it up. then install ubuntu by the conventional live cd method.

No, i didn´t use any XP-i was just messing with some gmail notifiers that are not LPIA adjusted.  So now the computer mixes Desktop Ubuntu and Dell Desktop Mode (showing in *ubuntu desktop mode* not functionally launcher bar from* dell desktop mode*), looses some icons  (for *language* e.g.) randomly...

Dell Mini 9, Ubuntu 8.04, 1GB RAM, 8GB SSD...

---

### Post by vickoxy on 2009-03-10
> **sirebral said:**
> You are using a DELL mini 9? I can help.

Do this.
[LIST]
[*]Open a Terminal: **Accessories > Terminal**
[*]Login to Nautilus: type **sudo nautilus** then your **password**
[*]Navigate to the grub folder: **/boot/grub/**
[*]Edit the **menu.lst**: **Right Click > Open in Text Editor**
[*]Change the **timeout** from **0** to **3**
[*]Reset
[*]When Grub Loader starts the countdown press **Esc**
[/LIST]

That should get you where you want to be.

Thanks, i made that, but all i get is:
[I]Ubuntu 8.04.1 kernel 2.6.24-19-lpia
Ubuntu 8.04.1 kernel 2.6.24-19-lpia (recovery mode)[/I]

And some other advices (press arrow keys, press e....)
When i press *Ubuntu 8.04.1 kernel 2.6.24-19-lpia (recovery mode)* computer does something (like analyze) and ends after some times on *root@sugar:* and-nothing. So, nothing similary as suggested here:
[http://linux.dell.com/wiki/index.php/Ubuntu_8.04/OS_Reinstallation](http://linux.dell.com/wiki/index.php/Ubuntu_8.04/OS_Reinstallation)

Does it look like i can not do this option restoring the system to its original factory settings?

---

### Post by vickoxy on 2009-03-10
And i noticed that led battery indicator is not working any more. And in dell desktop mode-if i moving mice cursor over trays, the display is blinking or for 1-2 sec it freezes. So i think that i need some reinstallation, but it seems that that grub option doesn´t work (which i would prefer because i don´t have any external drive...).
So if anyone can help...

---

### Post by sirebral on 2009-03-10
Ok, don't go too far.  I will look into a re install for you.

---

### Post by sirebral on 2009-03-10
What size HD do you have on your Mini 9?  I don't know if I have a utility partition that allows for a re install but I only have an 8GB SSD on my Mini 9.

---

### Post by sirebral on 2009-03-10
> **vickoxy said:**
> No, i didn´t use any XP-i was just messing with some gmail notifiers that are not LPIA adjusted.  So now the computer mixes Desktop Ubuntu and Dell Desktop Mode (showing in *ubuntu desktop mode* not functionally launcher bar from* dell desktop mode*), looses some icons  (for *language* e.g.) randomly...

Dell Mini 9, Ubuntu 8.04, 1GB RAM, 8GB SSD...

Oh. here is the info I was looking for.  Well,if you did something with GMail try and undo it to see if that corrects the situation.

---

### Post by armandh on 2009-03-10
I think you mean usb instilation
there is no re-install on the mini9 HDD
on the mini9
if you tap 2 on boot up
tab over to boot and tab to usb storage
FN+ the fn5(g) or fn6(h) key to move usb to the top
a regular [non dell] Live Ubuntu will then load from a USB stick
I am not sure if the dell ubuntu will work from other than an external DVD drive [with cd/dvd/cd-rw at the top of the boot list]

the dell "restore to factory original" DVD disk wipes the HDD and copies the dell instillation and extras to the HDD.

I prefer 8.10

---

### Post by sirebral on 2009-03-10
> **armandh said:**
> I think you mean usb instilation

if you tap 2 on boot up
tab over to boot and tab to usb storage
FN+ the fn5(g) or fn6(h) key to move to the top
a regular [non dell] Live Ubuntu will then load from a USB stick
I am not sure if the dell ubuntu will work from other than an external DVD drive [with cd/dvd/cd-rw at the top of the boot list]

the dell "restore to factory original" DVD disk wipes the HDD and copies the dell instillation and extras to the HDD.

I prefer 8.10

Be sure to check out the link the OP posted.  It is referring to the a DELL Utility partition to re install a factory distro.

---

### Post by vickoxy on 2009-03-11
Ok, guys, i lost you-is there anything i can do? Or just wait?
I have only Macbook with dvd drive-no external...

---

### Post by sirebral on 2009-03-11
Do you have a USB Flash Drive?  You can do what armandh suggested and install via a USB Flash drive.

---

### Post by vickoxy on 2009-03-11
> **sirebral said:**
> Oh. here is the info I was looking for.  Well,if you did something with GMail try and undo it to see if that corrects the situation.

I installed some notifiers from synaptic, and removed it. And some whitout synaptic, but i removed it also. Should i just type in terminal undo "program name" or?

After removing these notifiers, it all went up and down...

---

### Post by vickoxy on 2009-03-11
> **sirebral said:**
> Do you have a USB Flash Drive?  You can do what armandh suggested and install via a USB Flash drive.

Flash drive-meaning USB Stick-i have 2 GB Stick, and SDHC Memory Card

---

### Post by vickoxy on 2009-03-11
When i press 2 after rebooting, i have after Hard Disk, USB Storage, and removable storages as options to boot from, but i don´´t know if that would help. And i have one external hard disk if that can be used to make recovery image from original dell DVD...

---

### Post by sirebral on 2009-03-11
You can try this first.  sudo apt-get remove --whatever you installed--

> **vickoxy said:**
> I installed some notifiers from synaptic, and removed it. And some whitout synaptic, but i removed it also. Should i just type in terminal undo "program name" or?

After removing these notifiers, it all went up and down...

This size USB will work.  armandh would be better to ask about this then i would.  there is a whole page devoted to it.

> **vickoxy said:**
> Flash drive-meaning USB Stick-i have 2 GB Stick, and SDHC Memory Card

---

### Post by vickoxy on 2009-03-11
I would like to restore original dell ubuntu-because my wife sometimes uses dell desktop mode-could you maybe post me, sirebral, link to this thread (USB Installation)?
Thanks

---

### Post by sirebral on 2009-03-11
I actually have another idea.  If you go into Synaptic, look for **gnome-desktop** or do a search for gnome then look for it.  Mark it for re install. 

I kinda bricked my network so I started looking at Xubuntu.  Take a look at this: [http://www.xubuntu.org/get#intrepid](http://www.xubuntu.org/get#intrepid)

On the bottom of the page they describe how to install Xubuntu from Ubuntu. They also give a link to completely remove Ubuntu, which I might do.  I might just re install it that way.

Here is the link to remove Ubuntu: [http://www.psychocats.net/ubuntu/purexfce](http://www.psychocats.net/ubuntu/purexfce)

Which shows this: ```
sudo apt-get remove alacarte binfmt-support brltty brltty-x11 capplets-data cdrdao cli-common compiz compiz-core compiz-fusion-plugins-extra compiz-fusion-plugins-main compiz-gnome compiz-plugins compiz-wrapper compizconfig-backend-gconf contact-lookup-applet dcraw deskbar-applet ekiga eog evolution evolution-common evolution-data-server evolution-data-server-common evolution-exchange evolution-plugins evolution-webcal example-content f-spot fast-user-switch-applet firefox-3.0-gnome-support firefox-gnome-support gconf-editor gdm-guest-session gedit gedit-common gnome-about gnome-applets gnome-applets-data gnome-control-center gnome-desktop-data gnome-menus gnome-netstatus-applet gnome-nettool gnome-panel gnome-panel-data gnome-pilot gnome-pilot-conduits gnome-session gnome-settings-daemon gnome-spell gnome-terminal gnome-terminal-data gnome-themes gnome-user-guide gnome-utils gstreamer0.10-plugins-base-apps gstreamer0.10-pulseaudio gstreamer0.10-schroedinger gstreamer0.10-tools gvfs-bin gvfs-fuse human-icon-theme human-theme hwtest hwtest-gtk libao2 libart2.0-cil libasound2-plugins libcanberra-gnome libcanberra-gtk-module libcanberra-gtk0 libcanberra0 libcompizconfig0 libdecoration0 libdeskbar-tracker libdirectfb-1.0-0 libebackend1.2-0 libedata-book1.2-2 libedata-cal1.2-6 libedataserverui1.2-8 libeel2-2 libeel2-data libegroupwise1.2-13 libexchange-storage1.2-3 libexempi3 libflickrnet2.1.5-cil libgconf2.0-cil libgdata-google1.2-1 libgdata1.2-1 libgdiplus libgif4 libglade2.0-cil libglib2.0-cil libglitz-glx1 libglitz1 libgmime-2.0-2a libgmime2.2-cil libgnome-keyring1.0-cil libgnome-pilot2 libgnome-vfs2.0-cil libgnome-window-settings1 libgnome2.0-cil libgnomevfs2-bin libgpod-common libgpod3 libgtk2.0-cil libgtkhtml-editor-common libgtkhtml-editor0 libgtkhtml3.14-19 libhyphen0 libicu38 liblpint-bonobo0 libmono-addins-gui0.2-cil libmono-addins0.2-cil libmono-cairo1.0-cil libmono-cairo2.0-cil libmono-corlib1.0-cil libmono-corlib2.0-cil libmono-data-tds1.0-cil libmono-data-tds2.0-cil libmono-i18n1.0-cil libmono-i18n2.0-cil libmono-security1.0-cil libmono-security2.0-cil libmono-sharpzip0.84-cil libmono-sharpzip2.84-cil libmono-sqlite2.0-cil libmono-system-data1.0-cil libmono-system-data2.0-cil libmono-system-web1.0-cil libmono-system-web2.0-cil libmono-system1.0-cil libmono-system2.0-cil libmono0 libmono1.0-cil libmono2.0-cil libmtp8 libndesk-dbus-glib1.0-cil libndesk-dbus1.0-cil libneon27 libopal-2.2 libpisock9 libpisync1 libpt-1.10.10 libpt-1.10.10-plugins-alsa libpt-1.10.10-plugins-v4l libpt-1.10.10-plugins-v4l2 libpulsecore5 libsamplerate0 libschroedinger-1.0-0 libsdl1.2debian libsdl1.2debian-alsa libsgutils1 libspeexdsp1 libsqlite0 libtracker-gtk0 libts-0.0-0 libwps-0.1-1 libx11-xcb1 mesa-utils metacity mono-common mono-gac mono-jit mono-runtime mousetweaks mtools nautilus nautilus-cd-burner nautilus-data nautilus-sendto nautilus-share openoffice.org-base-core openoffice.org-calc openoffice.org-common openoffice.org-core openoffice.org-draw openoffice.org-emailmerge openoffice.org-gnome openoffice.org-gtk openoffice.org-impress openoffice.org-math openoffice.org-style-human openoffice.org-writer pkg-config pulseaudio pulseaudio-esound-compat pulseaudio-module-gconf pulseaudio-module-hal pulseaudio-module-x11 python-beagle python-gmenu python-gtksourceview2 python-uno rarian-compat rdesktop rhythmbox screen-resolution-extra sg3-utils sqlite sqlite3 syslinux tangerine-icon-theme tomboy tracker tracker-search-tool tracker-utils tsclient ubuntu-artwork ubuntu-desktop ubuntu-docs ubuntu-gdm-themes ubuntu-system-service ubuntu-wallpapers untex usb-creator usplash-theme-ubuntu vino whois wv xdg-user-dirs xdg-user-dirs-gtk xulrunner-1.9-gnome-support && sudo apt-get install xubuntu-desktop
```

But ... if you wanted to, terminal, re isntall Ubuntu you could probably just reverse it.  

```
sudo apt-get install alacarte binfmt-support brltty brltty-x11 capplets-data cdrdao cli-common compiz compiz-core compiz-fusion-plugins-extra compiz-fusion-plugins-main compiz-gnome compiz-plugins compiz-wrapper compizconfig-backend-gconf contact-lookup-applet dcraw deskbar-applet ekiga eog evolution evolution-common evolution-data-server evolution-data-server-common evolution-exchange evolution-plugins evolution-webcal example-content f-spot fast-user-switch-applet firefox-3.0-gnome-support firefox-gnome-support gconf-editor gdm-guest-session gedit gedit-common gnome-about gnome-applets gnome-applets-data gnome-control-center gnome-desktop-data gnome-menus gnome-netstatus-applet gnome-nettool gnome-panel gnome-panel-data gnome-pilot gnome-pilot-conduits gnome-session gnome-settings-daemon gnome-spell gnome-terminal gnome-terminal-data gnome-themes gnome-user-guide gnome-utils gstreamer0.10-plugins-base-apps gstreamer0.10-pulseaudio gstreamer0.10-schroedinger gstreamer0.10-tools gvfs-bin gvfs-fuse human-icon-theme human-theme hwtest hwtest-gtk libao2 libart2.0-cil libasound2-plugins libcanberra-gnome libcanberra-gtk-module libcanberra-gtk0 libcanberra0 libcompizconfig0 libdecoration0 libdeskbar-tracker libdirectfb-1.0-0 libebackend1.2-0 libedata-book1.2-2 libedata-cal1.2-6 libedataserverui1.2-8 libeel2-2 libeel2-data libegroupwise1.2-13 libexchange-storage1.2-3 libexempi3 libflickrnet2.1.5-cil libgconf2.0-cil libgdata-google1.2-1 libgdata1.2-1 libgdiplus libgif4 libglade2.0-cil libglib2.0-cil libglitz-glx1 libglitz1 libgmime-2.0-2a libgmime2.2-cil libgnome-keyring1.0-cil libgnome-pilot2 libgnome-vfs2.0-cil libgnome-window-settings1 libgnome2.0-cil libgnomevfs2-bin libgpod-common libgpod3 libgtk2.0-cil libgtkhtml-editor-common libgtkhtml-editor0 libgtkhtml3.14-19 libhyphen0 libicu38 liblpint-bonobo0 libmono-addins-gui0.2-cil libmono-addins0.2-cil libmono-cairo1.0-cil libmono-cairo2.0-cil libmono-corlib1.0-cil libmono-corlib2.0-cil libmono-data-tds1.0-cil libmono-data-tds2.0-cil libmono-i18n1.0-cil libmono-i18n2.0-cil libmono-security1.0-cil libmono-security2.0-cil libmono-sharpzip0.84-cil libmono-sharpzip2.84-cil libmono-sqlite2.0-cil libmono-system-data1.0-cil libmono-system-data2.0-cil libmono-system-web1.0-cil libmono-system-web2.0-cil libmono-system1.0-cil libmono-system2.0-cil libmono0 libmono1.0-cil libmono2.0-cil libmtp8 libndesk-dbus-glib1.0-cil libndesk-dbus1.0-cil libneon27 libopal-2.2 libpisock9 libpisync1 libpt-1.10.10 libpt-1.10.10-plugins-alsa libpt-1.10.10-plugins-v4l libpt-1.10.10-plugins-v4l2 libpulsecore5 libsamplerate0 libschroedinger-1.0-0 libsdl1.2debian libsdl1.2debian-alsa libsgutils1 libspeexdsp1 libsqlite0 libtracker-gtk0 libts-0.0-0 libwps-0.1-1 libx11-xcb1 mesa-utils metacity mono-common mono-gac mono-jit mono-runtime mousetweaks mtools nautilus nautilus-cd-burner nautilus-data nautilus-sendto nautilus-share openoffice.org-base-core openoffice.org-calc openoffice.org-common openoffice.org-core openoffice.org-draw openoffice.org-emailmerge openoffice.org-gnome openoffice.org-gtk openoffice.org-impress openoffice.org-math openoffice.org-style-human openoffice.org-writer pkg-config pulseaudio pulseaudio-esound-compat pulseaudio-module-gconf pulseaudio-module-hal pulseaudio-module-x11 python-beagle python-gmenu python-gtksourceview2 python-uno rarian-compat rdesktop rhythmbox screen-resolution-extra sg3-utils sqlite sqlite3 syslinux tangerine-icon-theme tomboy tracker tracker-search-tool tracker-utils tsclient ubuntu-artwork ubuntu-desktop ubuntu-docs ubuntu-gdm-themes ubuntu-system-service ubuntu-wallpapers untex usb-creator usplash-theme-ubuntu vino whois wv xdg-user-dirs xdg-user-dirs-gtk xulrunner-1.9-gnome-support
```

I just showed you how much of a Newbie I am.  :KS

---

### Post by vickoxy on 2009-03-11
> **sirebral said:**
> I actually have another idea.  If you go into Synaptic, look for **gnome-desktop** or do a search for gnome then look for it.  Mark it for re install. 

I kinda bricked my network so I started looking at Xubuntu.  Take a look at this: [http://www.xubuntu.org/get#intrepid](http://www.xubuntu.org/get#intrepid)

On the bottom of the page they describe how to install Xubuntu from Ubuntu. They also give a link to completely remove Ubuntu, which I might do.  I might just re install it that way.

Here is the link to remove Ubuntu: [http://www.psychocats.net/ubuntu/purexfce](http://www.psychocats.net/ubuntu/purexfce)

Which shows this: ```
sudo apt-get remove alacarte binfmt-support brltty brltty-x11 capplets-data cdrdao cli-common compiz compiz-core compiz-fusion-plugins-extra compiz-fusion-plugins-main compiz-gnome compiz-plugins compiz-wrapper compizconfig-backend-gconf contact-lookup-applet dcraw deskbar-applet ekiga eog evolution evolution-common evolution-data-server evolution-data-server-common evolution-exchange evolution-plugins evolution-webcal example-content f-spot fast-user-switch-applet firefox-3.0-gnome-support firefox-gnome-support gconf-editor gdm-guest-session gedit gedit-common gnome-about gnome-applets gnome-applets-data gnome-control-center gnome-desktop-data gnome-menus gnome-netstatus-applet gnome-nettool gnome-panel gnome-panel-data gnome-pilot gnome-pilot-conduits gnome-session gnome-settings-daemon gnome-spell gnome-terminal gnome-terminal-data gnome-themes gnome-user-guide gnome-utils gstreamer0.10-plugins-base-apps gstreamer0.10-pulseaudio gstreamer0.10-schroedinger gstreamer0.10-tools gvfs-bin gvfs-fuse human-icon-theme human-theme hwtest hwtest-gtk libao2 libart2.0-cil libasound2-plugins libcanberra-gnome libcanberra-gtk-module libcanberra-gtk0 libcanberra0 libcompizconfig0 libdecoration0 libdeskbar-tracker libdirectfb-1.0-0 libebackend1.2-0 libedata-book1.2-2 libedata-cal1.2-6 libedataserverui1.2-8 libeel2-2 libeel2-data libegroupwise1.2-13 libexchange-storage1.2-3 libexempi3 libflickrnet2.1.5-cil libgconf2.0-cil libgdata-google1.2-1 libgdata1.2-1 libgdiplus libgif4 libglade2.0-cil libglib2.0-cil libglitz-glx1 libglitz1 libgmime-2.0-2a libgmime2.2-cil libgnome-keyring1.0-cil libgnome-pilot2 libgnome-vfs2.0-cil libgnome-window-settings1 libgnome2.0-cil libgnomevfs2-bin libgpod-common libgpod3 libgtk2.0-cil libgtkhtml-editor-common libgtkhtml-editor0 libgtkhtml3.14-19 libhyphen0 libicu38 liblpint-bonobo0 libmono-addins-gui0.2-cil libmono-addins0.2-cil libmono-cairo1.0-cil libmono-cairo2.0-cil libmono-corlib1.0-cil libmono-corlib2.0-cil libmono-data-tds1.0-cil libmono-data-tds2.0-cil libmono-i18n1.0-cil libmono-i18n2.0-cil libmono-security1.0-cil libmono-security2.0-cil libmono-sharpzip0.84-cil libmono-sharpzip2.84-cil libmono-sqlite2.0-cil libmono-system-data1.0-cil libmono-system-data2.0-cil libmono-system-web1.0-cil libmono-system-web2.0-cil libmono-system1.0-cil libmono-system2.0-cil libmono0 libmono1.0-cil libmono2.0-cil libmtp8 libndesk-dbus-glib1.0-cil libndesk-dbus1.0-cil libneon27 libopal-2.2 libpisock9 libpisync1 libpt-1.10.10 libpt-1.10.10-plugins-alsa libpt-1.10.10-plugins-v4l libpt-1.10.10-plugins-v4l2 libpulsecore5 libsamplerate0 libschroedinger-1.0-0 libsdl1.2debian libsdl1.2debian-alsa libsgutils1 libspeexdsp1 libsqlite0 libtracker-gtk0 libts-0.0-0 libwps-0.1-1 libx11-xcb1 mesa-utils metacity mono-common mono-gac mono-jit mono-runtime mousetweaks mtools nautilus nautilus-cd-burner nautilus-data nautilus-sendto nautilus-share openoffice.org-base-core openoffice.org-calc openoffice.org-common openoffice.org-core openoffice.org-draw openoffice.org-emailmerge openoffice.org-gnome openoffice.org-gtk openoffice.org-impress openoffice.org-math openoffice.org-style-human openoffice.org-writer pkg-config pulseaudio pulseaudio-esound-compat pulseaudio-module-gconf pulseaudio-module-hal pulseaudio-module-x11 python-beagle python-gmenu python-gtksourceview2 python-uno rarian-compat rdesktop rhythmbox screen-resolution-extra sg3-utils sqlite sqlite3 syslinux tangerine-icon-theme tomboy tracker tracker-search-tool tracker-utils tsclient ubuntu-artwork ubuntu-desktop ubuntu-docs ubuntu-gdm-themes ubuntu-system-service ubuntu-wallpapers untex usb-creator usplash-theme-ubuntu vino whois wv xdg-user-dirs xdg-user-dirs-gtk xulrunner-1.9-gnome-support && sudo apt-get install xubuntu-desktop
```

But ... if you wanted to, terminal, re isntall Ubuntu you could probably just reverse it.  

```
sudo apt-get install alacarte binfmt-support brltty brltty-x11 capplets-data cdrdao cli-common compiz compiz-core compiz-fusion-plugins-extra compiz-fusion-plugins-main compiz-gnome compiz-plugins compiz-wrapper compizconfig-backend-gconf contact-lookup-applet dcraw deskbar-applet ekiga eog evolution evolution-common evolution-data-server evolution-data-server-common evolution-exchange evolution-plugins evolution-webcal example-content f-spot fast-user-switch-applet firefox-3.0-gnome-support firefox-gnome-support gconf-editor gdm-guest-session gedit gedit-common gnome-about gnome-applets gnome-applets-data gnome-control-center gnome-desktop-data gnome-menus gnome-netstatus-applet gnome-nettool gnome-panel gnome-panel-data gnome-pilot gnome-pilot-conduits gnome-session gnome-settings-daemon gnome-spell gnome-terminal gnome-terminal-data gnome-themes gnome-user-guide gnome-utils gstreamer0.10-plugins-base-apps gstreamer0.10-pulseaudio gstreamer0.10-schroedinger gstreamer0.10-tools gvfs-bin gvfs-fuse human-icon-theme human-theme hwtest hwtest-gtk libao2 libart2.0-cil libasound2-plugins libcanberra-gnome libcanberra-gtk-module libcanberra-gtk0 libcanberra0 libcompizconfig0 libdecoration0 libdeskbar-tracker libdirectfb-1.0-0 libebackend1.2-0 libedata-book1.2-2 libedata-cal1.2-6 libedataserverui1.2-8 libeel2-2 libeel2-data libegroupwise1.2-13 libexchange-storage1.2-3 libexempi3 libflickrnet2.1.5-cil libgconf2.0-cil libgdata-google1.2-1 libgdata1.2-1 libgdiplus libgif4 libglade2.0-cil libglib2.0-cil libglitz-glx1 libglitz1 libgmime-2.0-2a libgmime2.2-cil libgnome-keyring1.0-cil libgnome-pilot2 libgnome-vfs2.0-cil libgnome-window-settings1 libgnome2.0-cil libgnomevfs2-bin libgpod-common libgpod3 libgtk2.0-cil libgtkhtml-editor-common libgtkhtml-editor0 libgtkhtml3.14-19 libhyphen0 libicu38 liblpint-bonobo0 libmono-addins-gui0.2-cil libmono-addins0.2-cil libmono-cairo1.0-cil libmono-cairo2.0-cil libmono-corlib1.0-cil libmono-corlib2.0-cil libmono-data-tds1.0-cil libmono-data-tds2.0-cil libmono-i18n1.0-cil libmono-i18n2.0-cil libmono-security1.0-cil libmono-security2.0-cil libmono-sharpzip0.84-cil libmono-sharpzip2.84-cil libmono-sqlite2.0-cil libmono-system-data1.0-cil libmono-system-data2.0-cil libmono-system-web1.0-cil libmono-system-web2.0-cil libmono-system1.0-cil libmono-system2.0-cil libmono0 libmono1.0-cil libmono2.0-cil libmtp8 libndesk-dbus-glib1.0-cil libndesk-dbus1.0-cil libneon27 libopal-2.2 libpisock9 libpisync1 libpt-1.10.10 libpt-1.10.10-plugins-alsa libpt-1.10.10-plugins-v4l libpt-1.10.10-plugins-v4l2 libpulsecore5 libsamplerate0 libschroedinger-1.0-0 libsdl1.2debian libsdl1.2debian-alsa libsgutils1 libspeexdsp1 libsqlite0 libtracker-gtk0 libts-0.0-0 libwps-0.1-1 libx11-xcb1 mesa-utils metacity mono-common mono-gac mono-jit mono-runtime mousetweaks mtools nautilus nautilus-cd-burner nautilus-data nautilus-sendto nautilus-share openoffice.org-base-core openoffice.org-calc openoffice.org-common openoffice.org-core openoffice.org-draw openoffice.org-emailmerge openoffice.org-gnome openoffice.org-gtk openoffice.org-impress openoffice.org-math openoffice.org-style-human openoffice.org-writer pkg-config pulseaudio pulseaudio-esound-compat pulseaudio-module-gconf pulseaudio-module-hal pulseaudio-module-x11 python-beagle python-gmenu python-gtksourceview2 python-uno rarian-compat rdesktop rhythmbox screen-resolution-extra sg3-utils sqlite sqlite3 syslinux tangerine-icon-theme tomboy tracker tracker-search-tool tracker-utils tsclient ubuntu-artwork ubuntu-desktop ubuntu-docs ubuntu-gdm-themes ubuntu-system-service ubuntu-wallpapers untex usb-creator usplash-theme-ubuntu vino whois wv xdg-user-dirs xdg-user-dirs-gtk xulrunner-1.9-gnome-support
```

I just showed you how much of a Newbie I am.  :KS

Ok, is ther one or two advices?
What should i do first? Or wait a little bit?

---

### Post by ugm6hr on 2009-03-11
Without knowing exactly what you did to mess things up, it is impossible to advise on how to undo changes.

Installing and removing Gnome or alternative desktop managers will not change anything.

I have provided links to mydellmini which explains how to install Ubuntu from USB in mydellmini forum.

---

### Post by vickoxy on 2009-03-11
> **ugm6hr said:**
> Without knowing exactly what you did to mess things up, it is impossible to advise on how to undo changes.

Installing and removing Gnome or alternative desktop managers will not change anything.

I have provided links to mydellmini which explains how to install Ubuntu from USB in mydellmini forum.

Hi, thanks, i saw that-actually i am just downloading iso image from the link i found on forum, but i can not download usb-creator! I find it i synaptic-should i install it from there? And will it work with this immage from that i am downloading ([http://www.root-core.org/Inspiron_910_Ubuntu_A00.img)?](http://www.root-core.org/Inspiron_910_Ubuntu_A00.img)?) - is this lpia version mit dell desktop etc...?

And to say what have i mess up? It is hard-as said i was installing some gmail notifiers/deinstalling which were not all optimazed for lpia architecture-and in some point-as i removed one (i thing cGmail or kChekgmail notifier) app, started akward things to happen-problems with icons, blinking, keyboard setup mixed. I am newbie, so i know that my explanations are not clear-but to me it seeems that one reinstallation will fix this.

---

### Post by vickoxy on 2009-03-11
So, i downloaded img file but usb-creator works only with iso files. Does anyone know how to make USB Live stick of original Dell ubuntu .img file?

---

### Post by sirebral on 2009-03-11
Sorry I couldn't help you better vickoxy.  Look here for the DELL re-crafted ISO: [http://linux.dell.com/wiki/index.php/Products/Consumer](http://linux.dell.com/wiki/index.php/Products/Consumer)

---

### Post by armandh on 2009-03-11
the first thing I did B4 trashing the OS on my mini 9 was be sure I could re install the factory original. 

the factory restore disk is a DVD and I am not sure of the exact file size. there fore I am not sure if 2Gb memory stick is big enough.

I used a spare 5" DVD drive and external USB 5" drive case.
in a pinch one can open a usb hard-drive and connect a dvd drive instead [obviously not all may work, the one I tried did.]

on to usb mem [I have not done this]
on a known good working computer with software to make a bootable USB stick use the factory dvd as the source material to make the bootable usb drive.

making the usb stick on a semi working computer is a trip in to the unknown. 
bad cd/dvd drives are another problem.

Update: OOTB 8.04 system>administration>make bootable USB.....
did not recognize a DVD or iso of the dell DVD as valid source material.

---

### Post by vickoxy on 2009-03-11
> **armandh said:**
> the first thing I did B4 trashing the OS on my mini 9 was be sure I could re install the factory original. 

the factory restore disk is a DVD and I am not sure of the exact file size. there fore I am not sure if 2Gb memory stick is big enough.

I used a spare 5" DVD drive and external USB 5" drive case.
in a pinch one can open a usb hard-drive and connect a dvd drive instead [obviously not all may work, the one I tried did.]

on to usb mem [I have not done this]
on a known good working computer with software to make a bootable USB stick use the factory dvd as the source material to make the bootable usb drive.

making the usb stick on a semi working computer is a trip in to the unknown. 
bad cd/dvd drives are another problem.
 
I agree with you- ill wait till i find some external drive...Hoping it want crash down. Only hypotetical-why i can´t use my MacBook´s DVD drive? Is it possible to connect these computers and sharing dvd drive?

---

### Post by sirebral on 2009-03-11
> **armandh said:**
> I used a spare 5" DVD drive and external USB 5" drive case. in a pinch one can open a usb hard-drive and connect a dvd drive instead [obviously not all may work, the one I tried did.]

:KS

I look at my external HD case and begin to ponder.  Hrmm.. :-k

---

### Post by armandh on 2009-03-11
> **sirebral said:**
> :KS

I look at my external HD case and begin to ponder.  Hrmm.. :-k

just as long as it is not so new as to be SATA
UPDATE
8.04.1 ubuntu's create a usb startup disk does not recognize dvds or the iso of the dvd as a legitimate install disk.

but it has worked making an 8.10 stick I booted live

---

### Post by vickoxy on 2009-03-12
Hi,
on this site i found that is possible to make USB recovery stick of dell mini´s .img file:
[http://en.community.dell.com/forums/p/19233531/19379737.aspx](http://en.community.dell.com/forums/p/19233531/19379737.aspx)

I tried first option but nothing:
root@sugar:~# sudo dd if=/path_to_restore_image/restore_image.img of=/path_to_your_USB_key bs=1024
dd: öffne &#8222;/path_to_restore_image/restore_image.img&#8220;: No such file or directory

Can someone verified that these advices are good, and should i try to restore my Ubuntu with that. And of course - how?
Thanks

Ok-i reentered then, but still nothing:

root@sugar:~# sudo dd if=/home/sugar/Dokumente/Downloads/Inspiron_910_Ubuntu_A00.img of=//media/disk bs=1024
dd: öffne &#8222;**//media/disk**&#8220;: Is a directory

I do not recognize any other path to my usb stick

---

