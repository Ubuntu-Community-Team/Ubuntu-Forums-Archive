---
title: "Frostwire/Limewire"
date: 2006-08-02
forum: Desktop Environments
---

### Post by glasyalabolis on 2006-08-02
Hi all.
I'm trying to get Frostwire installed and I'm running into some problems.
I have installed the latest Java from Sun and typing java at the command prompt gives this
```
ron@Meander:~$ java
Usage: java [-options] class [args...]
           (to execute a class)
   or  java [-options] -jar jarfile [args...]
           (to execute a jar file)

where options include:
    -client       to select the "client" VM
    -server       to select the "server" VM
    -hotspot      is a synonym for the "client" VM  [deprecated]
                  The default VM is client.

    -cp <class search path of directories and zip/jar files>
    -classpath <class search path of directories and zip/jar files>
                  A : separated list of directories, JAR archives,
                  and ZIP archives to search for class files.
    -D<name>=<value>
                  set a system property
    -verbose[:class|gc|jni]
                  enable verbose output
    -version      print product version and exit
    -version:<value>
                  require the specified version to run
    -showversion  print product version and continue
    -jre-restrict-search | -jre-no-restrict-search
                  include/exclude user private JREs in the version search
    -? -help      print this help message
    -X            print help on non-standard options
    -ea[:<packagename>...|:<classname>]
    -enableassertions[:<packagename>...|:<classname>]
                  enable assertions
    -da[:<packagename>...|:<classname>]
    -disableassertions[:<packagename>...|:<classname>]
                  disable assertions
    -esa | -enablesystemassertions
                  enable system assertions
    -dsa | -disablesystemassertions
                  disable system assertions
ron@Meander:~$

```
So this isn't a java problem.. I hope.
anyway here is the output from running both Limewire and Frostwire, both of wich install without any problems what so ever.
- - - - -
Frostwire
```
ron@Meander:~$ frostwire
Starting FrostWire...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.4.2_12]
Configuring environment...
Loading FrostWire:
java.lang.UnsatisfiedLinkError: /usr/lib/j2re1.4-sun/lib/i386/libawt.so: libXp.so.6: cannot open shared object file: No such file or directory
        at java.lang.ClassLoader$NativeLibrary.load(Native Method)
        at java.lang.ClassLoader.loadLibrary0(Unknown Source)
        at java.lang.ClassLoader.loadLibrary(Unknown Source)
        at java.lang.Runtime.loadLibrary0(Unknown Source)
        at java.lang.System.loadLibrary(Unknown Source)
        at sun.security.action.LoadLibraryAction.run(Unknown Source)
        at java.security.AccessController.doPrivileged(Native Method)
        at java.awt.Toolkit.loadLibraries(Unknown Source)
        at java.awt.Toolkit.<clinit>(Unknown Source)
        at com.limegroup.gnutella.gui.Main.showInitialSplash(Main.java:66)
        at com.limegroup.gnutella.gui.Main.main(Main.java:38)

******************************************************************
Something went wrong with FrostWire.
Maybe you're using the wrong version of Java?
(Frostwire is tested against and works best with with Sun's JRE, Java 1.4+)
The version of Java in your PATH is:
java version "1.4.2_12"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.4.2_12-b03)
Java HotSpot(TM) Client VM (build 1.4.2_12-b03, mixed mode)

If you keep having trouble please come to our forum at
http://www.frostwire.com/forum/forum.php to find the answers
We're also available through irc at irc.peercommons.net on the #main channel

ron@Meander:~$

```
- - - - -
Limewire
```
ron@Meander:~$ limewire
Starting LimeWire...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.4.2_12]
Configuring environment...
Loading LimeWire:
java.lang.UnsatisfiedLinkError: /usr/lib/j2re1.4-sun/lib/i386/libawt.so: libXp.so.6: cannot open shared object file: No such file or directory
        at java.lang.ClassLoader$NativeLibrary.load(Native Method)
        at java.lang.ClassLoader.loadLibrary0(Unknown Source)
        at java.lang.ClassLoader.loadLibrary(Unknown Source)
        at java.lang.Runtime.loadLibrary0(Unknown Source)
        at java.lang.System.loadLibrary(Unknown Source)
        at sun.security.action.LoadLibraryAction.run(Unknown Source)
        at java.security.AccessController.doPrivileged(Native Method)
        at java.awt.Toolkit.loadLibraries(Unknown Source)
        at java.awt.Toolkit.<clinit>(Unknown Source)
        at com.limegroup.gnutella.gui.Main.showInitialSplash(Main.java:67)
        at com.limegroup.gnutella.gui.Main.main(Main.java:39)

******************************************************************
Something went wrong with LimeWire.
Maybe you're using the wrong version of Java?
(LimeWire is tested against and works best with with Sun's JRE, Java 1.4+)
The version of Java in your PATH is:
java version "1.4.2_12"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.4.2_12-b03)
Java HotSpot(TM) Client VM (build 1.4.2_12-b03, mixed mode)

ron@Meander:~$

```
Any help would be appreciated, thanks!

