---
title: "Holy moly, Toribash is free again?!"
date: 2008-05-16
forum: Gaming &amp; Leisure
---

### Post by Mr. Picklesworth on 2008-05-16
AND it has a native Linux version with an Apt repository and a proper .desktop file!
I had ended up ignoring this game a while ago when it had a price tag added. Today, I was reminded of it and started suffering withdrawal symptoms; I knew something had to be done when I started trying to throw my own head at people. I was just about to go back and pay for the full version when I discovered that the client is free again! They seem to have devised a much nicer profit model, with a little pay-for-perks system.

I now dearly hope [Toribash]("www.toribash.com") finds its way into Ubuntu's partner repo :)
Really, really cool game...

Edit:
Why the heck did I write that it's open source? It isn't. Sorry about that.

---

### Post by Vadi on 2008-05-16
edit, nvm

---

### Post by Tiftof on 2008-05-17
thanks for the heads up! I remember seeing it on youtube some months ago but totally forgot about it. Thanks for bringing it up. I'm going to try it in a moment :)

edit: hmmm, it seems to think my keyboard is qwerty and I don't see any option to change that. Common problem?

---

### Post by Sockerdrickan on 2008-05-17
That's a weird game.

---

### Post by Perfect Storm on 2008-05-17
> **Tux0r said:**
> That's a weird game.

Indeed, I havn't seen any like it. Very unique.
Though it's not my kind of game.

I'll just remove open source from the title.

---

### Post by kesman on 2008-06-24
Bringin this UP, since the game is so awesome =D
Wonder when there'll be an option to host a server on your own computer...

---

### Post by MaximB on 2008-06-24
The game is free (beer) mainly because Toribash 2 came out.
This game could be so much better if it were more serious, I mean something like Tekken or so ... but those models are so basic that even I can do them.

I like the blood and gore part ;)

---

### Post by kesman on 2008-06-25
I highly disagree with adding "characters" to the game, since it would make the fighters uneven, and so ruin the idea of the game. I personally hate it when something as great as this simple but fantastic game would turn into performance-eating monster with loads of useless junk in it. If you play well enough, and invest some money, you can customize your character to your likes, and doing so, support the developers.

Atm the game runs smoothly with my laptop, processor speed scaled down to 800mhz and radeon mobility x700, not causing the laptop to even heat, which is lovely.

---

### Post by ShodanjoDM on 2008-06-25
I love it. It's one of the games that I rated highly along with phun, stormbaan coureur and schorched3d.

Definitely unsuitable for children though.

---

### Post by myromance123 on 2008-06-25
Holy cow ~ This is one weird but innovative game. With this kinda game, who knows how many cool new moves could be added to fighting games for pcs and consoles like tekken and such :D 
  
 ~:guitar:

---

### Post by kesman on 2008-06-25
It would be awesome to see a mod with three or more fighters fighting at a time =D Personally, I don't like the mods with stuff in them, I mean swords and sabers and stuff. Jousting sucks too :F On the other side, GREAT game :P

---

### Post by kesman on 2008-07-29
Bringing this UP since the game is so great.
It's a shame that the developers or someone else is being lazy at their end, since the windows version has gone up to 3.32, but there's no release notes for it in the wiki, the latest version they have described in the wiki is 3.2, the same that the linux version is stuck in.

There's problems when playing against windows users, since to me it seems that the communication between two different versions of this game is troublematic. Many chat messages aren't shown, many special mods don't work and there's glitches and jumps in the game that make playing impossible.

Now what would be great, is that someone with enough awesome power would read this and do something about it =D The version in the repositories MUST be updated, or there should be a way to play the newest version of the game on linux some other way.

Cheers!

---

### Post by Mr. Picklesworth on 2008-07-29
Well, the Windows version does work in Wine since it's OpenGL. (As a rule of thumb, anything not done with DirectX will work well, often at good speed). It'd be nice to see that repo getting an update, though, considering that's the entire point of hosting one :/

---

### Post by jimi_hendrix on 2008-07-29
i watched the trailer...it seemed there was no such thing as blocks and every move ended in severd limbs and decapitations

---

### Post by Orlsend on 2008-07-29
> **MaximB said:**
> The game is free (beer) mainly because Toribash 2 came out.
This game could be so much better if it were more serious, I mean something like Tekken or so ... but those models are so basic that even I can do them.

I like the blood and gore part ;)
Yeah the Idea of the Game would be runined.

Toribash is awesome, Idint think they had a Linux version....

---

### Post by anotherconfused1 on 2008-07-29
When I click the link, it says my IP has been banned, yet I have never gone to the site before, and when I click contact the admin, it says there is no such thing? What the heck?

---

### Post by kesman on 2008-07-29
Try the forums, and irc on asia.toribash.com and channel #toribash ,maybe they can help you.

---

### Post by jimi_hendrix on 2008-07-29
downloaded it

dont know how to install it

the instructions on how to do the sudo apt-get install confused me

---

### Post by kesman on 2008-07-30
> **jimi_hendrix said:**
> downloaded it

dont know how to install it

