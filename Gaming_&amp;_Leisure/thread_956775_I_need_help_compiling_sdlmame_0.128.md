---
title: "I need help compiling sdlmame 0.128"
date: 2008-10-23
forum: Gaming &amp; Leisure
---

### Post by Moonfrost on 2008-10-23
I'm trying to compile sdlmame 0.128 (latest version) but I run into errors all the time (ahem...I always run into errors when trying to compile something!). Here's what happens:

There is a text file that doesn't really offer any help of how to compile it except that it tells you to use PTR64=1 for 64bit compiling (I'm using 64bit architecture) but otherwise it doesn't explain anything at all, there is a makefile but no config file which means it's one of those programs which probably only need the make and make install commands.

I cd'ed into the directory I have sdlmame for now which is:

```
/home/moonfrost/Desktop/sdlmame/sdlmame0128/
```

I then tried typing make PTR64=1 which gives me quite a lot of errors...

```
moonfrost@moonfrost-desktop:~/Desktop/sdlmame/sdlmame0128$ make PTR64=1
makefile:477: src/osd/sdl/sdl.mak: No such file or directory
makefile:480: src/mame/mame.mak: No such file or directory
makefile:481: src/emu/emu.mak: No such file or directory
makefile:482: src/lib/lib.mak: No such file or directory
makefile:483: src/build/build.mak: No such file or directory
makefile:485: src/tools/tools.mak: No such file or directory
make: *** No rule to make target `src/tools/tools.mak'.  Stop.
moonfrost@moonfrost-desktop:~/Desktop/sdlmame/sdlmame0128$
```

Typing only "make" gives me the exact same error, by the way I DO have the required SDL libraries (including the one -dev for compiling sdl apps/programs).

---

### Post by disturbedite on 2008-10-23
did you read this?:
[http://www.bannister.org/forums/ubbthreads.php?ubb=showflat&Number=35138#Post35138](http://www.bannister.org/forums/ubbthreads.php?ubb=showflat&Number=35138#Post35138)

---

### Post by Moonfrost on 2008-10-23
> **disturbedite said:**
> did you read this?:
[http://www.bannister.org/forums/ubbthreads.php?ubb=showflat&Number=35138#Post35138](http://www.bannister.org/forums/ubbthreads.php?ubb=showflat&Number=35138#Post35138)

Yeah...but those are just instructions for the required libraries and such...don't think you can install that way, besides this version of SDLmame is not on the repos at all.

---

### Post by FranMichaels on 2008-10-23
You have to put that value in the make file...

It's self explanatory, just try 

```
gedit /home/moonfrost/Desktop/sdlmame/sdlmame0128/makefile
```

> # uncomment next line if you are building for a 64-bit target
# PTR64 = 1

Just remove the # before PTR64 to uncomment.
It must look like this:
> # uncomment next line if you are building for a 64-bit target
 PTR64 = 1

Save. After that

```
make -f makefile
```

---

### Post by Moonfrost on 2008-10-23
> **FranMichaels said:**
> You have to put that value in the make file...

It's self explanatory, just try 

```
gedit /home/moonfrost/Desktop/sdlmame/sdlmame0128/makefile
```



Just remove the # before PTR64 to un-comment.

After that

make -f makefile

Can I use kate instead? I'm using KDE

---

### Post by wingnux on 2008-10-23
Any text editor is just fine.

---

### Post by Moonfrost on 2008-10-25
> **FranMichaels said:**
> You have to put that value in the make file...

It's self explanatory, just try 

```
gedit /home/moonfrost/Desktop/sdlmame/sdlmame0128/makefile
```



Just remove the # before PTR64 to uncomment.
It must look like this:


Save. After that

```
make -f makefile
```


After doing that, saving and typing make -f makefile I still get the same error every time I tried compiling using make PTR64=1:

```
makefile:477: src/osd/sdl/sdl.mak: No such file or directory
makefile:480: src/mame/mame.mak: No such file or directory
makefile:481: src/emu/emu.mak: No such file or directory
makefile:482: src/lib/lib.mak: No such file or directory
makefile:483: src/build/build.mak: No such file or directory
makefile:485: src/tools/tools.mak: No such file or directory
make: *** No rule to make target `src/tools/tools.mak'.  Stop.
```

