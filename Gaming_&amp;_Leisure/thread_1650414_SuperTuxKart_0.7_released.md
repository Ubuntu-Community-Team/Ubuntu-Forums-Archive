---
title: "SuperTuxKart 0.7 released"
date: 2010-12-21
forum: Gaming &amp; Leisure
---

### Post by Arthur_D on 2010-12-21
> After over a year of work, dozens upon dozens of new and fixed bugs,  over 3000 commits, a lot of work from artists, restless testing from our  faithful followers, and translations from contributors all over the  world, we are thrilled to offer you SuperTuxKart 0.7 just in time for  Christmas! This release is using irrlicht for graphics, and features: 
 
[LIST]
[*] new GUI
[*] kart and track animations
[*] new and improved tracks, karts, and items
[*] shortcut/alternative way support for tracks
[*] Asian fonts
[*] many many bugfixes.
[/LIST]
Enjoy!
Downloads can be found here: [http://supertuxkart.sourceforge.net/Downloads](http://supertuxkart.sourceforge.net/Downloads)
There are not any deb package for 0.7 yet, but hopefully it should be available soon.

---

### Post by Cavsfan on 2010-12-21
Great! Is it available for Maverick too? I just seen Karmic.
Thanks for the post!

---

### Post by wingnux on 2010-12-21
Thanks for the info! I'm gonna give it a try.

---

### Post by Arthur_D on 2010-12-21
[QUOTE=Cavsfan]Great! Is it available for Maverick too? I just seen Karmic.
Thanks for the post! 	[/QUOTE]

Sorry, but as I wrote, there are not any deb file for 0.7 as of yet, so the Karmic one is still the 0.6.2 version. Hopefully it will be in the repos for Natty (11.04).
Compiling from source is probably the best way for now - hopefully this inconvenience will be solved soon. There are unofficial PPA's for SuperTuxKart, but as far as I know they are updated with unstable releases and as such may not be the safest way to get 0.7 (as a later update may contain unstable features, or break things previously working).

---

### Post by thatguruguy on 2010-12-21
> **Arthur_D said:**
> Sorry, but as I wrote, there are not any deb file for 0.7 as of yet, so the Karmic one is still the 0.6.2 version. Hopefully it will be in the repos for Natty (11.04).
Compiling from source is probably the best way for now - hopefully this inconvenience will be solved soon. There are unofficial PPA's for SuperTuxKart, but as far as I know they are updated with unstable releases and as such may not be the safest way to get 0.7 (as a later update may contain unstable features, or break things previously working).

I guess that depends on what you mean by "unofficial".  The ppa for the SuperTuxKart development team is [here]("https://launchpad.net/%7Estk/+archive/dev").  It's not officially supported to Canonical/Ubuntu, but it is certainly supported by the guys making SuperTuxKart.  If you add it to your software repositories and get a working copy of SuperTuxKart, no one says you have to update it after you get it working.

---

### Post by Arthur_D on 2010-12-21
Well, the PPA is not handled by the two lead developers, and contains svn versions of STK and Irrlicht. While this should work for now, it could pose as an inconvenience if someone add the PPA to their sources and then STK later becomes crash-prone because it was updated alongside with all the other software when doing an update.

In other words: feel free to use the PPA, but at own risk.

---

### Post by wingnux on 2010-12-21
Just compiled/installed/tested and it's a great advance over the previous version! There's still a lot of work to be done  but it's great fun, I'm really surprised with it.

---

### Post by DangerOnTheRanger on 2010-12-22
*installs PPA*
*runs*
*jaw hits floor*

---

### Post by Arthur_D on 2010-12-22
Okay folks, just a quick update on the PPA issue: I have contacted the creator of the development PPA, and as such it will not be updated to more unstable versions later on, so it should be pretty safe to use the PPA. Hopefully in time for 0.7.1, there will be separate stable and development PPA's.
Sorry for the confusion - and for 0.7.1 this will hopefully be sorted.

I'll still recommend to download and build yourself, if you can.

---

### Post by Arthur_D on 2011-01-01
For those reluctant of building themselves, but still want all the last-minute changes that went into the final release, there's a Linux binary for i386 here: [http://sourceforge.net/projects/supertuxkart/files/SuperTuxKart/0.7/supertuxkart-0.7-linux-i386.tar.bz2/download](http://sourceforge.net/projects/supertuxkart/files/SuperTuxKart/0.7/supertuxkart-0.7-linux-i386.tar.bz2/download)

It should work fine with all recent GNU/Linux distributions.

---

### Post by Kevrox on 2011-03-06
Ok I'm running 10.04 LTS 2.6.32-29-generic, 2.30.2 and have a powerwave controller that was working on the old version. When the controller is plugged in and the game started the options highlight at a rate of knots not allowing one to pick menu options, it just jumps from one menu to another on its own. If I unplug the controller I am able to pick option with the mouse and play game with keyboard. 
Ay ideas on how to sort. The kids are sad they cannot use the controller, but love the new look and tracks. let me know what info you need to look at with terminal commands ........
cheers
kev

---

### Post by Arthur_D on 2011-03-07
Hi Kevrox, there have been a few changes to the gamepad handling after 0.7, so hopefully the upcoming 0.7.1 release will work for you. :)
If you know how to build from source, you can grab the latest SVN version from here: [https://supertuxkart.svn.sourceforge.net/svnroot/supertuxkart/main/trunk](https://supertuxkart.svn.sourceforge.net/svnroot/supertuxkart/main/trunk)
This would help us confirm that it works, and if not some more debug checks can be done using the SVN version.

---

### Post by Kevrox on 2011-03-07
> **Arthur_D said:**
> Hi Kevrox, there have been a few changes to the gamepad handling after 0.7, so hopefully the upcoming 0.7.1 release will work for you. :)
If you know how to build from source, you can grab the latest SVN version from here: [https://supertuxkart.svn.sourceforge.net/svnroot/supertuxkart/main/trunk](https://supertuxkart.svn.sourceforge.net/svnroot/supertuxkart/main/trunk)
This would help us confirm that it works, and if not some more debug checks can be done using the SVN version.

Many thanks for response mate, will look at the link and see if I can tinker with it,

---

### Post by Arthur_D on 2011-03-07
Let me know how it goes. :)

