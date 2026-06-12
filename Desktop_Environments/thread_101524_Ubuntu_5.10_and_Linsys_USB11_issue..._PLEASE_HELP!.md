---
title: "Ubuntu 5.10 and Linsys USB11 issue... PLEASE HELP!"
date: 2005-12-10
forum: Desktop Environments
---

### Post by Plastic9mm on 2005-12-10
First off, I admit it... I AM A COMPLETE AND TOTAL NEWBIE TO LINUX.

I'm used to the Mac OS, and havenever really used a Linux distro ever... I need a little help.
t it 
I've seen the Linsys USB11 tutorial on the support site, but I just cannot get it to work.

The first issue comes up when trying to run the command "sudo apt-get install build-essential linux-headers-uname -r" The terminal reports back "E: Command line option "r" [from -r] is not known."

But if I run it without the " -r" it runs, but "E: Couldn't find package linux-headers-uname"

I skipped over it and moved along

I'm on the latest release of Breazy, just downloaded it from the sight (not sure if it TRULY is the latest*), freshly installed on a Sony Vaio something or other (older PIII based model, 800mhz) Laptop. I can get as far as opening the Tar file.

I can get it to open the .tar file I need, when I attempt the "make" command, the  terminal reports back that "bash: make: command not found"

I can get no further.

Please anyone... help!

---

### Post by Susana on 2005-12-10
[QUOTE=Plastic9mm]
The first issue comes up when trying to run the command "sudo apt-get install build-essential linux-headers-uname -r" The terminal reports back "E: Command line option "r" [from -r] is not known."

But if I run it without the " -r" it runs, but "E: Couldn't find package linux-headers-uname"

I skipped over it and moved along
[/QUOTE]

sudo apt-get install build-essential linux-headers-`uname -r`

or in a terminal run uname -r and copy the numbers to the other command


[QUOTE=Plastic9mm]
I can get it to open the .tar file I need, when I attempt the "make" command, the  terminal reports back that "bash: make: command not found"

I can get no further.

Please anyone... help![/QUOTE]

this is probably because you didn't install build essential (previous command)

---

