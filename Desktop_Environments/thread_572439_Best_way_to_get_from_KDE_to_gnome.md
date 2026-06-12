---
title: "Best way to get from KDE to gnome?"
date: 2007-10-10
forum: Desktop Environments
---

### Post by bliffle on 2007-10-10
My #1 computer is running a nice stable, good-looking, reliable and useful ubuntu gnome system that I installed off the 7.04 liveCD about 4-6 months ago. It's a honey.

My #2 computer is an adventure. I installed KDE 7.04 on a dualboot with an XP system as an experiment and for a look at a different distro. I even added Xfce as a startup option. Then I decided that maybe I'll give this to my 9 yr. old granddaughter in Paris and go on to continue my experiments on computer #3.

So I figured it would ease any remote maintenance problems by making #2 the same as #1, so I better go to gnome on #2. So I tried psychocats technique, which consists of one huge CLI command, which ran and ran and ran and finally dumped me into an Xfce session. So I logged out and found the 'options'  panel in the logon with 'Xfce' and 'KDE' as options but no  'gnome'.

So I logged into KDE, which turned out to be a very primitive version with a double-high white bar at the bottom. No gnome anywhere , that I can see.

I spent a couple of fun hours messing around with that whitebar, adding applications and applets, moving them around, testing, etc. But it's not really what I want. And I couldn't see any way to get back to the place I started from on this particular adventure.

So i figure the easiest thing to do is to simply preserve my "/home" directory on a thumb drive and re-install 7.04 with gnome. I think I can do that straightaway, without doing anything to the old linux install, but I'm not sure. Should I clean off that partition first? 

Should I maybe clone the ubuntu partition I have on #1 to #2 to assure that it has all the same updates and additions? Will that work, will the system adjust to the slightly different hardware on #2?

---

### Post by rsambuca on 2007-10-10
You can just add the ubuntu desktop and then remove the kubuntu and xfce desktops.

---

### Post by bliffle on 2007-10-10
So I did that:

sudo aptitude install ubuntu-desktop

I'll see how it works.

---

### Post by maybeway36 on 2007-10-10
You could get an Alternate CD and do the OEM installation. It works really well; once you set it up, just run sudo oem-config-prepare and give it to your granddaughter.

---

### Post by bliffle on 2007-10-11
OK, I got it back to a gnome system. Now I've just gotta get some stuff like Amarok, gaim, etc., up and running. then she'll have plenty of space on that 80gb HDD.

I installed KDE and Xfce because I thought they'd be faster, but it looks to me like gnome is at least as fast, maybe faster.

---

### Post by rsambuca on 2007-10-11
One thing you might want to note is that if you use programs using different libraries, you can really slow down your system if you have low amounts of memory.  For example, since you are using Gnome now, you might want to avoid programs that require the kde set of libraries, since running them will require your computer to load both the gnome and kde libraries, which uses much more system resources.
Amarok is a KDE app.

---

### Post by bliffle on 2007-10-11
Good point. I have only 256mb on that computer and it won't take any more, AFIK.

Well, amarok seems to be a really good player, but on the other hand I don't play very much audio. I'm sure I'm using some other KDE apps, how can I finger them all so I can get rid of them?

---

### Post by rsambuca on 2007-10-11
Use Synaptic to search for kdelibs, or perhaps kdebase, if you select it for removal, it should tell you all of the kde apps that will also have to be removed.

---

