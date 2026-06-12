---
title: "Bluetooth Speaker/Headphone Automated Script"
date: 2009-10-22
forum: Desktop Environments
---

### Post by flyguy97 on 2009-10-22
Please see the post at [http://ubuntuforums.org/showthread.php?p=8154656#post8154656]("http://ubuntuforums.org/showthread.php?p=8154656#post8154656").

Cheers,
Jason

---

### Post by walmis on 2009-10-22
Blueman 1.21 already does this automatically.
Makes bluetooth device the default sink and moves all streams to it. You just need to connect to Audio Sink service listed in the device context menu.

---

### Post by flyguy97 on 2009-10-22
> **walmis said:**
> Blueman 1.21 already does this automatically.
Makes bluetooth device the default sink and moves all streams to it. You just need to connect to Audio Sink service listed in the device context menu.

Where were you at about 8:00 this morning :), that little script took forever to come up with (D-Bus is a major pain), well I guess it will work until the ppa I used for blueman is updated. Thanks for the heads up!

Cheers,
Jason

---

### Post by walmis on 2009-10-22
I suggest you use the official blueman ppa here:
[https://edge.launchpad.net/~blueman/+archive/ppa](https://edge.launchpad.net/~blueman/+archive/ppa)

---

### Post by flyguy97 on 2009-10-22
> **walmis said:**
> I suggest you use the official blueman ppa here:
[https://edge.launchpad.net/~blueman/+archive/ppa](https://edge.launchpad.net/~blueman/+archive/ppa)

Thanks for the heads up. However, after I did the update it still doesn't automatically switch over to my bluetooth speakers, it acted like it was trying to (studdering sound) but then the sound went back to my horrible laptop speakers.

Jason

---

### Post by flyguy97 on 2009-10-22
Walmis,

I didn't realize you were one of the developers of Blueman until I checked your profile. Thank you for all your work on that project. I hope the Gnome group will consider making Blueman the default bluetooth manager. Bluez-gnome is fine but lacks almost all of the advanced features of Blueman. The thing I like most as the user is even though Blueman makes it easy to access more of the advanced features, it is still very straightforward to use. The only suggestion I have on how to improve Blueman is to do away with some of the techie speak used when connecting. Due to the length of time I've been with linux (10 years) I am starting to become comfortable with terms link audio sink, however, new users coming from Windows find it very difficult to bridge the techie speak divide.

Cheers,
Jason

---

### Post by walmis on 2009-10-23
> **flyguy97 said:**
> Thanks for the heads up. However, after I did the update it still doesn't automatically switch over to my bluetooth speakers, it acted like it was trying to (studdering sound) but then the sound went back to my horrible laptop speakers.

Jason

Could you send me the logs of blueman-applet and pulseaudio -vvvv after doing some attempts to connect?  I'll try to debug this

---

### Post by flyguy97 on 2009-10-23
> **walmis said:**
> Could you send me the logs of blueman-applet and pulseaudio -vvvv after doing some attempts to connect?  I'll try to debug this

Walmis,

I did a restart and now everything is working great. Again, thank you for all your effort with this program. 

Cheers,
Jason

---

### Post by mvalenti on 2009-10-23
Hey Guys,

This is the thread I have been looking for!  I am a newbie to Ubuntu, and I love it. I have had a hard time though getting my Acer 8730 laptop to stream to my motorola ht820 stereo headset.  I followed the procedure on the Blueman site, but after I finish in terminal, what do I do? I tried looking for blueman in package manager... nothing came up.. I am obviously missing something..


Regards,

Mark

---

### Post by flyguy97 on 2009-10-23
> **mvalenti said:**
> Hey Guys,

This is the thread I have been looking for!  I am a newbie to Ubuntu, and I love it. I have had a hard time though getting my Acer 8730 laptop to stream to my motorola ht820 stereo headset.  I followed the procedure on the Blueman site, but after I finish in terminal, what do I do? I tried looking for blueman in package manager... nothing came up.. I am obviously missing something..


Regards,

Mark

Mark,

There should be a bluetooth symbol in the system tray, left click on it and you will be able to manage your devices from there. If there is no bluetooth icon in the system tray restart your computer. Let me know how it goes.

Cheers,
Jason

---

### Post by mvalenti on 2009-10-23
ahhh
ok
it is there...
let me try thanks!

---

### Post by mvalenti on 2009-10-23
Ok, so I have the icon, and it appears to be paired... No audio though...

---

### Post by walmis on 2009-10-23
Which pulseaudio version do you have installed?

---

### Post by mvalenti on 2009-10-23
how do find that?

---

### Post by mvalenti on 2009-10-23
0.9.14?

---

### Post by flyguy97 on 2009-10-23
> **mvalenti said:**
> 0.9.14?

The version required for Blueman is 0.9.15. If you have installed all the ppa's as per the instructions all you need to do is go to the command line and do the following:

```
sudo apt-get update
sudo apt-get upgrade
```

This will automatically upgrade all the pulseaudio items to the latest and greatest version.

Cheers,
Jason

---

### Post by mvalenti on 2009-10-23
ran sudo apt-get update

looks good until...
Fetched 198B in 0s (211B/s)
Reading package lists... Done
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: You may want to run apt-get update to correct these problems


then

mark@mark-laptop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by mvalenti on 2009-10-23
mark@mark-laptop:~$ sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 951DC1E2
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv-keys 951DC1E2
gpg: requesting key 951DC1E2 from hkp server keyserver.ubuntu.com
gpg: key 951DC1E2: "Launchpad PPA for Blueman Development Team" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
mark@mark-laptop:~$ sudo apt-get update
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-en_US
Get:1 [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release.gpg [197B]        
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free Translation-en_US      
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/non-free Translation-en_US  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release.gpg                  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Translation-en_US       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release.gpg           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release                          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Translation-en_US 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Translation-en_US   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Translation-en_US 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release.gpg          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Translation-en_US   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Translation-en_US     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Translation-en_US
Get:2 [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release [11.7kB]                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release                         
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages                              
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free Packages                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Packages         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Packages                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Packages          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Sources                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Sources           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Packages            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Sources                               
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/non-free Packages                     
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free Sources                
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/non-free Sources            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Packages   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Sources
Fetched 198B in 0s (260B/s)
Reading package lists... Done
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: You may want to run apt-get update to correct these problems

---

### Post by flyguy97 on 2009-10-23
> **mvalenti said:**
> ran sudo apt-get update

looks good until...
Fetched 198B in 0s (211B/s)
Reading package lists... Done
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: You may want to run apt-get update to correct these problems


then

mark@mark-laptop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

The issue is you have to import a key so your computer can verify the source of the packages. Assuming you used the PPAs from the tutorial use the following commands to import those keys:

```

sudo apt-key adv &#8211;keyserver keyserver.ubuntu.com &#8211;recv-keys B88A1AA8
sudo apt-key adv &#8211;keyserver keyserver.ubuntu.com &#8211;recv-keys 951DC1E2
```

The first one is for the pulseaudio stuff and the second one is for Blueman. Now that you have done that try and re-issue the sudo apt-get upgrade command again.

Cheers,
Jason

---

### Post by mvalenti on 2009-10-23
Ok done that...

---

### Post by flyguy97 on 2009-10-23
> **mvalenti said:**
> Ok done that...

After you do the sudo apt-get upgrade your bluetooth should work fine. Be aware you may need to restart.

Cheers,
Jason

---

### Post by mvalenti on 2009-10-23
Ok, I have the sound comming from the speakers on the laptop, still nothing from the headset, also, the sound doesnt seem as loud as it should...I really appreciate the time your taking to help me with this.


-Mark

---

### Post by flyguy97 on 2009-10-23
> **mvalenti said:**
> Ok, I have the sound comming from the speakers on the laptop, still nothing from the headset, also, the sound doesnt seem as loud as it should...I really appreciate the time your taking to help me with this.


-Mark

Have you paired the headset with your laptop?

---

### Post by mvalenti on 2009-10-23
yes, it is paired. I tried hcitool scan, it doesnt appear to detect it

---

### Post by flyguy97 on 2009-10-23
> **mvalenti said:**
> yes, it is paired. I tried hcitool scan, it doesnt appear to detect it

You shouldn't have to mess around with any of the command line tools. When you left-click on the bluetooth icon in the system tray does the headset show up in the list of bluetooth devices?

---

### Post by mvalenti on 2009-10-23
left clicking the icon shows a pulldown and only setup new device is there...

---

### Post by flyguy97 on 2009-10-23
> **mvalenti said:**
> left clicking the icon shows a pulldown and only setup new device is there...

I am not sure you have installed blueman. From a command prompt enter:

```
sudo apt-get install blueman
```

and then restart your computer

---

### Post by mvalenti on 2009-10-23
see attachments

---

### Post by mvalenti on 2009-10-23
mark@mark-laptop:~$ sudo apt-get install blueman
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  lib32ncurses5 libswfdec-0.8-0 lib32gcc1 lib32nss-mdns lib32z1 lib32stdc++6
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  bluez-gnome
The following NEW packages will be installed:
  blueman
0 upgraded, 1 newly installed, 1 to remove and 0 not upgraded.
Need to get 564kB of archives.
After this operation, 1667kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main blueman 1.21-1~ppa1j [564kB]
Fetched 564kB in 1s (503kB/s)   
dpkg: bluez-gnome: dependency problems, but removing anyway as you request:
 libmbca0 depends on bluez-gnome.
(Reading database ... 161343 files and directories currently installed.)
Removing bluez-gnome ...
Processing triggers for shared-mime-info ...
Unknown media type in type 'all/all'

Unknown media type in type 'all/allfiles'

Unknown media type in type 'uri/mms'

Unknown media type in type 'uri/mmst'

Unknown media type in type 'uri/mmsu'

Unknown media type in type 'uri/pnm'

Unknown media type in type 'uri/rtspt'

Unknown media type in type 'uri/rtspu'

Unknown media type in type 'fonts/package'

Unknown media type in type 'interface/x-winamp-skin'

Processing triggers for man-db ...
Selecting previously deselected package blueman.
(Reading database ... 161317 files and directories currently installed.)
Unpacking blueman (from .../blueman_1.21-1~ppa1j_amd64.deb) ...
Processing triggers for man-db ...
Processing triggers for hal ...
Regenerating hal fdi cache ...
 * Restarting Hardware abstraction layer hald                            [ OK ] 
Setting up blueman (1.21-1~ppa1j) ...
 * Reloading system message bus config...                                [ OK ]

---

### Post by flyguy97 on 2009-10-23
> **mvalenti said:**
> see attachments

click on the about menu item, I'm pretty sure it won't say blueman.

---

### Post by mvalenti on 2009-10-23
ok now i left click and i see my headset. shweet!i hit setup and i have the option of headset sink, a2dp sink, input service, dont connect...

---

### Post by flyguy97 on 2009-10-23
> **mvalenti said:**
> ok now i left click and i see my headset. shweet!i hit setup and i have the option of headset sink, a2dp sink, input service, dont connect...

Can you post a screenshot of the main window of blueman, I don't think it is properly recognized.

---

### Post by mvalenti on 2009-10-23
If this works this will be HUGE!....

---

### Post by flyguy97 on 2009-10-23
> **mvalenti said:**
> If this works this will be HUGE!....

Are you sure you installed the pulseaudio-module-bluetooth package. If not run the following from the command line:

```
sudo apt-get install pulseaudio-module-bluetooth
```

Once again restart.

---

### Post by mvalenti on 2009-10-23
mark@mark-laptop:~$ sudo apt-get install pulseaudio-module-bluetooth
[sudo] password for mark: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package pulseaudio-module-bluetooth
mark@mark-laptop:~$ 



hmmmmm

---

### Post by flyguy97 on 2009-10-23
> **mvalenti said:**
> mark@mark-laptop:~$ sudo apt-get install pulseaudio-module-bluetooth
[sudo] password for mark: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package pulseaudio-module-bluetooth
mark@mark-laptop:~$ 



hmmmmm

What version of Ubuntu do you have installed?

---

### Post by mvalenti on 2009-10-23
the latest 9.1

---

### Post by flyguy97 on 2009-10-23
> **mvalenti said:**
> the latest 9.1

That may be an issue. For now go into synaptic and search on pulseaudio, then post a screenshot.

---

### Post by flyguy97 on 2009-10-23
> **mvalenti said:**
> the latest 9.1

I guess I didn't explain too well. Version 9.1 is actually a release candidate right now, it won't be official for another 6 days, I am not sure on the status of all the pulseaudio packages in Karmic (a.k.a. 9.1) so it may not be possible at this time.

---

### Post by flyguy97 on 2009-10-23
> **mvalenti said:**
> the latest 9.1

Also, post the results of the following command:

```
apt-cache search pulseaudio | grep bluetooth
```

---

### Post by mvalenti on 2009-10-23
Sorry, i am running 9.04... not 9.1.... and i am having an upload issue.... let me reboot...

---

### Post by mvalenti on 2009-10-23
I cant get the last shot to upload

---

### Post by flyguy97 on 2009-10-23
> **mvalenti said:**
> I cant get the last shot to upload

It will suffice just to copy and paste the results of apt-cache search pulseaudio | grep bluetooth

---

### Post by mvalenti on 2009-10-23
mark@mark-laptop:~$ apt-cache search pulseaudio | grep bluetooth
mark@mark-laptop:~$ apt-cache search pulseaudio
libsdl1.2debian-all - Simple DirectMedia Layer (with all available options)
asoundconf-gtk - Applet to select the default ALSA sound card
audacious-plugins-extra - Various extra plugins for audacious
libsdl1.2debian-pulseaudio - Simple DirectMedia Layer (with X11 and PulseAudio options)
padevchooser - PulseAudio Device Chooser
paman - PulseAudio Manager
paprefs - PulseAudio Preferences
pavucontrol - PulseAudio Volume Control
pavumeter - PulseAudio Volume Meter
qmmp - feature-rich audio player with support of many formats
xmms2-plugin-pulse - XMMS2 - pulseaudio output plugin
vlc-plugin-pulse - PulseAudio plugin for VLC
gstreamer0.10-pulseaudio - GStreamer plugin for PulseAudio
libpulse-browse0 - PulseAudio client libraries (zeroconf support)
libpulse-browse0-dbg - PulseAudio client libraries (zeroconf support) debugging symbols
libpulse-dev - PulseAudio client development headers and libraries
libpulse-mainloop-glib0 - PulseAudio client libraries (glib support)
libpulse-mainloop-glib0-dbg - PulseAudio client libraries (glib support) debugging symbols
libpulse0 - PulseAudio client libraries
libpulse0-dbg - PulseAudio client libraries detached debugging symbols
libpulsecore9 - PulseAudio sound server core
libpulsecore9-dbg - PulseAudio sound server core detached debugging symbols
pulseaudio - PulseAudio sound server
pulseaudio-dbg - PulseAudio sound server detached debugging symbols
pulseaudio-esound-compat - PulseAudio ESD compatibility layer
pulseaudio-esound-compat-dbg - PulseAudio ESD compatibility layer debugging symbols
pulseaudio-module-gconf - GConf module for PulseAudio sound server
pulseaudio-module-gconf-dbg - GConf module for PulseAudio sound server debugging symbols
pulseaudio-module-hal - HAL device detection module for PulseAudio sound server
pulseaudio-module-hal-dbg - HAL module for PulseAudio sound server debugging symbols
pulseaudio-module-lirc - lirc module for PulseAudio sound server
pulseaudio-module-lirc-dbg - lirc module for PulseAudio sound server debugging symbols
pulseaudio-module-x11 - X11 module for PulseAudio sound server
pulseaudio-module-x11-dbg - X11 module for PulseAudio sound server debugging symbols
pulseaudio-module-zeroconf - Zeroconf module for PulseAudio sound server
pulseaudio-module-zeroconf-dbg - Zeroconf module for PulseAudio sound server debugging symbols
pulseaudio-utils - Command line tools for the PulseAudio sound server
pulseaudio-utils-dbg - PulseAudio command line tools detached debugging symbol

---

### Post by mvalenti on 2009-10-23
mark@mark-laptop:~$ apt-cache search bluetooth
bluez-gnome - Bluetooth utilities for GNOME
kdebluetooth - KDE Bluetooth Framework
totem-plugins - Plugins for the Totem media player
amora-server - use a bluetooth enabled mobile phone as desktop remote control
anyremote - Remote control daemon for applications using Bluetooth, IrDA or WiFi
anyremote-doc - Documentation for anyremote
bluemon - Activate or deactivate programs based on Bluetooth link quality
blueproximity - locks/unlocks your desktop tracking a bluetooth device
bluez-btsco - Bluez Bluetooth SCO tool
bluez-hcidump - Analyses Bluetooth HCI packets
btscanner - ncurses-based scanner for Bluetooth devices
ganyremote - GTK+ frontend for anyRemote
gnome-bluetooth - GNOME Bluetooth tools.
gnome-vfs-obexftp - GNOME VFS module for OBEX FTP
gpe-bluetooth - Bluetooth connectivity tool for GPE
gpodder - A free podcast aggregator written in PyGTK
grml-btnet - Programs to quickly build a bluetooth network
kanyremote - KDE frontend for anyRemote
libbtctl4 - GObject Bluetooth library
libbtctl4-dev - Development files for GObject Bluetooth library
libcwiid1 - library to interface with the wiimote
libgnomebt0 - GNOME Bluetooth library
libgnomebt0-dev - Development files for GNOME Bluetooth library
libmultisync-plugin-irmc - IrMc Mobile plugin for MultiSync
libmultisync-plugin-irmc-bluetooth - Adds Bluetooth support to the IrMC plugin
libnet-bluetooth-perl - Perl Bluetooth interface
libpam-blue - PAM module for local authenticaction with bluetooth devices
multisync - A program to synchronize PIM data
obexfs - mount filesystem of ObexFTP capable devices
obexftp - file transfer utility for devices that use the OBEX protocol
obexpushd - program for receiving files via Bluetooth or IRDA
opensync-plugin-irmc - IrMC plugin for opensync
osso-gwconnect - Bluetooth connectivity applications
osso-gwconnect-dev - Bluetooth connectivity applications - development files
p3nfs - to mount the file systems on the Psion/Symbian PDA/Phone
python-bluez - Python wrappers around BlueZ for rapid bluetooth development
python-libbtctl - Python bindings for libbtctl Bluetooth library
python-lightblue - cross-platform Bluetooth API for Python
ussp-push - Client for OBEX PUSH
wiipdf - present a PDF file using your wiimote
blueman - A Graphical bluetooth manager
obex-data-server - D-Bus service for OBEX client and server side functionality
bluetooth - Bluetooth support
bluez - Bluetooth tools and daemons
bluez-alsa - Bluetooth audio support
bluez-cups - Bluetooth printer driver for CUPS
bluez-gstreamer - Bluetooth gstreamer support
bluez-pcmcia-support - PCMCIA support files for BlueZ 2.0 Bluetooth tools
libbluetooth-dev - Development files for using the BlueZ Linux Bluetooth library
libbluetooth3 - Library to use the BlueZ Linux Bluetooth stack
mark@mark-laptop:~$

---

### Post by flyguy97 on 2009-10-23
> **mvalenti said:**
> mark@mark-laptop:~$ apt-cache search pulseaudio | grep bluetooth
mark@mark-laptop:~$ apt-cache search pulseaudio
libsdl1.2debian-all - Simple DirectMedia Layer (with all available options)
asoundconf-gtk - Applet to select the default ALSA sound card
audacious-plugins-extra - Various extra plugins for audacious
libsdl1.2debian-pulseaudio - Simple DirectMedia Layer (with X11 and PulseAudio options)
padevchooser - PulseAudio Device Chooser
paman - PulseAudio Manager
paprefs - PulseAudio Preferences
pavucontrol - PulseAudio Volume Control
pavumeter - PulseAudio Volume Meter
qmmp - feature-rich audio player with support of many formats
xmms2-plugin-pulse - XMMS2 - pulseaudio output plugin
vlc-plugin-pulse - PulseAudio plugin for VLC
gstreamer0.10-pulseaudio - GStreamer plugin for PulseAudio
libpulse-browse0 - PulseAudio client libraries (zeroconf support)
libpulse-browse0-dbg - PulseAudio client libraries (zeroconf support) debugging symbols
libpulse-dev - PulseAudio client development headers and libraries
libpulse-mainloop-glib0 - PulseAudio client libraries (glib support)
libpulse-mainloop-glib0-dbg - PulseAudio client libraries (glib support) debugging symbols
libpulse0 - PulseAudio client libraries
libpulse0-dbg - PulseAudio client libraries detached debugging symbols
libpulsecore9 - PulseAudio sound server core
libpulsecore9-dbg - PulseAudio sound server core detached debugging symbols
pulseaudio - PulseAudio sound server
pulseaudio-dbg - PulseAudio sound server detached debugging symbols
pulseaudio-esound-compat - PulseAudio ESD compatibility layer
pulseaudio-esound-compat-dbg - PulseAudio ESD compatibility layer debugging symbols
pulseaudio-module-gconf - GConf module for PulseAudio sound server
pulseaudio-module-gconf-dbg - GConf module for PulseAudio sound server debugging symbols
pulseaudio-module-hal - HAL device detection module for PulseAudio sound server
pulseaudio-module-hal-dbg - HAL module for PulseAudio sound server debugging symbols
pulseaudio-module-lirc - lirc module for PulseAudio sound server
pulseaudio-module-lirc-dbg - lirc module for PulseAudio sound server debugging symbols
pulseaudio-module-x11 - X11 module for PulseAudio sound server
pulseaudio-module-x11-dbg - X11 module for PulseAudio sound server debugging symbols
pulseaudio-module-zeroconf - Zeroconf module for PulseAudio sound server
pulseaudio-module-zeroconf-dbg - Zeroconf module for PulseAudio sound server debugging symbols
pulseaudio-utils - Command line tools for the PulseAudio sound server
pulseaudio-utils-dbg - PulseAudio command line tools detached debugging symbol

What is the result of the following command:

```
cat /etc/apt/sources.list | grep themuso
```

---

### Post by mvalenti on 2009-10-23
mark@mark-laptop:~$ cat /etc/apt/sources.list | grep themuso
mark@mark-laptop:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release amd64 (20090420.1)]/ jaunty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) jaunty free non-free
deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) jaunty free non-free
deb [http://ppa.launchpad.net/blueman/ppa/ubuntu](http://ppa.launchpad.net/blueman/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/blueman/ppa/ubuntu](http://ppa.launchpad.net/blueman/ppa/ubuntu) jaunty main
mark@mark-laptop:~$ cat /etc/apt/themuso
cat: /etc/apt/themuso: No such file or directory
mark@mark-laptop:~$ cat /etc/apt/sources.list | grep themuso
mark@mark-laptop:~$ cls
bash: cls: command not found
mark@mark-laptop:~$ clear

mark@mark-laptop:~$ cat /etc/apt/sources.list | grep themuso
mark@mark-laptop:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release amd64 (20090420.1)]/ jaunty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) jaunty free non-free
deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) jaunty free non-free
deb [http://ppa.launchpad.net/blueman/ppa/ubuntu](http://ppa.launchpad.net/blueman/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/blueman/ppa/ubuntu](http://ppa.launchpad.net/blueman/ppa/ubuntu) jaunty main
mark@mark-laptop:~$

---

### Post by flyguy97 on 2009-10-23
> **mvalenti said:**
> mark@mark-laptop:~$ cat /etc/apt/sources.list | grep themuso
mark@mark-laptop:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release amd64 (20090420.1)]/ jaunty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) jaunty free non-free
deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) jaunty free non-free
deb [http://ppa.launchpad.net/blueman/ppa/ubuntu](http://ppa.launchpad.net/blueman/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/blueman/ppa/ubuntu](http://ppa.launchpad.net/blueman/ppa/ubuntu) jaunty main
mark@mark-laptop:~$ cat /etc/apt/themuso
cat: /etc/apt/themuso: No such file or directory
mark@mark-laptop:~$ cat /etc/apt/sources.list | grep themuso
mark@mark-laptop:~$ cls
bash: cls: command not found
mark@mark-laptop:~$ clear

mark@mark-laptop:~$ cat /etc/apt/sources.list | grep themuso
mark@mark-laptop:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release amd64 (20090420.1)]/ jaunty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) jaunty free non-free
deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) jaunty free non-free
deb [http://ppa.launchpad.net/blueman/ppa/ubuntu](http://ppa.launchpad.net/blueman/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/blueman/ppa/ubuntu](http://ppa.launchpad.net/blueman/ppa/ubuntu) jaunty main
mark@mark-laptop:~$

The good news is you are just a couple of steps away from some sweet bluetooth love. You need to add ```
deb http://ppa.launchpad.net/themuso/ppa/ubuntu jaunty main
``` to the software sources applet found in the System menu. Go to the Third-Party Software tab and click add. Answer yes to the question about updating apt get and then issue the sudo apt-get install pulseaudio-module-bluetooth command in a terminal window. Restart the computer, use the audio sink service and let me know it worked for you.

---

### Post by mvalenti on 2009-10-23
holy crap it works! simple as 1,2,3....er 4...5... pages!  Thanks soooo much for your help! this rocks! this helps me get over a big hurdle switching to ubuntu permanently... I have an Acer 8730 laptop which came with vista... other than a cad app i have no use for windows.... My next task will be to tackle the buttons that arnt functional. But that isnt a huge deal.  


Thanks again,

Mark

---

### Post by flyguy97 on 2009-10-23
> **mvalenti said:**
> holy crap it works! simple as 1,2,3....er 4...5... pages!  Thanks soooo much for your help! this rocks! this helps me get over a big hurdle switching to ubuntu permanently... I have an Acer 8730 laptop which came with vista... other than a cad app i have no use for windows.... My next task will be to tackle the buttons that arnt functional. But that isnt a huge deal.  


Thanks again,

Mark

No problem Mark, I truly hope you become a permanent Linux convert. It would be great if Karmic improves on the user experience when it comes to bluetooth, needless to say it is overcomplicated. One last thing you will want to do is install a helper package for Flash, apparently there is some issues with Flash and pulseaudio. From a command line issue the following command:

```
sudo apt-get install flashplugin-nonfree-extrasound
```

Cheers,
Jason

---

### Post by mvalenti on 2009-10-24
> **flyguy97 said:**
> No problem Mark, I truly hope you become a permanent Linux convert. It would be great if Karmic improves on the user experience when it comes to bluetooth, needless to say it is overcomplicated. One last thing you will want to do is install a helper package for Flash, apparently there is some issues with Flash and pulseaudio. From a command line issue the following command:

```
sudo apt-get install flashplugin-nonfree-extrasound
```

Cheers,
Jason


I guess my reply never made it yesterday.  So here it goes again... ;)
LOL, overcomplicated, yeah, a little... Especially to new users like myself. Hopefully someone like me will read this thread and it will help them. 

