---
title: "Doom 3 Installation"
date: 2008-02-12
forum: Gaming &amp; Leisure
---

### Post by henz103 on 2008-02-12
I successfully installed Doom 3 using this installation steps.

> Installation :

Mount the image via loopback device

**mount -t iso9660 /path/to/doom3-CD1.iso /mnt/cdrom/ -o loop**

Install the linux client

**sh /mnt/cdrom/doom3-linux-1.1.1286.x86.run**

Now, install the game files

[B]cd /usr/local/games/doom3/base
tar -xjvf /mnt/cdrom/files-1.tar.bz2
umount /mnt/cdrom[/B]

Do the same for the remaining images

[B]mount -t iso9660 /path/to/doom3-CD2.iso /mnt/cdrom/ -o loop
tar -xjvf /mnt/cdrom/files-2.tar.bz2
umount /mnt/cdrom[/B]

[B]mount -t iso9660 /path/to/doom3-CD3.iso /mnt/cdrom/ -o loop
tar -xjvf /mnt/cdrom/files-3.tar.bz2
umount /mnt/cdrom[/B]

Now you can execute:

**doom3**

I'm new to linux so my question is, will there be any GUI user friendly game installer in the future (comparing installing Doom3 on Linux & installing Doom 3 on Windows) or it is the destiny of Linux that you'll have to use this type of installation?

Sincerely,
Hany

---

### Post by FrozenFox on 2008-02-12
One game requiring the use of the terminal does not account for all of Linux installation! :)

Most linux stuff, particularly on debian-based systems like ubuntu, can be insalled graphically through Synaptic (linux programs/games), Wine-Doors (Windows programs/games), PlayOnLinux (Windows programs/games), or through .DEB files that are installable via double clicking them just like windows EXE files. I imagine wine-doors will add in native doom3 at some point, they did it for quake4. For example, in Sabayon, I'm 90% sure you can install doom3 from a graphical interface (kuroo or whatever) by just putting in your cd, loading up kuroo, clicking to install d3. For ubuntu, we'll just have to wait for wine-doors or someone to make it easier, although it's really not very difficult to begin with.

---

### Post by grossaffe on 2008-02-13
yeah, i've noticed that linux is much more beginner-freindly than its reputation.

---

### Post by RRosset on 2008-03-08
BUMP

I know this is a waste of time, I just wanna tell everyone who's trying to install doom 3, please, dont double click on the icon. I waster more than a day executing a bloody file. And dunno why i said... ok, let's give a try to the console... i searched this thread, execute the sh sarasasarasa.run and now i plan to run doom 3...  cya guys

---

### Post by EnergySamus on 2008-03-08
I just installed the Doom 3 Demo... Much easier than I'd thought it would be!!!:lolflag:

---

