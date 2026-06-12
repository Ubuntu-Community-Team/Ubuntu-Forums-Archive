---
title: "Package manager wants to erase my whole computer..."
date: 2009-03-23
forum: General Help
---

### Post by Sarai the Geek on 2009-03-23
A while back I downloaded a cursor theme. When I asked about installing it, I was told to get the libxcursor1 package from synaptic. The program didn't work for me, so I just got sort of medieval and replaced all the pictures from an existing cursor theme with the ones I want. It worked great, *except* the cursor reverts to the old one when I mouse over the desktop and panels. I figure it's something screwy with the libcursor1 package, so I went to uninstall it. That's when things got a little strange...
Check this out:

```
sarai@Sarai-Laptop:~$ sudo apt-get remove libxcursor1
[sudo] password for sarai: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libopenal1 x11proto-resource-dev libpopt-dev liborbit2-dev python-alsaaudio
  python-gtk2-doc libsm-dev gtk-doc-tools libgsf-gnome-1-114 libartsc0
  libice-dev automake1.4 libgoffice-0-common x11proto-xext-dev libtasn1-3-dev
  libevolution3.0-cil libatk1.0-dev debhelper docbook-to-man libaudiofile-dev
  libxine1-x intltool-debian libsoup2.4-dev x11proto-kb-dev libglib2.0-dev
  libgpg-error-dev libgnome-speech-dev libosp5 mplayer-skins
  x11proto-xinerama-dev libsvga1 libgfortran3 libpango1.0-dev libsp1c2
  libcamel1.2-dev glade-common check libqt4-sql-mysql libqt4-dbus
  x11proto-render-dev libgnomeprint2.2-dev libgcrypt11-dev libxcb-xv0
  libqt4-qt3support docbook-xsl libxi-dev m4 libgtop2-dev libsqlite3-dev
  libxrender-dev po-debconf libgstreamer-plugins-base0.10-dev autoconf
  liboobs-1-dev libcairo2-dev python-dev libgnome-keyring-dev python-lxml sp
  verbiste libxine1-bin libxdmcp-dev libavahi-client-dev python2.5-dev
  libffi-dev libglide2 libstartup-notification0-dev libamrnb3 libpng12-dev
  python-utidylib libggi-target-x libfontconfig1-dev python-pyorbit-dev
  openjade libmail-sendmail-perl x11proto-record-dev x11proto-composite-dev
  xtrans-dev intltool libtool bodr libtidy-0.99-0 x11proto-core-dev gettext
  python-numpy libxklavier12-dev libamrwb3 libenca0 libbonobo2-dev
  libxine1-ffmpeg libggi2 libgnutls-dev libqtcore4 gnome-common
  libgnome-menu-dev x11proto-randr-dev x11proto-damage-dev libgii1
  libdbus-1-dev libwxbase2.6-0 autotools-dev libxcb-render-util0-dev
  libxcb-shape0 libxext-dev docbook-xsl-doc-html python-feedparser
  avant-window-navigator-data libxdamage-dev libnspr4-dev chemical-mime-data
  libuser1 libostyle1c2 zlib1g-dev liblzo2-2 libxml2-dev x11proto-input-dev
  libqt4-sql libltdl7-dev libidl-dev libfreetype6-dev libart-2.0-dev
  libesd0-dev libgii1-target-x x11proto-fixes-dev libverbiste-0.1-0
  libpthread-stubs0-dev libxau-dev libdbus-glib-1-dev libpthread-stubs0
  libqt4-xml python-uniconvertor libblas3gf libopenbabel3 libgnomevfs2-dev
  libxcomposite-dev automake libqt4-network libqt4-designer liblapack3gf
  libxrandr-dev libxvmc1 libexpat1-dev jade libqtgui4 libgconf2-dev
  libncurses5-dev libedataserver1.2-dev libselinux1-dev html2text
  libmodplug0c2 libpixman-1-dev libxft-dev libx11-dev libxcb-xlib0-dev
  libgstreamer0.10-dev docbook-dsssl libxres-dev libxcb-render0-dev
  libxfixes-dev libgnome2-dev libqt4-script orbit2 libavahi-glib-dev
  libxcb1-dev libavahi-common-dev libxcb-shm0 python-chardet libxinerama-dev
  libsepol1-dev libxtst-dev libsys-hostname-long-perl libenchant-dev docbook
  python-gobject-dev qt4-qtconfig libxine1-console
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  alacarte apport-gtk apturl at-spi avant-window-navigator awn-applets-c-core
  awn-applets-python-core awn-manager bluez-gnome brasero brltty-x11 compiz
  compiz-core compiz-fusion-plugins-extra compiz-fusion-plugins-main
  compiz-gnome compiz-plugins compizconfig-backend-gconf
  compizconfig-settings-manager contact-lookup-applet deskbar-applet ekiga
  emerald eog eve evince evolution evolution-plugins evolution-webcal f-spot
  fast-user-switch-applet file-roller firefox firefox-3.0 firefox-3.0-branding
  firefox-3.0-gnome-support firefox-gnome-support flashplugin-nonfree
  fontypython fusion-icon gcalctool gconf-editor gcu-bin gcursor gdebi gdm
  gdm-guest-session gedit gimp gksu glade gnome-about
  gnome-accessibility-themes gnome-app-install gnome-applets
  gnome-control-center gnome-core-devel gnome-do gnome-do-plugins gnome-games
  gnome-icon-theme gnome-keyring gnome-mag gnome-media gnome-menus gnome-mount
  gnome-netstatus-applet gnome-nettool gnome-orca gnome-panel gnome-pilot
  gnome-pilot-conduits gnome-power-manager gnome-screensaver gnome-session
  gnome-settings-daemon gnome-system-monitor gnome-system-tools gnome-terminal
  gnome-themes gnome-user-guide gnome-utils gstreamer0.10-plugins-good
  gtk2-engines gtk2-engines-murrine gtk2-engines-pixbuf gucharmap handbrake
  human-theme hwtest-gtk inkscape jockey-gtk language-selector libatspi-dev
  libatspi1.0-0 libavahi-ui0 libawn-extras0 libawn0 libbonoboui2-0
  libbonoboui2-dev libcanberra-gnome libcanberra-gtk-module libcanberra-gtk0
  libcryptui0 libdeskbar-tracker libedataserverui1.2-8 libeel2-2 libeel2-dev
  libemeraldengine0 libexchange-storage1.2-3 libgail-gnome-dev
  libgail-gnome-module libgcu0 libgegl-0.0-0 libgimp2.0 libgksu2-0 libglade2-0
  libglade2-dev libglade2.0-cil libgnome-desktop-2-7 libgnome-desktop-dev
  libgnome-media0 libgnome-window-settings1 libgnome2-canvas-perl
  libgnome2-perl libgnome2.0-cil libgnomecanvas2-0 libgnomecanvas2-dev
  libgnomedesktop2.20-cil libgnomekbd-dev libgnomekbd3 libgnomekbdui-dev
  libgnomekbdui3 libgnomeprintui2.2-0 libgnomeprintui2.2-dev libgnomeui-0
  libgnomeui-dev libgoffice-0-4 libgpod-common libgpod3 libgtk-vnc-1.0-0
  libgtk2-perl libgtk2.0-0 libgtk2.0-bin libgtk2.0-cil libgtk2.0-dev
  libgtkglext1 libgtkhtml-editor0 libgtkhtml2-0 libgtkhtml3.14-19
  libgtkhtml3.14-dev libgtkmm-2.4-1c2a libgtksourceview1.0-0
  libgtksourceview2.0-0 libgtksourceview2.0-dev libgtkspell0 libgucharmap7
  libgweather-dev libgweather1 liblaunchpad-integration1 liblpint-bonobo0
  libmagick++10 libmagick10 libmbca0 libmetacity0 libmono-addins-gui0.2-cil
  libnautilus-burn4 libnautilus-extension-dev libnautilus-extension1
  libnotify0.4-cil libnotify1 libpanel-applet2-0 libpanel-applet2-dev
  libpolkit-gnome0 libpoppler-glib3 librsvg2-2 librsvg2-2.18-cil
  librsvg2-common librsvg2-dev libsexy2 libtotem-plparser-dev
  libtotem-plparser12 libtracker-gtk0 libvte-dev libvte9 libwmf-bin
  libwmf0.2-7 libwnck-dev libwnck2.20-cil libwnck22 libwv-1.2-3 libwxgtk2.6-0
  libxcursor-dev libxcursor1 libxine1 libxine1-gnome libxine1-misc-plugins
  metacity mousetweaks mplayer nautilus nautilus-cd-burner nautilus-sendto
  nautilus-share network-manager-gnome notification-daemon nvidia-settings
  obex-data-server onboard perlmagick pidgin pidgin-otr policykit-gnome prism
  prism-google-docs prism-google-mail python-awn python-awn-extras
  python-awnlib python-beagle python-compizconfig python-glade2 python-gmenu
  python-gnome2 python-gnome2-desktop python-gnome2-desktop-dev
  python-gnome2-dev python-gnomecanvas python-gtk2 python-gtk2-dev
  python-gtkhtml2 python-gtksourceview2 python-launchpad-integration
  python-notify python-pyatspi python-sexy python-virtkey python-vte
  python-wxgtk2.6 python-wxversion rhythmbox rss-glx scim scim-bridge-agent
  scim-bridge-client-gtk scim-gtk2-immodule screenlets
  screensaver-default-images seahorse seahorse-plugins software-properties-gtk
  songbird ssh-askpass-gnome sun-java6-plugin synaptic
  system-config-printer-gnome tangerine-icon-theme tomboy totem
  totem-gstreamer totem-mozilla totem-plugins totem-xine tracker
  tracker-search-tool tracker-utils transmission-gtk tsclient ubufox
  ubuntu-artwork ubuntu-docs update-manager update-notifier usb-creator
  usermode verbiste-gnome vinagre vino virtualbox-2.1 wv x11-apps
  xbase-clients xdg-user-dirs-gtk xorg xsane xscreensaver-data xscreensaver-gl
  xulrunner-1.9 xulrunner-1.9-dom-inspector xulrunner-1.9-gnome-support yelp
  zenity
0 upgraded, 0 newly installed, 292 to remove and 0 not upgraded.
After this operation, 884MB disk space will be freed.
Do you want to continue [Y/n]? 

```:shock:

