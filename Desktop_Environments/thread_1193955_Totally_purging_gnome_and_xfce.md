---
title: "Totally purging gnome and xfce"
date: 2009-06-22
forum: Desktop Environments
---

### Post by Faceless79 on 2009-06-22
Ive searched the forum and havent really found a solid answer. Ive decided on using lxde on my xubuntu distro and want to know how to purge pretty much any remaining trace of gnome and xfce. Also how would i edit it to get rid of these options from the sessions menu? Ill be happy to post any additional info yall might need. Thanks everyone

---

### Post by T.J. on 2009-06-22
> **Faceless79 said:**
> Ive searched the forum and havent really found a solid answer. Ive decided on using lxde on my xubuntu distro and want to know how to purge pretty much any remaining trace of gnome and xfce. Also how would i edit it to get rid of these options from the sessions menu? Ill be happy to post any additional info yall might need. Thanks everyone

You won't be able to remove every last little bit because of package dependencies.  The only way to get around that is to compile the source code yourself, and that defeats the purpose of using a prebuilt distribution in the first place.

You can remove most of it by 

sudo aptitude purge libgnome2-0 xfce4*
sudo aptitude keep-all

The first command will remove the core bits of Gnome and XFCE.  The second will keep the package system from autoremoving things that it shouldn't because Gnome isn't installed anymore.  Ubuntu is designed for Gnome, so a lot of things that depend on Gnome cannot be entirely exorcised.

Personally, I don't care for Gnome either.  It has some really annoying low level bugs that are incompatible with scripts.  They stripped out every option that was "too complicated" making Gnome akin to Windows - pretty but not very usable IMHO.

It doesn't even have a decent menu editor. Alacarte is a bad joke.

---

### Post by XubuRoxMySox on 2009-06-22
I too use LXDE exclusively, because it is so very lightweight and fast! My CPU runs quiet and cool, applications load instantly and run quick.

**I'm very interested to hear if this works for you, since I want to try the same thing on another machine.** I did it the other way around, starting with minimal and installing only what I wished. But I'm still a noob - **how do I know what I need?** I needed lots of help, but I finally have a super-fast Debian/LXDE mix that flies at transwarp speed even on an old hand-me-down dinosaur.

And the sweetest part was when my family saw it and used it to get on the web and stuff, *they didn't even know they weren't using Windows.* They were like, "No way!" When I told them they were using Linux. LXDE was so easy and familiar-looking enough for them to use it effortlessly (and compliment me for resurrecting that old ancient computer and making it run "better than when it was new").

I couldn't have pulled that off without LXDE's beauty, simplicity, and very small footprint. Now I'm an LXDE fan!

Please post if it works, and how else you might purge the unneeded stuff from a standard *buntu installation.

Thanks,
Robin

---

### Post by Faceless79 on 2009-06-22
Thankyou for the responses i had a feeling it wasnt possible or advised to remove all of it but if i can get it down to a bare minimum thatll be great too, ill try it now and post back in a few

---

### Post by Faceless79 on 2009-06-22
Ok i tried but didnt go thru with it, when i ran the script it gave me nothing but dependancy errors, i think ill just keep doing what ive been doing (using synaptic to pick apart un-wanted un-used gnome and xfce components) or i may switch to crunch bang

---

### Post by XubuRoxMySox on 2009-06-22
> **Faceless79 said:**
> ... or i may switch to crunch bang

I did and it was sweet - for awhile. But gradually some big problems began to creep in. The worst was **forced shutdown.** LXDE's logout stopped working and I had use a terminal command to turn off the computer:

```
shutdown -h now
```

Sound was muted by default on bootup and I had to keep manually un-muting it.

It looks like LXDE doesn't play nice with Crunchbang (in spite of the fact that a few LXDE components are used in Crunchbang by default). But keep an eye on [U-Lite]("http://u-lite.org") and the Lubuntu project. 

In the meantime have a look also at [MoonOS]("http://moonos.co.cc") which has an LXDE version based on Ubuntu Intrepid. Access to Ubuntu repositories, Synaptic, all the good stuff.

All the best,
Robin

---

### Post by Faceless79 on 2009-06-22
Hey thanks for the info but i have a problem looking for linux distros and thats my wifi card (requires the prism54 driver) and i dnt thinj alot of distros have it. Plus how am i supossed to fix wifi without wifi? Anyhow thanks again