I have all the dependencies already and I'm sure. Those files it's looking for are not there at all, I checked on the folder pointed at on the terminal and they are empty.

I'm trying to compile sdlmame 0.128u1 if that matters.

EDIT: I found accidentally a site which has the latest mame releases on .deb packages:) the site is updated regularly and has both 32 *and* 64bit, it also has the latest version of sdlmame tools and a few other things, great site:

Here's the link [http://wallyweek.altervista.org/rel128u1.php]("http://wallyweek.altervista.org/rel128u1.php")

This site

---

### Post by swann on 2008-11-01
the Sdlmame Ubuntu package doesn't work on intrepid ibex (games run at 50% speed), and Wallyweek (the maintaner) won't compile the new packages. 
[http://www.bannister.org/forums/ubbthreads.php?ubb=showflat&Number=40909&page=5](http://www.bannister.org/forums/ubbthreads.php?ubb=showflat&Number=40909&page=5)

so, any help to compile Sdlmame for the new release 8.10 would be greatly appreciated, sorry for my poor English and thanks in advance.

---

### Post by Moonfrost on 2008-11-01
I gave up on this, I'm back using Windows for Mame and other emulators again...it's better left like that for now, someday things will be better.

---

### Post by BigSilly on 2008-11-02
It already is. MAME packages for Ubuntu are kept well up to date regularly [here.]("http://wallyweek.altervista.org/") Silly going back to Windows for emulators!

---

### Post by swann on 2008-11-02
MAME packages for ubuntu WERE well kept there. see my link two posts above. great sadness.

---

### Post by BigSilly on 2008-11-02
> **swann said:**
> MAME packages for ubuntu WERE well kept there. see my link two posts above. great sadness.

Apologies. Missed that. 

Have you tried to install the Hardy .deb? That'll probably be OK in truth. I'm surprised to hear that Carlos will no longer be maintaining this though. It's a real shame.

---

### Post by swann on 2008-11-02
the Hardy .deb runs very slowly, or better it doesn't run at all. I tried setting in mame.ini VIDEO OPTIONS video=soft: games run a little faster, but the graphic aspect is awful. so, it could be an opengl problem, but my knowledge stops here.

---

### Post by BigSilly on 2008-11-02
That's pretty bizarre, even for an older .deb. I'm currently using a Gutsy built .deb of SDLMame 0.120a, simply because I've no wish to update just yet, and that runs absolutely great. 

Your graphics drivers are all installed OK yeah? I'm sure someone else posted a similar issue to yours some time ago, and they hadn't set up their NVidia driver properly. Sorry, but that's about all I can offer. :(

---

### Post by swann on 2008-11-02
Anyway, thanks. I think my drivers are ok: they always worked fine in the past. I've the old classic intel 915, and I use the drivers coming with intrepid ibex (i810). Only with MAME gives me problems: films and other applications work. I will search through the forum and keep trying with mame.ini and opengl functions.

---

### Post by Moonfrost on 2008-11-02
> **BigSilly said:**
> It already is. MAME packages for Ubuntu are kept well up to date regularly [here.]("http://wallyweek.altervista.org/") Silly going back to Windows for emulators!

I know, but I still use Linux for everything else...

By the way I had that package and it worked perfectly but there were some settings I wanted to change and I needed a frontend for that, besides, Intrepid Ibex doesn't detect my Logitech Dual Action which Hardy did detect without problems.

---

### Post by swann on 2008-11-02
So sdlmame by wallyweek works for you on intrepid ibex? It's important to me to understand which is the problem of mine.
As frontend I use qmc2, and it works great even with my Logitech dual action..

---

### Post by Calculon64 on 2008-11-08
> **Moonfrost said:**
> I gave up on this, I'm back using Windows for Mame and other emulators again...it's better left like that for now, someday things will be better.

I did the same thing a few times I try Ubuntu and just found my self back on Windows for emulation. But now that there are Ubuntu SDL MAME builds, there is no reason for me to ever go back :)

