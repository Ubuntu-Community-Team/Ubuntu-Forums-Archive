---
title: "Compiling OpenGL renderer for native Unreal Tournament?"
date: 2010-04-10
forum: Gaming &amp; Leisure
---

### Post by quadomatic on 2010-04-10
So, there's been an updated OpenGL renderer for Unreal Tournament for some time now. However, it's never been compiled for linux.

The source code is available:

[http://www.cwdohnal.com/utglr/utglr36src.zip](http://www.cwdohnal.com/utglr/utglr36src.zip)

Instructions on the page say to email him at [email]smpdev@cwdohnal.com[/email] if someone wants to try compiling it for Linux, as well as this:

> 
I never seem to hear any good news about attempts to build the updated renderer on Linux. Unfortunately, I can only provide limited help in this area. I do try to keep the code cross platform friendly, but it's unlikely that I will be able to attempt to build it on other platforms anytime in the near future. I know the current code won't compile as is with gcc, but I expect that only minor syntax fixups and basic non-essential feature removal will be able to make the updates I added both compile cleanly and work correctly.

The first major step in attempting to build the updated renderer on Linux is to make sure you can build the original renderer code before I added any updates to it. This will ensure that there are not any major existing issues before going forward and attempting to use the new code. If any problems are encountered in this stage, it's not really anything I can help with much because I don't have a local build environment for this platform, didn't write this code, etc. If there's some problem like maybe the ut432 header files don't quite match the current Linux version of UT and cause problems because of this, that falls into the I didn't break it and I can't fix it category.

You'll need to use a compatible version of gcc. Unfortunately, ABI changes mean you will almost certainly not be able to use a newer version of gcc (unless the rest of the game were compiled with it of course).

You can easily ifdef out the SSE code I added because whatever compiler you use probably won't support it. This is not a major loss since the SSE code I added only provides very minor speedups.

There's a chance there will be problems with the sstream code I used for the debug stream when using an older gcc and/or older libraries. Although it requires numerous changes to remove it, this code is non-essential, and the changes should be simple.

There are good reasons to try to get an updated renderer working on Linux if running UT natively here. Besides just being very obsolete at this point, the original OpenGL renderer code does contain a couple of more major design/implementation issues that would be good to have fixed.

Anybody up to this?

---

### Post by YavkatA on 2011-08-15
Sounds interesting.. I have done some preliminary research, and it seems like the easiest way to do this is to convert the visual studio project file (.vcproj) to a makefile. There is a tool called sln2mak that is suppoed to be able to do this, but it's written in C# (.NET). The other option is to do the vcproj-makefile conversion manually, but I am not that familiar with GCC...

---

### Post by disabledaccount on 2011-08-17
I just want to say that every UT up to 2K4 works just blazingly fast in wine, so I see no reason for compiling new renderer for native version - unless for educational purposes..
F.e. in the mentioned UT v4.36 (UT99 GOTY) I get typically around 150-250fps using directX renderer on ATI HD 5670, and the worse result I've ever seen is around 40-50fps with everything maxed, huge map and with 20+ active players/bots during heavy fight :)

Besides, there are ready to use dlls, so it's possible to first check the binaries in wine.

---

### Post by Dlambert on 2011-08-19
Yeah, maybe a renderer for UT3, but not the games that run excellent on wine.

---