---

### Post by cstudent on 2006-08-02
The command to check your version is:
```

java -version

```

To change which is your default version:
```

sudo update-alternatives --config java

```

Follow the instruction to change to Sun Java.

---

### Post by glasyalabolis on 2006-08-02
```
ron@Meander:~$ java -version
java version "1.4.2_12"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.4.2_12-b03)
Java HotSpot(TM) Client VM (build 1.4.2_12-b03, mixed mode)
ron@Meander:~$



```
Which is also said
here```
Something went wrong with FrostWire.
Maybe you're using the wrong version of Java?
(Frostwire is tested against and works best with with Sun's JRE, Java 1.4+)
The version of Java in your PATH is:
java version "1.4.2_12"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.4.2_12-b03)
Java HotSpot(TM) Client VM (build 1.4.2_12-b03, mixed mode)
```
and here```
Something went wrong with LimeWire.
Maybe you're using the wrong version of Java?
(LimeWire is tested against and works best with with Sun's JRE, Java 1.4+)
The version of Java in your PATH is:
java version "1.4.2_12"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.4.2_12-b03)
Java HotSpot(TM) Client VM (build 1.4.2_12-b03, mixed mode)


```
- - - - -
```
ron@Meander:~$ sudo update-alternatives --config java

There is only 1 program which provides java
(/usr/lib/j2re1.4-sun/bin/java). Nothing to configure.
ron@Meander:~$

```
I have tried that before also.

---

### Post by cstudent on 2006-08-02
I would install the newer version of Sun's java
```

sudo aptitude install sun-java5-bin

```

You may have to run update-alternatives again. Even though it says that Limewire and Frostwire run on version 1.4, I don't think they will. I could be wrong about that.

---

