---
title: "steam on ubuntu 64 bit"
date: 2024-04-02
forum: Gaming &amp; Leisure
---

### Post by Shishimaru on 2024-04-02
Hi there.

I am trying to install Steam on a Ubuntu 64 bit OS. I am using the app store, but when I launch Steam, it says that I am lacking the 32bit libraries. I am trying to install them, but really struggling. Any ideas?

---

### Post by fizzyfanta on 2024-04-03
Uninstall it and do not use it.

Get the officially supported DEB package directly from steam. [https://store.steampowered.com/](https://store.steampowered.com/)

Truth of the matter is the snap version which is what you are trying to use is a pain.

---

### Post by Shishimaru on 2024-04-08
> **fizzyfanta said:**
> Uninstall it and do not use it.

Get the officially supported DEB package directly from steam. [https://store.steampowered.com/](https://store.steampowered.com/)

Truth of the matter is the snap version which is what you are trying to use is a pain.


I tried that too, but can't find dependencies. I'll try to manually install them, but seems that some packages do not exist.

Steam shouldn't be so hard to install. 8 or 9 years have passed since I stopped and it's sad that the Linux desktop situation is still like so.

---

### Post by fizzyfanta on 2024-04-09
In a default install of Ubuntu 22.04 and 23.10 installing steam using the official DEB file works without issue.

---

### Post by hyperlinxe on 2024-04-11
you always have to add 32 bit library support in order to install steam(because steam is still a 32bit program)

the commands to install it are like this

sudo dpkg --add-architecture i386 
sudo apt update
sudo apt install steam

and if you get the steam .deb from it's website
then you would navigate to the folder it's in and use
sudo dpkg -i steam.deb, after using the commands,
to add 32bit library support, and updating the apt
database listed above...

---

### Post by fizzyfanta on 2024-04-13
@hyperlinxe 

I dont know if that was something in the past you had to do but right now if you install the official steam *.DEB after launching the steam app it will automatically check and install the 32 bit libs for you. No need to manually install it yourself.

---

### Post by currentshaft on 2024-05-07
pop

---

### Post by keshara283 on 2024-05-09
I just recently installed 24.04 on my Desktop. Tried the Snap Steam, and that just caused too many unnecessary headaches. I found using the .deb version I was getting weird micro-stutters which did not exist on my old Arch setup. Finally I tried the Flatpak Steam and now things are working great on my system.

---

### Post by nicolasdentremont on 2024-05-09
I also started with the snap version of Steam. I had just installed Ubuntu to see what was new in the Linux world and I was surprised to see Steam in the software store. Anyway I couldn't get Protontricks to work with the Snap version so I switched to the .deb from the Steam website. Most of the information that I've read online said to avoid the Snap version of Steam (and most other snaps too). So far it's been working fairly well.

---

### Post by maximge on 2024-05-21
Can you provide more details about your computer?

---

### Post by basednev on 2024-06-25
Your frustrations are valid. The guy who said deb packages install on a default installation is not fully correct. You need to install something like GDebi Package Installer to properly install a local deb package properly and check for dependencies.

---

### Post by TenPlus1 on 2024-06-28
To install a .deb package without additional tools go to terminal, cd into the directory containint the deb and type this:

sudo apt install ./mypackage.deb

---

### Post by dunky.funky on 2024-06-29
The package states- 
[FONT=monospace][COLOR=#000000] 
Because Steam requires 32-bit libraries, before installing this package it [/COLOR]
 will be necessary to run, as root: 
 . 
   dpkg --add-architecture i386; apt update

once that is done you can use - sudo apt install steam-launcher.

Ive just done this and steam works fine im on 24.04 and playing world of warcraft through steam.
[/FONT]

---

