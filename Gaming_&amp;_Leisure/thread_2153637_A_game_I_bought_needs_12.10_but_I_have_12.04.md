---
title: "A game I bought needs 12.10 but I have 12.04"
date: 2013-06-11
forum: Gaming &amp; Leisure
---

### Post by EliteNeophyte on 2013-06-11
Okay so I recently bought Anna Extended Edition on Steam, the game had looked promising and I was looking forward to it, you can find screenshots of what it's supposed to look like here [http://store.steampowered.com/app/217690/](http://store.steampowered.com/app/217690/) , well when I got into the house I thought that considering all the light sources the place seemed too dark, but wrote it off as being for atmosphere, when I saw the screenshots I was suprised, it would seem that on my install most of the shader engine does not work, I got to looking at the minimum requirements and sure enough it requires the install above mine

Well I'm just wondering if there is a way I can run the game without having to install 12.10, as well as all of the redownloading and duplication of effort that comes along with that, is it possible to get the 12.10 drivers on a 12.04 system, or am I doomed to redownload close to fifty gigabytes

Quick info I'm running an Intell Pentium B940 integrated chipset, codename sandy bridge

I just performed a package update as specified here [https://wiki.ubuntu.com/Valve#Intel_Graphics](https://wiki.ubuntu.com/Valve#Intel_Graphics)

I'm running Kubuntu 12.04 I doubt that matters but mentioning anyway

and here are the screenshots from my copy, for the curious among you [http://steamcommunity.com/profiles/76561198084455947/screenshots/?appid=217690&sort=newestfirst&browsefilter=myfiles&view=imagewall](http://steamcommunity.com/profiles/76561198084455947/screenshots/?appid=217690&sort=newestfirst&browsefilter=myfiles&view=imagewall), the red door is from a weird glitch where things will suddenly start to flash around the room either red yellow or both, the game is unplayable in this state and I really want to enjoy it, so if anyone knows a solution to my troubles that wouldn't require redownloading the contents of my harddrive to a new partition I'm all ears

---

### Post by Cheesehead on 2013-06-11
> **EliteNeophyte said:**
> ...or am I doomed to redownload close to fifty gigabytes

Most complete downloads run about 700-900MB.
What do you have installed that adds 49GB of additional download?

Have you identified what the game's real (non-Ubuntu, if you compiled) dependencies are?

---

### Post by mastablasta on 2013-06-12
> **EliteNeophyte said:**
> I'm running Kubuntu 12.04 I doubt that matters but mentioning anyway



there is a setting in KDE that will automaticly turn off all special desktop effects when running fullscreen applications. it might be worth to turn it on. 
also you can use a PPA to upgrade intel driver to latest (they are opensource).

---

### Post by cRaZyBisCuiT on 2013-06-12
Indeed, the shipped graphics drivers with kernel 3.8 which is shipped with Ubuntu 13.04 offers much better Intel drivers. Performance is increased as well as supported opengl flags. Maybe you'd give it a try? Nervetheless, Intel graphics have never been the best things to play games. Allthough the igpu got better a lot, the driver (for gaming) ist still not the best.

---

### Post by EliteNeophyte on 2013-06-13
> [COLOR=#000000]Most complete downloads run about 700-900MB.[/COLOR]
[COLOR=#000000]What do you have installed that adds 49GB of additional download?[/COLOR]

[COLOR=#000000]Have you identified what the game's real (non-Ubuntu, if you compiled) dependencies are?[/COLOR]
Well Team Fortress 2 is over 12 gigs on it's own, not to mention other data that gets passed through the machine through downloads, VirtualBoxes, ect. tell you the truth it's probably closer to thirty but that's still a lot of binary

---

### Post by EliteNeophyte on 2013-06-13
Hm, well it looks like I'm upgrading then, I had heard concerns that 13.04 was unstable but it had only been out for a week at the time, that's why I went for 12, but if they've moved the LTS to 13 I guess those concerns are alleviated, as soon as I can figure out how to transfer my Home folder, and anything that my steamapps are dependent on I'll reinstall

---

### Post by cody1233 on 2013-06-13
Make a seperate partition for your home folder and make steam save everything on there.  I haven't tried to see if the games will still work after an update, but at least it'll save your documents and stuff...

---

### Post by EliteNeophyte on 2013-06-13
I've done a lot of digging since starting the thread and from what I can tell it IS an issue with the drivers however no matter how many times I update it won't make a difference, the ones I need simply aren't available on 12.04, I'm going to be doing an upgrade as soon as the torrent finishes, does anyone know how I can save my Home folder?

Addendum 1: this post is now pointless I'm just going to upgrade from within the environment

---

### Post by cody1233 on 2013-06-13
DL a LiveCD of Puppy Linux or something like it and make two seperate partitions: one for your home folder, the other for the OS then move everything into it.  When you're installing whatever version you're moving to on the advanced partition menu you'll see the OS and Home partitions.  Install to the OS partition and you can format it, but on the other one, double click it and select the mount point /home and do not let it get formatted.

---

### Post by mastablasta on 2013-06-14
13.04 is not LTS

> **EliteNeophyte said:**
> I've done a lot of digging since starting the thread and from what I can tell it IS an issue with the drivers however no matter how many times I update it won't make a difference, the ones I need simply aren't available on 12.04, I'm going to be doing an upgrade as soon as the torrent finishes, does anyone know how I can save my Home folder?


opensource drivers can be upgraded. you need to first add the PPA and then find them in Muon and install the new version of them.

otherwise you click drag and drop the home folder to copy the files :-D

---

