---
title: "Advancemame and Advancemenu"
date: 2006-09-25
forum: Gaming &amp; Leisure
---

### Post by easy_target on 2006-09-25
Hi everybody,

I tried compiling advancemame and advancemenu for a long time now and finally I did it! (or did I?)
I used checkinstall to keep track of the packages and I had problems with one  conflicting with a similar file present in both packages. Nothing that a dpkg  i --force-all wouldn't do, right? Now when I try to run advancemenu it says It didn't find any working emulators (although I have xmame working?) and advancemame complains about the Kernel Framebuffer interface. 
On the other hand I tried to compile the newest svgalib and the only thing I got was the exposure of my compiling shortcomings.
Would ANYONE be so kind and give us arcade gamers some pointers or a how-to on how to deal with those or PRETTY PLEASE provide packages? 
Absolutely any help is appreciated.

Thanks!](*,)

---

### Post by easy_target on 2006-09-29
I guess nobody knows how to do that... :-k

---

### Post by easy_target on 2006-10-21
bump?

---

### Post by easy_target on 2006-10-21
bump-de-bump?

---

### Post by amacieli on 2006-11-27
So did you ever get this sorted?  I'm having a problem with fb: unsupported in x myself...  If you dig around the documentation that came with AdvanceMENU (should be somewhere in /docs on your hard disk) you'll see something that will help you set up AdvanceMENU.  There is a file called something like advance.rc sitting in /home/adam/.advance that needs lines saying "emulator" and "emulator_roms" - these tell AdvanceMENU where the emulator you want to use is located, as well as where the ROMs are located.  The documentation also says that advmenu can "auto-configure" if you run it in the same dir as your emulator.  Of course, I can't test that this is everything because... fb: unsupported in x....

---

### Post by Number6 on 2007-02-09
I'm using Edgy and I can compile Advancemame no problems but Advance menu fails to compile with the following errors:

advance/menu/emulator.h:44: error: extra qualification ‘emulator::’ on member ‘attrib_compile’
advance/menu/emulator.h:366: error: extra qualification ‘generic::’ on member ‘load_info’


Can anyone please shed some light on what this might mean?

Cheers

](*,)

---

### Post by theToolman on 2007-04-23
I have  compiled advancedMenu with Feisty Fawn; wasn't compiling until I tweaked a header as described on this page: 