It does the same thing in synaptic.

Interestingly, this isn't the first time something strange like this happened. I tried to uninstall a package a while back, and was idly watching the terminal when I suddenly realized it was erasing stuff I wanted- notably my virtualbox!

What is going on?!

---

### Post by joewski on 2009-03-23
I had something similar happen to me just recently. Lost control of the system. I was going overboard installing everything interesting and with out thinking accepted the changes without looking.

The worst thing is it un-installed the package manager as well. I was sunk. I had to reinstall the entire system again.

I thought it was only me until I read your post.

---

### Post by Sarai the Geek on 2009-03-24
> **joewski said:**
> I had something similar happen to me just recently. Lost control of the system. I was going overboard installing everything interesting and with out thinking accepted the changes without looking.

The worst thing is it un-installed the package manager as well. I was sunk. I had to reinstall the entire system again.

I thought it was only me until I read your post.

Oi...

---

### Post by Acid_1 on 2009-03-24
I think it's a bug. When I was using Mint 4, the same thing happened to me to. Remove literally every application that I had. Had to reinstall the OS :(

---

### Post by mb_webguy on 2009-03-24
I'm not sure that this will work, but try the command "sudo update-apt-xapian-index" in the terminal.

---

### Post by Sarai the Geek on 2009-03-24
> **mb_webguy said:**
> I'm not sure that this will work, but try the command "sudo update-apt-xapian-index" in the terminal.

