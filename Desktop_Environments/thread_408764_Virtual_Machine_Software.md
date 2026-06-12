---
title: "Virtual Machine Software?"
date: 2007-04-13
forum: Desktop Environments
---

### Post by bradford72 on 2007-04-13
I would like to install virtual machine software on my system, but am having trouble figuring out what to use, and then how to install it.  A friend suggested that I check out VMWare, which I did, but am unable to install and get the software to work!  The deal is, I would like to be able to try other OS's without having to go through the trouble of rebooting my machine every time I want to check something out.  Any suggestions would be greatly appreciated!

---

### Post by hackerssidekick on 2007-04-13
Virtualbox is highly recommended ([http://www.virtualbox.org/)](http://www.virtualbox.org/)).

There is a forum post around here somewhere which gives detailed instructions on installing, although it should be straightforward.

Edit: Found the ubuntu wiki page on it: [https://help.ubuntu.com/community/VirtualBox](https://help.ubuntu.com/community/VirtualBox)

---

### Post by bradford72 on 2007-04-13
> **hackerssidekick said:**
> Virtualbox is highly recommended ([http://www.virtualbox.org/)]("http://www.virtualbox.org/%29").

There is a forum post around here somewhere which gives detailed instructions on installing, although it should be straightforward.

Edit: Found the ubuntu wiki page on it: [https://help.ubuntu.com/community/VirtualBox](https://help.ubuntu.com/community/VirtualBox)

Thanks a bunch!  I'll give it a shot!

---

### Post by bradford72 on 2007-04-13
Okay, I found the instructions, I have downloaded the tarball, installed the dependency packages, but the next instruction REALLY throws me...
> 
**Building VirtualBox[ ¶]("http://virtualbox.org/wiki/Linux%20build%20instructions#BuildingVirtualBox")**[LIST=1]
[*]Change to the root directory of the sources and execute the configure script: ./configure. If it finds everything it needs, it will create a file called 'AutoConfig.kmk' containing paths to the various tools on your system. Also, it will create an environment setup script called env.sh. This step only has to be done once (if something changes in your build tool setup, you might have to repeat it but keep in mind that both output files will be overwritten).[/LIST][LIST=1]
[*]Whenever you want to build VirtualBox, you have to open a shell and source the generated environment setup script 'env.sh', i.e. do source ./env.sh[/LIST][LIST=1]
[*]To build a release package, type kmk all. This produces the required binaries in out/linux.x86/release/bin/. (If you want to build a debug version, type kmk BUILD_TYPE=debug.) In case you have more than one CPU core, you could take advantage of our parallel build system by supplying -j3 (number of cores + 1) as an option to kmk.[/LIST]What does that mean...?  
ed. Okay, I got as far as doing ```
source ./env.sh 
kmk
```maybe I can figure out the rest too...
edit: Okay, I got it!...now, is there any way to build a launcher that I can stick on my panel?

---

### Post by hackerssidekick on 2007-04-15
Right-click on your panel, click add to panel.

Inside that Add to Panel window, click the Custom Application Launcher button, and then in that Create Launcher button, fill in the Name and Comment to whatever you like (freeform). As for the command, put in VirtualBox. To get the icon, click the no icon button, and then in that window scroll down until you see VBox.png. If the icon's not there, then you can browse to the source directory and find it in there somewhere.

Edit: Just read through the instructions from building from source, so if the binaries are still in the source directory, then you'll have to put the full path to the VirtualBox command in the command box above (there is a browse button :))

---

### Post by bradford72 on 2007-04-16
> **hackerssidekick said:**
> Right-click on your panel, click add to panel.

Inside that Add to Panel window, click the Custom Application Launcher button, and then in that Create Launcher button, fill in the Name and Comment to whatever you like (freeform). As for the command, put in VirtualBox. To get the icon, click the no icon button, and then in that window scroll down until you see VBox.png. If the icon's not there, then you can browse to the source directory and find it in there somewhere.

Edit: Just read through the instructions from building from source, so if the binaries are still in the source directory, then you'll have to put the full path to the VirtualBox command in the command box above (there is a browse button :))thanks a lot man! you rock! :guitar:  So, here's how it all went down:

I wound up downloading the binary files (I just don't know enough yet about all that compile and link stuff...or how to interpret error messages from make and make install...) , used archive manager to extract them to /tmp and installed them using ```
cd /tmp 
``` ```
dpkg -i *<packagename>*
``` (er...i already forgot the package name) then I had to add myself to the group "vboxusers (System->Administration->Users and Groups->Manage Groups->vboxusers-> *put a checkmark in the box next to my useraccount*  Then I tried the logout/login thing...didn't work for me (like I may have said before my box is a dinosaur...600MHz PIII 512MB RAM...and using EVERY CYCLE and address now!) so I went with rebooting.  VirtualBox came up as an option under Applications->System Tools...and well, if you gotta know the rest, just ask, I'd be glad to share anything I learn.

Took a screenshot (I'm about as proud of myself as a puppy with two...well this is supposed to be family friendly, so use alliteration and imagination...I hope you get a good laugh out of what you get >;-) ), which I would post, just to show people how it looks, but I don't know how...plus I really don't feel like uploading it to some web server and then turning on HTML....blah blah blah...can you tell I'm happy?!

Thanks again!

---

### Post by hackerssidekick on 2007-04-17
Hey no worries, glad to help! :D

For future reference, you can attach files to your posts, so if you have a screenshot or something just attach it to your post. Saves mucking about with uploads and stuff!

---

### Post by notatoad on 2007-04-17
what kind of performance do you get in a virtual machine on a p3/600?

my virtual machines are not that fast on an athlon 3500!

---

