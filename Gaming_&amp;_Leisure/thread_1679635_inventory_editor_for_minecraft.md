---
title: "inventory editor for minecraft?"
date: 2011-02-01
forum: Gaming &amp; Leisure
---

### Post by blackdahliatits on 2011-02-01
new to ubuntu, just got minecraft going and would like to mess around with an inventory editor. i found a working one for my other computer (macbook w/mac OSx) but cant seem to find one for linux.
can i run one designed for windows on ubuntu?
i tried using mono to run invedit on my mac but it kept crashing, not sure if im going to have the same luck on ubuntu and wine was a pain in the *** so i stopped messing with it. (doing it wrong?)
if i can run a windows based editor with mono, how?
walk me through ladies...baby steps please (not retarded, just new-ish to terminal and using commands)

---

### Post by directhex on 2011-02-01
INVedit seems fine here?

---

### Post by I8NY on 2011-02-01
I use InvGrid,(there is a deb package) it is similar to INVedit.  I couldn't get INVedit working in wine and idk what mono is but InvGrid works fine.

---

### Post by blackdahliatits on 2011-02-01
> **I8NY said:**
> I use InvGrid,(there is a deb package) it is similar to INVedit.  I couldn't get INVedit working in wine and idk what mono is but InvGrid works fine.

mono is a terminal based program that allows you to run windows programs in other OS's.

---

### Post by directhex on 2011-02-02
> **I8NY said:**
> I use InvGrid,(there is a deb package) it is similar to INVedit.  I couldn't get INVedit working in wine and idk what mono is but InvGrid works fine.

Mono is an open-source .NET implementation. INVedit is a .NET app, so it runs with Mono on Linux.

---

### Post by lordjj on 2011-06-28
InvGrid is available for Linux. [http://www.minecraftdl.com/invgrid-inventory-editor-1-6-6/]("http://www.minecraftdl.com/invgrid-inventory-editor-1-6-6/")
However the .DEB is for Ubuntu 10.10 or newer.
I had to download the source code and install some packages to compile it for my Ubuntu 10.04:
Install:
libboost1.42-dev
zlib1g-dev
liblua5.1-0-dev
libqt4-dev

Then:
cd InvGrid
sudo cmake .
sudo make
sudo make install

---

### Post by Skrack on 2011-07-04
> **lordjj said:**
> InvGrid is available for Linux. [http://www.minecraftdl.com/invgrid-inventory-editor-1-6-6/](http://www.minecraftdl.com/invgrid-inventory-editor-1-6-6/)
However the .DEB is for Ubuntu 10.10 or newer.
I had to download the source code and install some packages to compile it for my Ubuntu 10.04:
Install:
libboost1.42-dev
zlib1g-dev
liblua5.1-0-dev
libqt4-dev

Then:
cd InvGrid
sudo cmake .
sudo make
sudo make install

Please explain how you did that. I'm noob and i want to try that but i don't know how. 

Thank you

---

### Post by Perfect Storm on 2011-07-04
> **Skrack said:**
> Please explain how you did that. I'm noob and i want to try that but i don't know how. 

Thank you

The dependencies you can get through Synaptic Package Manager

The last part you need to open the terminal.

---

### Post by Skrack on 2011-07-05
> **Artificial Intelligence said:**
> The dependencies you can get through Synaptic Package Manager

The last part you need to open the terminal.

Thanks, now, the most is clear. I only need to know which archives i have to download in the source code web "https://github.com/jbendig/InvGrid" 
If somebody can answer that all would be clear and i will be able to install this program.

Thanks.

Edit: I tried to downoad all the files on synaptic and the file "libboost1.42-dev" i couldn't find it. If someone can help I would be so pleased.

Thanks again.

---

### Post by Perfect Storm on 2011-07-06
libboost1.42-dev is not available for 10.4 only libboost 1.40.

---

### Post by Skrack on 2011-07-06
> **Artificial Intelligence said:**
> libboost1.42-dev is not available for 10.4 only libboost 1.40.

but ... mmm will it work?

---

### Post by Perfect Storm on 2011-07-06
> **Skrack said:**
> but ... mmm will it work?

I don't know, I don't have the game - give it a try and see.

---

### Post by Skrack on 2011-07-07
> **lordjj said:**
> InvGrid is available for Linux. [http://www.minecraftdl.com/invgrid-inventory-editor-1-6-6/](http://www.minecraftdl.com/invgrid-inventory-editor-1-6-6/)
However the .DEB is for Ubuntu 10.10 or newer.
I had to download the source code and install some packages to compile it for my Ubuntu 10.04:
Install:
libboost1.42-dev
zlib1g-dev
liblua5.1-0-dev
libqt4-dev

Then:
cd InvGrid
sudo cmake .
sudo make
sudo make install
  
Can somebody help me?
I can't compile it and I dont know how to make it work
Thanks ...

---

### Post by ExileAmongYou on 2011-07-09
I don't know about INVgrid, but I just helped my little brother brother set up [TooManyItems]("http://www.minecraftforum.net/topic/140684-172-toomanyitems-in-game-invedit-july-1/") a couple weeks ago.

It should be fairly easy to set up (no compiling!) using the instructions on the site. The only thing you have to watch is that you don't copy the mod files into the minecraft.jar file you originally downloaded-you put them in the minecraft.jar file that's in the hidden .minecraft folder in your home folder (at ~/.minecraft/bin).

---

### Post by Skrack on 2011-07-10
> **ExileAmongYou said:**
> I don't know about INVgrid, but I just helped my little brother brother set up [TooManyItems]("http://www.minecraftforum.net/topic/140684-172-toomanyitems-in-game-invedit-july-1/") a couple weeks ago.

It should be fairly easy to set up (no compiling!) using the instructions on the site. The only thing you have to watch is that you don't copy the mod files into the minecraft.jar file you originally downloaded-you put them in the minecraft.jar file that's in the hidden .minecraft folder in your home folder (at ~/.minecraft/bin).

WOW ! Thanks, it's easy to install and use, and works well ! 
Problem solved.

Thank you everybody! \\:D/

---

### Post by lordjj on 2011-08-26
In case its still relevant:
InvGrid for Ubuntu 10.10 (32-bit) or later: [here]("http://starbytesoftware.com/downloads/InvGrid-0.9-ubuntu1010-32bit.deb")
InvGrid for Ubuntu 10.10 (64-bit) or later: [here]("http://starbytesoftware.com/downloads/InvGrid-0.9-ubuntu1010-64bit.deb")
for Ubuntu 10.04 or later, pm me, or try this link: [here]("http://uiu.me/M0lSgOMGBDLKbEWCCb4u5FWKT3NrzMOBMuGT.deb")

---