---

### Post by etlpkby on 2009-01-05
I've managed to get this working. \\:D/

I'm running on 8.10 (Intrepid) and 64bit (AMD64 CPU etc). Firstly I downloaded 'sdlmame' version 0.129 release, which came out **TODAY**..wow :)

Read about it here (with a link to download it):-
[http://www.bannister.org/forums/ubbthreads.php?ubb=showflat&Number=47196&gonew=1#UNREAD]("http://www.bannister.org/forums/ubbthreads.php?ubb=showflat&Number=47196&gonew=1#UNREAD")

I followed the compilation steps listed here:-
[http://www.bannister.org/forums/ubbthreads.php?ubb=showflat&Number=35138&page=2]("http://www.bannister.org/forums/ubbthreads.php?ubb=showflat&Number=35138&page=2")

Since I'm on 64bit OS, I did change makefile for "PTR64=1" and I did install gcc4.2 and use that version (and assembler) NOT 4.3. I **did** get a segmentation fault with 'as' during my build with 4.3 - I recommend you avoid and use 4.2 as per the 'sticky' on the forum.

Once built, I was left with 'mame' binary in my /usr/local/src/sdlmame0129 area. There's no 'install' target on the makefile, so I just did
```

cd /usr/local/bin; sudo ln -s ../src/sdlmame0129/mame
```

Tried to get ROMs to work with it. That did not work :( It appears you need to tell mame about the rompath

```
mame -rompath $HOME/.mame/roms kungfum
```

That picked up my Kung Fu Master ROM in my $HOME/.mame/roms area fine. Alter your rompath accordingly. The video resolution is POOR. The default build does not use 'opengl' for video, just the soft default.

So I dumped out a config file, thus

```
mame -createconfig
```

..to create 'mame.ini'. Edit it and firstly alter the 'rompath' to your rom area, thus you don't need to add '-rompath <path>' on cmdline. Scroll down to

```
#
# VIDEO OPTIONS
#
video                     opengl
```

Make sure video is set to 'opengl'. Put mame.ini in your ***$HOME/.mame*** area.Now this works as per the stock 'sdlmame' from synaptic (version 0.122), except I'm on latest 0.129 - which should be able to use laserdisc (.CHD files)

**Sorted** ;)

Patrick/

---

### Post by anon0 on 2009-02-14
> **etlpkby said:**
> I've managed to get this working. \\:D/

That's great... but can someone explain to newbies what the following step means? I got up to compiling the mame binary but it's placed under /usr/local/bin/ and my source files are elsewhere.
> ```

cd /usr/local/bin; sudo ln -s ../src/sdlmame0129/mame
```

> Tried to get ROMs to work with it. That did not work :( It appears you need to tell mame about the rompath

```
mame -rompath $HOME/.mame/roms kungfum
```

Why do you have to add "kungfum" if all your roms are under "$HOME/.mame/roms"?

---

### Post by litemirrors on 2010-02-19
So on his website [http://sdlmame.wallyweek.org/](http://sdlmame.wallyweek.org/) he says

"SDLMAME is no more, let's move to the unified source!"

Does this mean SDLMAME is dead? What happens to QMC2 then?

And someone explain why the PPA here

[https://launchpad.net/~mmbossoni-gmail/+archive/emu](https://launchpad.net/~mmbossoni-gmail/+archive/emu)

Doesn't actually work?! I'm on Ubuntu 9.10 and even though Synaptic shows sdlmame and QMC2 as being installed through this repository I still find it runs nothing, it merely shows the opening dialog and nothing happens afterward :?

I find this very odd..... is SDLMAME dead?

---

