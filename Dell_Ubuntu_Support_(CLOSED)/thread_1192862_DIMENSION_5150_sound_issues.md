---
title: "DIMENSION 5150 sound issues"
date: 2009-06-20
forum: Dell Ubuntu Support (CLOSED)
---

### Post by PiriForm on 2009-06-20
I have no sound when use ubuntu.

It's running on dual boot with windows XP (which has no trouble playing the sound.

I use a Dell Dimension 5150 desktop but I don't know what card is inside.

Any help/advice appreciated.

---

### Post by coffeeaddict22 on 2009-06-22
Hi,
There's a really thorough and up to date sound troubleshooter on the forums [here.]("http://ubuntuforums.org/showthread.php?t=205449")  Start with that; post back if you need more help.
If you open a terminal (Applications/Accessories/Terminal) and type in ```
lshw
```or ```
lspci
``` you'll find a bit of info about what's in your system.

---

### Post by PiriForm on 2009-06-23
Thanks, that page was very helpful, however...

I have the card Creative Labs Sound Blaster x-fi

On the page ([http://www.alsa-project.org/main/index.php/Matrix:Vendor-Creative_Labs](http://www.alsa-project.org/main/index.php/Matrix:Vendor-Creative_Labs)) it is listed as unstable.

I tried to follow the advice of the sound guide ([http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)) but I cannot understand what the make, configure and other instructions are or how i do them.

If anyone can help I'm almost there and I've tried to give as much information as possible, Thanks.

---

### Post by coffeeaddict22 on 2009-06-24
There's basically four ways of installing programs in Linux, particularly Ubuntu.
Firstly, many programs are kept in the repositories; I think about 15 000 separate packages.  These are accessible via three separate methods; Applications/ Add/Remove, the synaptic package manager in System/Administration/ (which has a more exhaustive list than in Apps/), or via the command line (open a terminal and type in man apt-get for more info).
Basically, the stuff in the repositories is screened, known to work in Ubuntu, and any programs that they rely on being installed to work get automatically downloaded as well.

The fourth option is building from source.  This is done in a terminal; essentially programs that are undergoing current modification are not packaged because by the time it's done there's another improvement come through.

The key commands to get a package from the source code to a binary package installed in the right directory are always the same.  First unzip it; double click on it and choose the extract option.  Then change into the directory that has your package in it; usually it's on your desktop, so you do that by opening a terminal and typing in ```
cd ~/Desktop/xxxx
``` where xxxx is the directory with the program in it.  Then type in ```
./configure
make
make install
```
configure runs a configure script that essentially modifies the installation to suit your hardware; make runs the compiler that installs creates the binary packages (ie converts the program from a human readable document to a machine-readable document), and make install is what actually installs it on your machine.
Few extra bits.  The ./ in front of configure is a quick and dirty way of saying the program is in the directory you're already in.  If ```
make
``` doesn't play, put it in front of that too.  When typing in a directory name in the terminal, anytime after the first 3 letters, hitting TAB will autocomplete if the name is unique at that point.  And (finally!) if you're cutting and pasting, Linux usually sets up the mouse so the middle button/wheel when clicked pastes any text that has just been highlighted.

Good luck, and post back if I've just confused you even more!

---

### Post by Aaron44126 on 2009-06-25
Note, before you try to compile anything, you should install the build-essential package.  You can either get it from the Synaptic package manager, or type this in the terminal:

sudo apt-get build-essential

This package contains the basics of what you need to compile programs.

---

