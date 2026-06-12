---
title: "Running Downloaded Programs"
date: 2009-05-28
forum: General Help
---

### Post by John C 1989 on 2009-05-28
I am a complete novice to Linux and Ubuntu. 

I put the operating system on to my machine last night and I am slowly but surely finding my way about. 

I downloaded Audacity to my desktop and when I went to run it I got archive manager and the message " an error has occured while loading the archive (null)". 

I was told to try and open the program with PeaZip. When PeaZip tries to open up audacity it takes me to the archive manager still with the message " an error has occured while loading the archive (null)".

Any help would be great.

---

### Post by JohnB-nbr on 2009-05-28
Welcome to the forum!

Why don't you download Audacity from the Synaptics package manager?

It would be easier for you...

---

### Post by _Purple_ on 2009-05-28
To install audacity type in terminal (application > accessories > terminal )
```
sudo apt-get install audacity
```

To install packages, it is better to use either terminal or the synaptic package manager (System > Administration > Synaptic package manager) or add/remove (Application > Add/ remove). You can check this link for details:
[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

For more details on audacity, check 
[https://help.ubuntu.com/community/Audacity](https://help.ubuntu.com/community/Audacity)

---

### Post by The Cog on 2009-05-28
One of the big differences to Windows is the way you normally install software. Instead of searching the net for downloads, you should always check the Ubuntu repositories first. Audacity is there, and the repositories installer will do all the setup needed too. 
Look in either Add/Remove... or in System->Administration->Synaptic Package Manager.

Edit:
or, if you know the package name, it is probably quicker to enter a command into the console as _Purple_ suggests. I always use the command line if I know the package name.

---

