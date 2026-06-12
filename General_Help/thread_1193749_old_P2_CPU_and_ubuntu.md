---
title: "old P2 CPU and ubuntu"
date: 2009-06-21
forum: General Help
---

### Post by leftkidney on 2009-06-21
OK so I have a old Compaq 1800T it has a P2 384MHz CPU with 64MB of ram and a 5GB HD - it has Windows XP PRO now but the HD is to small to update to SP2 and any programs so Linux it is

can this computer even run ubuntu properly or do I have to get a different distro for really old computers like this one - I know I have to use the alternative install method because of the ram but should I waste my time of throw this computer out

---

### Post by Bachstelze on 2009-06-21
A standard Desktop installation of Ubuntu would be a bit too much for that hardware. What I'd do if I were you is starting with a command-line system, and installing XFCE on top of it.

---

### Post by dawynn on 2009-06-21
I haven't really worked with installing a recent Linux on a computer that old.  Xubuntu is a thought (although I prefer Linux Mint, XFCE version).  The Mint distributions try to add in the usual desired codecs as a default (think mp3's, dvd's, and other media-based codecs)  

Crunchbang is also worth investigating.  CB is based on Ubuntu, and very lightweight as it uses Openbox as its frontend.  My main gripe with CB is that it does not auto-update menus like Gnome, XFCE, and KDE do.  So, if you install or remove any software, expect to update your own menus.

Opengeu is a cross between Ubuntu and E17 (formerly Enlightenment).  Not quite as rough as a straight E17 install, but stil in beta mode.  As I recall, Opengeu at least auto-updates menus.  I kinda liked where this distribution was going, but it was still a bit rough around the edges.

All of these would keep your feet at least somewhat in the Ubuntu and Ubuntu-derivative world.

---

### Post by louieb on 2009-06-21
lol got a p2-400mHz whitebox myself. I spent a little on eBay and and maxed it out w/384MB ram and a 30GB harddrive. (came with 4.7GB hard drive, 64MB ram and win 98 )

It has puppy and crunchbang  linux  also has XP home.  

Of the 3 OS on it now Puppy is by far the fastest to boot and load programs.

---

### Post by egalvan on 2009-06-21
> **leftkidney said:**
> ...I have a Compaq 1800T.. P2 384MHz, **64MB ram and 5GB HD**
 - WinXP PRO now but HD is too small to update to SP2 and any programs so Linux it is

can this computer even run ubuntu properly do I have to get a different distro for ..old computers ..
- have to use the alternative install method because of the ram but **should I waste my time or throw this computer out**

The RAM and HD space are tight.
That said, used 10-20Gb laptop drives are fairly cheap,
 but being used, may have a limited life.
RAM may or may not be expandable.
It may be proprietary (yes, it's that old, and Compaq played the "Buy it From Us, or No One" game back in the day)

You will have a tough time finding a graphical Linux distro to run in a reasonable fashion.

Even TinyCore, which is a 10Meg download, states
[B]Minimal hardware requirements include an i486DX processor (486 with math processor) and 32MB of RAM.
 A Pentium 2 or better processor with [COLOR="Red"]128 MB of RAM is recommended.[/COLOR][/B]

Command-line is always an option, and you have lots of RAM for that.

Anyway, look at it as a fun project, or a learning project :)

And rather than throw it out, and help clog the land fills,
I'll pay postage to South Texas :)

EGalvan

---

### Post by leftkidney on 2009-06-21
yea I can upgrade the ram there is an open slot but its got to cost a lot and I have spinrite so I can test a used drive if it isnt to much to buy I dont care if it is bad

the only real use for this computer would be for occasional internet viewing and video playack - but in WIN-XP it wont even play youtube videos or dvd's maybe because it is paging out 100% of the time

---

### Post by DGortze380 on 2009-06-21
dsl (damn small linux) is always my choice on old machines... although, I've never run it on anything older than a P3 with 128mb.

