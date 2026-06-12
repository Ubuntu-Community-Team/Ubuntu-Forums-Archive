---
title: "[SOLVED] Someone please make a .deb of the new open arena"
date: 2008-04-29
forum: Gaming &amp; Leisure
---

### Post by eragon100 on 2008-04-29
There is no 0.7.6 open arena .deb on getdeb or on openarena.ws. It is not in hardy 's repo since it was released one or two days after hardy, and the new version isn't backwards compatible. Downloading the new version and extracting it to folder x and running it from there, gives me an error: invalid game folder whenever I trie to join a server :(

Can anyone please make a .deb or tell me where to it on my harddisk :confused:

---

### Post by Perfect Storm on 2008-04-29
Wouldn't it be easier to post the error than waiting for someone in the future makes .deb? Can you post the error?

---

### Post by eragon100 on 2008-04-29
It 's already there: "invalid game folder" when I try to join a server :(

---

### Post by Perfect Storm on 2008-04-29
Even after you do;
```
cd <into Open Arena directory>
./ioquake3.x86_64
```
(second line is diffrent, depends which core your computer have)

---

### Post by eragon100 on 2008-04-29
I am re-downloading it right now to see how it goes, but in the meantime I also have a huge problem with another game that just arrived in the mail this morning, namely the old loki game Heretic 2:

Startup in terminal:

eragon@Asgard:/media/cdrom0$ heretic2
Registered 11 signal handlers

========================== Heretic II ===========================

Added packfile /usr/local/games/heretic2/base/htic2-0.pak (4347 files)
Executing global default.cfg
Executing /home/eragon/.loki/heretic2/config.cfg
NET Initialized
Loaded DLL /usr/local/games/heretic2/base/client_effects.so as 0x8a27848
Setting default sound support "snd_sdl.so"
Loaded DLL /usr/local/games/heretic2/snd_sdl.so as 0x8a27c88
Console initialized.
VID: initial refresh soft
Loading /usr/local/games/heretic2/ref_soft.so 
Loaded DLL /usr/local/games/heretic2/ref_soft.so as 0x8a2aba0
Initializing VID module
Initialize software renderer
Setting mode x11 for device mouse
Initialized 640x480 16bit display
Shutting down sound.
Shutting down input handling
Shutting down sound.
Warning: currently only R5G6B5 mode supported

Exiting Heretic II...
recursive shutdown
eragon@Asgard:/media/cdrom0$ 


I have found out that the mode it needs (R5G6B5) is in normal english better known as 16-bit colour, but how do I make it believe that that is what I am using. Because going into a terminal with ctr-alt-F1 and typing in:

1: sudo /etc/init.d/gdm stop

2: sudo startx -- -depth 16

and ignoring the stupid warning about it not being smart to run a session with root rights, gives EXACTLY the same problem and output when I try to start it.

Then I decided to try it in hardware accelerator mode, but I have a nvidia geforce card and not a 3dfx voodoo. So although it worked after installing libglide 2 and libglide 3 from synaptic, it doesn't run fullscreen, and is 100 % unplayably slow, even in 320 x 240 (and you can imagine how small that is on a 20 inch monitor) :(

How do I make this stupid program believe that I am running in "R5G6B5" mode :confused: :(

I have payed 30 euro's for this game :(

---

### Post by eragon100 on 2008-04-29
And sorry, but nope: Open arena still ain't working :(

And it's raining and I just had to go through the rain :(

Bad Day :lolflag: :(:(:(:(:(

---

### Post by Perfect Storm on 2008-04-29
You might check this site: [http://gentoo-wiki.com/HOWTO_Running_Old_Loki_Games](http://gentoo-wiki.com/HOWTO_Running_Old_Loki_Games)

But it suggest compiling dev-libs/glib-1.2.10-r5 (sounds risky for the system)


Best to avoid games that use Loki installers as it's ancient old and work bad on newer systems.

---

### Post by eragon100 on 2008-04-29
Might be but heretic 2 is probably a fun game and i paid 30 euro's for it, so I don't give a **** if its dangerous for the system :lolflag:

And btw, it already works! It's just to slow to play in opengl mode, so I have to make it belief that I am running 16-bit color mode so it runs in software mode, not install some ancient glibc which will break hardy :)

---

### Post by linuxlizard on 2008-04-29
I've got a stack of old loki games that now sits in my drawer waiting for someone to come up with patches. Heroes of might and magic 3 still works (not fullscreen or network) on pcfluxboxos which uses an older kernel which is better for older hardware, but the rest I can't get running anywhere. 

Linux needs a sort of kernel for libs. When new libs come out, it breaks the commercial games that we paid money for. If linux used a sort of kernel for libs, the lib kernel could still point to the proper lib.

---

### Post by eragon100 on 2008-04-29
There is no problem with the libs! It runs in opengl mode just to slow to play because I have a GeForce and not a voodoo! I just need to make it think my display is running in 16 bit mode, that's all!

---

### Post by wingnux on 2008-04-29
The "invalid game folder" error is related to the SERVER you're trying to connect to and not to you (the client). It means the server is using another (older, in this case) version of OpenArena. You won't get this error when connecting to 0.7.6 servers ;)

---

### Post by eragon100 on 2008-04-29
ok, thanx for the info. Now I want heretic2 working. I want to cast fireballs :lolflag:

---

### Post by eragon100 on 2008-04-29
anyone knows of a glide wrapper (or ANY other voodoo card emulator(s)) running with geforce cards under linux ?

---

### Post by eragon100 on 2008-04-29
I am stupid :lolflag: I just wasted an entire day:lolflag:

Simple and not dangerous:

1. download an ancient linux distro which can only support 16-bit color from around 2000 from doest-matter-where-on the web.

2. Install said dinosaur in virtualbox

3. Install heretic 2 in virtualbox in ancient distro

4. Play :lolflag:

Anyone having any idea where I can get an ancient linux release (say a redhat from 1999-2000 or something) :popcorn:

---

### Post by wingnux on 2008-04-29
Have you tried using the Win32 build? It works flawlessly with wine.

---

### Post by Vadi on 2008-04-29
You can always use the "contact us" link on the left side of getdeb.net to ask for a .deb

At least that's what I do and it works

---

### Post by eragon100 on 2008-04-30
I have already contacted getdeb. They will try to release before the end of the week. :)

---

### Post by eragon100 on 2008-04-30
Heretic 2 is working now, inside a ubuntu 7.10 virtual machine with 8 mb of video memory and with default xdepth in /etc/X11/xorg.conf set to 16 :)

It runs fine, just one more question: How do I get the keyboard to perform properly? It's very "shocky" (sorry I don't know how to say it in good english :lolflag:)

---

### Post by eragon100 on 2008-04-30
I solved the problem with the keyboard, Heretic 2 is now working 100 % perfect :) :) :) Very fun game (especcially slashing enemies with the cool fighting staf, one of its ends is a blade :) )