---

### Post by XubuRoxMySox on 2009-06-22
> **Faceless79 said:**
>  Plus how am i supossed to fix wifi without wifi? Anyhow thanks again

**MoonOS **has several pre-installed codecs that may allow your wifi to work right out of the box. PCLinuxOS does that, as do a few others. PCLinuxOS is not an LXDE-based distro, but it will run on low-resource computers and is one of those "best recommended for newbies" distros, too. Ubuntu-based Linux Mint has pre-installed codecs as well, but I cannot recommend it for reasons that are probably inappropriate to post here.

It sounds like MoonOS, LXDE edition may fit your bill. But you would have to download it from another internet-connected computer and burn a live CD, then carry it to your wifi machine to install it.

-Robin

---

### Post by 37fleetwood on 2009-06-22
just a thought, have you tried Puppy Linux? it runs live so you can see if you like it without changing your current setup. it even can save sessions to the cd if you burn it multi-session to begin with. you can install to usb or hard drive, you can even install it inside a Windows partition and boot it from usb or floppy. if you want more info let me know.
here is a cap of my Puppy with LXDE and Compiz:
[IMG]http://i14.photobucket.com/albums/a315/hotshot66/puppy/lxdepup.jpg[/IMG]

---

### Post by Faceless79 on 2009-06-22
I have tried puppy, dsl, pclinuxos and a few others but dont like them non of them recognized my wifi card.

After playing around i found a combo that works, im now running gnome desktop with openbox as my wm and even on my little pIII laptop it runs 9x faster than the default xubuntu install, especially when combined with opera instead of firefox

---

### Post by RandyNose on 2009-06-22
> **37fleetwood said:**
> just a thought, have you tried Puppy Linux? it runs live so you can see if you like it without changing your current setup. it even can save sessions to the cd if you burn it multi-session to begin with. you can install to usb or hard drive, you can even install it inside a Windows partition and boot it from usb or floppy. if you want more info let me know.
here is a cap of my Puppy with LXDE and Compiz:
/lxdepup.jpg[/IMG]


I like Puppy, and if I could get it to look and run like that, I might put it on my HP Mini.  I tried it, and it didn't like my Wifi, i think...   I need to try it again. Koppix also looked good w/ LXDE

---

### Post by XubuRoxMySox on 2009-06-23
> **RandyNose said:**
>  Knoppix also looked good w/ LXDE

It does look good! The only thing is, *it is not meant to be installed on your hard drive*. You run it entirely from the live CD or in RAM. That's kinda weird... what if I wanted to burn a music CD? Sorry, the drive is occupied by the OS.

Okay, now totally off topic, but "*Geek stuck in a Big Rig*:" How's freight by the way? I imagine it must be really hard on truckers these days, especially owner operators. And relying on wifi exclusively is a pain, especially if you have to pay for it (*IdleAire, Flying J, Pilot, TA* - they all charge for wifi don't they?). It must be hard on a geek to be stuck in a big rig. :)

-Robin

---

### Post by Faceless79 on 2009-06-24
Final 'update' cuz im bored. Im now running a straight openbox desktop (not just as window manager but full desktop) with a gnome core and using gnome-panel. It runs 10x faster than xubuntu in the initial install and looks wicked awesome.
And yes knoppix is meant to be run off of a cd but so is dsl and puppy. You do have the option of installing all 3 if you wish

---

### Post by XubuRoxMySox on 2009-06-24
> **Faceless79 said:**
> Final 'update' cuz im bored. Im now running a straight openbox desktop (not just as window manager but full desktop) with a gnome core and using gnome-panel.

So I imagine it looks a lot like Crunchbang? Or do you have a desktop with like wallpaper and stuff? Post a screenshot and a how-to! Sounds like it's way cool.

>  It runs 10x faster than xubuntu in the initial install and looks wicked awesome. 

I have no doubt that it's a bunch faster than Xubuntu. There have been a few threads on these forums about how bloated and heavy Xubuntu has become - nothing lightweight about it at all anymore.

 "Lubuntu" is not aiming for lightweightness much anymore either, but they really don't need to. One can simply use a minimal Ubuntu install and add only what they want to it to acheive a true "Ubuntu Lite."

Looking forward to a screenshot and how-you-did-it post,

Robin

---