```
sarai@Sarai-Laptop:~$ sudo update-apt-xapian-index
[sudo] password for sarai: 
The index /var/lib/apt-xapian-index is up to date
```

Thanks for trying, though. :)

---

### Post by rhcm123 on 2009-03-24
> **Sarai the Geek said:**
>  That's when things got a little strange...


weel.. that's one way to free up space - i don't honestly have a clue how to fix this, i'm just going to be monitoring to see if i can't learn a little more about linux

---

### Post by lavinog on 2009-03-24
libxcursor1 is installed on my machine. Is it possible that it was installed by default?

---

### Post by Sarai the Geek on 2009-03-24
> **lavinog said:**
> libxcursor1 is installed on my machine. Is it possible that it was installed by default?

Hmm, now that I look, you're right. The package I should have been uninstalling was gcursor.
However, isn't it still bad that my package manager is bent on wiping my apps? Especially since this has happened before...?

---

### Post by mb_webguy on 2009-03-24
> **lavinog said:**
> libxcursor1 is installed on my machine. Is it possible that it was installed by default?

It's installed on my system as well.  I don't know why I didn't think of it before, but I'd think this would be a dependency of quite a few fairly basic applications.  That could certainly be why update manager is trying to uninstall everything.

---

### Post by lavinog on 2009-03-24
> **Sarai the Geek said:**
> Hmm, now that I look, you're right. The package I should have been uninstalling was gcursor.
However, isn't it still bad that my package manager is bent on wiping my apps? Especially since this has happened before...?