BTW, I also found the very old heretic 1 for dos on an abandonware site, and it runs perfectly under DOSbox (but wat doesn't) with sound and everything :)

So I have got both the heretic games to play, and I have also discovered that my problem with openarena is indeed server-sided, since there are some servers I can join.

Good day!

Now how do I mark this thread as solved, with the upgraded forum :lolflag: :confused:

---

### Post by Perfect Storm on 2008-04-30
Can you post how you solved the keyboard thing, so people with the same problem can benefit from it, thanks :KS

In exchange I'll mark the thread solved ;)

---

### Post by eragon100 on 2008-04-30
By going to system -> preferences -> keyboard and disabling the "Key presses repeat etc" option in both the real and the virtual installation.

I have also discovered how to get the mouse to move normally (it's 10 times too fast when you first start heretic2): go to system -> preferences -> mouse and bring both the sensivity and the acceleration WAY down (almost to minumum) in both the real and the virtual installation. This will make your mouse move very slowly in Ubuntu, but it will give you a normal speed in heretic 2.

Offcourse, you will have to restore both these settings to normal when you want to play another game (or do something useful if it's that time of year again :lolflag:), because Ubuntu is pretty unusable whit them.

I have posted the required steps to get heretic2 running in the heretic 2 thread under 3rd party projects -> ubuntu gamer's arena -> specific games, because I wasn't the only one who couldn't get it running first.

Now I will just wait for people to press the "thanx" button :lolflag:

And for you to mark this thread solved, offcourse :KS

---

### Post by Perfect Storm on 2008-04-30
Done. :guitar:

---

### Post by mcurtiss1970 on 2008-05-05
> **eragon100 said:**
> I have already contacted getdeb. They will try to release before the end of the week. :)


it's out: [http://www.getdeb.net/app/OpenArena](http://www.getdeb.net/app/OpenArena)

---

