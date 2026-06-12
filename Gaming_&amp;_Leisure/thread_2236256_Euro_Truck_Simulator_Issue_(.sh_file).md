---
title: "Euro Truck Simulator Issue (.sh file)"
date: 2014-07-25
forum: Gaming &amp; Leisure
---

### Post by HarryPannell on 2014-07-25
Hi, so I recently obtained Euro Truck Simulator 2 from a Humble bundle, however I am having some issues.

Whenever I drag the .sh file into Terminal, I recieve the error: "Error opening terminal: xterm"...

I've looked around and can't find anything. Hopefully someone can help me fix this.

---

### Post by Dennis N on 2014-07-25
I would suggest instead to enter at the terminal command prompt the full path (starting from / ) to the file that starts the program.

---

### Post by HarryPannell on 2014-07-25
> **Dennis N said:**
> I would suggest instead to enter at the terminal command prompt the full path (starting from / ) to the file that starts the program.

It applies the whole path when I drag it in anyway. If it didn't work surely it would say could not locate the specified file or w.e.

---

### Post by Peter_Solver on 2014-07-25
Are you using Ubuntu 14.04? Is xterm installed?  Try this:

sudo mkdir -p /usr/share/terminfo/l
cd /usr/share/terminfo/l
sudo ln -s /lib/terminfo/l/linux linux
export TERM="linux"

Then start the game and see if it works.

---

### Post by HarryPannell on 2014-07-26
> **Peter_Solver said:**
> Are you using Ubuntu 14.04? Is xterm installed?  Try this:

sudo mkdir -p /usr/share/terminfo/l
cd /usr/share/terminfo/l
sudo ln -s /lib/terminfo/l/linux linux
export TERM="linux"

Then start the game and see if it works.


Yes, I am running 14.04 Ubuntu version. I can find xterm in the start menu, so I assume it's installed...

I've run everything you suggested, however I get the folllowing error (I've included the whole code to help).

[SIZE=1]harry@harry-ThinkCentre-Edge71:/usr/share/terminfo/l$ export TERM="linux"

Verifying archive integrity... All good.
Uncompressing Installer for Euro Truck Simulator 2..........
Uncompressing sub archiveWarning: No binaries for "x86_64" found, trying to default to x86...
................................................
Collecting info for this system...
Operating system: linux
CPU Arch: x86
Nixstaller version 0.5.1, Copyright (C) 2006 - 2009 of Rick Helmus
Nixstaller comes with ABSOLUTELY NO WARRANTY.
Nixstaller is free software, and you are welcome to redistribute it
under certain conditions; see the about section for details.
Error opening terminal: linux.[/SIZE]


I then opened a new terminal, and tried it:
[I]
[SIZE=1]harry@harry-ThinkCentre-Edge71:~$ '/home/harry/Desktop/EuroTruckSimulator2.sh' 
Verifying archive integrity... All good.
Uncompressing Installer for Euro Truck Simulator 2..........
Uncompressing sub archiveWarning: No binaries for "x86_64" found, trying to default to x86...
................................................
Collecting info for this system...
Operating system: linux
CPU Arch: x86
Nixstaller version 0.5.1, Copyright (C) 2006 - 2009 of Rick Helmus
Nixstaller comes with ABSOLUTELY NO WARRANTY.
Nixstaller is free software, and you are welcome to redistribute it
under certain conditions; see the about section for details.
Error opening terminal: xterm.[/SIZE][/I]

---

### Post by merlin5 on 2014-10-09
Hi there,

I had the same problem and solved the way described...

are you sure you entered it like this:

[ATTACH=CONFIG]257077[/ATTACH]

yes, I get an error because i allready created the link (sry for german OS)

then start the installation (e.g.: [sudo] sh /home/merlin/Downloads/EuroTruckSimulator2.sh)

should work:

[ATTACH=CONFIG]257076[/ATTACH]

Greetings
Merlin :)

---

