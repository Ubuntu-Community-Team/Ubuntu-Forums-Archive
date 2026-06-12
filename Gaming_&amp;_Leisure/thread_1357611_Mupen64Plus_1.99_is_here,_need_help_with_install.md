---
title: "Mupen64Plus 1.99 is here, need help with install"
date: 2009-12-17
forum: Gaming &amp; Leisure
---

### Post by nominal on 2009-12-17
Well the new version of mupen64plus is here...and i was hoping it'd play nicer with my graphics card (Wasn't really working out...)

the only problem is, it's not in the ubuntu software center (1.5 is, 1.99 isn't). I manually downloaded the package, but I'm not sure how to install it.

Can anyone help?

---

### Post by murderslastcrow on 2009-12-17
As far as I know, they don't package it as a deb you install, but as a binary. I'm sure they have instructions inside on how to install it to your system, but I typically just run the program straight from the folder due to laziness.

To be honest, it's almost easier to compile from source than to install to your local directories for me. Anyway, I'm fairly certain there's an install script/instructions in the main folder of the package.

---

### Post by Grishka on 2009-12-17
if you got the binary package, there's an installation script included. just run
```
 sudo ./install.sh
```

---

### Post by manco on 2010-01-08
> **Grishka said:**
> if you got the binary package, there's an installation script included. just run
```
 sudo ./install.sh
```
Thanks; I wish the README was that simple :)

---

### Post by segalion on 2010-01-11
Thanks a lot! I will try when lastest glide64 is released...

---

### Post by galaga4991 on 2010-01-29
I'm a complete linux newbie so this may sound stupid, but how do I actually run Mupen64Plus once it's installed?

---

### Post by SteamInc on 2010-10-16
Yea anybody mind helping me with this. No idea how to run the program.

---

### Post by mister_playboy on 2010-10-16
Open a terminal and type ```
mupen64plus
```.  You can also create launcher for the program in your menu in Gnome or KDE.

---

### Post by SteamInc on 2010-10-17
Apprently I found out why it wasn't working. For some reason it does not install the files in the necessary folders (usr/local/bin Also I do not have a bin folder). Maybe because 10.10 has just been released and it is having compatibility problems. 

Anybody know how to fix this?

---

### Post by sendblink23 on 2010-10-17
I tried to use the latest one from their website... but it doesn't start up or anything for me.. no clue why

so instead I'm using the 1.5v from the USC and its working fine over here on my 10.10 x64 - at least for the games I've tested

---

### Post by mister_playboy on 2010-10-17
> **sendblink23 said:**
> I tried to use the latest one from their website... but it doesn't start up or anything for me.. no clue why

The current version does not come with a GUI and can only be run from the command line.

---

### Post by sendblink23 on 2010-10-17
> **mister_playboy said:**
> The current version does not come with a GUI and can only be run from the command line.

I did tried it through command line

I'm going to re download it again... hopefully it works this time


This is what I did..,  extracted it to my own directory inside downloads ... then did  sudo ./install.sh
```
sendblink23@sendblink23-MS-7577:~/Downloads/Emulators/mupen64plus-bundle-linux64-1.99.3$ sudo ./install.sh
[sudo] password for sendblink23: 
Installing Mupen64Plus Binary Bundle to /usr/local
install: creating directory `/usr/local/share/mupen64plus'
install: creating directory `/usr/local/share/mupen64plus/doc'
install: omitting directory `doc/emuwiki-api-doc'

```

afterwards... I tried as you have mentioned on a previous post on this thread - opening terminal & typing in: mupen64plus

This happens:
```
The program 'mupen64plus' is currently not installed.  You can install it by typing:
sudo apt-get install mupen64plus

