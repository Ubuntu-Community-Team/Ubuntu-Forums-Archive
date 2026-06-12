---
title: "What to download and how to install S.C.O.U.R.G.E."
date: 2008-10-22
forum: Gaming &amp; Leisure
---

### Post by Arukas on 2008-10-22
I read other scourge post and I still don't understand.

Which files am I suppose to download.  All I know is they aren't deb files so its not an easy install.  

Then what am I suppose to do with the files once I download them?

I don't follow the post of read, and found many broken links.  

Thanks,
Arukas

---

### Post by Perfect Storm on 2008-10-23
[http://gaming.gwos.org/doku.php/guides:64bit:scourge](http://gaming.gwos.org/doku.php/guides:64bit:scourge)

scourge-0.20.data.tar.gz (data)

and 

scourge-0.20.src.tar.gz (source codes)

---

### Post by Arukas on 2008-10-23
I have another question, its about the guide.  And it didn't install correctly.

I follow the commands.  The one for install the correct libs, says everything was update.

but when I get to the step that says enter

scon

I get this

:: Checking for libs
Checking for SDL_Init(SDL_INIT_VIDEO) in C library SDL... yes
Checking for Mix_CloseAudio() in C library SDL_mixer... yes
Checking for SDLNet_Quit() in C library SDL_net... yes
Checking for TTF_Init() in C library SDL_ttf... yes
Checking for IMG_GetError() in C library SDL_image... no
Did not find libSDL_image, exiting!


I'm thinking the "did not find" means something is wrong, or then again I don't know.  Can anyone shed some light in the right direction?

---

### Post by Perfect Storm on 2008-10-23
> Checking for IMG_GetError() in C library SDL_image... no
Did not find libSDL_image, exiting!

install libsdl_image the -dev package.

---

### Post by Arukas on 2008-10-24
How do I do that?  I thought that what the first commands did.  I try my adding the lib to the command lines but it says it can't find the lib.

---

### Post by Perfect Storm on 2008-10-24
You can search synaptic Package Manager for libsdl - there should be one that called libsdl-image1.2-dev


or

```
sudo apt-get install libsdl-image1.2-dev
```

---

### Post by neigun on 2009-12-13
Has anyone managed to compile this successfully for 9.10 64 bit? And if so, could they post the details please.

Neil

---

### Post by Duskao on 2009-12-13
You can also try djl, and install it with that. [http://en.djl-linux.org/](http://en.djl-linux.org/) Makes it rather simple, plus there are 120 other games you can do the same with. Have fun.

---

### Post by neigun on 2009-12-15
> **neigun said:**
> Has anyone managed to compile this successfully for 9.10 64 bit? And if so, could they post the details please.

Neil

Hi Guys

Artificial Intelligence's guide for compiling S.C.O.U.R.G.E. works for 9.10 64 bit as well.

See:[http://gwos.org/doku.php/guides:64bit:scourge](http://gwos.org/doku.php/guides:64bit:scourge)

djl has a good range of games in its repository too.

Neil

---

### Post by Melcar on 2009-12-15
I have it working on Karmic 64bit with no problems.  Just installed the dependencies outlined in the [gaming guide]("http://gwos.org/doku.php/guides:64bit:scourge") , download both the source and data files, extract them both (move the data folder into the source one), cd into the source folder, and do:

```
./configure
scons
```

Install it if you want with scons install, but it runs just fine without that step.

---

### Post by benleedy on 2010-01-06
I followed the instructions here:

[http://gwos.org/doku.php/guides:64bit:scourge](http://gwos.org/doku.php/guides:64bit:scourge)

Now I get the following error:

Could not launch 'Scourge'
Failed to execute child process
"scourge" no such file or directory

---

### Post by Toadmund on 2010-10-30
I am trying to try out S.c.o.u.r.g.e. , but when the game wants me to input character details the only button that does not work is the 'accept' button.

Therefore I cannot play.

I am using 10.04, scourge v.0.21.

---

### Post by Xcursion666 on 2010-12-13
i installed the game but it wont load 
when i try to run it in terminal i get this error
robert@laptop:~$ scourge
Constructing root path:
    not using binreloc...
    temp rootDir=/usr/share/scourge
*** Can't find local version of data dir. You're running a distribution.
Looking for localized resources in: /usr/share/scourge/translations
Starting session. Final rootDir=/usr/share/scourge
Setting video mode: 1024x768x32
Video mode set failed: No video mode large enough for 1024x768
Segmentation fault
:-k anybody else get this error
i installed the game and data packages both were rpms converted using alien

---

### Post by Cyrian on 2011-04-16
I want to install SCOURGE as well, however I am using the Natty 11.04 beta.  Any suggestions, or should I drop all attempts?

---

### Post by brothergrok on 2011-12-01
I downloaded the data and the src files, attempted to install via terminal using the cd, ./configure, make, etc commands, and it doesn't seem to be working out for me. The make commands don't appear to be working, and the direction in the INSTALL don't seem to work either. 

I am currently using 11.10 ubuntu.

---

### Post by Perfect Storm on 2011-12-02
> **brothergrok said:**
> I downloaded the data and the src files, attempted to install via terminal using the cd, ./configure, make, etc commands, and it doesn't seem to be working out for me. The make commands don't appear to be working, and the direction in the INSTALL don't seem to work either. 

I am currently using 11.10 ubuntu.

[http://www.playdeb.net/updates/ubuntu/11.10/?q=scourge](http://www.playdeb.net/updates/ubuntu/11.10/?q=scourge)


Old thread. Thread closed.

---

