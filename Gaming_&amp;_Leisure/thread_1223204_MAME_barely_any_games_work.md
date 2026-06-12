---
title: "MAME barely any games work"
date: 2009-07-25
forum: Gaming &amp; Leisure
---

### Post by babujbf on 2009-07-25
Most of the games that I use to run in windows no longer work in ubuntu.

Is it like this for you guys too?

---

### Post by BoyOfDestiny on 2009-07-25
No, works like it should.

What version of MAME did you have on Windows? What version of MAME (sdlmame hopefully, and not the outdated xmame) do you have on Ubuntu? 

The thing is between versions, the romsets/requirements themselves change.

[quote=Mame Dev FAQ]It is not unusual for the ROMs to change for a game between releases of MAME. Why would this happen? Oftentimes, better or more complete ROM dumps are made, or errors are found in the way the ROMs were previously defined. Early versions of MAME were not as meticulous about this issue, but more recent MAME builds are. Additionally, there can be more features of a game emulated in a later release of MAME than an earlier release, requiring more ROM code to run.[/QUOTE]

[http://mamedev.org/devwiki/index.php/FAQ:ROMs#Why_does_MAME_report_.22missing_files.22_even_if_I_have_the_ROMs.3F](http://mamedev.org/devwiki/index.php/FAQ:ROMs#Why_does_MAME_report_.22missing_files.22_even_if_I_have_the_ROMs.3F)

---

### Post by wingnux on 2009-07-25
Nope. Everything works just fine.

---

### Post by babujbf on 2009-07-25
what version of sdl mame should I install? is gxmame a ok front end? Wahcade doesn't convince me, kxmame doesn't support gamepads and gxmame when I am going to install the deb it says it needs to remove sdlmame

By the way I have another display a tv next to my regular monitor, which works as an extension with X screen. When I go full screen with movie player it works great it stays there in the tv and I can work on my regular monitor. But when I try it with the nes or snes emulator it come to my regular monitor and I am guessing it because when I right click on the toolbar its checked "Only on This Workspace" how can I uncheck that?

Thanks guys

---

### Post by ShadowTek on 2009-07-25
> **babujbf said:**
> what version of sdl mame should I install?
I'm not familiar with sdlmame, but in general, you should have a version that matches whatever ROM set that you have.

Or, you can just download a new ROM set, whichever one matches the version of mame that you have installed.

---

### Post by binbash on 2009-07-26
Every game works on windows also works on Ubuntu or any other linux.YOU just do not have required BIOS files probably.

---

### Post by ShadowTek on 2009-07-26
> **binbash said:**
> YOU just do not have required BIOS files probably.

Last time I checked (which *was* several years ago), BIOS were only required for a minority of games.

Also, he could be missing a CHD image.

There's no telling exactly what his problem is without further information.

---

### Post by babujbf on 2009-07-26
guys guys help me with something first. I installed sdlmame but before we find out about the roms and stuff I need to know something.

I have my tv as a secondary display on using X-screen, which means the tv works as an extension of my desktop. When I want to play movies I just move the movie player to the tv space and press full screen and wala the tv goes full screen and my regular monitor stays at desktop.

But if I move the terminal to the tv and then run sdlmame my regular monitor goes full screen the same thing happens with the nes and snes emulators. and I am guessing its because of this:
[[IMG]http://img93.imageshack.us/img93/3065/screenshotngz.th.png[/IMG]](http://img93.imageshack.us/i/screenshotngz.png/)

See the toolbar I right clicked on GFCE Ultra and it says "Only on this workspace." Thats why I think it goes full screen on my normal monitor. Anyway to uncheck that? Because the other option is "A;ways visible workspace." and I cant go to the tv's work space on the regular monitor... I think.


The same thing is going to happen with sdlmame so we need to figure this out.


Thanks guys.

---

### Post by Grishka on 2009-07-26
> **babujbf said:**
> is gxmame a ok front end?

GXMame is no longer developed, use [GMAMEUI](http://gmameui.sourceforge.net/).

---

### Post by babujbf on 2009-07-26
> **Grishka said:**
> GXMame is no longer developed, use [GMAMEUI](http://gmameui.sourceforge.net/).

How do you install it?

---

### Post by Grishka on 2009-07-26
> **babujbf said:**
> How do you install it?

incidentally, I happen to maintain GMAMEUI Jaunty package in [my PPA](https://launchpad.net/~thir/+archive/ppa). :) you're advised, however, not to add it to your sources.list, since I also have some stuff there you might not necessarily want (experimental audio stuff, mostly). grab the GMAMEUI package for your system's architecture, and run. ;)

---

### Post by babujbf on 2009-07-26
> **Grishka said:**
> incidentally, I happen to maintain GMAMEUI Jaunty package in [my PPA](https://launchpad.net/~thir/+archive/ppa). :) you're advised, however, not to add it to your sources.list, since I also have some stuff there you might not necessarily want (experimental audio stuff, mostly). grab the GMAMEUI package for your system's architecture, and run. ;)

LOL I have no idea what you said

---

### Post by Grishka on 2009-07-26
> **babujbf said:**
> LOL I have no idea what you said

heh, alright, here's the same thing, only simpler:
[here](https://launchpad.net/~thir/+archive/ppa/+files/gmameui_0.2.10-2_i386.deb)'s a package for a 32-bit system, and [here](https://launchpad.net/~thir/+archive/ppa/+files/gmameui_0.2.10-2_amd64.deb)'s a package for a 64-bit system. :)

---

### Post by babujbf on 2009-07-26
I'm on hardy though. Don't know if it will still work.

---

### Post by Grishka on 2009-07-26
> **babujbf said:**
> I'm on hardy though. Don't know if it will still work.

well, in this case you'll have to compile from source. it's easy, in this case. get [the source](http://sourceforge.net/projects/gmameui/files/gmameui/0.2.10/gmameui-0.2.10.tar.gz/download), unpack it, then:
```
cd gmameui-0.2.10
sudo aptitude install libglade2-dev libgnome2-dev libarchive-dev
./configure
make
sudo make install
```
then, you can run it with "/usr/local/bin/gmameui".

---

### Post by babujbf on 2009-07-26
hey thanks alot for the help. One more question, its asking me to locate mame executables. Where are they? I installed sdlmame of a deb package.

---

### Post by Grishka on 2009-07-26
> **babujbf said:**
> hey thanks alot for the help. One more question, its asking me to locate mame executables. Where are they? I installed sdlmame of a deb package.

that depends on the package. it's probably /usr/games/sdlmame, or perhaps /usr/share/games/sdlmame/mame. if not, check out the package properties in Synaptic, you can see where the files are installed.

---

### Post by babujbf on 2009-07-26
I wonder why it starts up and runs so slow can't even refresh my game list... I can run doom 3 fine but can't run this lol

got any ideas?

---

### Post by Grishka on 2009-07-27
> **babujbf said:**
> I wonder why it starts up and runs so slow can't even refresh my game list... I can run doom 3 fine but can't run this lol

got any ideas?

idk, maybe you have a huge game list.

---

### Post by babujbf on 2009-07-27
nah is not that big... I am having problems with the computer locking up and stuff... I hadnt sudo apt-get upgrade yet so I am going to see if that has anything to do with it.

---

### Post by williamts99 on 2009-10-24
> **babujbf said:**
> nah is not that big... I am having problems with the computer locking up and stuff... I hadnt sudo apt-get upgrade yet so I am going to see if that has anything to do with it.

Have you ever resolved this issue?  You also might want to consider upgrading to the latest release, or I should say, waiting a week until 9.10 is available as a LOT of things have changed/improved.

Best Regards,
Williamts99

---

