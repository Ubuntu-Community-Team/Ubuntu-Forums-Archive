---
title: "How do I install JDoom?"
date: 2006-07-31
forum: Gaming &amp; Leisure
---

### Post by GStubbs43 on 2006-07-31
Hi all, I want to use Doom, so I'm gonna install jdoom. Do I just need to install:

deng-jdoom-rp-core; deng-jdoom-ep; deng-jdoom-rp-decorations;                   deng-jdoom-rp-effects; deng-jdoom-rp-hud; deng-jdoom-rp-items; deng-jdoom-rp-monsters; deng-jdoom-sycraftsdoommusic; deng-jdoom-ui deng-jdoom-tp 

after adding 
deb [http://eyagi.bpa.nu/~jamie/debian](http://eyagi.bpa.nu/~jamie/debian) sarge main contrib non-free
deb-src [http://eyagi.bpa.nu/~jamie/debian](http://eyagi.bpa.nu/~jamie/debian) sarge main contrib non-free
to sources.list?

or am I completely missing something? Is it free to use, because I don't have any money to spend on it. :)

Do i need #

deng; deng-iwad-doomu-installer; deng-iwad-doom2-installer 
and if so, can I do it after installing the above packages, since they are already being installed? I'm really confused. :( :confused: :confused: 

Thanks for any help!

---

### Post by Yagisan on 2006-07-31
First, have you read here ?
[http://eyagi.bpa.nu/eyagi/community-projects/yagisan-s-doomsday-for-debian-ubuntu/](http://eyagi.bpa.nu/eyagi/community-projects/yagisan-s-doomsday-for-debian-ubuntu/)

Next, Use the *Ubuntu* repos listed on that page.

You need deng (thats the engine) and one of deng-iwad-doomu-installer, deng-iwad-doom2-installer, deng-iwad-plutonia-installer or deng-iwad-tnt-installer. They will ask you for the location of the wad file in their name so they can install it to the correct location.

deng-jdoom-rp-core; deng-jdoom-ep; deng-jdoom-rp-decorations; deng-jdoom-rp-effects; deng-jdoom-rp-hud; deng-jdoom-rp-items; deng-jdoom-rp-monsters; deng-jdoom-sycraftsdoommusic; deng-jdoom-ui deng-jdoom-tp etc are resource packs. They make the game look pretty.

So, assuming you have one of doomu.wad, doom2.wad, tnt.wad or plutonia.wad you should be good to go. If not, it is a bit harder, and if needed I'll post instructions on that later.

---

### Post by GStubbs43 on 2006-07-31
I couldn't get any Doom-iwad-*-installer's to install... Is that because I need the WAD file? Because I don't. ;)

---

### Post by Yagisan on 2006-08-01
> **GStubbs43 said:**
> I couldn't get any Doom-iwad-*-installer's to install... Is that because I need the WAD file? Because I don't. ;)
That's absolutley right - you need the wad files. No they are not free, no I can not supply them.

There is a freedoom project, but freedoom does not work correctly with Doomsday at the moment. What you can do is download freedoom, rename it to doom2.wad and install it with the deng-iwad-doom2-installer, but because freedoom does not yet work correctly you need to run a pwad, such as deng-jdoom-pwad-mm with it.

---