the instructions on how to do the sudo apt-get install confused me

Just add the lines starting with deb and deb-src to your sources.list -file in /etc/apt
then run
```

sudo apt-get update
sudo apt-get install toribash

```

---

### Post by Mr. Picklesworth on 2008-07-30
> Just add the lines starting with deb and deb-src to your sources.list -file in /etc/apt*Shudder*
Don't do that! Go to System -> Administration -> Software Sources (or Software Sources in Synaptic), flip to Third Party Software, click Add and paste the "deb ..." line they give you.
(Hmm, that process definitely should be more discoverable).

---

### Post by lkirlin on 2008-07-30
This is a great game, however it causes my computer to freeze completely or log me out:confused:. running on 2 gb of ram with an intel dual core E6300. One would think that you could run such a simple game with such hardware without a problem, but thats not the case. Anyone have any ideas on what is causing it?

---

### Post by kesman on 2008-07-31
> **lkirlin said:**
> This is a great game, however it causes my computer to freeze completely or log me out:confused:. running on 2 gb of ram with an intel dual core E6300. One would think that you could run such a simple game with such hardware without a problem, but thats not the case. Anyone have any ideas on what is causing it?

Have you enabled the shaders? Try running the game from terminal to see if there's any error output during the freeze. Also, have you correctly installed your graphics drivers?

---

### Post by kesman on 2008-07-31
> **Mr. Picklesworth said:**
> *Shudder*
Don't do that! Go to System -> Administration -> Software Sources (or Software Sources in Synaptic), flip to Third Party Software, click Add and paste the "deb ..." line they give you.
(Hmm, that process definitely should be more discoverable).

What's wrong with adding the lines manually to the list? Of course, the Software Sources -application may check the lines for errors and typos, but it shouldn't be such a big deal to correct them by yourself too if apt-get update fails.

---

### Post by PC_load_letter on 2008-08-03
I'm having a problem running it under Feisty (7.04) amd64. I installed it from the amd64 deb package from the web site. When I run it from terminal I get this error.
```
/usr/games/toribash.bin: error while loading shared libraries: libglut.so.3: cannot open shared object file: No such file or directory

```

I then did the following, which did nothing as I kept getting the same error:
```
sudo ln -s /usr/lib/libglut.so.3.8.0  libglut.so.3

```

The symbolic link has been created but here is the weird part:
(1) It doesn't show up when I do a search.
(2) when I do an ls from the /usr/games directory it shows up in a cyan color.

Worth mentioning is that there is another identical (i.e. same name & target) symbolic link but in another folder, is it relevant?

---

### Post by PC_load_letter on 2008-08-03
Ok, so I ran```
/usr/games$ ldd toribash.bin
``` and I got the following: 

```

        linux-gate.so.1 =>  (0xffffe000)
        libSDL-1.2.so.0 => /usr/lib32/libSDL-1.2.so.0 (0xf7e5c000)
        libSDL_mixer-1.2.so.0 => /usr/lib32/libSDL_mixer-1.2.so.0 (0xf7dee000)
        libglut.so.3 => not found
        libSDL_ttf-2.0.so.0 => not found
        libstdc++.so.6 => /usr/lib32/libstdc++.so.6 (0xf7d03000)
        libm.so.6 => /lib32/libm.so.6 (0xf7cdc000)
        libgcc_s.so.1 => /usr/lib32/libgcc_s.so.1 (0xf7cd0000)
        libc.so.6 => /lib32/libc.so.6 (0xf7b8e000)
        libdl.so.2 => /lib32/libdl.so.2 (0xf7b8a000)
        libpthread.so.0 => /lib32/libpthread.so.0 (0xf7b73000)
        libGL.so.1 => /usr/lib32/libGL.so.1 (0xf7b13000)
        libGLU.so.1 => /usr/lib32/libGLU.so.1 (0xf7a93000)
        libasound.so.2 => /usr/lib32/libasound.so.2 (0xf79ce000)
        libdirectfb-0.9.so.25 => /usr/lib32/libdirectfb-0.9.so.25 (0xf7976000)
        libfusion-0.9.so.25 => /usr/lib32/libfusion-0.9.so.25 (0xf7970000)
        libdirect-0.9.so.25 => /usr/lib32/libdirect-0.9.so.25 (0xf7961000)
        /lib/ld-linux.so.2 (0xf7f0a000)
        libvorbisfile.so.3 => not found
        libvorbis.so.0 => not found
        libogg.so.0 => not found
        libsmpeg-0.4.so.0 => not found
        libX11.so.6 => /usr/lib32/libX11.so.6 (0xf786f000)
        libXext.so.6 => /usr/lib32/libXext.so.6 (0xf7861000)
        libXxf86vm.so.1 => /usr/lib32/libXxf86vm.so.1 (0xf785c000)
        libdrm.so.2 => /usr/lib32/libdrm.so.2 (0xf7852000)
        libXau.so.6 => /usr/lib32/libXau.so.6 (0xf784f000)
        libXdmcp.so.6 => /usr/lib32/libXdmcp.so.6 (0xf784a000)

```
The problem is I DO have all the missing libraries, so do I just need to symbolic link them? In which directory should I put the symbolic links?