I tried the command for flash you suggested but it didn't work. results as follows.

mark@mark-laptop:~$ sudo apt-get install flashplugin-nonfree-extrasound
[sudo] password for mark: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package flashplugin-nonfree-extrasound
mark@mark-laptop:~$ 
mark@mark-laptop:~$ 

The laptop I have is fairly new, less than a year, its fast, and blistering with ubuntu. its 98% working at this point which I am happy with. It has a touch volume bar that does not play well with the computers volume. But thats not a huge issue at the moment.. ;)

Thanks again!

Mark

---

### Post by flyguy97 on 2009-10-24
> **mvalenti said:**
> I guess my reply never made it yesterday.  So here it goes again... ;)
LOL, overcomplicated, yeah, a little... Especially to new users like myself. Hopefully someone like me will read this thread and it will help them. 

I tried the command for flash you suggested but it didn't work. results as follows.

mark@mark-laptop:~$ sudo apt-get install flashplugin-nonfree-extrasound
[sudo] password for mark: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package flashplugin-nonfree-extrasound
mark@mark-laptop:~$ 
mark@mark-laptop:~$ 

The laptop I have is fairly new, less than a year, its fast, and blistering with ubuntu. its 98% working at this point which I am happy with. It has a touch volume bar that does not play well with the computers volume. But thats not a huge issue at the moment.. ;)

