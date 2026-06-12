---
title: "Rhythmbox mp3 not working on Breezy GNOME"
date: 2005-12-03
forum: Desktop Environments
---

### Post by masingerz on 2005-12-03
Dear Ubuntu community:

I cant hear mp3's using rhythmbox: I followed the directions in the following link:

[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

I downloaded a lot of stuff and when I try the command "sudo apt-get install gstreamer0.8-plugins gstreamer0.8-plugins-multiverse gstreamer0.8-ffmpeg"


I get:

carlos@ubuntu:~$
carlos@ubuntu:~$ sudo apt-get install gstreamer0.8-plugins gstreamer0.8-plugins-multiverse gstreamer0.8-ffmpeg
Reading package lists... Done
Building dependency tree... Done
gstreamer0.8-plugins is already the newest version.
E: Couldn't find package gstreamer0.8-plugins-multiverse
carlos@ubuntu:~$
carlos@ubuntu:~$


The player shows that its playing an mp3, but I hear nothing, however the volume is set to its maximum...

PS: The mp3's are in an fat32 HDD that I had previously configured to mount on boot. The mp3 are seen in linux normally but no sound yet...

I'm also thinking of moving to Kubuntu

please advise

---

### Post by bursto22 on 2005-12-03
I have a similar problem when i try to play mp3's off of windows over my home netowrk connectionwith XMMS. if i understand properly i dont think the problem is in the player i think its in the fat filesystem conversion. i have to copy files first into unix for the to play properly. Try copying files first although its not really the best solution

---

### Post by doclivingston on 2005-12-03
It shouldn't matter what kind of partition the files are on. Do you get any error message when you try to play them?

---

### Post by masingerz on 2005-12-03
Dear Forum

I don't see any error messages, I'm willing to try other mp3 players: which one should I try?

regards Masingerz

---

### Post by irish rebel on 2005-12-03
Okay go to synaptic search for gstreamer and download gstreamer0.8 flac
also gstreamer0.8 lame  why not download gstreamer0.8 mad and scroll down a little and you will see all gstreamer plugins install these and you can then use rhythmbox .

---

### Post by flopsy on 2005-12-03
Are you sure it's a gstreamer problem?

Try sudo apt-get install mpg123 and play a file on the command line with mpg123 /path/to/file.mp3

If it is, make sure [universe and multiverse]("https://wiki.ubuntu.com/AddingRepositoriesHowto#head-cfe9af383ef6c914c44eb782c1dc1e0a76921049") are enabled and try apt-get again.

---

### Post by masingerz on 2005-12-03
Dear Forum

I already have all possible gstreamer0.8 files, I checked synaptic:

I also used the command:

carlos@ubuntu:~$ sudo apt-get install mpg123
Reading package lists... Done
Building dependency tree... Done
Note, selecting mpg321 instead of mpg123
The following NEW packages will be installed:
  mpg321
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 34.5kB of archives.
After unpacking 131kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe mpg321 0.2.10.3 [34.5kB]
Fetched 34.5kB in 1s (26.5kB/s)

Preconfiguring packages ...
Selecting previously deselected package mpg321.
(Reading database ... 62923 files and directories currently installed.)
Unpacking mpg321 (from .../mpg321_0.2.10.3_i386.deb) ...
Setting up mpg321 (0.2.10.3) ...

carlos@ubuntu:~$

When I double clik on an mp3 totem comes up and no audio. I closed that and then I tried rhythmbox and no audio either

I also tried this:
carlos@ubuntu:~$ dir
Desktop
carlos@ubuntu:~$
carlos@ubuntu:~$
carlos@ubuntu:~$
carlos@ubuntu:~$ cd Desktop
carlos@ubuntu:~/Desktop$ dir
boot-grub-menu-lst-old  song.mp3
carlos@ubuntu:~/Desktop$ mpg123 song.mp3
High Performance MPEG 1.0/2.0/2.5 Audio Player for Layer 1, 2, and 3.
Version 0.59q (2002/03/23). Written and copyrights by Joe Drew.
Uses code from various people. See 'README' for more!
THIS SOFTWARE COMES WITH ABSOLUTELY NO WARRANTY! USE AT YOUR OWN RISK!
Title  : Garden Grove                    Artist: Sublime
Album  : Sublime                         Year  : 1996
Comment:                                 Genre : Ska

Playing MPEG stream from song.mp3 ...
MPEG 1.0 layer III, 192 kbit/s, 44100 Hz stereo



[1:08] Decoding of song.mp3 finished.
carlos@ubuntu:~/Desktop$

---o---
I heard no audio with mpg123

Please advise

regards masingerz

---

### Post by flopsy on 2005-12-03
It should be mpg123, not mp**e**g123.

---

### Post by masingerz on 2005-12-03
Dear Forum:

Sorry for the typo while typing the command: I tried mpg123 and mpg321 and no audio persists.

regards masingerz

---

### Post by flopsy on 2005-12-03
If you open System/About Ubuntu, do you hear the plonk noise as it opens?

If you do, try apt-get remove mpg321 && apt-get install mpg123-esd. Then run mpg123 file.mp3 again. If that works, go to System/Preferences/Multimedia Systems Selector and select ESD for the sink and source.

If not, I suspect your sound card has not been correctly configured.

---

### Post by masingerz on 2005-12-03
i do not hear audio when going into system/about ubuntu

Here is the info for the embedded sound card:
    Intel High Definition Audio: Flexible 6-channel Intel® High Definition Audio Flexible: 6-channel
® ®     ®
    audio with jack sensing                        audio with jack sensing

---o---
      • Intel 915P Express Chipset
Audio
      • Intel® High Definition Audio
      • Realtek codec
---o---
Audio Subsystem
   Desktop Board D915PGN/D915PSY/D915PCY/D915PCM includes a flexible 6-channel audio
   subsystem based on a Realtek Semiconductor Corporation codec:
   The audio subsystem features:
   • Impedance sensing capability for jack re-tasking
   • S/N (signal-to-noise) ratio: > 90 dB
   • Power management support for ACPI 2.0 (driver dependent)
   • Intel 82801FB I/O Controller Hub (ICH6)
   • Realtek ALC860 audio codec
18
                                                                               Desktop Board Features
     •   Microphone input that supports:
             Microphone array
             Acoustic Echo (AEC)
             Beam Forming (BF)
             Noise Supression (NX) technology
     The subsystem includes the following connectors:
     • Front panel audio connector, including pins for:
             Line out
             Line in
     • Back panel audio connectors that are configurable through the drivers of the audio devices:
             Line in or Rear left/right out
             Line out or Front left/right out
             Mic in or Center LFE out
Related Links
     Go to the following link or pages for more information about:
     • Audio drivers and utilities [http://support.intel.com/support/motherboards/desktop/](http://support.intel.com/support/motherboards/desktop/)
     • Installing the front panel audio solution, page 45 in Chapter 2
     • The location of audio connectors, page Figure 22 on page 47

---

### Post by flopsy on 2005-12-03
Have a look at [http://linux.iuplog.com/default.asp?item=94639]("http://linux.iuplog.com/default.asp?item=94639")

---

### Post by Gray. on 2005-12-03
Try seeing if the settings in System > Preferences > Multimedia Systems Selector are working properly maybe?
If you want an all-in-one media player you can get [VLC]("http://www.videolan.org/vlc/"), using
sudo apt-get install vlc

---

### Post by masingerz on 2005-12-03
0000:00:1b.0 0403: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definiti on Audio Controller (rev 03)
0000:00:1c.0 PCI bridge: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Exp ress Port 1 (rev 03)
0000:00:1c.1 PCI bridge: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Exp ress Port 2 (rev 03)
0000:00:1c.2 PCI bridge: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Exp ress Port 3 (rev 03)
0000:00:1c.3 PCI bridge: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Exp ress Port 4 (rev 03)

card seems to be recognized
---o---
carlos@ubuntu:~$
carlos@ubuntu:~$ sudo totem
Password:

(totem:10809): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed

(totem:10809): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed
carlos@ubuntu:~$

and on the gui I see totem opened up I select a file to play and I see error message


Totem could not play 'file:///media/windows/Incoming/Bob Marley - Babylon By Bus/01. Positive Vibration.mp3'.
Failed to play: Could not open resource for writing.

---

### Post by masingerz on 2005-12-03
carlos@ubuntu:~$
carlos@ubuntu:~$ sudo apt-get install alsamixergui
Password:
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  libfltk1.1
The following NEW packages will be installed:
  alsamixergui libfltk1.1
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 370kB of archives.
After unpacking 958kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main libfltk1.1 1.1.6-6ubuntu1 [342kB]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe alsamixergui 0.9.0rc2-1-7ubuntu1 [28.3kB]
Fetched 370kB in 9s (39.6kB/s)

Preconfiguring packages ...
Selecting previously deselected package libfltk1.1.
(Reading database ... 62935 files and directories currently installed.)
Unpacking libfltk1.1 (from .../libfltk1.1_1.1.6-6ubuntu1_i386.deb) ...
Selecting previously deselected package alsamixergui.
Unpacking alsamixergui (from .../alsamixergui_0.9.0rc2-1-7ubuntu1_i386.deb) ...
Setting up libfltk1.1 (1.1.6-6ubuntu1) ...

Setting up alsamixergui (0.9.0rc2-1-7ubuntu1) ...

carlos@ubuntu:~$ dir alsamixergui
dir: alsamixergui: No such file or directory
carlos@ubuntu:~$ dir alsamixergui -s
dir: alsamixergui: No such file or directory
carlos@ubuntu:~$ dir alsamixergui /s
dir: alsamixergui: No such file or directory
dir: /s: No such file or directory
carlos@ubuntu:~$ cd
carlos@ubuntu:~$ dir
Desktop
carlos@ubuntu:~$ alsamixergui

in alsamixergui I locked all the locks and I reised the volume on all of them and I heard the system heartbeat, I player totem and it didnt work, I played rythmbox and it workd, I put the front mic in mute and the heartbeat went away ( i was hearing mp3 and heartbeat at the same time) now I hear mpo3 with a little bit of static.

i got this far thanks to starscalling a person on #ubuntuforums freenode irc

---

### Post by masingerz on 2005-12-04
So to work on the static in the audio while playing mp3's on rhythmbox:

I closed rythmbox (I had an mp3 playing with "snow like static" at the moment)

I went to system - preferences - multimedia systems selector: 

I pressed the test buttons, having to do a force quit in some other combinations that didn't work:

I used "ALSA" default synk, and "ESD" default source and it worked.

Also check applications - sound & video - volume control

Problem solved: credits to a person called navarone in #ubuntu irc.freenode.net

---

### Post by CKCK on 2005-12-04
Same problem, other user.
When I type:
sudo apt-get install mpg123
Reading package lists... Done
Building dependency tree... Done
Note, selecting mpg321 instead of mpg123
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  mpg321: Depends: libid3tag0 (>= 0.15.0b) but it is not installable
          Depends: libmad0 (>= 0.15.1b) but it is not installable
E: Broken packages

So ALL advices stops when ubuntu's package server didn't have those 
packages. Any ideas???

---

### Post by flopsy on 2005-12-04
Change your sources.list to that of [http://www.ubuntuforums.org/showthread.php?t=92672](http://www.ubuntuforums.org/showthread.php?t=92672) and try again. Don't forget to sudo apt-get update afterwards.

---