Thanks.

---

### Post by kesman on 2008-08-04
[http://forum.toribash.com/showthread.php?t=34478&page=16](http://forum.toribash.com/showthread.php?t=34478&page=16)

YEAH! There's still light at the end of the tunnel \o/.

For those who don't dare to open the link, they are actually compiling binaries of 3.4 for linux right now.

---

### Post by Perfect Storm on 2008-08-04
> **PC_load_letter said:**
> Ok, so I ran```
/usr/games$ ldd toribash.bin
``` and I got the following: 

```

        linux-gate.so.1 =>  (0xffffe000)
        libSDL-1.2.so.0 => /usr/lib32/libSDL-1.2.so.0 (0xf7e5c000)
        libSDL_mixer-1.2.so.0 => /usr/lib32/libSDL_mixer-1.2.so.0 (0xf7dee000)
        libglut.so.3 => not found
        libSDL_ttf-2.0.so.0 => not found
        libstdc++.so.6 => /usr/lib32/libstdc++.so.6 (0xf7d03000)
        libm.so.6 => /lib32/libm.so.6 (0xf7cdc000)
        libgcc_s.so.1 => /usr/lib32/libgcc_s.so.1 (0xf7cd0000)
        libc.so.6 => /lib32/libc.so.6 (0xf7b8e000)
        libdl.so.2 => /lib32/libdl.so.2 (0xf7b8a000)
        libpthread.so.0 => /lib32/libpthread.so.0 (0xf7b73000)
        libGL.so.1 => /usr/lib32/libGL.so.1 (0xf7b13000)
        libGLU.so.1 => /usr/lib32/libGLU.so.1 (0xf7a93000)
        libasound.so.2 => /usr/lib32/libasound.so.2 (0xf79ce000)
        libdirectfb-0.9.so.25 => /usr/lib32/libdirectfb-0.9.so.25 (0xf7976000)
        libfusion-0.9.so.25 => /usr/lib32/libfusion-0.9.so.25 (0xf7970000)
        libdirect-0.9.so.25 => /usr/lib32/libdirect-0.9.so.25 (0xf7961000)
        /lib/ld-linux.so.2 (0xf7f0a000)
        libvorbisfile.so.3 => not found
        libvorbis.so.0 => not found
        libogg.so.0 => not found
        libsmpeg-0.4.so.0 => not found
        libX11.so.6 => /usr/lib32/libX11.so.6 (0xf786f000)
        libXext.so.6 => /usr/lib32/libXext.so.6 (0xf7861000)
        libXxf86vm.so.1 => /usr/lib32/libXxf86vm.so.1 (0xf785c000)
        libdrm.so.2 => /usr/lib32/libdrm.so.2 (0xf7852000)
        libXau.so.6 => /usr/lib32/libXau.so.6 (0xf784f000)
        libXdmcp.so.6 => /usr/lib32/libXdmcp.so.6 (0xf784a000)

```
The problem is I DO have all the missing libraries, so do I just need to symbolic link them? In which directory should I put the symbolic links?

Thanks.

I can see you use 64-bit version of Ubuntu and Toribash is 32-bit binary. What you do is use a program called getdeb (a search on our 64-bit forum). Via GetDeb install the 32-bit libs, thereafter make symblink if needed.

---

### Post by PC_load_letter on 2008-08-04
I did install the amd64 deb from the toribash web site, here:
[https://redmoonstudios.org/~aszlig/toribash/debian/](https://redmoonstudios.org/~aszlig/toribash/debian/)

---

### Post by Perfect Storm on 2008-08-04
It's not compiled/build with 64-bit libs, it requires 32-bit libs. You can see from the list that they are pointing to lib32

---

### Post by kesman on 2008-08-05
Damn I hate the developer's way of NOT to tell people what's going on. There's been NO information of the delay of releasing the Linux port of the newest version of the game. Yes I know that Linux users are a small minority in the whole gaming population, but sure they ought to release new versions for all platforms at once :F
FFS

---

### Post by kesman on 2008-08-05
What does this have to do with Toribash, if I may ask?

---

### Post by Perfect Storm on 2008-08-05
> **kesman said:**
> What does this have to do with Toribash, if I may ask?

Nothing, it was a spammer, which are now terminated.

---

### Post by conorsulli on 2008-08-06
Thank you! never saw this game before!!! it look's good!

---

### Post by kesman on 2008-08-10
Heya!

So the updated version is now available trough the repository they provide on the download-section on the page, and it kicks *** so much! :D
There are minor bugs still laying around, but I've been in contact with the linux-developer of the game via IRC and he's working on them right now, so there's gonna be an update quite soon I guess.

---

### Post by kesman on 2008-08-19
Yeah allright, go to [http://linux.toribash.com](http://linux.toribash.com) and install the latest build, it rocks so hard! There still are some error messages shown when run on terminal, but the game itself works flawlessly. Dunno about the custom textures and shaders though, since I don't use them because I play just for fun :P

The private servers kick ***!

---