Side note: SuperTuxKart 0.7 can now be installed directly with apt-get install supertuxkart in Debian Testing and Ubuntu 11.04 Natty Narwhal. Hooray! :)

---

### Post by Kevrox on 2011-03-21
Ok so do I follow these instruction then?
[https://supertuxkart.svn.sourceforge.net/svnroot/supertuxkart/main/trunk/INSTALL](https://supertuxkart.svn.sourceforge.net/svnroot/supertuxkart/main/trunk/INSTALL)
running 10.04LTS

---

### Post by Arthur_D on 2011-03-22
Yeah, that should hopefully do the trick. If you build Irrlicht 1.7.2 yourself, [these instructions ]("http://www.irrlicht3d.org/wiki/index.php?n=Main.InstallingIrrlicht")seems more correct than in the file you linked to.

Any trouble, just ask. :)

---

### Post by Kevrox on 2011-04-16
> **Arthur_D said:**
> Yeah, that should hopefully do the trick. If you build Irrlicht 1.7.2 yourself, [these instructions ]("http://www.irrlicht3d.org/wiki/index.php?n=Main.InstallingIrrlicht")seems more correct than in the file you linked to.

Any trouble, just ask. :)
Thanks for the link, I ran the script but still no good.
what next.....
is there any terminal command I can run to provide anyone with more info...
cheers
kev

---

### Post by Kevrox on 2011-04-16
gone back to v0.6, kids are happy again...

---

### Post by Arthur_D on 2011-04-16
0.7.1 is officially out - try the static Linux binary on the website and see if it works for you. :)

---

### Post by Kevrox on 2011-04-16
> **Arthur_D said:**
> 0.7.1 is officially out - try the static Linux binary on the website and see if it works for you. :)