I would give it a shot. It's going to be better than what you've got now, that's for sure.

---

### Post by aglc2005 on 2009-06-21
I have an old Dell with a P2 in it. I have 256mb in it and installed Xubuntu and it works just fine. It is a little slow for video, well it doesn't do video well at all. But playing music is fine and I have yet to put it on the interwebs, but networking stuff worked just fine as well. I'd give xubuntu a try first.

---

### Post by egalvan on 2009-06-21
> **leftkidney said:**
> **yea I can upgrade the ram there is an open slot but its got to cost a lot **

OK, with this in mind, I can recommend you take the machine to an old "Mom&Pop"-type computer repair store, 
and see if they don't have any ancient RAM they were going to throw out :)
Another try is a computer club, or the local college's computer department.
All of these have given me results. Cheap/free, usually.


> and I have spinrite so I can test a used drive if it isnt to much to buy I dont care if it is bad

Yeah, spinrite can help, I used to use it. 

> the only real use for this computer would be for [B]occasional internet viewing and video playack -
 [/B]but in WIN-XP it wont even play youtube videos or dvd's maybe because **it is paging out 100% of the time**

Yes, the same uses I was thinking for.
I donate these to indigent students for Internet and word processing.

And as for XP paging out a lot... well, with only 64Megs, I'm surprised it doesn't *crash* every ten minutes. *

Try Puppy, if you get some more RAM. 128M is OK for it, 256M almost ideal.
Puppy is a 100Meg download for the LiveCD.

I find Puppy easier to use than DSL (Damm Small Liunx).

I haven't done much besides play a little with TinyCore.

(*
that said, stripping XP down to bare bones will make it much more stable.
But I have a life-time license for 98Lite/XP-Lite, so I have an advantage in this.
My smallest XP-Pro/Lite install was WELL under 2Gig, with page file, if I remember.
My smallest 98/lite was around 100Meg.
)

---

### Post by egalvan on 2009-06-22
I want to add that downloading an "alternate Install" CD from Ubuntu is a good start.
This uses much less ram than the LiveCD.
It allows you to install a basic system, then build it up.

Another option is the "Server Install", which is a command-line only version.
Again, allowing you to build it up.

See Herman's Linux Zone for some good info on this

[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)

---

### Post by leftkidney on 2009-06-22
yea I will look in some old hole in the wall computer stores to find old ram

I dont really need this computer I just dont like to waste anything and the battery still works for about 2 hours

I will try DSL but first I will focus on trying to get ram seeing as that is the major problem so far and the HD later - I can use USB storage for other things

---

### Post by ugm6hr on 2009-06-22
> **DGortze380 said:**
> dsl (damn small linux) is always my choice on old machines... although, I've never run it on anything older than a P3 with 128mb.

Works well on a P2 with 48MB RAM (that was DSL3.3); no reason it shouldn't work just fine with 64MB.

Puppy Linux 2.14 (and presumably the latest 4.x) will work on it with a swap partition, but be a little slow.  If you do upgrade to 128MB, I would strongly recommend Puppy (or one of its derivatives).

Other option is DeliLinux, which I never got to work properly myself.

---

### Post by Arup on 2009-06-22
I don't see any reason Xubuntu wouldn't run on it.

---

### Post by StOlEnDeStInY on 2009-06-22
I have my inhibitions regarding Xubuntu working on it. But how about Debian Lenny or an Ubuntu with minimal programs added and using Rox-filer and Icewm in place of Nautilus and Gnome?
I ask this here coz am having similar problems wit my office computer.

---

### Post by leftkidney on 2009-06-24
well I have downloaded the DSL and puppydog and the netbook edition of the *ubuntu stuff and I will try them out and see what happens

I think that the *ubuntu's wont work that well since I have already installed them on an older p3 733MHz with 128 ram and it is slow as hell but I dont use that computer anymore so it dont matter

---

