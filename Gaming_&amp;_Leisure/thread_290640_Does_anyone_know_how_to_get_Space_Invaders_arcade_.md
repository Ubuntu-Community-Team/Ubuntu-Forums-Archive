---
title: "Does anyone know how to get Space Invaders arcade game for Ubuntu"
date: 2006-11-01
forum: Gaming &amp; Leisure
---

### Post by javierfh on 2006-11-01
Hello,

i am looking for the Space Invaders game for Ubuntu.
I have found that xinv3d but its not exactly what im looking for.
And then ninvaders it is close to what i want, but i would like to have the classic one from the arcade machines that you could find in bars or places where they have them.

Any help would be very nice.

Javi

---

### Post by lazyart on 2006-11-01
You probably want to start with MAME/XMAME/GXMAME, then hunt around for the Space Invaders ROM.

MAME (Multiple Arcade Machine Emulator) is faithful to the original games, as it doesnt try to rewrite them, just reproduce the system they ran under.

---

### Post by megamania on 2006-11-01
> **javierfh said:**
> i am looking for the Space Invaders game for Ubuntu.
I have found that xinv3d but its not exactly what im looking for.
And then ninvaders it is close to what i want, but i would like to have the classic one from the arcade machines that you could find in bars or places where they have them.
I've never tried it, but there should be a MAME version for linux - then you can easily find the original Space Invaders rom.

---

### Post by lazyart on 2006-11-01
I didnt mention it, but gxMAME is available in Synaptic Package Manager.  It should grab MAME along with it, which is the underlying engine.

That being said, I love playing Millipede. :)

---

### Post by javierfh on 2006-11-01
> **lazyart said:**
> I didnt mention it, but gxMAME is available in Synaptic Package Manager.  It should grab MAME along with it, which is the underlying engine.

That being said, I love playing Millipede. :)

Thanks a lot...
im going to try to get Mame right away.

So do you know where i can find the Space Invaders ROM ? and once i get it,if i can...where to put it?

Javi

---

### Post by javierfh on 2006-11-01
Ok i found the rom image from here 

[http://www.romnation.net/srv/roms/mame/s.html](http://www.romnation.net/srv/roms/mame/s.html)

So where should i put that one or how can i invoke it?

Javi

---

### Post by lazyart on 2006-11-01
where ever you put the rom (I put mine in ~/roms) you'll have to go into gxMAME where it is.  Run gxMAME (Alt-F2, then type gxmame) and go to Options > Directories and set (add) the location of your rom to it.

More info here: [http://gxmame.sourceforge.net](http://gxmame.sourceforge.net)

I've used it in Windows and even have it on a USB stick so I can play my games whereever I can find a machine.  With this and the Zork trilogy I have all the old-school games I could ever wish for. :)

---

### Post by marx2k on 2006-11-02
So...the last update to gxMAME was in Dec of 2003? That's awful.  Is there a better package to install for Ubuntu? What version is the Ubuntu Synaptic version install?

---

### Post by javierfh on 2006-11-02
> **marx2k said:**
> So...the last update to gxMAME was in Dec of 2003? That's awful.  Is there a better package to install for Ubuntu? What version is the Ubuntu Synaptic version install?

Hi i finnally installed kxmame, and well somehow it worked.
That should be more up to date.

Let me know if you have problems.. its not straight forward in my oppinion, but at least i managed to have the space invaders working.

Javi

---

### Post by marx2k on 2006-11-02
> **javierfh said:**
> Hi i finnally installed kxmame, and well somehow it worked.
That should be more up to date.

Let me know if you have problems.. its not straight forward in my oppinion, but at least i managed to have the space invaders working.

Javi

kxMAME is for KDE, right?

So what was the method for installation in Gnome?

---

### Post by javierfh on 2006-11-02
> **marx2k said:**
> kxMAME is for KDE, right?

So what was the method for installation in Gnome?

I suppose that it is for KDE but i have Gnome and no problem at all..
just go to synaptics and search for it.. and select it for instalation.
It works just fine under Gnome.

Javi

---

### Post by Jasper Houtman on 2006-11-02
There is an easier way. You can download the flash version from miniclip.com and play it in Firefox. I have a nice collection of flash games on my HD, which I bookmarked (use Ctrl-D) in firefox. 

Some sites allow you to download the flashgames, on others you can use the VideoDownloader extension for Firefox to grab them of the site.

---

### Post by megamania on 2006-11-03
> **Jasper Houtman said:**
> Some sites allow you to download the flashgames, on others you can use the VideoDownloader extension for Firefox to grab them of the site.

I remember that when I used Windows I used to simply browse the Internet Explorer folders, because all the flash-games were stored there. I think it could easily be the same with Firefox.

Anyway, with MAME you play the real thing...  ;-)

---

### Post by wererabbit on 2006-11-03
here's a link:
[http://www.ababasoft.com/flash_games/space_invaders.html](http://www.ababasoft.com/flash_games/space_invaders.html)
-w-

---

### Post by evil_core on 2008-09-20
Easier ? I dont like flash, and he wanted original. I can recommend downloading some rom pack by torrent or rapidshare. My 800 games for SNES takes 1,2GB(NES or MAME games usually take much less space), they are unpacked, but most emulators(like ZSNES) supports also zipped archives. And its later damny easy to use, you open emulator like ZSNES, configures inputs(like joypads/keyboard, resolution, filters, etc. but only ONCE for all the games !), and later you open ypu choose game list, or recently played games, and simply runs it by one click.

And 

[QUOTE=marx2k]kxMAME is for KDE, right?

So what was the method for installation in Gnome? [/QUOTE]
WTF ? Do you know what is X and how it works ? You install any application in system(by system package manager), not in a Desktop Environment. It displays using X trough some libraries. And game designed for KDE uses dome subset of KDE libraries, which is installed using dependencies(rpm and deb has it), and doesnt requires all KDE to be installed(only small subset of libraries), and runs whatever Desktop Environment, do you use, but because of different widgets it will not look as others apps that uses GTK(KDE) apps uses Qt, GNOME uses GTK for menu, buttons, etc drawing). Why do you not wonders how GNOME or KDE works with compiz, it replaces they default window managers, and please learn what is X Server, Window Manager, GTK and Qt.

---

### Post by Glucklich on 2008-09-20
I've got the ROM for Gens if you want. It's the Megadrive version, just like the original. Send me a PM if your interest, I'll post on RS.

---

