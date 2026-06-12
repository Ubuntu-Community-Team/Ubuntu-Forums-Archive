---
title: "I just got an ancient laptop - looking for suggestions on UI"
date: 2007-06-06
forum: Desktop Environments
---

### Post by qpieus on 2007-06-06
I just inherited a very old laptop, a dell something or other, Pentium 233 with 64 MB ram. This baby has a "designed for windows 95" sticker on it. Neato!

Anyway, do I have any hope of installing linux, preferrably *buntu, and having a graphical desktop on this supercomputer? I've been doing a little reading on fluxbox and icewm and I'm hoping these might work with this laptop. I have no experience with those though and I'm having trouble determining if this laptop can even handle those window managers.

I would love to hear any suggestions on what I should do with this laptop. I was hoping to be able to at least use it for web browsing....

Thanks!

edit - forgot to add, the HD is only about 2 GB.

---

### Post by trippinnik on 2007-06-06
The windows managers you mentioned will probably work, or even Enlightenment 16 (not the under development e17).  What do you want to you use that monster for?  You may want to try something like DSL, Feather, or Puppy they have much smaller install sizes.

---

### Post by Lord Illidan on 2007-06-06
Forget Ubuntu. Try Damn Small Linux...

---

### Post by ppd on 2007-06-07
Better try DeLiLinux

---

### Post by joselin on 2007-06-07
I tried xubuntu in a machine like you mention and works fine... slow, but fine. One thing, you must use the alternate install cd.

[http://www.xubuntu.org/get#feisty](http://www.xubuntu.org/get#feisty)

To run the Desktop CD (LiveCD + Install CD), you need 128 [MB]("http://en.wikipedia.org/wiki/Megabyte") [RAM]("http://en.wikipedia.org/wiki/RAM") to run or 192 [MB]("http://en.wikipedia.org/wiki/Megabyte") [RAM]("http://en.wikipedia.org/wiki/RAM") to install. **The Alternate Install CD only required you to have 64 [MB]("http://en.wikipedia.org/wiki/Megabyte") [RAM]("http://en.wikipedia.org/wiki/RAM").**
 To install Xubuntu, you need 1.5 [GB]("http://en.wikipedia.org/wiki/Gigabyte") of free space on your hard disk.
 Once installed, Xubuntu can run with 64 MB RAM, but it is strongly recommended to use at least 128 MB RAM.

---

### Post by matt_risi on 2007-06-07
I've really got into light-weight, resource-conservative linux installs lately, and any type of Ubuntu install, even just installing the text-only version and adding a very lightweight window manager such as OpenBox or FluxBox gives a RAM footprint of around 50 megs, bumping up to 70+ megs with Firefox running.

I'd go with Puppy Linux, Damn Small Linux or possible Arch or DeliLinux.

Have fun, that sounds like a cool project!

---

### Post by joselin on 2007-06-07
> **matt_risi said:**
> I've really got into light-weight, resource-conservative linux installs lately, and any type of Ubuntu install, even just installing the text-only version and adding a very lightweight window manager such as OpenBox or FluxBox gives a RAM footprint of around 50 megs, bumping up to 70+ megs with Firefox running.

Only firefox without extensions and with only one open tab waste about 30 Mb. Definitively firefox isn't a good browser for that king of machines.

---

### Post by qpieus on 2007-06-07
Thanks for the replies, I appreciate the help.
I've run DSL and Puppy from a USB stick before, and liked them, but as I was reading more about them it sounded like both of them are not that easy to install to a hard drive. 
Somehow I had not heard of DeliLinux before now, I will definitely check that out. It looks like it has a simple install method, similar to a *buntu alternate installation. I can handle that :)
Feather linux also interests me, being debian based, but like Puppy and DSL, it looks like it is primarily a live cd that isn't necessarily made to install the hard drive. 
And thanks joselin for your comment on xubuntu on a similar machine. I'm comfortable with *buntu so I may just start with that one and see how it works. The 1.5 GB install size may be a problem though,my HD is only a little bigger than that.

---