### Post by glasyalabolis on 2006-08-02
I tried
sudo aptitude install sun-java5-bin
but it didn't find the package, so I did a 
apt-cache search sun
and found something like sun-j2re1.5
this is the output and the follow up from trying to install that
```
ron@Meander:~$ sudo apt-get install sun-j2re1.5
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  sun-j2re1.5: Depends: libxp6 but it is not going to be installed
E: Broken packages
ron@Meander:~$ sudo apt-get install libxp6
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libxp6: Depends: x-common but it is not going to be installed
E: Broken packages
ron@Meander:~$ sudo apt-get install x-common
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  acpi-support appres azureus beep-media-player beforelight bitmap
  bittornado-gui blender bmp-mp4 boson boson-base boson-data boson-music
  bug-buddy bzflag cupsys cupsys-driver-gimpprint cupsys-driver-gutenprint
  cupsys-pt dbus editres eog epdfview epiphany-browser evince evolution
  fglrx-control fglrx-kernel-2.6.15-23-server file-roller firefox
  foomatic-db-gutenprint foomatic-db-hpijs freeglut3 freeloader fstobdf gaim
  gcalctool gconf-editor gdk-imlib1 gdk-imlib11 gdm gedit gimp gimp-print
  gkrellm gksu glife gnome-about gnome-applets gnome-bin gnome-control-center
  gnome-core gnome-cups-manager gnome-desktop-environment gnome-games
  gnome-icon-theme gnome-keyring gnome-keyring-manager gnome-libs-data
  gnome-media gnome-netstatus-applet gnome-nettool gnome-panel
  gnome-power-manager gnome-session gnome-system-monitor gnome-system-tools
  gnome-terminal gnome-themes gnome-utils gnome-volume-manager gnomemeeting
  gs-common gs-esp gstreamer0.10-plugins-base gstreamer0.10-plugins-good
  gstreamer0.10-x gstreamer0.8-misc gstreamer0.8-swfdec gstreamer0.8-x
  gtk2-engines-clearlooks gtk2-engines-crux gtk2-engines-lighthouseblue
  gtk2-engines-mist gtk2-engines-pixbuf gtk2-engines-redmond95
  gtk2-engines-smooth gtk2-engines-thinice gtkhtml3.8 gucharmap gxine hal
  hpijs hplip iceauth ico ijsgutenprint k3b kalzium kcontrol kdebase-bin
  kdelibs-bin kdelibs4c2a kicker kmplayer kmplayer-base kstars libaa1
  libarts1c2a libaudio2 libavahi-qt3-1 libbcprov-java libbonoboui2-0
  libcairo-java libcairo2 libcommons-cli-java libdbus-qt-1-1c2 libdmx1
  libedataserverui1.2-6 libeel2-2 libfontenc-dev libfontenc1 libfs6
  libgail-common libgail17 libgcj7-awt libggi2 libgii0 libgii0-target-x
  libgimp2.0 libgksu1.2-1 libgksuui1.0-1 libgl1-mesa libglade-gnome0 libglade0
  libglade2-0 libglitz-glx1 libglu1-mesa libgnome-desktop-2 libgnome-keyring0
  libgnome32 libgnomecanvas2-0 libgnomecupsui1.0-1c2a libgnomeprint2.2-0
  libgnomeprintui2.2-0 libgnomesupport0 libgnomeui-0 libgnomeui32 libgnorba27
  libgnorbagtk0 libgnucrypto-java libgtk-java libgtk-jni libgtk1.2 libgtk2.0-0
  libgtk2.0-bin libgtk2.0-common libgtkhtml3.8-15 libgtksourceview1.0-0
  libgtkspell0 libgucharmap4 libgutenprintui2-1 libice6 libk3b2 libkdeedu3
  libkonq4 liblaunchpad-integration0 liblog4j1.2-java liblpint-bonobo0
  libmetacity0 libnautilus-burn3 libnautilus-extension1 libnotify1
  libopal-2.2.0 libopenh323-1.15.3c2 libpanel-applet2-0 libpango1.0-0
  libpango1.0-common libpoppler1-glib libpt-1.8.3c2 libpt-plugins-avc
  libpt-plugins-oss libqt3-mt librsvg2-2 librsvg2-common libsdl1.2debian
  libsdl1.2debian-alsa libsexy2 libsm6 libstartup-notification0 libswfdec0.3
  libswt3.1-gtk-java libswt3.1-gtk-jni libtotem-plparser1 libvte4 libwmf0.2-7
  libwnck18 libwxgtk2.6-0 libx11-6 libx11-dev libxau-dev libxau6 libxaw7
  libxcomposite1 libxcursor1 libxdamage1 libxdmcp-dev libxdmcp6 libxext-dev
  libxext6 libxfixes3 libxfont-dev libxfont1 libxft1 libxft2 libxi-dev libxi6
  libxine-main1 libxinerama1 libxkbfile1 libxklavier10 libxmu6 libxmuu1
  libxpm4 libxrandr2 libxrender1 libxres1 libxss1 libxt6 libxtrap6 libxtst6
  libxv1 libxvmc1 libxxf86dga1 libxxf86misc1 libxxf86vm1 limewire-free listres
  mesa-utils metacity mozilla-browser mozilla-mplayer mplayer mplayer-386
  msttcorefonts nautilus nautilus-cd-burner notification-daemon oclock
  powermanagement-interface python-glade2 python-gnome2 python-gtk2
  python-wxgtk2.6 python2.4-cairo python2.4-glade2 python2.4-gnome2
  python2.4-gtk2 quake2 realplay smproxy sound-juicer sun-j2re1.4 swf-player
  synaptic tetex-bin tilda tipa totem totem-gstreamer ttf-arphic-bkai00mp
  ttf-arphic-bsmi00lp ttf-arphic-gbsn00lp ttf-arphic-gkai00mp ttf-arphic-ukai
  ttf-arphic-uming ubuntu-artwork viewres vino wine x-ttcidfont-conf
  x11-common x11perf x11proto-core-dev x11proto-fonts-dev x11proto-input-dev
  x11proto-kb-dev x11proto-randr-dev x11proto-render-dev x11proto-video-dev
  x11proto-xext-dev x11proto-xf86dri-dev xauth xbase-clients xbiff xcalc xchat
  xchat-common xchat-gnome xchm xclipboard xclock xconsole xcursorgen xditview
  xdpyinfo xdriinfo xev xeyes xf86dga xfd xfonts-100dpi xfonts-75dpi
  xfonts-a12k12 xfonts-artwiz xfonts-ayu xfonts-baekmuk xfonts-base
  xfonts-bitmap-mule xfonts-bolkhov-75dpi xfonts-bolkhov-cp1251-75dpi
  xfonts-bolkhov-cp1251-misc xfonts-bolkhov-isocyr-75dpi
  xfonts-bolkhov-isocyr-misc xfonts-bolkhov-koi8r-75dpi
  xfonts-bolkhov-koi8r-misc xfonts-bolkhov-koi8u-75dpi
  xfonts-bolkhov-koi8u-misc xfonts-bolkhov-misc xfonts-cmex-big5p
  xfonts-cronyx-100dpi xfonts-cronyx-75dpi xfonts-cronyx-cp1251-100dpi
  xfonts-cronyx-cp1251-75dpi xfonts-cronyx-cp1251-misc
  xfonts-cronyx-isocyr-100dpi xfonts-cronyx-isocyr-75dpi
  xfonts-cronyx-isocyr-misc xfonts-cronyx-koi8r-100dpi
  xfonts-cronyx-koi8r-75dpi xfonts-cronyx-koi8r-misc
  xfonts-cronyx-koi8u-100dpi xfonts-cronyx-koi8u-75dpi
  xfonts-cronyx-koi8u-misc xfonts-cronyx-misc xfonts-efont-unicode
  xfonts-efont-unicode-ib xfonts-intl-arabic xfonts-intl-asian
  xfonts-intl-chinese xfonts-intl-chinese-big xfonts-intl-european
  xfonts-intl-japanese xfonts-intl-japanese-big xfonts-intl-phonetic
  xfonts-jmk xfonts-kaname xfonts-kapl xfonts-kappa20 xfonts-knickers
  xfonts-marumoji xfonts-mplus xfonts-nexus xfonts-scalable xfonts-shinonome
  xfonts-terminus xfonts-terminus-dos xfonts-terminus-oblique xfonts-thai
  xfonts-thai-manop xfonts-thai-nectec xfonts-thai-ttf xfonts-thai-vor
  xfonts-tipa xfonts-utils xfonts-wqy xfontsel xgamma xgc xhost xinit xkbutils
  xkeyboard-config xkill xload xlogo xlsatoms xlsclients xlsfonts xmag xman
  xmessage xmms xmms-mp4 xmodmap xmore xorg-driver-fglrx xpmutils xprop xrandr
  xrdb xrefresh xserver-xephyr xserver-xgl xserver-xorg xserver-xorg-air-core
  xserver-xorg-core xserver-xorg-dev xserver-xorg-driver-all
  xserver-xorg-driver-apm xserver-xorg-driver-ark xserver-xorg-driver-ati
  xserver-xorg-driver-chips xserver-xorg-driver-cirrus
  xserver-xorg-driver-cyrix xserver-xorg-driver-dummy
  xserver-xorg-driver-fbdev xserver-xorg-driver-glint xserver-xorg-driver-i128
  xserver-xorg-driver-i740 xserver-xorg-driver-i810 xserver-xorg-driver-imstt
  xserver-xorg-driver-mga xserver-xorg-driver-newport xserver-xorg-driver-nsc
  xserver-xorg-driver-nv xserver-xorg-driver-rendition xserver-xorg-driver-s3
  xserver-xorg-driver-s3virge xserver-xorg-driver-savage
  xserver-xorg-driver-sis xserver-xorg-driver-sisusb xserver-xorg-driver-tdfx
  xserver-xorg-driver-tga xserver-xorg-driver-trident
  xserver-xorg-driver-tseng xserver-xorg-driver-v4l xserver-xorg-driver-vesa
  xserver-xorg-driver-vga xserver-xorg-driver-via xserver-xorg-driver-vmware
  xserver-xorg-input-acecad xserver-xorg-input-aiptek xserver-xorg-input-all
  xserver-xorg-input-calcomp xserver-xorg-input-digitaledge
  xserver-xorg-input-dmc xserver-xorg-input-dynapro xserver-xorg-input-elo2300
  xserver-xorg-input-elographics xserver-xorg-input-evdev
  xserver-xorg-input-fpit xserver-xorg-input-hyperpen
  xserver-xorg-input-jamstudio xserver-xorg-input-joystick
  xserver-xorg-input-magellan xserver-xorg-input-magictouch
  xserver-xorg-input-microtouch xserver-xorg-input-mutouch
  xserver-xorg-input-palmax xserver-xorg-input-penmount
  xserver-xorg-input-spaceorb xserver-xorg-input-summa
  xserver-xorg-input-synaptics xserver-xorg-input-tek4957
  xserver-xorg-input-ur98 xserver-xorg-input-void xserver-xorg-input-wacom
  xset xsetmode xsetpointer xsetroot xsm xstdcmap xtrap xutils xvidtune xvinfo
  xwd xwininfo xwud yelp zenity
The following NEW packages will be installed:
  x-common
0 upgraded, 1 newly installed, 483 to remove and 0 not upgraded.
Need to get 0B/19.3kB of archives.
After unpacking 1129MB disk space will be freed.
Do you want to continue [Y/n]? n
Abort.
ron@Meander:~$

```
Hope this helps..