In this case, it wants to remove all programs that require libxcursor1 (which I assume is anything that uses a mouse.) Without libxcursor1 those programs will not function and would thus be pointless to have installed.

Fortunately the package manager doesn't automatically remove anything without your approval. And if you see a huge list of things being removed you should abort.

Had you removed those packages, you should be able to install them again from the command line.
ubuntu-desktop should install all the packages you need to get your system back up also:
```
sudo apt-get install ubuntu-desktop
```

---

### Post by redseventyseven on 2009-04-03
Let's rephrase that subject: "Package manager wants to erase my whole computer..."

More accurately, it should be "I accidentally told the package manager to remove a program, the removal of which would render lots of other programs useless, and the package manager told me that that's what would have happened and gave me the chance to change my mind."

You should be thankful that the package manager actually gave you the chance to back out. In fact, it was a similar situation that prompted me to try Linux in the first place. While doing a little routine maintenance in Windows, I wanted to remove a program that I didn't use any more. Its uninstall routine was written so badly that it deleted a whole load of system files *without warning*, rendering just about every other program useless. I was forced into reinstalling Windows and a friend of mine suggested that since I had to do it anyway, I should give Ubuntu a try. And that's my story.

---

### Post by Cheesehead on 2009-04-03
The libxcursor1 package is a dependency of over a thousand other packages.
When you tell the system to remove such a critical component, it will naturally try to remove everything that depends on it.

```
$ apt-cache rdepends libxcursor1 | wc -l   #Xubuntu 8.04 cache
1105
```

---

### Post by anjames on 2009-04-07
Well it seems like two problems are at least loosely related. Adept popped up an update notifier a couple of days ago and in the process somehow kubuntu-desktop was selected for removal. It got most of the way through before I noticed, and now I can't get it to reinstall.