[http://enzerink.net/peter/wiki/index.php?title=DebMAME#svaglib](http://enzerink.net/peter/wiki/index.php?title=DebMAME#svaglib)

I quote from that link:
[COLOR=Blue]
Download the advancemenu source code then change to advancemenu directory and configure the build process.

We need to fix a couple of bugs in an advancemenu header file along the way.[/COLOR] [INDENT][INDENT][FONT=Courier New][COLOR=Blue]
[/COLOR][/FONT][/INDENT][FONT=Courier New][COLOR=Lime] $ wget [http://prdownloads.sourceforge.net/advancemame/advancemenu-2.4.13.tar.gz?download](http://prdownloads.sourceforge.net/advancemame/advancemenu-2.4.13.tar.gz?download)[/COLOR][/FONT][COLOR=Lime]
[/COLOR][FONT=Courier New][COLOR=Lime] $ tar -xvf advancemenu-2.4.13.tar.gz[/COLOR][/FONT][COLOR=Lime]
[/COLOR][FONT=Courier New][COLOR=Lime] $ cp advancemenu-2.4.13/advance/menu/emulator.h advancemenu-2.4.13/advance/menu/emulator.h.orig[/COLOR][/FONT][COLOR=Lime]
[/COLOR][FONT=Courier New][COLOR=Lime] $ sed -e 's/emulator::attrib_compile/attrib_compile/g' < advancemenu-2.4.13/advance/menu/emulator.h.orig [/COLOR][/FONT][FONT=Courier New][COLOR=Lime]> advancemenu-2.4.13/advance/menu/emulator.h.p1[/COLOR][/FONT][COLOR=Lime]
[/COLOR][FONT=Courier New][COLOR=Lime] $ sed -e 's/generic::load_info/load_info/g' < advancemenu-2.4.13/advance/menu/emulator.h.p1 [/COLOR][/FONT][FONT=Courier New][COLOR=Lime]> advancemenu-2.4.13/advance/menu/emulator.h[/COLOR][/FONT][COLOR=Lime]
[/COLOR][FONT=Courier New][COLOR=Lime] $ cd advancemenu-2.4.13 ; ./configure --prefix=/usr[/COLOR][/FONT][COLOR=Lime]
[/COLOR][FONT=Courier New][COLOR=Lime] [/COLOR][/FONT][/INDENT][COLOR=Blue]At this point the configuration script will run and check whether optional libraries are available or not. At end of the process a summary of supported options is displayed which should match this:

[/COLOR] [INDENT][FONT=Courier New][COLOR=Lime] == Drivers/Libraries ==[/COLOR][/FONT][COLOR=Lime]
[/COLOR][FONT=Courier New][COLOR=Lime] Video : fb slang ncurses sdl[/COLOR][/FONT][COLOR=Lime]
[/COLOR][FONT=Courier New][COLOR=Lime] Sound : alsa oss sdl[/COLOR][/FONT][COLOR=Lime]
[/COLOR][FONT=Courier New][COLOR=Lime] Keyboard : sdl raw event[/COLOR][/FONT][COLOR=Lime]
[/COLOR][FONT=Courier New][COLOR=Lime] Joystick : sdl raw event[/COLOR][/FONT][COLOR=Lime]
[/COLOR][FONT=Courier New][COLOR=Lime] Mouse : sdl raw event[/COLOR][/FONT][COLOR=Lime]
[/COLOR][FONT=Courier New][COLOR=Lime] Misc : zlib expat pthread freetype2[/COLOR][/FONT][COLOR=Blue]
[/COLOR][/INDENT] [COLOR=Blue]
If the make options are the same you can now compile the advancemenu source code:

[/COLOR] [INDENT][FONT=Courier New][COLOR=Lime] $ make[/COLOR][/FONT][COLOR=Lime]
[/COLOR][/INDENT] [COLOR=Blue]
If the (lengthy) compilation completes successfully, the program and support files can be installed:

[/COLOR] [INDENT][FONT=Courier New][COLOR=Lime] $ sudo make install[/COLOR][/FONT][/INDENT]

---

### Post by Mega_Mike on 2008-03-03
I created .deb packages of AdvanceMenu 2.4.13 and AdvanceMame 0.106 for Ubuntu Gutsy.

[http://rapidshare.com/files/96721182/advancemenu_2.4.13-1_i386.deb.html](http://rapidshare.com/files/96721182/advancemenu_2.4.13-1_i386.deb.html)

[http://rapidshare.com/files/96721185/advancemame_0.106.0-1_i386.deb.html](http://rapidshare.com/files/96721185/advancemame_0.106.0-1_i386.deb.html)

---

### Post by jdsony on 2008-03-03
I think part of your problems is that advancemenu is supposed to be used with advancemame and not xmame.

Thanks for the packages Mike. I will try them out.

---

### Post by Ronni Joensen on 2008-05-16
> **Mega_Mike said:**
> I created .deb packages of AdvanceMenu 2.4.13 and AdvanceMame 0.106 for Ubuntu Gutsy.

[http://rapidshare.com/files/96721182/advancemenu_2.4.13-1_i386.deb.html](http://rapidshare.com/files/96721182/advancemenu_2.4.13-1_i386.deb.html)

[http://rapidshare.com/files/96721185/advancemame_0.106.0-1_i386.deb.html](http://rapidshare.com/files/96721185/advancemame_0.106.0-1_i386.deb.html)

Is there a chance you could create .deb packages for Hardy on x86_64 architecture as well?

---

