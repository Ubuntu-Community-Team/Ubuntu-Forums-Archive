---
title: "No HDMI Audio in Mupen64plus Ubuntu 16.04"
date: 2019-02-23
forum: Emulators
---

### Post by jas513842 on 2019-02-23
I'm still kinda new to Linux and RetroPie. I had everything working great but had to do a complete reinstall. So I followed the directions posted here: [https://github.com/retropie/retropie-setup/wiki/Debian](https://github.com/retropie/retropie-setup/wiki/Debian) . I have done nothing extra. I'm trying to just get Super Mario 64 to run at the moment. The video runs perfect but there is no audio. I tried the steps listed here: [https://github.com/retropie/retropie-setup/wiki/Debian#no-audio-in-mupen64plus](https://github.com/retropie/retropie-setup/wiki/Debian#no-audio-in-mupen64plus) but all it did was make the audio cut in and out more often and when I would reboot there was no audio or audio devices listed until I ran the Mupen64plus emulator in RetroPie. All the other emulators and desktop audio work flawlessly. So I have completely reinstalled everything stated above and I am ready to start some troubleshooting.
Thank you 
John

Specs:
Asus mobo (on board audio disabled in Bios)
PNY Nvidia GTX 760 (HDMI Audio Source)
8gb G.Skill 2x4gb DDR3 1600
AMD Phenom x4 965 3.4ghz

---

### Post by pqwoerituytrueiwoq on 2019-02-23
I am unable to reproduce this using 18.04 on a GTX 1060 3GB
RetroArch: Frontend for libretro -- v1.4.1 -- d8855ca --
Compiler: GCC (6.3.0) 64-bitBuilt: Feb 26 2017

retroarch -L /usr/lib/x86_64-linux-gnu/libretro/mupen64plus_libretro.so --appendconfig ~/.config/retroarch/retroarch.n64.cfg /path/to/rom.z64

Mupen64Plus 2.0-rc2 (i compiled this from source)
**attached to post

sounds settings in retroarch
Audio Mute: Off
Audio Volume Level (dB): 0.0
Audio Sync: ON
Audio Latency (ms): 64

---

### Post by jas513842 on 2019-02-23
I appreciate you taking the time to help. Since I have Mupen64plus installed through RetroPie is there a special way I need to install what you compiled? Sorry for my ignorance I'm new to the workings of Linux.

I forgot to mention. The Libretro emulator works just fine. The other Mupen64plus emulators don't have audio with retropie.

I'm trying to use the mupen64plus-glide64 emulator so I can load Hi Res textures later when it's working again. I noticed an error message that show at the bottom of the screen when starting the emulator. it shows quickly but reads: /opt/retropie/supplementary/runcommand/runncommand.sh: line 961: read: read error: 0: Resource temporarily unavailable.

---

### Post by pqwoerituytrueiwoq on 2019-02-23
the package [libretro-mupen64plus](apt:libretro-mupen64plus) installs a file here: /usr/lib/x86_64-linux-gnu/libretro/mupen64plus_libretro.so
i replaced this file with the one i compiled after moving the original to /usr/lib/x86_64-linux-gnu/libretro/mupen64plus_libretro.so.bak
```
sudo mv /usr/lib/x86_64-linux-gnu/libretro/mupen64plus_libretro.so /usr/lib/x86_64-linux-gnu/libretro/mupen64plus_libretro.so.bak
sudo cp Downloads/mupen64plus_libretro.so /usr/lib/x86_64-linux-gnu/libretro/mupen64plus_libretro.so
```

My setup is based on retropi, i installed emulationstation from source (originally i used the deb and updated the files on my system, this was back when the original dev was still maintaining it, retropi has taken it up since then) and installed retroarch from the repos along with the libretro libraries and if a library gave me a issue i compiled it from source to see if it would help
with N64 emulation if you fix one thing you will break another so in the past i have tried several different versions
I wrote my own es_systems config file based on how retro pi worked

My setup is a bit hackish from before everything was easy to install, so outside of running mupen64 via retroarch i have never done that

---

### Post by jas513842 on 2019-02-23
[COLOR=#333333][FONT=&quot]The specific emulator I'm having trouble with is mupen64plus-glide64[/FONT][/COLOR]
[COLOR=#333333][FONT=&quot]the lr-mupen64plus works fine but looks awful and won't load high res textures. The mupen64plus-glide64 emulator worked great until I had to reinstall everything for other reasons. No system hardware has changed since I've started this.[/FONT][/COLOR]

---

### Post by pqwoerituytrueiwoq on 2019-02-23
for a while i was having some silly audio issues with hdmi i purged all nvidia drivers sudo apt-get purge nvidia-* and installed the newest drive i had part of a old driver version installed

---

### Post by jas513842 on 2019-02-23
It's a fresh install of Ubuntu 16.04 I have tried it with the newest proprietary drivers and with the xorg drivers. fresh installs both times since I was trying all different things to get it to work I kept breaking my installs so I would have to reinstall the OS. As of right now it fresh with the xorg drivers. Do you want me to install the nvidia drivers again?

---

### Post by pqwoerituytrueiwoq on 2019-02-23
Do not install the driver by running the installer you can get on the  nvidia website, i'd only suggest it to someone who wants the latest  driver (a good reason right now is free sync support) and is a advanced user (as in you knows how to use a command line  well enough to not require a desktop environment to install the driver)
the best way that will not result in you not having to touch a command  line after the install would be to use the graphics driver ppa
[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)
You can run the 2 commands on that page or add it via the "Software & Updates" GUI in the "Other Software" tab
> [FONT=courier new]deb [http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu](http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu) xenial main[/FONT]
*I have bionic cause i am on 18.04, for 16.04 you use xenial
Then install the driver using the "Additional Drivers" tab

If you ever have a problem with the driver, you can remove it with this command:
[FONT=courier new]sudo apt-get purge nvidia-*[/FONT]
you can do this from recovery mode if necessary
if you have some special settings that you made manually you will likely need to move/delete/rename your Xorg.conf file [FONT=courier new]/etc/X11/xorg.conf[/FONT], this file can be created from within nvidia-settings it does not exist by default
after removing it you can install it via the "Software & Updates" GUI in the "Additional Drivers" tab


** Free-sync support on nvidia only applies to the GTX 10 and 16 as well as the RTX series

---

### Post by jas513842 on 2019-02-23
ok I reinstalled Ubuntu Using the newest LTS 18.04 so we have the same OS. I tried what you suggested above but I don't get any open source drivers only the proprietary 390 drivers. Should I just check that and install that way? That's what I normally do.

---

### Post by pqwoerituytrueiwoq on 2019-02-23
if you do what i did on those screenshots you will be good
if you would prefer the terminal:
```
sudo add-apt-repository ppa:graphics-drivers/ppa -y && sudo apt-get update && sudo apt-get install nvidia-driver-415
```
I know the window says open source, but it is really the proprietary driver, not sure why it mislabels them

---

### Post by jas513842 on 2019-02-23
Ok I'll give it a shot in the morning. When I tried to get the drivers through the software center like in your second screen shot it asked to update something but then errored saying something about invalid keys or some security thing. I'll have to double-check. Also when I looked at the list of compatible video cards for the drivers the gtx 760 was only listed up to the 390 set of drivers could that be why only the 390 drivers are listed and nothing higher?

---

### Post by pqwoerituytrueiwoq on 2019-02-23
for some reason i thought you were on the GTX 900 series
anyway your card is supported on the 415 driver and i would expect the 418 driver to be available in the next week or two via the ppa
I forgot about the key part (adding the ppa via command line auto install the key, but the gui way does not)
run this command:
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 2388FF3BE10A76F638F80723FCAE110B1118213C && sudo apt-get update
```
that should make the key warning go away
If you want to add it via the GUI save this page to a file: [https://keyserver.ubuntu.com/pks/lookup?op=get&search=0xFCAE110B1118213C](https://keyserver.ubuntu.com/pks/lookup?op=get&search=0xFCAE110B1118213C)
then import the key (file you just saved) on the "Authentication" tab in "Software & Updates"
you may need to check for updates after doing that  via the GUI

---

### Post by jas513842 on 2019-02-23
Thanks I'll give it a shot in the morning and report back.

OK everything installed as it should. I was able to choose the newer drivers. I still have no sound coming from the mupen64plus-glide64 emulator within retropie.

---

### Post by pqwoerituytrueiwoq on 2019-02-24
Just to be sure it is no sound and not broken sound (out of pitch, scratchy, slowed, and/or spend up)
this only affects mupen64 right?

---

### Post by jas513842 on 2019-02-24
The lr-mupen64plus emulator works as it should. The mupen64plus-glide64 has great video but no sound, (occasionally it will make some noise but keeps cutting in and out, mostly no sound) I haven't bothered with the other emulators in the options since they never worked. These are pickable when pressing the "A" button on your controller when starting a N64 Rom.

all Other emulators and roms work and sound great. It's only when I try to run a N64 Rom using mupen64plus-glide64

---

### Post by pqwoerituytrueiwoq on 2019-02-24
have your tried the glidemk2 version?
currently installing retropi into a virtaulbox for a test, but i just noticed i need to change some bios settings

---

### Post by jas513842 on 2019-02-24
None of the mupen64plus emulators have audio except for the libretro lr-mupen64plus. I read somewhere that mupen64plus uses sdl audio and ubuntu is using pulse and they conflict causing audio issues. I tried the fix they suggested in the post but it broke my audio when I rebooted the pc and still didn't correct the issue anyway. mupen64plus-glide64 = glide64mk2 according to emulators.cfg

---

### Post by pqwoerituytrueiwoq on 2019-02-24
When i did the basic install in my virtaulbox it worked as expected and had sound and it was using the mk2 version in the ou of the box configuration
video was not working cause 3d acceleration was not enabled
i just followed the commands then dropped a rom in the n64 folder opened emulationstation and it was able to run it
I used the xfce variant of ubuntu - [https://xubuntu.org/release/18-04/](https://xubuntu.org/release/18-04/) not sure if that matters for this or not
```
$ md5sum Super\ Mario\ 64.z64 
20b854b239203baf6c961b850a4a51a2  Super Mario 64.z64
```
if you want to be sure your rom is not corrupt

---

### Post by jas513842 on 2019-02-24
it's not just that one rom they all have no audio. I'm at a loss. Well thank you for the help.

---

### Post by pqwoerituytrueiwoq on 2019-02-24
wait it is rom specific? i thought it was the emulator specific
check the MD5sum of your rom and compare it
Have you tired running it from [mupen64plus-qt](apt:mupen64plus-qt)
that worked fine on my system

---

### Post by jas513842 on 2019-02-24
It's the emulator. They work fine in lr- mupen64plus

---

### Post by jas513842 on 2019-02-28
from my readings it appears the sdl audio driver conflicts with the pulseaudio driver

---