[INDENT]root@amaterasu:/etc# apt-get install kubuntu-desktop
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
kubuntu-desktop: Depends: kde-window-manager but it is not going to be installed
Depends: kdebase-workspace-bin but it is not going to be installed
Depends: ksysguard but it is not going to be installed
Recommends: kate but it is not going to be installed
Recommends: kdebase-plasma but it is not going to be installed
Recommends: kdebluetooth but it is not going to be installed
Recommends: kdeplasma-addons but it is not going to be installed
Recommends: openoffice.org-kde but it is not going to be installed
Recommends: plasmoid-quickaccess but it is not going to be installed
E: Broken packages[/INDENT]

Any ideas why it says the dependencies are not going to be installed? I would think that if it knows the dependencies, it would try to install them right?

FWIW these 'E: Broken packages' errors are surfacing fairly often in the forums these past couple have days. More details at: 
[http://ubuntuforums.org/showthread.php?p=7031384#post7031384](http://ubuntuforums.org/showthread.php?p=7031384#post7031384)

---

### Post by lavinog on 2009-04-08
have you tried
```
sudo apt-get update
```
It could be a temporary issue.

---

### Post by Jouke74 on 2009-04-08
Dear Users,

As was pointed out a few times in previous posts libxcursor1 is a very essential package in the Ubuntu system. If you remove this package, or even worse autoremove this package all packages that depend on it will be removed by the package manager as well since they cannot function. This works as a chain reaction since the packages that depend on these packages will also be removed. Hence if you say "yes" to Synaptic or Apt for removing, you will almost loose your complete Ubuntu system. 

See it as trying to remove the beating heart from a human. As a result all blood flow won't function anymore so it assumes that it is safe to take out all arteries, and subsequently all vital organs. The end result is a dead human. That's why synaptic clearly asks if it is ok? (not...)

However if i put the heart back it will only go through all required dependencies for the heart (not the system). Meaning the nerves that innervate it and the all things that make the heart work, maybe some coronary arteries included. That does not however mean that the full artery system is turned back to it's original state, as well as all organs that depend on this artery system.

---

### Post by anjames on 2009-04-08
Temporary or not, maybe there should be some sort of warning if you're removing a package that half of your system depends on, so that future updates don't try to uninstall the rest of your system having assumed your package dependency removal meant you wanted all the dependers removed as well!

Fun enough anyway, now that I'm fixed I don't think I'll be updating for a while.

---

### Post by lavinog on 2009-04-08
> **anjames said:**
> Temporary or not, maybe there should be some sort of warning if you're removing a package that half of your system depends on, so that future updates don't try to uninstall the rest of your system having assumed your package dependency removal meant you wanted all the dependers removed as well!

Fun enough anyway, now that I'm fixed I don't think I'll be updating for a while.

Your issue is not the same as the OPs. The OPs issue is that they tried to manually remove the wrong package. Yours is a legitimate bug.
You are right about the update manager should give a better warning, but your comment on this thread looks like you are referring to apt which does give you a significant warning.

Maybe you should file a bug report stating that the update manager should give a more detailed report about packages that will be removed.

---

### Post by Mmmtobacco on 2009-04-09
i had the same problem. i think i may have to reinstall ubuntu as all the text files (or maybe the application that reads the fonts) was removed along with the package manager. 

i tried using the sudo apt-get install ubuntu-desktop as well as the update and it worked. i even downloaded gnome again, but i could not access my desktop still. i tried the startx command and it came up with an error with the authority file. is the package manager just bugged?

---

### Post by cariboo on 2009-04-09
Both of the problems mentioned in this thread are due to operator error. Where the user is in a Windows state of mind, and just clicks next without actually reading what is on the screen. 

If you want to uninstall a program, and it lists a number of files that will also be removed stop and check the list to see if any thing it wants to remove is something important.

Partial upgrades are bad, if an upgrade wants to remove programs, stop and make sure nothing imortant is being removed. Personally when I'm presented with a partial upgrade, I leave it until all the dependencies are met, or I use:

```
sudo apptitude safe-upgrade
```

Using the safe-upgrade method nothing is removed and packages with unmet dependencies are not installed until the dependencies are met.

Jim

---