---

### Post by cstudent on 2006-08-02
Ok,

1> Are you running Dapper?
2> Do you have the extra repositories enabled?

---

### Post by glasyalabolis on 2006-08-02
Yes, I am running 6.06.
Yes, I have extra repositories installed.
I got the list from the Ubuntu Wiki page, so if I am missing any just let me know.
```
## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  
## You may replace "us" with your country code to get the closest mirror.

deb http://us.archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu breezy main restricted
## MAJOR BUG FIX UPDATES produced after the final release
deb http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted
## UBUNTU SECURITY UPDATES
deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted
deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe
## UNIVERSE AND MULTIVERSE REPOSITORY (Unsupported by Ubuntu.  Use at own risk.)
deb http://archive.ubuntu.com/ubuntu breezy universe multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy universe multiverse
## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://packages.freecontrib.org/ubuntu/plf breezy free non-free
deb-src http://packages.freecontrib.org/ubuntu/plf breezy free non-free 
deb http://www.getautomatix.com/apt dapper main

```

---

### Post by cstudent on 2006-08-02
The sources.list you pasted is for Breezy, not Dapper. 

This is my sources.list:
```

####################################
### Official Ubuntu Repositories ###
####################################

# Dapper Final Release Repository
deb http://archive.ubuntu.com/ubuntu dapper main
deb-src http://archive.ubuntu.com/ubuntu dapper main

deb http://archive.ubuntu.com/ubuntu dapper restricted
deb-src http://archive.ubuntu.com/ubuntu dapper restricted

deb http://archive.ubuntu.com/ubuntu dapper universe
deb-src http://archive.ubuntu.com/ubuntu dapper universe

deb http://archive.ubuntu.com/ubuntu dapper multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper multiverse

# Dapper Security Updates
deb http://archive.ubuntu.com/ubuntu dapper-security main
deb-src http://archive.ubuntu.com/ubuntu dapper-security main

deb http://archive.ubuntu.com/ubuntu dapper-security restricted
deb-src http://archive.ubuntu.com/ubuntu dapper-security restricted

deb http://archive.ubuntu.com/ubuntu dapper-security universe
deb-src http://archive.ubuntu.com/ubuntu dapper-security universe

deb http://archive.ubuntu.com/ubuntu dapper-security multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-security multiverse

# Dapper Bugfix Updates
deb http://archive.ubuntu.com/ubuntu dapper-updates main
deb-src http://archive.ubuntu.com/ubuntu dapper-updates main

deb http://archive.ubuntu.com/ubuntu dapper-updates restricted
deb-src http://archive.ubuntu.com/ubuntu dapper-updates restricted

deb http://archive.ubuntu.com/ubuntu dapper-updates universe
deb-src http://archive.ubuntu.com/ubuntu dapper-updates universe

deb http://archive.ubuntu.com/ubuntu dapper-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-updates multiverse

# Dapper Backports (new software versions, provided by the Ubuntu Backports Project)
deb http://archive.ubuntu.com/ubuntu dapper-backports main
deb-src http://archive.ubuntu.com/ubuntu dapper-backports main

deb http://archive.ubuntu.com/ubuntu dapper-backports restricted
deb-src http://archive.ubuntu.com/ubuntu dapper-backports restricted

deb http://archive.ubuntu.com/ubuntu dapper-backports universe
deb-src http://archive.ubuntu.com/ubuntu dapper-backports universe

deb http://archive.ubuntu.com/ubuntu dapper-backports multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-backports multiverse

deb http://archive.canonical.com/ubuntu dapper-commercial main


##############################
### Automatix Repositories ###
##############################

# deb http://www.beerorkid.com/automatix/apt dapper main

##################
### Dapper PLF ###
##################

deb http://packages.freecontrib.org/ubuntu/plf/ dapper free non-free
deb-src http://packages.freecontrib.org/ubuntu/plf/ dapper free non-free

##########################################################
### Cipherfunk multimedia packages (GPG key: 33BAC1B3) ###
##########################################################
## To add the GPG key for cipherfunk                    ##
## gpg --keyserver subkeys.pgp.net --recv 33BAC1B3      ##
## gpg --export --armor 33BAC1B3 | sudo apt-key add -   ##
##########################################################

deb ftp://cipherfunk.org/pub/packages/ubuntu/ dapper main
deb-src ftp://cipherfunk.org/pub/packages/ubuntu/ dapper main

##########################
### jEdit Repositories ###
##########################

deb http://dl.sourceforge.net/sourceforge/jedit ./
deb-src http://dl.sourceforge.net/sourceforge/jedit ./

```

If you are POSITIVE you are running Dapper Drake and not Breezy Badger then you'll want to do the following:

```

sudo cp /etc/apt/sources.list /etc/apt/sources.list.breezy

```

```

cd
sudo gedit sources.list

```

Copy and paste my sources.list above into the blank document and save it. Then:

```

sudo cp sources.list /etc/apt/

```
```

sudo apt-get update

```

You'll probably get an error about the gpg for ciferfunk. Before saving the file you can put a # in front the the lines for it that start with deb. That will disable those repositories.

If all goes well, then you should be able to install the package I suggested earlier. That should fix the broken package problem too.

---

### Post by glasyalabolis on 2006-08-03
Thanks for all the help.
I had alittle trouble, GNOME wouldn't start etc but I got it all sorted out in the end, thanks alot for the help.
:D

---

