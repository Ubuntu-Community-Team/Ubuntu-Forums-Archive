---
title: "Virtualbox problem"
date: 2009-01-25
forum: General Help
---

### Post by orchidfire on 2009-01-25
Hi everyone,

I just attempted to upgrade my Virtualbox to 2.1, but that didn't seem to work, so I went and reinstalled the virtualbox-ose packages through Synaptic.  Everything seems to have worked fine&#8212;it shows up when I bring up the run dialog, and it's in my menu&#8212;but, whenever I attempt to run Virtualbox, it doesn't bring anything up.

This is an issue for me because there are a couple bits of software that I can only run through Virtualbox (unless someone can help me figure out why the audio in my Wine isn't working&#8212;but that seems to be a whole different thread).  I'm running Intrepid.

Thanks in advance!

---

### Post by x33a on 2009-01-25
try uninstalling all virtualbox related packages. and again install it from a deb using dpkg.

---

### Post by Ahadiel on 2009-01-25
Try running 'VirtualBox' from the commandline and posting any errors.

---

### Post by orchidfire on 2009-01-25
I uninstalled all Virtualbox-related packages through Synaptic, then went to the Virtualbox site and installed 2.1 using the .deb provided.  However, after that, I tried running it through the run dialog and the command wasn't recognized (whereas with my 2.0 it worked fine); I tried through Terminal and got the following:

```
stephany@discworld:~$ virtualbox
The program 'virtualbox' is currently not installed.  You can install it by typing:
sudo apt-get install virtualbox-ose
bash: virtualbox: command not found
```

Reinstallation of virtualbox-ose got me this:

```
stephany@discworld:~$ sudo apt-get install virtualbox-ose
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libglib1.2ldbl dvdrip-doc liblzo1 libevent-execflow-perl libgtk1.2
  libnet-ssleay-perl libfame-0.9 libwxgtk2.6-0 libintl-perl toolame libpvm3
  transcode-doc transfig libsox0 libgammu-common python-bluez
  libakonadiprivate1 subtitleripper libgammu3 libevent-rpc-perl ogmtools
  gtk2-ex-formfactory-perl libwxbase2.6-0 lsdvd openssh-blacklist ffmpeg
  libmjpegtools0c2a transcode fping netpbm pvm anyevent-perl libsox-fmt-base
  sox libgtk1.2-common gocr libsox-fmt-alsa libevent-perl libnetpbm10
  mjpegtools xine-ui imagemagick libio-socket-ssl-perl libquicktime1 libimlib2
  kdepimlibs-data libavdevice52
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  virtualbox-ose-source
Suggested packages:
  bridge-utils
The following packages will be REMOVED:
  virtualbox-2.1
The following NEW packages will be installed:
  virtualbox-ose virtualbox-ose-source
0 upgraded, 2 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B/6613kB of archives.
After this operation, 39.8MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 182836 files and directories currently installed.)
Removing virtualbox-2.1 ...
 * Stopping VirtualBox kernel module                                             *  done.
Selecting previously deselected package virtualbox-ose.
(Reading database ... 182426 files and directories currently installed.)
Unpacking virtualbox-ose (from .../virtualbox-ose_2.0.4-dfsg-0ubuntu1_i386.deb) ...
Selecting previously deselected package virtualbox-ose-source.
Unpacking virtualbox-ose-source (from .../virtualbox-ose-source_2.0.4-dfsg-0ubuntu1_all.deb) ...
Setting up virtualbox-ose (2.0.4-dfsg-0ubuntu1) ...
Installing new version of config file /etc/init.d/vboxdrv ...
Starting VirtualBox host networking * Starting VirtualBox kernel module vboxdrv                                                                                 
 * No suitable module for running kernel found.

Setting up virtualbox-ose-source (2.0.4-dfsg-0ubuntu1) ...
 * Reloading kernel event manager...                                     [ OK ] 
Adding Module to DKMS build system
Doing initial module build
Installing initial module
Done.
 * Stopping VirtualBox kernel module vboxdrv                             [ OK ] 
 * Starting VirtualBox kernel module vboxdrv                             [ OK ] 
```

This line was headed by a red asterisk, though:

```
 * No suitable module for running kernel found.
```

Afterward, I tried the following:

```
stephany@discworld:~$ virtualbox
Could not find VirtualBox installation. Please reinstall.
```

I'm probably missing something obvious; that's usually the case with me... particularly because I'm still pretty new to Ubuntu.  I mean, I've been using it since September or so, but I still only have a basic grasp of how things work. :???:

---

### Post by tpl on 2009-01-25
I was just about to post the same thing as Orchidfire.  Just want the very latest Virtualbox... don't care if it is shining white opensource or not!

---

### Post by sumit.kalra999 on 2009-01-25
just edit into ~/.wine/config file.


[WinMM]
; Uncomment the "Drivers" line matching your sound setting by removing ";".



"Drivers" = "winealsa.drv"    ; for ALSA users
;"Drivers" = "wineoss.drv"     ; default for most common configurations
;"Drivers" = "winearts.drv"    ; for KDE
;"Drivers" = "winejack.drv"    ; for the JACK sound server
;"Drivers" = "winenas.drv"     ; for the NAS sound system
;"Drivers" = "wineaudioio.drv" ; for Solaris machines
;"Drivers" = ""                ; disables sound
"WaveMapper" = "msacm.drv"	 ; do not change !
"MidiMapper" = "midimap.drv"	 ; do not change !

---

### Post by orchidfire on 2009-01-25
Apparently that file doesn't exist for me&#8212;do I need to create it, or should I reinstall Wine?  I never use Wine, so it wouldn't be a big deal for me to reinstall.

---

### Post by orchidfire on 2009-02-08
Hi everyone,

I'm still having problems with my Virtualbox.  :/ I've tried uninstalling, reinstalling, etc.  Has anyone else had this problem?

I tried reinstalling 2.0.4 (the last version I had) via the .deb provided on the website.  I completely removed all my virtualbox files through Synaptic, then installed and reinstalled the 2.0.4 deb.  Terminal says:

```
stephany@discworld:~$ virtualbox
The program 'virtualbox' is currently not installed.  You can install it by typing:
sudo apt-get install virtualbox-ose
bash: virtualbox: command not found
```

.deb Terminal says:

```
(Reading database ... 197291 files and directories currently installed.)
Preparing to replace virtualbox-2.0 2.0.4-34806_Ubuntu_intrepid (using .../virtualbox-2.0_2.0.4-28406_Ubuntu_intrepid_i386-1.deb) ...
 * Stopping VirtualBox kernel module
 *  done.
 * Shutting down VirtualBox host networking
 *  done.
Unpacking replacement virtualbox-2.0 ...
Setting up virtualbox-2.0 (2.0.4-38406_Ubuntu_intrepid) ...
addgroup: The group `vboxusers' already exists as a system group. Exiting.
Messages emitted during module compilation will be logged to /var/log/vbox-install.log
Success!
 * Starting VirtualBox kernel module
 *  done.
 * Starting VirtualBox host networking
 *  done.
```

What am I doing wrong?  Is there something I'm completely overlooking?  This is really frustrating, because certain software that I have to use for school isn't Ubuntu-friendly, and Wine continues to lack sound.  If I can't fix VirtualBox, I'll probably have to use another emulator—VirtualBox was working perfectly for me until I screwed it up by trying to upgrade :/

---

### Post by howefield on 2009-02-08
> **orchidfire said:**
> stephany@discworld:~$ virtualbox
The program 'virtualbox' is currently not installed.  You can install it by typing: sudo apt-get install virtualbox-ose
bash: virtualbox: command not found

The error is telling you what is wrong, virtualbox isn't installed, but you may find that VirtualBox is.

It is case sensitive.

---

### Post by orchidfire on 2009-02-08
...Wow, seriously, was that all I had to do?  *headdesk* Thanks so much&#8212;I tend to overlook the obvious.  :/

---