### Post by ugm6hr on 2007-06-08
> **qpieus said:**
> Thanks for the replies, I appreciate the help.
I've run DSL and Puppy from a USB stick before, and liked them, but as I was reading more about them it sounded like both of them are not that easy to install to a hard drive. 
Somehow I had not heard of DeliLinux before now, I will definitely check that out. It looks like it has a simple install method, similar to a *buntu alternate installation. I can handle that :)
Feather linux also interests me, being debian based, but like Puppy and DSL, it looks like it is primarily a live cd that isn't necessarily made to install the hard drive. 
And thanks joselin for your comment on xubuntu on a similar machine. I'm comfortable with *buntu so I may just start with that one and see how it works. The 1.5 GB install size may be a problem though,my HD is only a little bigger than that.

Not sure how long it's been since you've tried Puppy, but doing a full install to HD is not hard at all.  In fact, on Puppy2.14, the full install option is easier than the frugal install, since it automatically installs Grub.  It's in the menu on the LiveCD.  I suspect Puppy2.16 is no different.  The thing I like about Puppy is it's GUI tools for USB/CD/floppy/HD mounting, networking, wireless etc.  It also comes with good choices for software on that type of hardware - AbiWord, Gnumeric, Gxine...  Only other suggestion would be try Opera for browsing - it's quite a lot faster than Mozilla based brosers (Puppy uses Seamonkey as default).  I have put a Puppy-based installation on something similar.

Another thought is Fluxbuntu, which I have just tried the LiveCD for.  Although you will probably need to use an alternative LiveCD (e.g. Puppy or DSL) to create a swap partition to run it with only 64MB RAM.  I quite like it - and the idea of access to Ubuntu apt-get / Synaptics appeals.

---

### Post by qpieus on 2007-06-09
Thanks ugm6hr. I did not know puppy had an install option right from the live cd. I will try that.
I installed a fiesty barebones using the mini.iso as described at psychocats. It took forever but it installed just fine and the touchpad and ethernet card work properly. I tried out firefox, but it definitely was slow. I also installed dillo. That runs fast, but I don't like how it renders most pages. Like these forums for example - the forum main page loads with a single, long column of links to Home, User CP, gallery, etc. on the left side of the screen. To get to the actual subforums links I have to scroll way down the screen. That's a PITA. I'll give opera a try. I haven't used that in quite some time, but I suspect it will render pages better than dillo.

Fluxbuntu does appeal to me too since I like the whole apt-get thing.

---

### Post by Gruelius on 2007-06-10
Ive got a simmilar situation but my laptop is a bit more beefy :P

533mhz transmetta cpu, 116mb available ram, 40gb hdd.

Installing FF 7.04 Gnome then setting up fluxbox has me using 47mb ram and 33mb swap but i havent done any tweaking yet

---

### Post by steveneddy on 2007-06-10
I vote for Damn Small or Puppy - small but powerful distros.

My favorite is gonna be the DSL.

---

### Post by ugm6hr on 2007-06-10
Just thought I'd report on my Fluxbuntu experiment.

The LiveCD looks good on a 128MB desktop, but the ubuquity installer hangs after selecting partition mount points.  No errors, nothing.  Screen, keyboard, mouse cursor etc all just freeze for hours (waited for 8 hours - nothing - twice).

I do wonder about re-burning a fresh CD, but I burnt it at 2x the first time.  Seems bizarre that the LiveCD would work, and it would still be a CD fault....  Since it's not an important issue for me - I might leave it alone for now.  Minimal install seems a possibility - as below:

[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

Got the 6.06LTS minimal .iso onto a USB (to save wasting any more CD-Rs), and then discovered the machine doesn't have BIOS option to boot from USB!  Shame - I was really pleased with my bootable USB (which works on my laptop).

As for my older machine - I think I might stick with DSL.  Would like AbiWord and Opera though, and I don't think DSL plays nicely with .deb files (or any package manager).

---

### Post by qpieus on 2007-06-10
> **ugm6hr said:**
> 

.... Minimal install seems a possibility - as below:

[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)


I have the minimal installation running right now. The initial attempt failed when I tried the default "server" installation. I then tried it with the pentium boot code option and it installed without a hitch. It's too slow though. I think I'm gonna try the latest puppy linux and see how that goes. I'll miss my apt-get though:(

I'm also trying to buy another 64 mb stick of edo ram. That'll boost the total up to 128 mb. That should help.

I really hate buying from ebay though - most sellers charge too much for shipping. For a stick of this ram most sellers are charging $8+ for shipping. That just pisses me off. I could ship that ram for 41 cents by throwing it in an envelope and slapping a stamp on it, it doesn't weigh anything. Bunch of crooks. [end ebay rant]

---

### Post by Shazaam on 2007-06-10
Try this for old parts-
[http://www.kahlon.com/](http://www.kahlon.com/)

---

### Post by ugm6hr on 2007-06-10
If you don't get around to the extra RAM...

DSL-N looks like a reasable distro too (haven't yet had a try):
[http://www.damnsmalllinux.org/dsl-n/](http://www.damnsmalllinux.org/dsl-n/)

They have included more useful apps than DSL, with GTK2 and the 2.6 kernel.  Should run just about OK on your system.

You can install DSL to HD too:
[http://www.damnsmalllinux.org/dsl-n/f/viewtopic/177.html](http://www.damnsmalllinux.org/dsl-n/f/viewtopic/177.html)

---

### Post by smartboyathome on 2007-06-10
> **qpieus said:**
> I have the minimal installation running right now. The initial attempt failed when I tried the default "server" installation. I then tried it with the pentium boot code option and it installed without a hitch. It's too slow though. I think I'm gonna try the latest puppy linux and see how that goes. I'll miss my apt-get though:(

I'm also trying to buy another 64 mb stick of edo ram. That'll boost the total up to 128 mb. That should help.

I really hate buying from ebay though - most sellers charge too much for shipping. For a stick of this ram most sellers are charging $8+ for shipping. That just pisses me off. I could ship that ram for 41 cents by throwing it in an envelope and slapping a stamp on it, it doesn't weigh anything. Bunch of crooks. [end ebay rant]

I am experimenting now with FVWM-Crystal and Ubuntu. So far so good. All is going well, and it is REALLY fast. I would HIGHLY recommend trying it out. If you want to, try [this guide]("https://help.ubuntu.com/community/FVWM-Crystal"). You do not need to use the server for FVWM-Crystal to work, just follow the guide. ;) This is smartboy, over and out! :p

---

### Post by qpieus on 2007-06-12
smartboy - what's the PC's specs that you are running FVWM-Crystal on? That does look good. Since I already have the minimal installation loaded, I'll try it out. The setup for it looks to be simple.

---

### Post by nightfire117 on 2007-06-15
> **matt_risi said:**
> I've really got into light-weight, resource-conservative linux installs lately, and any type of Ubuntu install, even just installing the text-only version and adding a very lightweight window manager such as OpenBox or FluxBox gives a RAM footprint of around 50 megs, bumping up to 70+ megs with Firefox running.

I'd go with Puppy Linux, Damn Small Linux or possible Arch or DeliLinux.

Have fun, that sounds like a cool project!

I'm not the first person to "second" this, so I guess I've got to come up with another term. Actually, I think ancient UIs look great, but not with a more modern PC. Heh. It makes them look more... eh... well, movie-esque...? I'm not sure how to describe it. T__T

Anyways, I'd use FVWM or Fluxbox. Even Fluxbox might not run so well on that...?

~Nightfire

---

### Post by rcarroll215 on 2007-06-15
I used to have a computer with almost the exact same specs as this.  In fact, I installed my first ever Linux distro on it... Mandrake 8.2.  If you can find it, I highly recommend it.  It's old... very old... but it does come with a version of KDE and Gnome.  The version I had came with 2 CD's of "Commercial Apps" that contained alot of useful stuff.

Good luck!

---

### Post by raul_ on 2007-06-15
I own an old toshiba satellite, 333 Mhz, 128mb RAM, runs Fluxbox just fine, i'm experimenting with fvwm-crystal and it looks ok. It's actually fast until you load a Web Browser. Linux lacks good lightweight browsers (don't even mention Dillo) and Kazehakaze's feisty version is borked

---

### Post by smartboyathome on 2007-06-15
I actually have had good time with my web browser (Opera). It seems that the Mozilla browsers don't work very well with it. So if you were using one of these, that might have been the problem.

---

### Post by raul_ on 2007-06-15
I'm actually using Opera :)

---

### Post by qpieus on 2007-06-16
raul - I totally agree with you about light browsers. I don't like dillo, page rendering is not good. I've used Kazehakaze on my dapper box and it is pretty good, but I tried it on this low spec laptop and the browser barely runs - it's unbearably slow and seems to lock up. Firefox is slow. Opera has been the best so far, but it's still pretty slow. If I can get another stick of ram to bring it up to 128 mb total, it'll probably be acceptable.

---

