---
title: "Need suggestions to make ubuntu more lightweight for an old computer."
date: 2009-06-07
forum: General Help
---

### Post by user sam on 2009-06-07
Problem: I have a crummy old computer that has a little less than 128 mb ram and a Celeron processor from the cretaceous period. It could potentially run crunch-bang ubuntu with openbox window manager. Crunch bang's just a little bit too big to be of much use. 
It would be nice to know just how much I can get rid of safely. I could use some lightweight substitutes for popular programs. It would also be nice if the distribution still works when I get done slimming it down. Thanks.

---

### Post by Soul-Sing on 2009-06-08
fluxbuntu? : [http://www.fluxbuntu.org/js.html](http://www.fluxbuntu.org/js.html)

---

### Post by dmizer on 2009-06-08
What CPU speed does your laptop have? I run Xubuntu on a 600 MHz PIII with 256 meg of RAM. 128M is a bit small, but it should still be ok. If it's still slow even with fluxbuntu, then you may have a hardware driver problem. The most likely culprit is video.

Edit:
Almost forgot about this thread -> [http://ubuntuforums.org/showthread.php?t=478237](http://ubuntuforums.org/showthread.php?t=478237)

---

### Post by snowpine on 2009-06-08
I would recommend leaving the Ubuntu family behind and trying some lightweight distros like Puppy, DSL, SliTaz-Loram, Tinycore, Antix, etc. Currently I have Antix on my 128mb computer and it is running ok. (ps Don't install Fluxbuntu; it is based on Ubuntu 7.10, which is no longer supported.)

---

### Post by user sam on 2009-06-08
> **leoquant said:**
> fluxbuntu? : [http://www.fluxbuntu.org/js.html](http://www.fluxbuntu.org/js.html)
crunch bang is about the same as fluxbuntu. its a little newer. homepage:[http://crunchbanglinux.org/]("http://crunchbanglinux.org/")
The really minimalist stuff, like Puppy and DSL, doesn't work for me. No offense, but it's the first thing I thought of. I have an old compaq desktop from 199something that used to run windows ME. The cpu is 633 MHz. Allow me to reiterate my question: What can I do to make Ubuntu smaller(as in use less ram, fewer system resources) for my computer? Keep in mind that I'm already working with a pretty lightweight distro.
This is something Xubuntu won't work on.

---

### Post by snowpine on 2009-06-08
> **user sam said:**
> crunch bang is about the same as fluxbuntu. its a little newer. homepage:[http://crunchbanglinux.org/]("http://crunchbanglinux.org/")
The really minimalist stuff, like Puppy and DSL, doesn't work for me. No offense, but it's the first thing I thought of. I have an old compaq desktop from 199something that used to run windows ME. The cpu is 633 MHz. Allow me to reiterate my question: What can I do to make Ubuntu smaller(as in use less ram, fewer system resources) for my computer? Keep in mind that I'm already working with a pretty lightweight distro.
This is something Xubuntu won't work on.

CrunchBang is based on Ubuntu, and I recommend you will get the best results on your old hardware if you experiment beyond the Ubuntu family. 128mb of ram just is not enough.

Here is an interesting thread on what can be done to make CrunchBang lighter: [http://crunchbanglinux.org/forums/topic/2504/lighten-crunchbang/](http://crunchbanglinux.org/forums/topic/2504/lighten-crunchbang/)

ps the single best thing you could do is get more ram, is that an option?

---

### Post by Soul-Sing on 2009-06-08
user sam and snowpine thx for the crunchbang link. It seems fluxbuntu isn't an option any more...

---

### Post by yaroto98 on 2009-06-08
If you're looking for speed on an old legacy system, your best bet is to compile your own version of linux. (not for the faint-hearted) Like Arch-Linux, Slackware, Gentoo, or FreeBSD.

---

### Post by reeseslover531 on 2009-06-08
As much as I love Ubuntu, Damn Small Linux really is incredible on low ram and other low end systems. I run it on a 500 mhz P3 with 64 megs of ram and it runs wonderfully!

---

### Post by user sam on 2009-06-08
I am very grateful for your help, everyone. And I may indeed try a do-it-yourself system. However, I need to know the answer to my question. I know it's the million dollar question, but *what can I throw away*?
I am sorry to say that upgrading my hardware is not an option, at least for now. The computer is my personal project.
Thanks for the #! forum link, snowpine!
Which would you say is lighter, pcman or emelfm?

---

### Post by snowpine on 2009-06-08
> **user sam said:**
> However, I need to know the answer to my question. I know it's the million dollar question, but *what can I throw away*?

Ubuntu.

---

### Post by reeseslover531 on 2009-06-08
Yeah it really is much easier if you just install one of the pre-done lightweight distros

---

### Post by Polaris96 on 2009-06-08
OK here's what I have done when installing ubuntu on low mem machines:

Use the Xubuntu CD to install XFCE as your front end.
Then, install openbox, which is a nice, small, lightweight window manager.

Manually run through your applets and remove anything you don't feel you need.

Stay away from mozilla for browsing - there are some small ones out there you can find them in the forum.  I use dillo but it doesnt do flash or java, so look around.

You can incorporate many of DSL's appas from source code, just install the build-essential package, so you have compilers, linkers, etc. available.

And DO recompile your OS first chance you get.  Keep Xubuntu/openbox as your fallback, if you have enough storage space.  Even if it doesn't work out, you learn a lot by compiling kernel.  At some point, everybody should try it.

---

### Post by user sam on 2009-06-08
Okay. So far I've thrown out cups(I use a different computer to print, anyway) conky, firefox, a bunch of email stuff since i don't use email clients anyway, openoffice and gimp help pages, not that either was installed to begin with, and installed Opera web browser. PCmanfm is pretty lightweight, right? Is emelfm lighter? Any other suggestions would be helpful.
[COLOR="Red"]Note: getting rid of cups or conky is probably a bad idea.[/COLOR] I'm just doing it because I'm just trying random stuff.

---

### Post by N1c0_ds on 2009-06-08
Why not start from a minimal install? Just get the minimal install CD for Ubuntu or Debian, then add a desktop environment of your choice and your required software. It's easy and it just works :)

---

### Post by egalvan on 2009-06-08
OK, a few questions that haven't been asked.....

what type and speed CPU do you have now?

what size hard drive?

what type of video card do you have

You stated that "*The really minimalist stuff, like Puppy and DSL, doesn't work for me.*"

Why does Puppy 4.2 not work for you?
What type of work/play do you need to do on your computer?

---

### Post by Nythain on 2009-06-08
download alternate install iso
hit f4 at the main screen
select command line system or whatever its called

when thats done
sudo apt-get install hal xorg <insert lightweight window manager of choice here>

done :)

i currently run a cli install + x + awesome + xfce4-terminal(8 of them open at once) + a bunch of ncurses apps, and sit roughly around 100mb of ram usage (and over half of that is rtorrent)

---

### Post by user sam on 2009-06-08
Okay. One last time, this is a personal project. I just want my computer to work. I already mentioned that my processor is an intel celeron 633MHz. 15 GB hard drive, possibly a little more, it might have been upgraded without my notice. And as for Puppy, it won't work because the screen does not extend to the button that should launch the installer, and i don't feel like tabbing my way through a system that isn't that great anyway. The vid card is probably old and dirt encrusted, and entirely a mystery to me. I can't find it inside the computer, and it isn't in compaq's support site(that i could find). My computer is a Presario 5BW220 5000 series desktop pc. It should stil have the card it came with.

---

### Post by dmizer on 2009-06-08
> **N1c0_ds said:**
> Why not start from a minimal install? Just get the minimal install CD for Ubuntu or Debian, then add a desktop environment of your choice and your required software. It's easy and it just works :)

+1 for this. Rather than trying to remove what you don't want, just install only what you need: [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

---

### Post by Nythain on 2009-06-08
seriously, what you need is either ubuntu-alternate or ubuntu-minimal or hell, even ubuntu-server (just dont install the actual servers) iso.

with either one of those, you can install a command line only system (the bare minimum ubuntu experience) and apt-get what you want from there.

on that machine, i would recomend either one of the boxes, or a really lightweight window manager like jwm or evilwm or hell, even xfce (just not the xubuntu-desktop package)

thats abotu as lightweight of an ubuntu as you're gonna get, short of that you're lookin at one of the lightweight distros, wich you say dont work, so thats not an option.

---

### Post by user sam on 2009-06-08
I wish you would just please answer my question and tell me what to point my mouse at so I can delete it. I'll go ahead and try the minimal thing in the meantime, but this is my pet project. thanks, I appreciate all the advice.
sorry, that was a bit harsh. even if i don't benefit someone else might

---

### Post by mrbiggbrain on 2009-06-08
> **user sam said:**
> I wish you would just please answer my question and tell me what to point my mouse at so I can delete it. I'll go ahead and try the minimal thing in the meantime, but this is my pet project. thanks.

essentialy... everything but

```
kernel + components + moduals
Bash
Binutils
bison
bzip2
coreutils
diffutils
findutils
gawk
gcc
glibc
grep
gzip
make
ncurses
patch
sed
tar
texinfo
lilo/grub
```

then there are packages im guessing you want, 

```
synaptic
webbrowser (lynx)
text editor (vi)
gui (xwindows + window manager[xfce/fluxbox])
```


iv listed the core requirments for linux to function, trying to ask what is needed is like trying to figure out whats needed in a house... 4 walls and a roof... you can get rid of everything else and still have a house. but most people really wouldnt call that a house, more a shack... so get rid of what you dont need... and add what you do

---

### Post by marshag63 on 2009-06-08
User Sam,
The better question is what do you need it to do and must it be done in a GUI, what programs must you exclude because you do not like them.

I installed linux on a Presario similar to yours - it was Sam linux (which is lightweight) and it still ran slow because Presario is so MS centered.  The one I worked on didn't even have an ethernet card - only  USB and I could not get it to recognize an ethernet card, so I had to buy an ethernet to USB adapter just to get on the net.  This was almost 2 years ago - things have advanced since then.  It ran acceptable - older computers can't run a GUI like new ones, so adjust expectations according.  

First we need to know exactly the things you must must must have and what you have no need for, and the programs you have tried that you don't like before we can help you get something you will like.  Linux is not windows - just deleting stuff is not a good idea.  You will have to compromise a little bit of ease for "speed"

BTW, I found out that a Belkin F5D7050 USB adapter (version 4) works out of the box in Ubuntu based distro (Mint 6).  (Version 3 works with NDIS wrapper).  I get mine at Walmart for about $40.

If you are wanting to use this computer for web-surfing/entertainment, that might be pretty tough - streaming video/audio.  If you plan to chat and do "research" type stuff - should not be a problem, especially if you can get used to a couple of great CLI apps (irssi for IRC/chatting, and Elinks (graphical) for internet browsing, MOC for listening to music), or give the live CD INX a try (version 1.1) - you will be amazed.

I don't think you will be satisfied with anyone's answers to "click my mouse" and remove anything until you can tell us what you need this PC tailored to do.

MarshaG.
P.S. Use Synaptic to add/remove programs - its safer.

---

### Post by user sam on 2009-06-08
Ok. here we go again. 
1.in response to marthag, i was kidding about clicking and deleting stuff.
2.I want a gui, a text editor, web browser, package manager, maybe some office programs, basic stuff like that. preferably graphical. I can install anything else i need with the package manager.
3. everyone's comments so far have been pretty good.
4. comments number 6, 23, and 22 were to most helpful to me.
5. this pc will probably not do anything more than get online, write stuff, maybe play a couple of card games, and be subject to the occasional experiment.
6. I can train other people to use a gui, however minimal, but they get all jittery around the command line.
7. Nothing against Presario, but the one i have didn't even run windows well.

---

### Post by marshag63 on 2009-06-08
user sam,

Did you like XFCE or are you open to fluxbox or openbox (lighter than fluxbox?)  

Did you say you had a crunchbang CD?  I think you might find it better. Its based on openbox and made for machines with 128 MB ram or less.  If you don't like the little cheatsheet to the left side of the screen, just kill conky (Ctrl + Alt + Escape turns pointer to an "X" and then left click on the window you want to close, i.e. conky transparent window).

Package manager is Synaptic, unless you go command line with apt-get (its very fast if you are the one doing the installing and not the other users).

Both Xubuntu and crunchbang (most distros) have a text editor, office apps (Abiword or if you are lucky OpenOffice suite) picture viewer, picture editor.  If you want a lightweight music app for playing CD/listening to songs you have ripped the good old XMMP program is not bad to use - but there are lots of music apps (kinda fun to try out the different ones).

As for browser - I prefer firefox if I am wanting to watch a video or access a flash site (I trade the speed for the abilities).  If I need to find info on something fast I use something much lighter (CLI or sometimes Dillo (GUI) (Dillo doesn't do much beyond find your text and pictures, but it can be pretty fast, but not as fast a CLI.)  Opera is good too (not that much lighter than Firefox though).

Looking forward to hearing what you decide.

Just in case you decide to try crunchbang, here is the link.
[http://crunchbanglinux.org/](http://crunchbanglinux.org/)

MarshaG63

---

### Post by Nythain on 2009-06-08
here we go with nythain's amazing lightweight list of lightweight apps... all can be gotten with a simple sudo apt-get install <package>

Window Managers - xfce, openbox, fluxbox, jvwm, evilwm, or a tiler like wmii, xmonad, awesome
Text editors - for a simple editor, Leafpad, for a decent word processor, AbiWord
Web Browsers - id stick with firefox if it runs (wich it should)
File Manager - Thunar or even better, PCManFM
Terminal Emulator - xfce4-terminal pwns, its default behavior of spawning new terminals from the first main instance is the cats pajamas for light resource consumption

what more do you need on a lightweight system, lol... Apps i personally use (most are ncurses, wich is like a gui in the console)

IRC - weechat
IM - centerim
Shell - zsh
System Monitor - htop
Torrent - rtorrent
Email - mutt
Music Player - moc(p) aka Music on Console
Text Editor - geany
Word Processor - abiword
Package Manager - synaptic
Run Dialog - gmrun
Terminal Emulator - xfce4-terminal

it doesnt get much more lightweight than all of that... for a gui on the music side of things, i would suggest mpd (music player daemon, its technically a server) and Sonata as a front end, or without mpd, just Exaile.

If you are looking into video, either VLC or mplayer (argument for and against both are everywhere). Ummm... hmmm... well, all of this can be gotten onto a pretty lightweight system by downloading and burning the minimal iso wich should just leave you with a command line system, then
sudo apt-get --no-install-recommends install hal xorg <insert wm of preference> firefox abiword leafpad anyotherappsyouwantorlike

if you really arent looking into re-installing, then just use the above mentioned list of stuff to remove from a current ubuntu system, its pretty decent

---

### Post by andrew.46 on 2009-06-13
Hi yaroto98,

> **yaroto98 said:**
> If you're looking for speed on an old legacy system, your best bet is to compile your own version of linux. (not for the faint-hearted) Like Arch-Linux, Slackware, Gentoo, or FreeBSD.

Just a small nitpick from an old slacker: Slackware is not a *compiled* distro as such, it is distributed as a series of binary packages. To get a fully featured system further compiling is often necessary but it depends what you are after from the system.

Apologies for picking on this small issue :-),

Andrew

---

### Post by user sam on 2009-06-17
Okey doke. I got Ubuntu jaunty to work on the old computer by installing the base system from the mini installer. Its got icewm and gdm after I apt-got(apt-got? apt-getted? apt- whatever) and installed xorg and stuff. Its kinda buggy, but I can say one thing about it. It works. thanks a lot. sorry I was so stubborn.

---

