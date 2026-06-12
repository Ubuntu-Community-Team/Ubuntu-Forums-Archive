---
title: "[How-To] Wine 0.9.25,World Of Warcraft"
date: 2006-11-15
forum: Gaming &amp; Leisure
---

### Post by =Kevin= on 2006-11-15
Since I've had lots of success with the new Wine and World Of Warcraft, I'd be delighted to share my experience to help others :D 

This guide is about setting up Wine 0.9.25 and World Of Warcraft. I trust you to know how to use the Terminal, if you can't.. it's found under Applications->Accesoires->Terminal. You can copy&paste into the Terminal by just selecting the code here and copy'ing it with Ctrl+C, pasting into the Terminal is done with the keycombo Shift+Insert.

_Have fun, and hopefully after you've read this guide, happy gaming!_

*Note: you should have your graphical drivers installed correctly, refer to other guides on this forums for howto's on NVIDIA/ATI cards.*


_1.Setting up Wine 0.9.25_

First of all, make sure we are in the /home/yourname directory:
```
cd ~
```

Now we need to download the new Wine archive:
```
wget http://ibiblio.org/pub/linux/system/emulators/wine/wine-0.9.25.tar.bz2
```

Let's extract the archive:
```
tar xvj wine-0.9.25.tar.bz2
```

This will create a new directory named wine-0.9.25,let's go in:
```
cd wine-0.9.25
```

Now we are going to configure,make and install it:
1st step, configuring:
```
./configure
```

2nd step, making (aka compiling, this will take long, like 30 minutes)
```
make depend && make
```

Final step,installing your freshly compiled Wine:
```
sudo make install
```

Now you have your own compiled Wine installed! That wasn't so hard, was it?;)

_2.Configuring Wine_

Fire up your terminal and enter:
```
winecfg
```

We need to adjust some minor things here according the sound.
Move to the Audio Tab.
*NOTE:*If it crashes as soon as you're trying to reach the Audio tab, do the following:
```
sudo mv /usr/local/libs/wine/winearts.drv.so /usr/local/libs/wine/winearts.drv.so.backup
```

Now your audio tab should work, so let's move to it!
In the Audio Tab, uncheck the ALSA Driver box and check the OSS Driver box. Also we need to change the Hardware Acceleration from the dropdown box to Emulation. 
Click Apply and close your winecfg, we are done here!

_3.World Of Warcraft_

If you have World Of Warcraft already installed, good!Ignore the installing part :)

If you don't have it installed yet, then let's do something about it!
Copy everything from the CD's to a folder on your hard-drive, starting with CD1. Overwrite when asked. If everything is copied to your disk, open up your terminal:

```

cd yourfolder     (changed "yourfolder" to the name you've given the map)
wine Install.exe

```

This should launch the installer and you should be able to normally install the game.

Now it's time to edit your Config.wtf. First, we need to the folder where you've installed WoW.(normally ~/.wine/drive_c/Program\ Files/World\ Of\ Warcraft). Then we need to edit the Config.wtf file in the WTF folder. We'll also backup the Config.wtf should things go wrong.

```

cd ~/.wine/drive_c/Program\ Files/World\ Of\ Warcraft/WTF/
cp Config.wtf Config.wtf.backup  
gedit Config.wtf

```       

Edit your values or add these values to match the following:
```

SET SoundOutputSystem "1"
SET SoundBufferSize "100"
SET gxApi "OpenGL"

```

Save the file and exit. Now you're able to run WoW by giving the following command:

```

wine ~/.wine/drive_c/Program\ Files/World\ Of\ Warcraft/WoW.exe

```

But as you can see, this is not very efficient, so let's make a launcher!
```

sudo gedit /usr/local/bin/wow

```

Paste the following inside:
```

#!/bin/sh

wine ~/.wine/drive_c/Program\ Files/World\ Of\ Warcraft/WoW.exe

```

Now you are able to start World Of Warcraft by entering
```
wow
``` into the terminal!

If this all went fine, you will be able to play World of Warcraft freely, with good fps!

Only thing not working is the minimap inside dungeons,towns etc., it will just go blank. This is a known bug and there is no workaround yet.

This is my first guide, so be gentle ;)

Happy WoW'ing & Greets,

Keviin, Gnome Mage, Spinebreaker EU-Realm

---

### Post by Drezliok on 2006-11-15
Cool, I had every thing else but the launcher set up. I'll do that when I get the chance.

---

### Post by =Kevin= on 2006-11-16
Glad I could helpe ;)

---

### Post by deaz on 2006-11-16
Hey, i would like to thank you for making this guide tho i didn't get it to work ;)

When i get to "winecfg" i get this:
```
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
Application tried to create a window, but no driver could be loaded.
The X11 driver is missing.  Check your build!
Application tried to create a window, but no driver could be loaded.
The X11 driver is missing.  Check your build!
```

Hope you can help me out here :-k 

- deaz

---

### Post by scotty2hott2k on 2006-11-16
you could just add the official wine repo's for ubuntu to your apt sources then update then upgrade wine to the latest version, beats the hell out of compiling it each time :)

---

### Post by deaz on 2006-11-16
I DID do that afterwards, but still same problem.

---

### Post by =Kevin= on 2006-11-17
@deaz,

Do you have your video drivers correctly installed?

---

### Post by deaz on 2006-11-17
> **=Kevin= said:**
> @deaz,

Do you have your video drivers correctly installed?

Yes, the fglrx driver works perfectly with my ati radeon mobility x600 card.

---

### Post by mots on 2006-11-17
im experiencing exactly the same problem with an ati mobility x700

---

### Post by appdx on 2006-11-18
when I try to do 

```
cd ~/.wine/drive_c/Program\ Files/World\ Of\ Warcraft/WTF/
cp Config.wtf Config.wtf.backup  
gedit Config.wtf
```

I get

```
cp: cannot stat `Config.wtf': No such file or directory
```

If I try to just play it after the cut-scene I get this 
```
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
Exceeded max nr indirect texture lookups
DRM_I830_CMDBUFFER: -22
```

---

### Post by appdx on 2006-11-18
/bump

---

### Post by BitTorrentBuddha on 2006-11-18
I get an error about the patch, where can it be downloaded?

---

### Post by mots on 2006-11-18
*bump*

---

### Post by klund on 2006-11-19
My wow hangs the entire system after 10sec in the game. Anyone else have the same problem with fglrx?

---

### Post by Conde on 2006-11-19
so far this is working very very very very well. but now for the WoW running and testing. dum dum durrr.
nice 1 Kev

---

### Post by YokoZar on 2006-11-20
> **deaz said:**
> I DID do that afterwards, but still same problem.
Hmm, sounds like you didn't uninstall the version you built from source.  Go to the source directory (where you did make install) and do make uninstall.


Then check the output of "which wine" - if it says /usr/local/bin/wine rather than /usr/bin/wine, you didn't uninstall it.

---

### Post by Kelnoky on 2006-11-22
My audio tab in the winecfg crashes the whole thing like it said in the how-to. But ```
sudo mv /usr/local/libs/wine/winearts.drv.so /usr/local/libs/wine/winearts.drv.so.backup
``` only tells me "mv: cannot stat `/usr/local/libs/wine/winearts.drv.so': No such file or directory"