Thanks again!

Mark

Do you have the medibuntu repository installed?

---

### Post by mvalenti on 2009-10-24
I think so, i saw it wasnt checked, so I checked it, then got the message in the screenshot.

---

### Post by flyguy97 on 2009-10-24
> **mvalenti said:**
> I think so, i saw it wasnt checked, so I checked it, then got the message in the screenshot.

The problem is you don't have the gpg key installed issue the following command: 

```

sudo apt-get -q update &&
sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring &&
sudo apt-get -q update

```

Then re-issue the command to install the flash package I referenced earlier.

Cheers,
Jason

---

### Post by mvalenti on 2009-10-24
Jason,

Here are the results... That keyring always gets me...

mark@mark-laptop:~$ sudo apt-get -q update &&
> 
> sudo apt-get -q update
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Translation-en_US
Get:1 [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release.gpg [197B]
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free Translation-en_US
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/non-free Translation-en_US
Get:2 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg [307B]
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release
Get:3 [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release [11.7kB]
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release
Get:4 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release [74.6kB]
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/non-free Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free Sources
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/non-free Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Sources
Fetched 506B in 1s (501B/s)
Reading package lists...
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 0B47F0A6B88A1AA8
W: You may want to run apt-get update to correct these problems
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-en_US
Get:1 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg [307B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Translation-en_US
Get:2 [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release.gpg [197B]
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free Translation-en_US
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/non-free Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release
Get:3 [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release [11.7kB]
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release
Get:4 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release [74.6kB]
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Sources
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/non-free Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free Sources
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/non-free Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Sources
Fetched 506B in 1s (255B/s)
Reading package lists...
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 0B47F0A6B88A1AA8
W: You may want to run apt-get update to correct these problems
mark@mark-laptop:~$ sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring
Reading package lists...
Building dependency tree...
Reading state information...
The following NEW packages will be installed:
  medibuntu-keyring
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 3448B of archives.
After this operation, 49.2kB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  medibuntu-keyring
Authentication warning overridden.
Get:1 [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free medibuntu-keyring 2008.04.20 [3448B]
Fetched 3448B in 0s (11.3kB/s)
Selecting previously deselected package medibuntu-keyring.
(Reading database ... 163462 files and directories currently installed.)
Unpacking medibuntu-keyring (from .../medibuntu-keyring_2008.04.20_all.deb) ...
Setting up medibuntu-keyring (2008.04.20) ...
OK

mark@mark-laptop:~$ sudo apt-get -q update
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-en_US
Get:1 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg [307B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Translation-en_US
Get:2 [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release.gpg [197B]
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free Translation-en_US
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/non-free Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release
Get:3 [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release [11.7kB]
Get:4 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release [74.6kB]
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/non-free Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free Sources
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/non-free Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Sources
Fetched 506B in 0s (768B/s)
Reading package lists...
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 0B47F0A6B88A1AA8
W: You may want to run apt-get update to correct these problems
mark@mark-laptop:~$ sudo apt-get install flashplugin-nonfree-extrasound
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package flashplugin-nonfree-extrasound
mark@mark-laptop:~$

---

### Post by flyguy97 on 2009-10-24
> **mvalenti said:**
> Jason,

Here are the results... That keyring always gets me...

mark@mark-laptop:~$ sudo apt-get -q update &&
> 
> sudo apt-get -q update
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Translation-en_US
Get:1 [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release.gpg [197B]
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free Translation-en_US
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/non-free Translation-en_US
Get:2 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg [307B]
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release
Get:3 [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release [11.7kB]
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release
Get:4 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release [74.6kB]
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/non-free Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free Sources
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/non-free Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Sources
Fetched 506B in 1s (501B/s)
Reading package lists...
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 0B47F0A6B88A1AA8
W: You may want to run apt-get update to correct these problems
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-en_US
Get:1 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg [307B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Translation-en_US
Get:2 [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release.gpg [197B]
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free Translation-en_US
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/non-free Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release
Get:3 [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release [11.7kB]
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release
Get:4 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release [74.6kB]
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Sources
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/non-free Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free Sources
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/non-free Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Sources
Fetched 506B in 1s (255B/s)
Reading package lists...
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 0B47F0A6B88A1AA8
W: You may want to run apt-get update to correct these problems
mark@mark-laptop:~$ sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring
Reading package lists...
Building dependency tree...
Reading state information...
The following NEW packages will be installed:
  medibuntu-keyring
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 3448B of archives.
After this operation, 49.2kB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  medibuntu-keyring
Authentication warning overridden.
Get:1 [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free medibuntu-keyring 2008.04.20 [3448B]
Fetched 3448B in 0s (11.3kB/s)
Selecting previously deselected package medibuntu-keyring.
(Reading database ... 163462 files and directories currently installed.)
Unpacking medibuntu-keyring (from .../medibuntu-keyring_2008.04.20_all.deb) ...
Setting up medibuntu-keyring (2008.04.20) ...
OK

mark@mark-laptop:~$ sudo apt-get -q update
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-en_US
Get:1 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg [307B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Translation-en_US
Get:2 [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release.gpg [197B]
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free Translation-en_US
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/non-free Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release
Get:3 [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release [11.7kB]
Get:4 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release [74.6kB]
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/non-free Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free Sources
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/non-free Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Sources
Fetched 506B in 0s (768B/s)
Reading package lists...
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 0B47F0A6B88A1AA8
W: You may want to run apt-get update to correct these problems
mark@mark-laptop:~$ sudo apt-get install flashplugin-nonfree-extrasound
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package flashplugin-nonfree-extrasound
mark@mark-laptop:~$

I'm not sure why that's not working, try the following:

```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

---

### Post by mvalenti on 2009-10-24
mark@mark-laptop:~$ sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
[sudo] password for mark: 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release.gpg                  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Translation-en_US                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-en_US                     
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release.gpg                           
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free Translation-en_US                
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/non-free Translation-en_US            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Translation-en_US    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release                         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Translation-en_US           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Translation-en_US   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Translation-en_US 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release.gpg          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release                      
Get:1 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg [307B]             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-en_US           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release                          
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release             
Get:2 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release [74.6kB]              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Packages                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Packages                          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages                              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Sources                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Sources              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Packages               
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free Packages                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release                                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Sources                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Sources                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Packages                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Sources                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Sources                               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Sources                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Packages   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Sources    
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/non-free Packages           
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free Sources                
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/non-free Sources            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Packages          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Sources
Fetched 308B in 0s (369B/s)
Reading package lists... Done
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 0B47F0A6B88A1AA8
W: You may want to run apt-get update to correct these problems
Reading package lists... Done
Building dependency tree       
Reading state information... Done
medibuntu-keyring is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release.gpg                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Translation-en_US          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Translation-en_US    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-en_US                     
Get:1 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg [307B]                       
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release.gpg                           
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free Translation-en_US                
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/non-free Translation-en_US            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Translation-en_US           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Translation-en_US   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Translation-en_US 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release.gpg          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release                                
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Translation-en_US      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Translation-en_US    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-en_US                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release                                    
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release                        
Get:2 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release [74.6kB]                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release                                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Packages                   
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free Packages                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Packages                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Packages          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Sources                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Sources                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Packages                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Sources                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Packages   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Sources          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Sources              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Packages               
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/non-free Packages                     
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free Sources                
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/non-free Sources            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Sources             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Packages          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Sources           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Packages        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Packages  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Sources         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Sources   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Sources      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Sources
Fetched 308B in 0s (470B/s)
Reading package lists... Done
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 0B47F0A6B88A1AA8
W: You may want to run apt-get update to correct these problems
mark@mark-laptop:~$

---

### Post by flyguy97 on 2009-10-24
> **mvalenti said:**
> mark@mark-laptop:~$ sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
[sudo] password for mark: 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release.gpg                  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Translation-en_US                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-en_US                     
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release.gpg                           
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free Translation-en_US                
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/non-free Translation-en_US            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Translation-en_US    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release                         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Translation-en_US           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Translation-en_US   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Translation-en_US 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release.gpg          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release                      
Get:1 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg [307B]             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-en_US           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release                          
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release             
Get:2 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release [74.6kB]              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Packages                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Packages                          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages                              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Sources                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Sources              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Packages               
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free Packages                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release                                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Sources                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Sources                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Packages                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Sources                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Sources                               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Sources                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Packages   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Sources    
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/non-free Packages           
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free Sources                
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/non-free Sources            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Packages          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Sources
Fetched 308B in 0s (369B/s)
Reading package lists... Done
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 0B47F0A6B88A1AA8
W: You may want to run apt-get update to correct these problems
Reading package lists... Done
Building dependency tree       
Reading state information... Done
medibuntu-keyring is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release.gpg                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Translation-en_US          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Translation-en_US    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-en_US                     
Get:1 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg [307B]                       
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release.gpg                           
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free Translation-en_US                
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/non-free Translation-en_US            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Translation-en_US           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Translation-en_US   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Translation-en_US 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release.gpg          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release                                
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Translation-en_US      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Translation-en_US    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-en_US                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release                                    
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release                        
Get:2 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release [74.6kB]                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release                                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Packages                   
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free Packages                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Packages                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Packages          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Sources                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Sources                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Packages                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Sources                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Packages   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Sources          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Sources              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Packages               
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/non-free Packages                     
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free Sources                
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/non-free Sources            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Sources             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Packages          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Sources           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Packages        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Packages  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Sources         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Sources   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Sources      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Sources
Fetched 308B in 0s (470B/s)
Reading package lists... Done
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 0B47F0A6B88A1AA8
W: You may want to run apt-get update to correct these problems
mark@mark-laptop:~$

I must admit, don't know why this is happening, try the following two commands then give it a go:

```

gpg --keyserver keyserver.ubuntu.com --recv B88A1AA8
gpg --export --armor 6F087E5A | sudo apt-key add - && sudo apt-get update
```

---

### Post by mvalenti on 2009-10-24
OH no, I cant stump the MASTER! 

I think I am doing something wrong.

mark@mark-laptop:~$ gpg --keyserver keyserver.ubuntu.com --recv B88A1AA8
gpg: requesting key B88A1AA8 from hkp server keyserver.ubuntu.com
gpg: key B88A1AA8: "Launchpad PPA for Luke Yelavich" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
mark@mark-laptop:~$ gpg --export --armor 6F087E5A
gpg: WARNING: nothing exported
mark@mark-laptop:~$ sudo apt-get add -&&
> sudo apt-get update
E: Invalid operation add
mark@mark-laptop:~$

---

### Post by flyguy97 on 2009-10-24
> **mvalenti said:**
> OH no, I cant stump the MASTER! 

I think I am doing something wrong.

mark@mark-laptop:~$ gpg --keyserver keyserver.ubuntu.com --recv B88A1AA8
gpg: requesting key B88A1AA8 from hkp server keyserver.ubuntu.com
gpg: key B88A1AA8: "Launchpad PPA for Luke Yelavich" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
mark@mark-laptop:~$ gpg --export --armor 6F087E5A
gpg: WARNING: nothing exported
mark@mark-laptop:~$ sudo apt-get add -&&
> sudo apt-get update
E: Invalid operation add
mark@mark-laptop:~$

That was my fault, try the following instead:

```

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys B88A1AA8

```

---

### Post by mvalenti on 2009-10-24
mark@mark-laptop:~$ sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys B88A1AA8
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv-keys B88A1AA8
gpg: requesting key B88A1AA8 from hkp server keyserver.ubuntu.com
gpg: key B88A1AA8: "Launchpad PPA for Luke Yelavich" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
mark@mark-laptop:~$ 


that seemed to work

---

### Post by flyguy97 on 2009-10-24
> **mvalenti said:**
> mark@mark-laptop:~$ sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys B88A1AA8
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv-keys B88A1AA8
gpg: requesting key B88A1AA8 from hkp server keyserver.ubuntu.com
gpg: key B88A1AA8: "Launchpad PPA for Luke Yelavich" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
mark@mark-laptop:~$ 


that seemed to work

did you install the flash sound package?

---

### Post by mvalenti on 2009-10-24
mark@mark-laptop:~$ sudo apt-get install flashplugin-nonfree-extrasound
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package flashplugin-nonfree-extrasound
mark@mark-laptop:~$

---

### Post by mvalenti on 2009-10-24
mark@mark-laptop:~$ sudo apt-get install flashplugin-nonfree-extrasound
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package flashplugin-nonfree-extrasound
mark@mark-laptop:~$ sudo apt-get -q update &&
> clear
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release.gpg
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Translation-en_US
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free Translation-en_US
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/non-free Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Translation-en_US
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release
Get:1 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg [307B]
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release.gpg
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release
Get:2 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release [74.6kB]
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/non-free Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free Sources
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/non-free Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Sources
Fetched 308B in 1s (184B/s)
Reading package lists...

mark@mark-laptop:~$ sudo apt-get -q update
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Translation-en_US
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release.gpg
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free Translation-en_US
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/non-free Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release.gpg
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release.gpg
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/non-free Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free Sources
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/non-free Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Sources
Reading package lists...
mark@mark-laptop:~$ sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring
Reading package lists...
Building dependency tree...
Reading state information...
medibuntu-keyring is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
mark@mark-laptop:~$ sudo apt-get -q update
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-en_US
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release.gpg
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free Translation-en_US
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/non-free Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release.gpg
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/non-free Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free Sources
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/non-free Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Sources
Reading package lists...
mark@mark-laptop:~$ sudo apt-get install flashplugin-nonfree-extrasound
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package flashplugin-nonfree-extrasound
mark@mark-laptop:~$

---

### Post by flyguy97 on 2009-10-24
> **mvalenti said:**
> mark@mark-laptop:~$ sudo apt-get install flashplugin-nonfree-extrasound
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package flashplugin-nonfree-extrasound
mark@mark-laptop:~$ sudo apt-get -q update &&
> clear
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release.gpg
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Translation-en_US
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free Translation-en_US
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/non-free Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Translation-en_US
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release
Get:1 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg [307B]
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release.gpg
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release
Get:2 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release [74.6kB]
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/non-free Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free Sources
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/non-free Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Sources
Fetched 308B in 1s (184B/s)
Reading package lists...

mark@mark-laptop:~$ sudo apt-get -q update
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Translation-en_US
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release.gpg
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free Translation-en_US
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/non-free Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release.gpg
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release.gpg
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/non-free Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free Sources
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/non-free Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Sources
Reading package lists...
mark@mark-laptop:~$ sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring
Reading package lists...
Building dependency tree...
Reading state information...
medibuntu-keyring is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
mark@mark-laptop:~$ sudo apt-get -q update
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-en_US
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release.gpg
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free Translation-en_US
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/non-free Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release.gpg
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/non-free Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free Sources
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/non-free Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Sources
Reading package lists...
mark@mark-laptop:~$ sudo apt-get install flashplugin-nonfree-extrasound
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package flashplugin-nonfree-extrasound
mark@mark-laptop:~$

This is a long-shot but you may not have the multiverse repository enabled, I would have thought this was a default repository but please check to make sure that System -> Software Sources -> Ubuntu Software tab looks like the attached screenshot. If it doesn't look like the following make all the necessary changes and reissue the update install commands.

---

### Post by mvalenti on 2009-10-24
Does it matter that I am in the US? Also, the last checkbox changes color when clicked, no mark appears...

---

### Post by flyguy97 on 2009-10-24
> **mvalenti said:**
> Does it matter that I am in the US? Also, the last checkbox changes color when clicked, no mark appears...

In the second tab, "Third-Party Software", enable the unchecked canonical repositories. Again, I'm not really sure what's going on, the flash sound package looks to be in the multiverse repository which you have enabled. Not sure why you are unable to do this. As for your questions about the states. I am an American expat living in the UK and I never had issues installing anything from Ubuntu when I lived in the states so I don't believe this is an issue, I think it has something to do with an uninstalled repository.

---

### Post by mvalenti on 2009-10-24
Same issues.... I will reboot and try again... Thanks for the patience..

-Mark

---

### Post by mvalenti on 2009-10-24
Same issues..after reboot also..

---

### Post by flyguy97 on 2009-10-24
> **mvalenti said:**
> Same issues..after reboot also..

give me the exact commands you are trying to execute please.

---

### Post by mvalenti on 2009-10-24
Sorry I think I got a little lost...

If I backtrack thru the thread I believe I would run the commands as follows:

sudo apt-get install flashplugin-nonfree-extrasound

sudo apt-get -q update

sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring

sudo apt-get -q update

---

### Post by flyguy97 on 2009-10-24
> **mvalenti said:**
> Sorry I think I got a little lost...

If I backtrack thru the thread I believe I would run the commands as follows:

sudo apt-get install flashplugin-nonfree-extrasound

sudo apt-get -q update

sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring

sudo apt-get -q update

Yes, that would be it.

---

### Post by mvalenti on 2009-10-25
found this:

[http://ubuntuforums.org/showthread.php?t=1193567](http://ubuntuforums.org/showthread.php?t=1193567)


did this... 

sudo apt-get remove swfdec-mozilla
sudo apt-get remove mozilla-plugin-gnash
sudo apt-get remove adobe-flashplugin
sudo apt-get remove flashplugin-nonfree
sudo apt-get install flashplugin-nonfree



seems to be working, conflict between installed packages I think..

I appreciate the help thanks again!

-Mark

---

### Post by tinagus2000 on 2010-05-11
Hi, I hope someone can help me.

I have a Nokia Bh-105 Bluetooth device correctly paired and connected according to blueman. However when I select it as the output device in the sound preferences panel, I get no sound. I'm using an HP Xompaq Nx7000 and Ubuntu Karmic.

Thanks in advance for your reply!

Agustín

---