```

Am I missing something after running the sudo ./install.sh

---

### Post by sendblink23 on 2010-10-17
any ideas *mister_playboy ?

---

### Post by Quadunit404 on 2010-10-18
Just build it from source. Well, that's what I did anyway.

Since I had trouble launching it from the terminal I also downloaded CuteMupen to launch it and its games. After setting everything up I decided to test out my newly built Mupen64 using some good ol' Super Mario 64, as you can see in the attached screenshot. (Don't feel like playing it again just to get that same screenshot but with just the Mupen64Plus window so that'll do.)

Also, I'm surprised at how well Super Mario 64 controls using an *Xbox 360 controller.* lol, irony...

---

### Post by sendblink23 on 2010-10-19
I haven't tried building from source... but oh well gave up on that version, and went back to 1.5 which works perfectly fine for me

For fun here a screen shot running 3 emulators at the same time, together all at 60fps: Mupen64Plus 1.5v(Mario64), PJ64*wine(Zelda OOT) & Dolphin Emulator(NSMBW)
[[IMG]http://img243.imageshack.us/img243/1372/screenshotys.th.jpg[/IMG]](http://img243.imageshack.us/img243/1372/screenshotys.jpg)

I use a PS2 controller to play each.. its fun almost all controllers work with these emulators perfectly

---

### Post by Quadunit404 on 2010-10-19
Don't you feel that's a bit overkill? I mean, two Nintendo 64 emulators and a Wii emulator running at the same time?

---

### Post by sendblink23 on 2010-10-20
> **Quadunit404 said:**
> Don't you feel that's a bit overkill? I mean, two Nintendo 64 emulators and a Wii emulator running at the same time?

Did you even read my system hardware? Quadcore 4Ghz, 8gb ddr3 1333Mhz & CrossfireX 5770's ?

Its not overkill for me... but ofcourse reality I will never be playing 3 games at the same time... but I can run them extremely fine at full speed.

This was simply a screenshot for fun

---

### Post by Quadunit404 on 2010-10-20
> **sendblink23 said:**
> Did you even read my system hardware? Quadcore 4Ghz, 8gb ddr3 1333Mhz & CrossfireX 5770's ?

Its not overkill for me... but ofcourse reality I will never be playing 3 games at the same time... but I can run them extremely fine at full speed.

This was simply a screenshot for fun

Well of course I did read your specs. I still find three emulators at the same time a bit overkill though :wink:

---

### Post by emoguitarist06 on 2010-11-02
> **sendblink23 said:**
> I haven't tried building from source... but oh well gave up on that version, and went back to 1.5 which works perfectly fine for me

For fun here a screen shot running 3 emulators at the same time, together all at 60fps: Mupen64Plus 1.5v(Mario64), PJ64*wine(Zelda OOT) & Dolphin Emulator(NSMBW)
[[IMG]http://img243.imageshack.us/img243/1372/screenshotys.th.jpg[/IMG]](http://img243.imageshack.us/img243/1372/screenshotys.jpg)

I use a PS2 controller to play each.. its fun almost all controllers work with these emulators perfectly

Can you help me with getting mine to run?
I'm running Maverick Amd64 and installed Mupen 1.5 via USC
but look at my terminal results
```
phillipguy@phillipguy-laptop:~$ mupen64plus Pokemon\ Snap.zip 
 __  __                         __   _  _   ____  _             
|  \/  |_   _ _ __   ___ _ __  / /_ | || | |  _ \| |_   _ ___ 
| |\/| | | | | '_ \ / _ \ '_ \| '_ \| || |_| |_) | | | | / __|  
| |  | | |_| | |_) |  __/ | | | (_) |__   _|  __/| | |_| \__ \  
|_|  |_|\__,_| .__/ \___|_| |_|\___/   |_| |_|   |_|\__,_|___/  
             |_|         http://code.google.com/p/mupen64plus/  
Version 1.5

Config Dir:  /home/phillipguy/.config/mupen64plus/
Data Dir:  /home/phillipguy/.local/share/mupen64plus/
Cache Dir:  /home/phillipguy/.cache/mupen64plus/
Install Dir: /usr/share/mupen64plus/
Plugin Dir:  /usr/lib/mupen64plus/

Rescanning rom cache.
Rom cache up to date. 0 ROMs.
Compression: Zip
Imagetype: .z64 (native)
Rom size: 16777216 bytes (or 16 Mb or 128 Megabits)
MD5: FC3C9329B7CDD67CF7650ABF63B9A580
80 37 12 40
ClockRate = f
Version: 1449
CRC: ca12b547 71fa4ee4
Name: POKEMON SNAP
Manufacturer: Nintendo
Cartridge_ID: 4650
Country: USA
PC = 80100400
EEPROM type: 0
init timer!
[RiceVideo] SSE processing enabled.

```
**And it just hangs there. If I run the GUI it just turns dark grey and hangs there.**

I thought maybe it was because I was running a .zip but even when I try .v64 or .z64 it still has the problem. I of course tried a different rom I retrieved from a different site.

Any ideas?

---

### Post by emoguitarist06 on 2010-11-04
**UPDATE**

Okay I found Mupen64Plus to work if I do not have my PS3 Controller connected! Very weird. I'm using a program developed by a fellow Ubunter

See here:[http://ubuntuforums.org/showthread.php?p=10069468](http://ubuntuforums.org/showthread.php?p=10069468)
And I posted my problem in greater detail here:[http://ubuntuforums.org/showthread.php?p=10069468#post10069468](http://ubuntuforums.org/showthread.php?p=10069468#post10069468)

If anyone is willing else is using QtSixA by FalkTX and has resolved this problem please help me!

**UPDATE**
So it works via USB but not via Bluetooth

**[COLOR="Red"]FINAL UPDATE[/COLOR]**
It works both USB & Bluetooth. For bluetooth you must disable the rumbe function in QtSixA

---