-.-
So, something wrong with my wine installation? Maybe - I installed it from synaptic (but after adding the right repository to my sources.lst) and synaptic tells me that I got 0.9.25 installed - but in the winecfg tab "about" it says that I got 0.9.21. So what's the case now? :D

---

### Post by Aurora on 2006-11-24
Greetings,

I have not been able to extract, either from the command line or the graphical archiver.

In the terminal, it looks like this:

100%[====================================>] 11,318,798   163.19K/s    ETA 00:00

13:32:53 (105.73 KB/s) - `wine-0.9.26.tar.bz2' saved [11318798/11318798]

[email]username@mycomputer:~/.wine[/email]$ tar xvj wine-0.9.26.tar.bz2


The command prompt never comes back, there's just a cursor.

(I had previously created the directory /.wine to install into)

When I tried to extract the source tarball with the graphical archiver, there were dozens of lines of errors.  I could do it again if you really want to see them....they mostly were about dlls; saying "cannot open, no such file or directory"

I wasn't wanting to install the Warquest game, but I did need a WINE with working sound, which you seem to have sorted out.  A lot of Ubuntu users are not getting sound with WINE.

Can you see anything I might do differently?

Thanks,

Paul in Seattle

---

### Post by seethru on 2006-11-24
There is a .deb file in the official Wine repo.

---

### Post by RockinRob2258 on 2006-11-26
One thing I noticed, it's still making the installation...
I haven't done any hard C or C++ coding in awhile, since before I installed Dapper.  Make sure you have g++, gcc, and make all installed on your computer.  After running ./configure , you may get some warnings and such requesting you to install further packages.  Be sure to install those things.

---

### Post by jaredvolkl on 2006-11-26
> **deaz said:**
> Hey, i would like to thank you for making this guide tho i didn't get it to work ;)

When i get to "winecfg" i get this:
```
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
Application tried to create a window, but no driver could be loaded.
The X11 driver is missing.  Check your build!
Application tried to create a window, but no driver could be loaded.
The X11 driver is missing.  Check your build!
```

Hope you can help me out here :-k 

- deazI'm seeing the same thing. I have a Core 2 Duo with an nvidia 7600GT. I know the drivers are working OK.

Do you have Beryl (or Compiz) installed? I haven't done any checking around, but I'm thinking that may be part of the problem.

---

### Post by Or'Enn on 2006-11-26
I get a whole bunch of probably very interesting text for those who can read it:
```
fixme:win:EnumDisplayDevicesW ((null),0,0x33f230,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33eee0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f6ec,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f6ec,0x00000000), stub!
fixme:d3d:IWineD3DImpl_GetDeviceCaps Caps support for directx9 is nonexistent at the moment!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found! (XRandR)
fixme:d3d:IWineD3DDeviceImpl_GetAvailableTextureMem (0x173918) : stub, simulating 64MB for now, returning 64MB left
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0x173918) Unhandled query type 8
fixme:win:EnumDisplayDevicesW ((null),0,0x33ee5c,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 112 (SPI_GETMOUSESPEED)
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:sync:CreateIoCompletionPort (0xffffffff, (nil), 00000000, 00000000): stub.
fixme:dbghelp:elf_load_debug_info_from_map Alpha-support for Dwarf2 information for msvcrt<elf>
fixme:dbghelp_dwarf:dwarf2_compute_location Only supporting one reg (-2147483611 -> 37)
fixme:dbghelp_dwarf:dwarf2_parse_variable NIY: const value 00657865 for EXE
fixme:dbghelp_dwarf:dwarf2_parse_variable NIY: const value 00626174 for BAT
fixme:dbghelp_dwarf:dwarf2_parse_variable NIY: const value 00636d64 for CMD
fixme:dbghelp_dwarf:dwarf2_parse_variable NIY: const value 00636f6d for COM
fixme:dbghelp_dwarf:dwarf2_parse_variable NIY: const value 00780065 for WCEXE
fixme:dbghelp_dwarf:dwarf2_parse_variable NIY: const value 00610074 for WCBAT
fixme:dbghelp_dwarf:dwarf2_parse_variable NIY: const value 006d0064 for WCCMD
fixme:dbghelp_dwarf:dwarf2_parse_variable NIY: const value 006f006d for WCCOM
fixme:dbghelp:elf_new_wine_thunks Duplicate in msvcrt<elf>: pf_fill<7ecc19c0-0000050d> subprogram_218<7ecc19c0-50d>
fixme:dbghelp:elf_new_wine_thunks Duplicate in msvcrt<elf>: pf_output_stringA<7ecc1350-0000016d> subprogram_194<7ecc1350-16d>
fixme:dbghelp:elf_load_debug_info_from_map Alpha-support for Dwarf2 information for kernel32<elf>
fixme:dbghelp_dwarf:dwarf2_parse_variable NIY: const value 00000000 for Installed
fixme:dbghelp_dwarf:dwarf2_parse_variable NIY: const value 00000000 for CtrlWord_Internal
fixme:dbghelp_dwarf:dwarf2_parse_variable NIY: const value 0000000b for StatusWord_1
fixme:dbghelp_dwarf:dwarf2_parse_variable NIY: const value 000000af for StackTop
fixme:dbghelp_dwarf:dwarf2_parse_variable NIY: const value 7aa08097 for default_ComputerName
fixme:dbghelp:elf_new_wine_thunks Duplicate in kernel32<elf>: __wine_stub_HeapSetFlags<7ee36b98-0000001b> ret<7ee36b98-0>
fixme:dbghelp:elf_new_wine_thunks Duplicate in kernel32<elf>: __wine_stub_ConvertDDEHandleLS<7ee3e668-0000001b> startup<7ee3e668-0>
fixme:dbghelp:elf_new_wine_thunks Duplicate in kernel32<elf>: __wine_stub_BaseAttachCompleteThunk<7ee362bc-0000001b> ptr<7ee362bc-0>
fixme:dbghelp:elf_new_wine_thunks Duplicate in kernel32<elf>: DebugBreakProcess<7ee4df60-000000bb> inherit<7ee4df60-0>
fixme:dbghelp:elf_load_debug_info_from_map Alpha-support for Dwarf2 information for libwine.so.1
fixme:dbghelp_dwarf:dwarf2_parse_variable NIY: const value 7a15d0af for server_config_dir
fixme:dbghelp_dwarf:dwarf2_parse_variable NIY: const value 0000ffff for granularity_mask
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:wave:OSS_AddRingMessage two fast messages in the queue!!!! toget = 30(WINE_WM_UPDATE), tosave=31(UNKNOWN(0x00000000))
```
Any idea?

---

### Post by ojko on 2006-11-28
Well i'm very impressed with Wine. So far Wines performance has out stripped Cedega quite considerably, in some cases by a good 20fps or so and is almost on par with my XP installation. :)

I do have one minor problem though. When I type wow into the terminal I get the following message:

bash: /usr/local/bin/wow: Permission denied

Anyone know how to fix this?

---

### Post by qrm on 2006-11-28
this howto worked perfectly, I play rarely WoW (once a week and then max for an hour) but it gives me the possibility to play it :D

---

### Post by Vord on 2006-11-30
just went through most of the steps, and up until I actually had to launch wow, everything went flawlessly. I installed like normal, clicked Play World Of Warcraft, nothing happened, so I cd ~/.wine/drive_c/Program\ Files/World\ of\ Warcraft/ and tried wine WoW.exe and got this error.

[email]vord@vord-desktop:~/.wine[/email]/drive_c/Program Files/World of Warcraft$ wine WoW.exe
err:module:import_dll Library OPENGL32.dll (which is needed by L"C:\\Program Files\\World of Warcraft\\WoW.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\World of Warcraft\\WoW.exe" failed, status c0000135

Now, I'm assuming this would be the fault of my video drivers not being installed, but quite the contrary. I used Automatix to install nvidia drivers the day that I instaleld ubuntu, so I don't believe that to be the problem. Can someone help me out?

---

### Post by Vord on 2006-11-30
Bump? I really need help with this, I'm completely in the dark here.

---

### Post by Vord on 2006-11-30
Well, I fixed that error by downloading GLU32.dll and putting it in my ~./wine/drive_c/windows/system32 folder, and now I'm getting this error, accompanied by a WoW execution error, terminating the process, should I just uninstall and try again?

```

vord@vord-desktop:~/.wine/drive_c/Program Files/World of Warcraft$ wine WoW.exe
fixme:process:IsWow64Process (0xffffffff 0x33fb98) stub!
err:ddraw:DDRAW_Create Couldn't load WineD3D - OpenGL libs not present?
fixme:advapi:SetSecurityInfo stub
fixme:powrprof:DllMain (0x7dff0000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 11
fixme:powrprof:DllMain (0x7dff0000, 0, (nil)) not fully implemented
fixme:win:EnumDisplayDevicesW ((null),0,0x33eedc,0x00000000), stub!
err:module:import_dll Library wined3d.dll (which is needed by L"c:\\windows\\system32\\d3d9.dll") not found
fixme:win:EnumDisplayDevicesW ((null),0,0x33f124,0x00000000), stub!
fixme:dbghelp:elf_load_debug_info_from_map Alpha-support for Dwarf2 information for kernel32<elf>
fixme:dbghelp_dwarf:dwarf2_parse_variable NIY: const value 0000005f for deflt
fixme:dbghelp_dwarf:dwarf2_parse_variable NIY: const value 0000000c for info_size
fixme:dbghelp:elf_new_wine_thunks Duplicate in kernel32<elf>: __wine_stub_InvalidateConsoleDIBits<7ee44bec-0000001b> key<7ee44bec-0>
fixme:dbghelp:elf_new_wine_thunks Duplicate in kernel32<elf>: __wine_stub_SetTaskInterchange<7ee4bf84-0000001b> in_index<7ee4bf84-0>
fixme:dbghelp:elf_new_wine_thunks Duplicate in kernel32<elf>: __wine_stub_WOWREGISTERSHELLWINDOWHANDLE<7ee4c534-0000001b> non_block<7ee4c534-0>
fixme:dbghelp:elf_new_wine_thunks Duplicate in kernel32<elf>: __wine_stub_RECCOM<7ee4afb0-0000001b> count<7ee4afb0-0>
fixme:dbghelp:elf_new_wine_thunks Duplicate in kernel32<elf>: __wine_stub_ThunkTheTemplateHandle<7ee4c6bc-0000001b> pipe_wait<7ee4c6bc-0>
fixme:dbghelp:elf_load_debug_info_from_map Alpha-support for Dwarf2 information for libwine.so.1
fixme:dbghelp_dwarf:dwarf2_parse_variable NIY: const value 0000ffff for granularity_mask

```

---

### Post by Vord on 2006-11-30
Bump? This one has me banging my head against a wall, I have no idea where to go from here, and I've been working at this for too many hours now.

---

### Post by Vord on 2006-11-30
One last bump before I give up on this all together, I can't figure out what's going on, can someone please tell me what I need to do to get this running?

---

### Post by Vord on 2006-11-30
So, since nobodies replying, I figure nobody knows what in the hell that error would mean, if it's an error at all. When I try to launch WoW from either Terminal or the desktop icon, they both result in this

```
This application has encountered a critical error:

ERROR #132 (0x85100084)
Program:	C:\Program Files\World of Warcraft\WoW.exe
Exception:	0xC0000005 (ACCESS_VIOLATION) at 0073:00604D73

The instruction at "0x00604D73" referenced memory at "0x00000054".
The memory could not be "read".


WoWBuild: 4449
```

Within a "WowError" window. This is my last hope of getting this running as I've not seen support for this problem anywhere else.

---

### Post by qrm on 2006-11-30
You could try deleting the whole World of Warcraft folder (uninstalling it), scraping wine from your system and beginning all over. It looks like a file corruption, ive seen it somewhere before loong time ago

you could check your memory sticks with memtest too

---

### Post by MACRI on 2006-11-30
Ok, i have a WoW disk, im trying to ditch winblows all together. how do i install WoW onto this if its a Windows disk?

---

### Post by Vord on 2006-11-30
I've done that (scrapping the WINE install, deleting WoW) at least three or four times, I come to the same error at the same point every time. As for MACRI, it outlines all of that in the first post of the thread.

---

### Post by Thursdae on 2006-11-30
Problem!!

```
jake@computer:~/wine-0.9.25$ ./configure
checking build system type... i686-pc-linux-gnuoldld
checking host system type... i686-pc-linux-gnuoldld
checking whether make sets $(MAKE)... no
checking for gcc... no
checking for cc... no
checking for cl.exe... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.

```

---

### Post by Vord on 2006-11-30
Thursdae - sudo apt-get install build-essential

Okay, so, someone found the file I was missing upon install, I put it into the filder it needed to be in, and tried starting WoW. Lo and behold, it worked...Kinda. When doing wine WoW.exe it loads up, I get a black screen at 800x600 implying that it's booting normally, but when the beginning movie starts and I hit escape at the "Ten years" screen, I get loud scratchy audio and it errors out before I get get to the login screen. Help?

---

### Post by hikaricore on 2006-11-30
> **Vord said:**
> Thursdae - sudo apt-get install build-essential

Okay, so, someone found the file I was missing upon install, I put it into the filder it needed to be in, and tried starting WoW. Lo and behold, it worked...Kinda. When doing wine WoW.exe it loads up, I get a black screen at 800x600 implying that it's booting normally, but when the beginning movie starts and I hit escape at the "Ten years" screen, I get loud scratchy audio and it errors out before I get get to the login screen. Help?

You topic jump too much :P  hard to keep track of you.

Try adding..

```

SET movie "0"
SET readTOS "1"
SET readEULA "1"

```

..to your config.wtf file, and see if that helps any.
I know you know where that is by now. :P

---

### Post by Vord on 2006-11-30
Haha, and I love you for keeping up with me :P

As for my config.wtf file, it doesn't exist..my world of warcraft/wtf folder is 100% empty. the config file doesn't present itself until you actually log into the game, I believe, which is why it hasn't been made yet. Should I just make one myself? or what?

---

### Post by hikaricore on 2006-11-30
Yes make one yourself.  :P

There are dozens of examples on the wine appdb page for WoW if you don't know where to start.

[http://appdb.winehq.org/appview.php?iVersionId=5606](http://appdb.winehq.org/appview.php?iVersionId=5606)

---

### Post by Vord on 2006-11-30
Well, suffice to say, I'm not sure how to do that, I'll check the wine appdb in a sec for how to. I just tried running wine WoW.exe -opengl and it gave me the error "Unable to start 3D accelleration" If this still has to do with the changes I have to make to my config.wtf file then I'm not too worried, but it doesn't seem like any of those changes would fix this.

---

### Post by hikaricore on 2006-12-01
I get the "Unable to start 3D accelleration" error when I'm running in 16bit color, if you change to 24 bit color there should be no reason for you to get this error.

Really config.wtf is just a text file, put in the lines I mentioned and wow will fill out the rest.

Just get to your WTF directory in konq or nautilus and right click to make a new text file, name it config.wtf .... copy+paste FTW and save.

As far as checking your color depth:

```

cat /etc/X11/xorg.conf | grep DefaultDepth

```

If this outputs: *DefaultDepth    16* 

You may need to edit you xorg.conf file:

```
gksudo gedit /etc/X11/xorg.conf
```

And change this to:  **DefaultDepth 24**

You will ofcourse need to restart your X session after this by hitting (SAVE ANYTHING IMPORTANT FIRST OR YOU'LL BE MAD) ctrl+alt+backspace, logging out, or rebooting.

Everyone's xserver is configured a little differently so this may be the case.  The most important this is not to get discouraged, it's usually a long hard road getting WoW working in linux.  But it can be very rewarding when you can finally sit around and waste all of your time in a virtual world while getting nothing else in your life done.  Spending hours in raids with complete ****ing morons who are the textbook example of how to play the ______ class worse than badly.

---

### Post by Vord on 2006-12-01
Already at 24-bit depth. I got the indication from the wine bugdb that 0.9.23 works better than .25, so I'm gonna go ahead and try that. I already sudo aptitude ~/.wine, so .25 is gone and .23 is installed. Reinstalling WoW right now to see if that MIGHT work. Cross your fingers.

---

### Post by Vord on 2006-12-01
Hmm, installed with wine 0.9.23, still getting the problem of "World of warcraft was unable to start 3D acceleration"

Any ideas beyond that?

Edit: I think I have a problem with my OpenGL, considering that's what most of these errors are stemming from. Any suggestions as to fixing/checking on that?

---

### Post by hikaricore on 2006-12-01
At this point I'm going to have to be stumped.  The issues you're having I've only encountered when using 16bit color :/  Sorry I couldn't be more help.

---

### Post by Vord on 2006-12-01
Haha, no worries man, you helped tons. I WILL NOT BE BEATEN.

Worst case scenario is me buying a third hard drive and installing all my games to that, and using Ubuntu as my primary OS. I'm here to stay, undoubtedly, but I can't rightfully live without my WoW fix, so I guess compromises will have to be made. I need the third drive to install BF2/2142 anyway, so all is good. :D

Thanks again, I appreciate all your help.

---

### Post by ch604 on 2006-12-01
i'm having a similar problem with 16 bit color, but it alwasy want to switch to 32 bit. any flags i can put in to make it use 24?

EDIT: i fixed that problem, but still hangs on the opening screen. Theres a bunch of fixme:s on the terminal, but i cant copy paste because linux is totally frozen.

---

### Post by ch604 on 2006-12-01
I tried running in -d3d, and i got about the same error message:
```
libGL warning: 3D driver claims to not support visual 0x5b
libGL warning: 3D driver claims to not support visual 0x5b
fixme:advapi:SetSecurityInfo stub
fixme:powrprof:DllMain (0x7c680000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 11
fixme:powrprof:DllMain (0x7c680000, 0, (nil)) not fully implemented
fixme:win:EnumDisplayDevicesW ((null),0,0x33eedc,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f148,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f6e8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f6e8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33ee58,0x00000000), stub!

---THIS IS WHERE OPENGL WOULD FREEZE---

fixme:d3d:IWineD3DImpl_GetDeviceCaps Caps support for directx9 is nonexistent at the moment!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:d3d:IWineD3DDeviceImpl_GetAvailableTextureMem (0x198800) : stub, simulating 64MB for now, returning 64MB left
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0x198800) Unhandled query type 9
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0x198800) Unhandled query type 8
fixme:win:EnumDisplayDevicesW ((null),0,0x33ee58,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 112 (SPI_GETMOUSESPEED)
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:sync:CreateIoCompletionPort (0xffffffff, (nil), 00000000, 00000000): stub.
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 4
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
Exceeded max nr indirect texture lookups
DRM_I830_CMDBUFFER: -22

```

any ideas?

---

### Post by qrm on 2006-12-01
> **hikaricore said:**
> 

 But it can be very rewarding when you can finally sit around and waste all of your time in a virtual world while getting nothing else in your life done.  Spending hours in raids with complete ****ing morons who are the textbook example of how to play the ______ class worse than badly.

Yeah, I know, im afraid Im addicted again, ....may....not....take...the...credit...card...out...of...my...pocket....nnnngh

Btw I dont get it, why are you building wine from source. There are repositorys with prebuilt pakcages. This is how I got my WoW running - with the additional help from the aforementioned howto. And If you need to create config.wtf file just cd to that folder and type gedit config.wtf and after getting the setting right just save it.

---

### Post by reiki on 2006-12-01
> **Vord said:**
> Haha, no worries man, you helped tons. I WILL NOT BE BEATEN.

Worst case scenario is me buying a third hard drive and installing all my games to that, and using Ubuntu as my primary OS. I'm here to stay, undoubtedly, but I can't rightfully live without my WoW fix, so I guess compromises will have to be made. I need the third drive to install BF2/2142 anyway, so all is good. :D

Thanks again, I appreciate all your help.

Vord-
Can you put your system info into a signature? I went back 3 pages to see what kind of hardware you have and didn't see it (I'm not really lazy... I'm at work.. hehehe).

I have WoW running in Wine on both Dapper and Edgy (with an nVidia card). Dapper is using nvidia drivers 8776 and Edgy is using drivers .... uh... 9629 I think is the number... new ones. 

Dapper is using a custom patched wine version 0.9.17 (I haven't touched it to upgrade it because it is simply working...) and Edgy is using a completely unmodified wine 0.9.26 from the winehq repositories. On Edgy, prior to wine 0.9.26, I was using an unmodified wine 0.9.25 also from those repositories.

There should be no need for you to be compiling wine and in fact I ran into trouble because bits of my compiled version (in Edgy) were screwing up my eventual installs from repositories. Had me pulling my hair out. 

On the Edgy install, using the new nVidia drivers and wine 0.9.26 and always running WoW in openGL mode, it works so well I can even run it WHILE Beryl is active. I did notice my framerates are lower if I have Beryl running. About 35-40fps as opposed to 60-80fps without Beryl running.

---

### Post by qrm on 2006-12-01
darn, i cant get wow running with beryl. It just spits out some "cannot activate 3d" or something like that

---

### Post by reiki on 2006-12-01
> **qrm said:**
> darn, i cant get wow running with beryl. It just spits out some "cannot activate 3d" or something like that
I think it works on Edgy because of the built-in aiglx and the new nVidia drivers. I did not install XGL on Edgy. I installed teh new nVidia drivers, installed beryl and emerald, and away she went. 

My experience with XGL/Compiz on Dapper was that WoW would not run in openGL mode. I have all that stuff turned off on Dapper and on Edgy it is off by default but easy to turn on. It's pretty eye candy but it doesn't do anything advantageous for me in the way I use my computer.

---

### Post by Vord on 2006-12-01
Hardware specs updated in profile, left out motherboard because I didn't really feel it was necessary, though I'm running an ASUS A8N-SLi, for reference. As for me compiling, should I just ./configure then make install? Both guides I've come across have asked me to compile.

---

### Post by hikaricore on 2006-12-01
Honestly some of us still don't understand why you're compiling from source, when wine 0.9.25 and 0.9.26 work nearly flawlessly without patching for almost everyone.  Are you aware there are dapper and edgy debian packages for these files?  [Downloads]("http://wine.budgetdedicated.com/archive/index.html") &  [Info]("http://www.winehq.org/site/download-deb")

I'm not saying there is anything wrong with compiling the source on your own as a learning experience.. just that when many people have had a similar issue when compiling using premade working packages may be the best solution.

---

### Post by Vord on 2006-12-01
I'm compiling from source because this guide instructs me to.

make depend && make IIRC, I'm at school right now, so I'll go ahead and check out those links when I get home. I'll just get the packges and install when I get home.

---

### Post by reiki on 2006-12-01
Vord-

To be honest I think if I were you I'd go into the sources directory where you compiled wine and make uninstall to remove it.

The add the respositories and get the new version of wine ( 0.9.26 ). Teh latest 2 versions of wine have worked "out of the box", required no patching, and as repository packages they are easily updateable. I have an nVidia 7300GT with 512MB of ram on it (hey it was cheap) so your card is quite a bit better than mine and that 8N-SLI board of yours.... well that was my original intention before I decided I REALLY didn't need SLI and probably would not use it within the next 3 years :) so I have the Asus P5LD2. 

I guess what I'm saying is that I think you're struggling needlessly. And that's not a harsh criticism or anything. Just the voice of experience because I was struggling as well. Then I spent a TON of time on the wineHQ site working with Nick Law and Alan J over there and they really got this working for 0.9.25 and 0.9.26. Those guys know their stuff and as a result I am no longer struggling, I'm playing WoW at 60 to 80fps under Wine (in openGL) and enjoying it rather than fighting with it. :)

THEN.... I spent an appropriate amount of time kicking my own (butt) because I had spent so much time compiling and having stuff blow up. Relax.... make uninstall ... make sure it's gone... and then just do a package install. You will like yourself ... heheh.

Oh... keep in mind that many guides instructing you to compile were made before 0.9.25 and 0.9.26 came out. Before those 2 versions you had to compile to patch sources and/or get around an incompatibility in the compiling parameters that made the packages break on Edgy. You don't need to compile any more.

---

### Post by Vord on 2006-12-01
so should I just do sudo aptitude ~/.wine to uninstall it? or should I go about uninstalling it in another fashion?

---

### Post by hikaricore on 2006-12-01
Have the source handy that you were using to build, and do(from source dir):

```

./configure
make uninstall

```

That should clean up the mess.  Then try installing from the latest ubuntu deb package :)  I really hope this solves your troubles.

---

### Post by Vord on 2006-12-01
Yeah, you and me both. I'm still in class but I'll head home and get started on that, I'll let you know how it comes out. Wish me luck :D

---

### Post by Vord on 2006-12-01
So what if I don't have the source handy nymore? I did sudo rm -r ~/.wine last night, will that suffice as an uninstall?

---

### Post by Vord on 2006-12-01
Erdi: Nevermind, reinstalling now

---

### Post by CoryLeePeterson on 2006-12-01
ok this is messed up i have downloaded wine_0.9.26~winehq0~ubuntu~6.06-1_i386.deb
istalled the package but now i have no clue what to do. i think the wine website is down or something cuz everytime i go to this [http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb) i get nothing. just error or loads for 10 mins and then just comes up with blank.
im realy new to linux. i just wana play my wow. so if someone could help me the quicker the better :)

---

### Post by hikaricore on 2006-12-01
> **CoryLeePeterson said:**
> ok this is messed up i have downloaded wine_0.9.26~winehq0~ubuntu~6.06-1_i386.deb
istalled the package but now i have no clue what to do. i think the wine website is down or something cuz everytime i go to this [http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb) i get nothing. just error or loads for 10 mins and then just comes up with blank.
im realy new to linux. i just wana play my wow. so if someone could help me the quicker the better :)

Assuming your video drivers and everything are all setup correctly it shouldn't be much more complicated than opening a terminal and typing:

```
wine ~/.wine/drive_c/Program\ Files/World\ of\ Warcraft/WoW.exe -opengl
```

You should also be able to make a desktop launcher with the same command line.

Beware you won't be able to change your video settings in wow with opengl mode as wow will most likely crash, but if you launch it with:

```
wine ~/.wine/drive_c/Program\ Files/World\ of\ Warcraft/WoW.exe -d3d
```

You should be able to change them and then logout, just make sure when you play you use opengl, or your experience may not be great.

---

### Post by hikaricore on 2006-12-01
^This is assuming the location of your WoW installation is the default.  :)

---

### Post by CoryLeePeterson on 2006-12-01
how/where would i install wow ?

---

### Post by hikaricore on 2006-12-01
Your best bet is to copy the cds (all of them) to a temporary location on your system, just drag and drop the files somewhere (even your desktop will work fine) from each cd 1 by 1.  If you're prompted about overwriting just say yes.  Once you're done with all of them you should be able to just double click on Setup.exe, it will launch using wine automaticly (usually) and then follow through the normal install procedure.  Once it completes (this can take longer than you're used to) just follow the directions I posted above to run the game.

---

### Post by CoryLeePeterson on 2006-12-01
how do i kno if wine is even installed properly? sry for such newb questions. but i literaly just installed about n hr ago. ive tryed ubuntu b4 with cs and steam and all that but i dont remember anything.

---

### Post by hikaricore on 2006-12-01
Did you double click on the wine package you downloaded?  A box should have come up with an option to install if you did.

---

### Post by CoryLeePeterson on 2006-12-01
yes it did all that. so i should be good to go right? im on the last dic coppying to my desktop right now

---

### Post by CoryLeePeterson on 2006-12-01
hld up i did it! ... or so i think :) its installing right now. if this works then i love u :)

---

### Post by Vord on 2006-12-02
and I'm still haveing serious problems, that's pretty discouraging :P. I have no idea why I'm having such major opengl problems.

---

### Post by CoryLeePeterson on 2006-12-02
man it works so far. but no sound.. how could i fix that?

---

### Post by hikaricore on 2006-12-02
> **CoryLeePeterson said:**
> man it works so far. but no sound.. how could i fix that?

The wine application database seems to be working again.

[http://appdb.winehq.org/appview.php?iVersionId=5606](http://appdb.winehq.org/appview.php?iVersionId=5606)

You may find some fixes for sound issues there, I've never had any so I don't know any solutions.

---

### Post by hikaricore on 2006-12-02
> **Vord said:**
> and I'm still haveing serious problems, that's pretty discouraging :P. I have no idea why I'm having such major opengl problems.

Arg, I wish there were an easy solution to this for you but I'm right back to where I was before with ideas.  :/

On an interesting note I just realized something funny.

All of the folks who get WoW this year for christmas will be SOL the following morning when server maintainance takes the world of warcraft down for countless hours.  =)  If that doesn't put a smile on your face I don't know what will.

---

### Post by CoryLeePeterson on 2006-12-02
haha. well its working everyone. dont kno on the sound yet. just got the patch had troubles downloading it.. kept freezing at 99% but yeah im just excited. ive been able to dl steam. xfire . vent. everything. thanks for the help with wine. basicly for the install. it takes alot longer than usual but hang in there cuz it works.

btw is everyone getin the new expantion in jan?

---

### Post by hikaricore on 2006-12-02
I had to tell my girl she's not getting the expansion until she gets a job... I'm still paying for both of our account, and she's the only one using them.  >.<  Alllll day.  I stopped playing about 5 months ago.  Sometimes I get bored and farm SM with my rogues.

---

### Post by CoryLeePeterson on 2006-12-02
lol nice. this sucks. the game works great but no sound. can anyone help me?

---

### Post by Vord on 2006-12-02
Haha, well, I just formatted, and now that I'm starting with a fresh install, I'm gonna go ahead and try the process that CoryLee went through. Hopefully it should all go well, and I'll be able to get patched and everything. Cross your fingers, guys.

---

### Post by hikaricore on 2006-12-02
> **CoryLeePeterson said:**
> lol nice. this sucks. the game works great but no sound. can anyone help me?

One thing you could try is changing the sound driver wine is using.

```
winecfg
```

Goto the audio tab and choose a different sound driver, it's probably set as ALSA so try chaning it to OSS, hit apply, close the panel and try starting WoW again.

You might also want to try adding the following to your config.wtf file in the WTF folder of your World of Warcraft directory:

> 
SET ffxDeath "0"
SET SoundOutputSystem "1"
SET SoundBufferSize "232" 


Found em real quick at the wine DB

Hope it helps.

-----



> **Vord said:**
> Haha, well, I just formatted, and now that I'm starting with a fresh install, I'm gonna go ahead and try the process that CoryLee went through. Hopefully it should all go well, and I'll be able to get patched and everything. Cross your fingers, guys.

Good luck, I know this isn't the most pleasant solution to the issue but some people have luck doing just that. :)

---

### Post by Vord on 2006-12-02
Well, thus far I've installed wine from the 0.9.26 tarball, and ripped all the CDs, tried double clicking the exe (going exactly by your word here) and it didn't work, so I just cd ~/WoW (ripped directory) and now it's installing after wine Installer.exe. so let's hope this works out :D

---

### Post by hikaricore on 2006-12-02
The ubuntu packages set mimetypes for exe files, I don't know about other methods of installing wine, but I doubt they do.  So my guess is that's why the installer didn't launch via double click  .You can fix this yourself by rightclicking an exe selecting open with and typing in the box:

wine


Anyway I'm off to watch the direct to video 5th american pie movie..  so far it's looking aweful.  ROFL

---

### Post by Vord on 2006-12-02
......It Worked!

Patching now :D

---

### Post by CoryLeePeterson on 2006-12-02
should i .. emulate or no ? what sux is that it all runs great except sound. lol i want my sound! let me kno if urs works vord

---

### Post by hikaricore on 2006-12-02
no luck with any of the sound tips I gave you then? :/

---

### Post by testbenchdude on 2006-12-02
nm I'm dumb :) lol

---

### Post by Vord on 2006-12-02
> **CoryLeePeterson said:**
> should i .. emulate or no ? what sux is that it all runs great except sound. lol i want my sound! let me kno if urs works vord

Hah, I don't run sound, man, I always have music playing or vent on. I haven't used sound in ages, but just for you, I'll try and get it to work :P

---

### Post by Vord on 2006-12-02
Update: It works, and it works well. Runs flawlessly, and I'm ecstatic about it. Thanks to everybody who helped me out.

---

### Post by CoryLeePeterson on 2006-12-02
hey did u see all the words ok when u installed?

---

### Post by CoryLeePeterson on 2006-12-02
K ive reinstalled wow and wine. still no sound. i think i might have found a way by following this. 

Now it's time to edit your Config.wtf. First, we need to the folder where you've installed WoW.(normally ~/.wine/drive_c/Program\ Files/World\ Of\ Warcraft). Then we need to edit the Config.wtf file in the WTF folder. We'll also backup the Config.wtf should things go wrong.

Code:

cd ~/.wine/drive_c/Program\ Files/World\ Of\ Warcraft/WTF/
cp Config.wtf Config.wtf.backup  
gedit Config.wtf

Edit your values or add these values to match the following:
Code:

SET SoundOutputSystem "1"
SET SoundBufferSize "100"
SET gxApi "OpenGL"

Save the file and exit. Now you're able to run WoW by giving the following command:

Code:

wine ~/.wine/drive_c/Program\ Files/World\ Of\ Warcraft/WoW.exe

But as you can see, this is not very efficient, so let's make a launcher!
Code:

sudo gedit /usr/local/bin/wow

Paste the following inside:
Code:

#!/bin/sh

wine ~/.wine/drive_c/Program\ Files/World\ Of\ Warcraft/WoW.exe

Now you are able to start World Of Warcraft by entering
Code:

wow


but i have no clue how to get the the directory. when i type in the code he gives ig et this. 


cory@cory-desktop:~$ cd ~/.wine/drive_c/Program\ Files/World\ Of\ Warcraft/WTF/
bash: cd: /home/cory/.wine/drive_c/Program Files/World Of Warcraft/WTF/: No such file or directory
cory@cory-desktop:~$

help me plZ :(

---

### Post by Vord on 2006-12-02
Well, the thing about the terminal is, it recognizes spaces as a break in the directory, and it's case sensitive, so what you probably need to be entering is
```
 cd ~/.wine/drive_c/Prorgram\ Files/World\ of\ Warcraft/WTF
```

and then gedit the config file from there. The "o" in of is lowecase, not caps.

---

### Post by CoryLeePeterson on 2006-12-02
not workin :( is there a way to get to it without treminal?

---

### Post by reiki on 2006-12-02
Use the file browser in the GUI, navigate to the directory, right click the file, edit with text editor

---

### Post by Dieter24 on 2006-12-03
I was wondering if this worked the same for Xubuntu or not. If it should, then I'm having major problems right away because the terminal doesn't recognize cd as a command in the fourth step. Also, I'm not sure if the package is even unpacking. I do this

```
tar xvj wine-0.9.25.tar.bz2
```then it goes to the next line without even
```
bray@bray-laptop:~$
```So yeah, either problems, or it doesn't work with Xubuntu, in which case I'll just install Ubuntu, though I like Xfce...

---

### Post by qrm on 2006-12-03
Dieter you may just install KDE or Gnome just by typing

sudo apt-get install kubuntu-desktop
sudo apt-get install ubuntu-desktop

besides window managers and some software all ubuntu subflavors are the same. If you want to change WM just from he login window select sessions and change session to KDE or XFCE or Gnome

---

### Post by Naegling23 on 2006-12-09
Hmm, so I have warcraft up and running, it runs fine...but only in a window.  If I try to fullscreen it, I have problems

I have it running under windows xp version
Allow direct x to keep mouse from leaving windows...checked
enable desktop double buffering...checked
allow the windows manager to control the windows...checked
emulate a virtual desktop...checked
vertex shader support...hardware
allow pixel shader...checked
I also launch the game with the command Wow.exe -opengl

I guess im doing something wrong, if I bump up the resolution in game to 1024x768 (my native desktop resolution) then the screen ends up hanging off the desktop, so I cant access everything.  If I uncheck emulate a virtual window, then I get sound, but a black screen.  

By the way, Im running this on AIGlx/beryl on kubuntu.

thanks for the help, Im almost there!!!!

ps, I had some problems with the oss audio, it kept cracking and popping, the alsa mixer seemed to reduce this problem, so I've been using them.

---

### Post by mitchbones on 2006-12-10
Is anyone having problems with it crashing after you try to alter your video settings

---

### Post by Thursdae on 2006-12-10
Anyone have x11drv_fbconfig_fix-0001.bin? WineHQ.com is down or seomthing and i needa install it...

Also anyone know why my WoW is lagging real bad video wise? Im guessing its because i dont have the x11drv_fbconfig_fix-0001.bin in but idk, please help kthx

---

### Post by Thursdae on 2006-12-10
bump

---

### Post by chadk on 2006-12-11
> **mitchbones said:**
> Is anyone having problems with it crashing after you try to alter your video settings

I think this is a known issue.
[http://gentoo-wiki.com/HOWTO_Install_and_update_World_Of_Warcraft_with_wine#Crashing_on_Video_Option_change](http://gentoo-wiki.com/HOWTO_Install_and_update_World_Of_Warcraft_with_wine#Crashing_on_Video_Option_change)

Naegling23: I think the fact you're using AIGlx/beryl is complicating your installation.

---

### Post by Naegling23 on 2006-12-11
chadk:  yea, I tried that last night, disabling beryl, and running it.  It worked fullscreen.  When I exited the game, my desktop was all messed up, and I had to ctl-alt-bksp.  Im not sure, but it could be due to the fact that I was running wow at 800x600, and my desktop resolution is 1068x768(or whatever that resolution is, I can never remember).  I changed the wow resolution to my desktop resolution, and will try again when I get the chance.  Its dissapointing, because games like doom3 and neverwinter nights run just fine in beryl, but its easy enough to toggle...beats rebooting into windows.

Ill also see if the beryl update (to 0.1.3) helps or not.

---

### Post by chadk on 2006-12-11
I don't think resolution is your problem.  What version of Wine and what video card are you using?

---

### Post by Spoik on 2006-12-13
My graphics are are so bad opengl that the game is unplayable. Playing in d3d is much better but still funky.

I'm also getting:
 libGL warning: 3D driver claims to not support visual 0x4b
when i start the game. Don't know if it related at all.

I'm running WoW 2.0.1 with wine 0.9.26 on edgy.

---

### Post by Naegling23 on 2006-12-13
chadk:

Im running the latest wine 0.9.27, and an nvidia 6800gt.

---

### Post by Naegling23 on 2006-12-14
Im still sitting at the cusp of having this work well.  If I go to change my video settings in game, the game crashes.  Can I change them manually in the settings file in my warcraft directory(I cant remember the name, or location off the top of my head, im not at that computer).  Or is there a patch or fix to be able to change this?

---

### Post by hikaricore on 2006-12-14
> **Naegling23 said:**
> Im still sitting at the cusp of having this work well.  If I go to change my video settings in game, the game crashes.  Can I change them manually in the settings file in my warcraft directory(I cant remember the name, or location off the top of my head, im not at that computer).  Or is there a patch or fix to be able to change this?

WTF/config.wtf in your WoW dir, and to make ingame video setting changes run wow with:

```
wine WoW.exe -d3d
```

DO NOT TRY TO PLAY THIS WAY unless you know it will work for you, it doesn't usually end/look pretty and is often slow.  But it is possible to change settings while in the game.  :)

---

### Post by douglett on 2006-12-15
> **Naegling23 said:**
> Hmm, so I have warcraft up and running, it runs fine...but only in a window.  If I try to fullscreen it, I have problems

I have it running under windows xp version
Allow direct x to keep mouse from leaving windows...checked
enable desktop double buffering...checked
allow the windows manager to control the windows...checked
emulate a virtual desktop...checked
vertex shader support...hardware
allow pixel shader...checked
I also launch the game with the command Wow.exe -opengl

I guess im doing something wrong, if I bump up the resolution in game to 1024x768 (my native desktop resolution) then the screen ends up hanging off the desktop, so I cant access everything.  If I uncheck emulate a virtual window, then I get sound, but a black screen.  


I'm having the same problem :(

---

### Post by Naegling23 on 2006-12-15
Well, the fullscreen problem was solved...sort of.  If I turn beryl off, then it works fine.  Beryl causes the same problem in mythtv, but for some reason, my other programs all work fine.  

So I have wow running fullscreen, I changed my ingame settings using d3d.  But there is still one problem:

The game runs fine.  It runs smooth, and is playable....most of the time.  If I change the camera view, it slideshows.  This goes for rotating the camera, or turning my character (right/left).  When I do this, the game stutters, badly, unplayable badly.  When I run straight ahead, or attack an enemy, the game runs fine.  I have dont the wine hack to speed up the framerate, this does not help.  Any suggestions.  Turning down the detail does not seem to affect this at all.

---

### Post by Naegling23 on 2006-12-15
alright, fixed the framerate issue.  Turns out that I misspelled a word when setting up the wine hack.  Fixed it, the game runs very smooth on an 800x600 window in beryl.  Graphically, its not quite where windows is, but I think thats a resolution issue.  Does anyone run WoW at a resolution higher than their native desktop resolution?  Would this work?

---

### Post by reiki on 2006-12-16
> **Naegling23 said:**
> alright, fixed the framerate issue.  Turns out that I misspelled a word when setting up the wine hack.  Fixed it, the game runs very smooth on an 800x600 window in beryl.  Graphically, its not quite where windows is, but I think thats a resolution issue.  Does anyone run WoW at a resolution higher than their native desktop resolution?  Would this work?

My native resolution is 1280 x 1024
I run WoW in a window rather than full screen and teh window is like.... 1152 x ......something.... it's listed in the WoW screen size configuration thing within the game. Then I set Wine to use the same size. So the window is NEARLY full screen. .... not sure why I do it that way but I like it so I ain't switching. :)

Your frame rates will be MUCH higher if you turn Beryl off when you play WoW (assuming you are playing in openGL mode which you should be).

If WoW crashes when you change the resolution in-game, start it in d3d mode, change resolution, and then start it back up in openGL mode. Seems to work well that way.

---

### Post by adrift on 2006-12-23
> **ojko said:**
> Well i'm very impressed with Wine. So far Wines performance has out stripped Cedega quite considerably, in some cases by a good 20fps or so and is almost on par with my XP installation. :)

I do have one minor problem though. When I type wow into the terminal I get the following message:

bash: /usr/local/bin/wow: Permission denied

Anyone know how to fix this?

I'm having the same problem.

Ah never mind. apparently i had to make the script executable by typing in 
```
sudo chmod +x /usr/local/bin/wow
```
then 
```
wow
```

---

### Post by Vord on 2006-12-26
So, is there any way to get around the window that pops up initially, telling you the latest news/releases/things like that? It prompts a background downloader that's crashing WoW. I have to install an HTML parser everytime it comes up, and it's just getting annoying

---

### Post by Poka64 on 2007-01-14
How do we Wine users install Burning crusade?
Should we just copy the content on the cd:s and install it from the harddrive?

---

### Post by chronusdark on 2007-01-15
> **Vord said:**
> So, is there any way to get around the window that pops up initially, telling you the latest news/releases/things like that? It prompts a background downloader that's crashing WoW. I have to install an HTML parser everytime it comes up, and it's just getting annoying

point your launcher to WoW.exe not Launcher.exe

as for the HTML parser download [this]("http://puzzle.dl.sourceforge.net/sourceforge/wine/wine_gecko.cab") and use cabextract to extract it to your Program Files folder and that wont happen again



good luck

---

### Post by daller on 2007-01-21
Thanks for you howto! - I don't have WoW myself, but my sister has it...

Am I able to borrow the game from her and test this howto without running into CD-key issues...?

The problem is that she dual-boot just to play WoW, and I would really like to change that :D - But she lives far away from me, so I plan copy the disc to my PC, and take it from there... But will it work?

---

### Post by Naegling23 on 2007-01-21
daller, you can download a 10 day trial for free from blizzards website.  The original game is basically free at this point.  After you install the game, just enter your sister's, or your account info to log in and play.

I had some cd issues when I tried to install wow, so I just used this method to get it on my linux partition.

---

### Post by Blindraven on 2007-03-02
ISSUE:

I get in to the login screen, where it puts me through to the charatcer selection screen, but this screen is all black where the 3D would otherwise be, leaving only the character selection gumps on the side.

What could this issue be caused by?

My graphics are running perfectly, I know this for a fact.

---

### Post by Sammi on 2007-03-02
This howto isn't terrible out of date, but a updated and easier howto can be found here: [https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

---

