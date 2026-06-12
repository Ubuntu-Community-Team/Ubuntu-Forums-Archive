---
title: "Downloading Snes9x?"
date: 2008-01-13
forum: Gaming &amp; Leisure
---

### Post by Tyler5794 on 2008-01-13
Okay, so I downloaded Snes9x off of [this]("http://www.lysator.liu.se/snes9x/") site.
I clicked on "Linux x86 binaries" and when it downloaded, clicked the file there (snes9x-1.43-linus-x86.tar.gz) and clicked on the folder there (/snes9x-1.43/) and I don't really get the readme.txt file, so... I'm a complete idiot with this kind of stuff. I need help getting Snes9x open.

---

### Post by TwoWordz on 2008-01-13
Its on the mirrors, just apt-get zsnes. 

TW

---

### Post by acoustibop on 2008-01-13
Put the file in your home directory, Tyler5794, open a terminal and enter
```
tar xvpf snes9x-1.43-linux-x86.tar.gz
```
That's it.  To start the emulator, open a terminal again and enter
```
cd snes9x-1.43
./snes9x
```
Best to paste and copy my entries: your typing of the package name is a little off... Note that this is a command line version of the emulator.  You'll need a frontend as well if you want a GUI.

BTW most people seem to prefer ZSNES to SNES9x - any particular reason for preferring SNES9X?

Edit@TwoWordz: the repository versions seem to be older ones, though, and you appear to be confusing ZSNES with SNES9x.

---

### Post by Tyler5794 on 2008-01-13
Um, what do you mean, put the file in my home directory?
I'm such an idiot today.

I've ver used ZSNES before, snes9x was the first one I tried.

---

### Post by DoktorSeven on 2008-01-13
If you want a Super NES emulator, ZSNES is the one you want.  Snes9x used to be a good one but ZSNES has surpassed it, in my view, plus configuring Snes9x seems to be very hit or miss in Linux in my experience.

Search for how to enable (and update after you do) the Universe repositories, then use Synaptic to search for and install ZSNES (or do **sudo apt-get install zsnes**).

---

### Post by Tyler5794 on 2008-01-13
Er. I just started using Linux. I'm a noob in this stuff. What are Universe repositories and Synaptic?

---

### Post by DoktorSeven on 2008-01-13
[What are Repositories?](https://help.ubuntu.com/community/Repositories/Ubuntu)

Synaptic: a way to add and remove packages from your system.  System->Administration->Synaptic Package Manager

---

### Post by Tyler5794 on 2008-01-13
Um, the Synaptic Package Manager isn't under Administration, and neither is Software Properties (for adding repositories).

Sorry for the slow responses.

---

### Post by DoktorSeven on 2008-01-13
On mine it is; though Software Properties has changed the name to Software Sources.  This is on plain (Gnome) Ubuntu by the way; if you're using Kubuntu things will be a bit different; just do some searches online to get an idea of what to use instead.

If you can't find Synaptic in plain Ubuntu, maybe it's not installed (though I am pretty sure it was by default when I installed it).  Find a terminal (on mine, it's Applications->Accessories->Terminal, though if yours differs, you may have to look for the equivalent), and type **sudo apt-get install synaptic** (it will ask for your user password).

It's best if you read up on some of these basic administrative things to really get going in Ubuntu.  You will have to do things like this again to install and run programs, and the more you understand, the easier it will be in the future.  It's not difficult, but it does take a little bit of time to familiarize yourself with it.

Good luck.

---

### Post by acoustibop on 2008-01-14
Ubuntu documentation is [here]("https://help.ubuntu.com/"), Tyler5794.

---

### Post by 2manydrugsago on 2008-01-27
I used add remove programs searching for all available applications to get znes and snes9x . Znes doesn't work with some older grafics cards so If you have an old system like me then snes9x is better.   
here are the default controls. the rest is pretty easy to figure out if ya have have problems playing games on it then [www.snes9x.com](www.snes9x.com)  has a forums and a FAQ and is rather helpful.

Z,B,W = Top Right button
A,V,Q= Top Left
SME = Xbutton
XR = right button
DT = A button
CY = B button
enetr = start
space bar = select
Shift + F!-9 save states
F1-9 load states

---

