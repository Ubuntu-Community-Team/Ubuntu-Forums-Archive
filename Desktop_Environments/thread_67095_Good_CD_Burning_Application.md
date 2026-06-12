---
title: "Good CD Burning Application?"
date: 2005-09-19
forum: Desktop Environments
---

### Post by erik-the-red on 2005-09-19
I tried using GNOMEbaker, but it didn't seem to quite like writing to my CDs.

What are some good CD Burning Applications, preferably with a GUI?

---

### Post by aysiu on 2005-09-19
K3B, and I believe it'll work in Gnome, too.

---

### Post by Zodiac on 2005-09-19
[QUOTE=aysiu]K3B, and I believe it'll work in Gnome, too.[/QUOTE]
 Indeed. K3B is wonderful... but be prepared to make a lot of coasters before you have it set up properly...

:(

---

### Post by Imek on 2005-09-19
AFAIK you can use Nautilus to write files to CDs easily. If you need more features, though, I'd definitely go with K3B, as it is a very slick piece of software. For the record, K3B wrote CDs perfectly for me from the offset.

---

### Post by jamesford on 2005-09-19
graveman rocks
btw the gnomebaker version in breezy is wastly better than the one in hoary, at least no my system

---

### Post by paulvandenberg on 2005-09-19
I'm using Breezy and have found no need for a dedicated CD burning app now. Nautilus will write files to CD/DVD. Now it will also copy CDs/DVDs (new for Gnome 2.12). Go to the Computer folder and right click on an optical drive icon and you will see an option to copy the disk. It will copy either data or audio disks. Breezy also has Serpentine, which works excellently for creating audio CDs from .ogg or .mp3 files. I always had a problem getting Graveman or Gnomebaker to work, but now I don't need it.

Paul

---

### Post by skoal on 2005-09-19
K3B alone converted me to KDE...

\\//_

---

### Post by oneybm on 2005-09-19
I use(d) K3B with my install of Hoary and Gnome.  It's very simple as long as you know a little bit about your hardware capabilities.  If you are unsure I would suggest starting with really concservative settings on write speeds and such and maybe working your way up. 

The only issue I had with K3b using an unknown DVD RW drive, still don't know everything about it, was it corrupting or causing issues with the .ICEAuthority file.  But that didn't seem to be an issue with my next install

Mi dos pesetas (My two cents),

---

### Post by erik-the-red on 2005-09-19
[QUOTE=oneybm]I use(d) K3B with my install of Hoary and Gnome.  It's very simple as long as you know a little bit about your hardware capabilities.  If you are unsure I would suggest starting with really concservative settings on write speeds and such and maybe working your way up. 

The only issue I had with K3b using an unknown DVD RW drive, still don't know everything about it, was it corrupting or causing issues with the .ICEAuthority file.  But that didn't seem to be an issue with my next install

Mi dos pesetas (My two cents),[/QUOTE]
 Is K3B on the Hoary CD?

---

### Post by cutOff on 2005-09-20
[QUOTE=jamesford]graveman rocks
btw the gnomebaker version in breezy is wastly better than the one in hoary, at least no my system[/QUOTE]
Graveman has a serious lack. It doesn't show past sessions in multisessions CD  [-X

---

### Post by Hairy_Palms on 2005-09-20
k3b isnt available on the cds but if u add the multiverse and universe repositorieys you can get it through synaptic

---

### Post by Perfect Storm on 2005-09-20
You could also take a shot at NeroLinux and see if it's something for you. Better than installing KDE libs to get K3b working ;)


.:=The AI Dude=:.

---

### Post by jworr on 2005-09-20
I use k3b in gnome, I did have one problem getting it to work properly.  I have to manually install cdrdao_1.1.9-3ubuntu2_i386.deb. After that the program worked perfectly.  It is great for burning audio cds, all you have to do is drag and drop. :)

---

### Post by skoal on 2005-09-20
[QUOTE=Artificial Intelligence]You could also take a shot at NeroLinux and see if it's something for you. Better than installing KDE libs to get K3b working [/QUOTE]
That's a good suggestion, especially for those already familiar with that product on Windows and migrating to Linux.  In the spirit of this thread, just a few personal observations about Nero on linux (since I've tried it on linux and own the original Windows CD):

1. It is a commercial product, so you must provide a serial number to use the linux version.  

2. They do have a free demo version available (even a .deb file), which has a time lapsed license agreement.  Download it and install it with: sudo dpkg -i <pkg>.  Personally, I'm quite leary of installing any 3rd party closed source apps (this way) which are not already in our trusted repositories.  But that's just me.

* 3. The Nero gui uses GTK-1.x.  Why?! I dunno, but be prepared for horrible fonts (unless you create your own ~.gtkrc).  Hopefully, they will include a QT/GTK-2.x interface sometime soon.  I welcome commercial support on linux, but Nero needs to update their GUI interface.

With that said, I stilll prefer K3B over Nero, and actually find it more intuitive an interface.  Difference in features between the two? I haven't noticed any...

\\//_

---

### Post by Mr Frosti on 2005-09-22
I want to thank Nero for making a CD burning app for Linux. I think that it is a step in the right direction. NeroLINUX seems to be a little rough around the edges though. I ran into these issues after several uses:

1) My CD ROM drive has to be in DMA mode for the program to recognize the device.

2) I have to manually select which device I want to burn with everytime I use the program.

3) When burning .iso files, the program will lockup and I have to wait about 10 minutes for the CD drive to stop clicking, or restart the machine. I cannot even force end the program. 

In the end I still support the company for their efforts and I will continue to use the program and give feedback to Nero, but K3B is probably a better solution for the average user.

---

### Post by bsussman on 2005-09-22
K3B is great - I do use it - but...

Webmin, which is an excellent management tool for a linux system, has a cd burner module.

Simple, very few options, hard to screw up.

I pretty much only burn ISOs so it works for me.

---