downloaded the above , [http://sourceforge.net/projects/supertuxkart/files/SuperTuxKart/0.7.1/supertuxkart-0.7.1-linux-glibc2.12-i686.tar.bz2/download](http://sourceforge.net/projects/supertuxkart/files/SuperTuxKart/0.7.1/supertuxkart-0.7.1-linux-glibc2.12-i686.tar.bz2/download)

Ran the game and it has stopped the menu skipping. It sees the PowerWave controller as a "DragonRise Inc" Generic USB Joystick. But does not allow customisation. No stick or button usage.

So no control of the game, almost like the controller was not there, still I think it is an improvement .... just need to figure out why on V0.6 it works fine and V0.7.1 not...

ok does anyone think that because I ran the script from here [https://supertuxkart.svn.sourceforge.net/svnroot/supertuxkart/main/trunk/INSTALL](https://supertuxkart.svn.sourceforge.net/svnroot/supertuxkart/main/trunk/INSTALL)

it has stuffed the controller connection,..... but still works with v0.6 so I guess no.....

---

### Post by Kevrox on 2011-04-17
ok here is an interesting one
I can run the same controller on Natty in my T101mt Netbook.
The controller works but the main rig I have is running on Lucid 10.04. This is the version I am having the trouble with.
Extremetuxracer works with the same controller.
oh well....

---

### Post by Arthur_D on 2011-04-17
So, does it work on another computer with SuperTuxKart?
Try running 'supertuxkart --gamepad-visualisation' on the troublesome computer, use some buttons/pads and post the output here (if any).

---

### Post by D-G on 2011-04-17
Mario Kart: Double Dash!! on the GameCube was better than this. And that game was released 2003, on a hardware platform from late 2001. Honestly, why would someone want to play Super Tux Kart? Because it's free?

---

### Post by Kevrox on 2011-04-18
> **Arthur_D said:**
> So, does it work on another computer with SuperTuxKart?
Try running 'supertuxkart --gamepad-visualisation' on the troublesome computer, use some buttons/pads and post the output here (if any).

Ok net book tester is running Natty and it works
Main PC running Lucid is the one having trouble. Please clarify the Supertuxkart --gamepad-virtualisation option, is this a third party install or within the game itself?

---

### Post by Arthur_D on 2011-04-18
If you have 0.7.1, the --gamepad-visualisation flag is included by default.

---

### Post by Arthur_D on 2011-07-15
SuperTuxKart 0.7.2 is up for grabs today!

New features:
* Added in-game addon manager
* Fixed major memory leaks
* New Snow Peak track by Samuncle
* Improved star track UFO by Rudy
* New Beastie kart.
* Show when you get a highscore
* Improve gamepad configuration under Windows (add ability to tell gamepads apart)
* Various other tweaks done and glitches fixed

Find it here on our [download]("https://sourceforge.net/projects/supertuxkart/files/SuperTuxKart/0.7.2/") page.

---

### Post by Erik1984 on 2011-07-15
Thanks for mentioning, SuperTuxKart is a very nice game.

---

### Post by Arthur_D on 2011-11-14
SuperTuxKart 0.7.3 is here!
> 4 months after SuperTuxKart 0.7.2, 128 tickets later and a truckload of changes, we are proud to present the latest and greatest version, SuperTuxKart 0.7.3. The big surprise is the very late-minute inclusion of the very beautiful Minigolf track by Mac, thanks for the contribution! (Don't let its childish look trick you however as it is a very challenging track :)
The biggest changes since 0.7.2 include :
New Minigolf track
New Zen Garden track
New Subsea track
New Island battle arena
New Suzanne kart
New graphical effects
New weapons 'Swatter' and 'Rubber Ball'
Added Thunderbird as race referee
3 Strikes Battles now displays lives as spare tires
Improved bubble gum
See progression during Grand Prix
Improve physics for tall karts (e.g. Adiumy)
Lots of bug fixes
Improved kart control at high speeds
Better placement of rescued karts
Transition track-making to blender 2.5/2.6

So now head to our downloads page, enjoy and give us a lot of feedback on the forum!

---

### Post by Erik1984 on 2011-11-15
Great! Downloaded the i386 binary and it runs fine. Good to be back at STK. Is it just me or is the new track "Zen Garden" pretty hard?

---

### Post by Arthur_D on 2011-11-15
It's a bit tricky yeah - lots of bananas, and the bridge is narrow with a nasty jump, but practice makes perfect, as always. ;)

---

### Post by ubudog on 2011-11-16
Awesome game, I love it!

---

### Post by Erik1984 on 2011-11-17
> **Arthur_D said:**
> It's a bit tricky yeah - lots of bananas, and the bridge is narrow with a nasty jump, but practice makes perfect, as always. ;)

I've discovered that if you collect enough nitro you can cut the corner before the bridge (between the trees), still the corner after the bridge remains tricky.

---

### Post by Erik1984 on 2011-11-17
It interacts nicely with a PlayStation controller (with a hardware converter to USB) btw. Only need to find a good key mapping. Bad idea to put 'reset' under L2 and nitro on L1 :)

---

### Post by Arthur_D on 2011-11-19
Yeah, some shortcuts are allowed, i.e. if they are short ones like that.

Glad to hear it's working well; gamepads are tricky because they often have their own special cases. That also explains why default mappings can be pretty useless for some of them. ;)

---

### Post by Erik1984 on 2011-11-21
> **Arthur_D said:**
> Yeah, some shortcuts are allowed, i.e. if they are short ones like that.

Glad to hear it's working well; gamepads are tricky because they often have their own special cases. That also explains why default mappings can be pretty useless for some of them. ;)

It wasn't the default mapping. I changed some keys but made the wrong decisions :P Now I've found a sane mapping. Just use 'select' now as the reset button. L1 to nitro, L2 for a sharp turn, R1 for items, R2 for looking back. X for gas and Square for breaking. Stick or D-Pad (depending if the 'analog' button is pressed or not) for steering... looks like the game was made for the playstation :P

---

### Post by Erik1984 on 2011-11-30
Tip: If you are having speed issues, for instance Tux Tollway was very slow on my system, it might help to update video drivers. I updated from Nvidia 173.something to 195.something via System > Hardware Drivers and now the game seems to run much smoother.

---

### Post by Arthur_D on 2011-11-30
Video drivers are probably the number #1 issue when something isn't right in STK (or any other 3D game, for that matter). Also, if you just don't have the hardware for it, you can turn down graphical effects in options, like animations etc.

For 0.8 we'll get better physics and some kind of story mode, and possibly better AI as well. :D

---

