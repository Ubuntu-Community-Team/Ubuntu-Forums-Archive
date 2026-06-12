---
title: "[HOWTO] World of Warcraft [OUTDATED]"
date: 2005-11-19
forum: Gaming &amp; Leisure
---

### Post by SKLP on 2005-11-19
I made a WoW under wine howto: 
[https://wiki.ubuntu.com/WorldofWarcraftHowto](https://wiki.ubuntu.com/WorldofWarcraftHowto)

This is the official discuss/support thread for it... ;-)


UPDATE: I've not updated the howto in a long time and I probably won't so it is probably OBSOLETE and not working. Sorry

---

### Post by basse1989 on 2005-11-19
I'm playing WoW with the same setup and it works super nice. :D

I'm Selmak on the EU Burning Legion.

---

### Post by Burkey on 2005-11-21
Cool, I can NOT get WoW to work under Cedega, and so far have not had any decent support.. basically Cedega insists on switching to software mode.

Anyway, I tried with Wine 0.9.1 and guess what.. 3D acceleration is fine, but!  whenever I try to run in opengl mode it gives me the unable to start 3D acceleration dialog and quits, under DX it runs reasonably but with a LOT of missing textures, making it unplayable.

I am on a 2Ghz laptop with integrated i915 graphics... I suspect there is a problem allocating memory for the textures?  Or is it normal in DX mode?

Also, I have 1Gig RAM, I would love to reserve 128 of that for the video card...

---

### Post by SKLP on 2005-11-21
```

SET gxColorBits "24"
SET gxDepthBits "24"

```
Try changing those things to those specific values in WTF/Config.wtf

Tell me if that works; if so, i will add it to my howto ;-)

EDIT: This is to make OpenGL work

---

### Post by SKLP on 2005-11-21
[QUOTE=Burkey]I suspect there is a problem allocating memory for the textures?  Or is it normal in DX mode?[/QUOTE]Wine's DirectX support is very limited so, yes, this is normal. (that's why we use OpenGL mode in the guide)

---

### Post by themainecane on 2005-11-21
It doesn't seem to have anything on the "mouse bug", and that's the only thing keeping me from WOWing on Ubuntu. -MC

---

### Post by SKLP on 2005-11-21
[QUOTE=themainecane]It doesn't seem to have anything on the "mouse bug", and that's the only thing keeping me from WOWing on Ubuntu. -MC[/QUOTE]The "mouse bug" = can't click stuff bug, or?

in that case we have wine_wowfixes which fixes that pretty nicely ;-)

---

### Post by siplus on 2005-11-21
I was using cedega, and the mouse problems i had included not being able to target with the mouse (had to F1-F5 and Tab everything)

I was directed here: [http://cedegawiki.sweetleafstudios.com/wiki/World_of_Warcraft#Mouse_Issues](http://cedegawiki.sweetleafstudios.com/wiki/World_of_Warcraft#Mouse_Issues)

Section 2.2 fixed me up. I don't know if this is cedega specific, or if it will work with wine as well, but hopefully some googler will find this useful :-D

---

### Post by callahan on 2005-11-21
I just installed WoW again on my Breezy over the weekend.  I did it somewhat differently than the howto here.

First, follow the instructions on [http://www.winehq.com/site/download-deb](http://www.winehq.com/site/download-deb) for installing wine from souce code using the debian packages.  Here they are paraphrased:


Add the following to your repositories (just stick it at the end of /etc/apt/sources.list or use synaptic to add it as a repository).

deb-src [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) source/


Next grab all the wine building dependencies:
  sudo apt-get build-dep wine

Now grab but don't compile the wine source.  This will fail out a the compilation part because you didn't do it as root:

  mkdir ~/winesrc
  cd ~/winesrc
  apt-get --build source wine

The wine source needs to be patched for WoW to work.  There are two fixes that you should apply.  WoW needs a bug workaround in glPolygonOffset to see targetting rings and it needs a memory mapping fix in order to select things with the mouse.  They are the same fixes as listed in the wiki (although the patch may not apply correctly if the wine version gets updated).


Next compile up a wine package and install it:

  sudo apt-get --build source wine
  dpk -i wine*.deb

I would expect this process to become easier as these workarounds are incorporated into the wine source code so that you just have to install wine from the repository as usual.


Installing WoW was also somewhat tricky.  Stick the dll in your ~/.wine directory as directed under the Wiki.  Then copy all of the CDs into some directory.   A number of the files will be duplicated, you should end up with an autorun, Installation.exe, Installation.something, and 4 big data files.  "wine Installation.exe" and wait a while.  Then run wow several times (once for each of several patches).  It's a rather lengthy process to get it all there and up to date.

  Michael

---

### Post by SKLP on 2005-11-21
hmm, and I was just thinking about changing the wiki page to "debianize" the instructions. well, will do so when i have time ;)

---

### Post by themainecane on 2005-11-22
[QUOTE=SKLP]The "mouse bug" = can't click stuff bug, or?

in that case we have wine_wowfixes which fixes that pretty nicely ;-)[/QUOTE]

Its the bug where the mouse thinks the background is in front of the foreground objects, so you cannot click to target or select anything in game unless you look straight up so that the only thing behind whatever you're trying to target is the sky. Tell me of these wowfixes... are they part of the HOWTO that I missed? *rechecks the HOWTO* -MC

---

### Post by glaze on 2005-11-22
[QUOTE=themainecane]Its the bug where the mouse thinks the background is in front of the foreground objects, so you cannot click to target or select anything in game unless you look straight up so that the only thing behind whatever you're trying to target is the sky. Tell me of these wowfixes... are they part of the HOWTO that I missed? *rechecks the HOWTO* -MC[/QUOTE]

Fixes are applied in howto section "Installing Wine".

---

### Post by Weav on 2005-11-22
Great HowTo, looks like it has great potential, but still missing the vital "Installing WoW" section.

---

### Post by basse1989 on 2005-11-22
If you already have WoW installed in windows/on another computer, just copy it to your ubuntu partition, cd there and do a "wine WoW.exe"

As  Michael said
{
If you don't have it installed somewhere, just copy all the stuff from the cds to the same dir on the HD (some files will be duplicated, just overwrite them) and then just cd there and start the installation with "wine Installation.exe"
}

:D

---

### Post by SKLP on 2005-11-22
[QUOTE=Weav]Great HowTo, looks like it has great potential, but still missing the vital "Installing WoW" section.[/QUOTE]Thank you.

And i think the Installing WoW part simply consists of inserting the cd's, copying the files to a folder, executing the installer and installing.

I didn't post that in the howto because i haven't tried it in a while so I'm not sure if it works.

---

### Post by Burkey on 2005-11-24
Ok, I actually went all the way to delete my Config.wtf and create a new one with ONLY the lines
```

SET gxApi "opengl"
SET gxColorBits "24"
SET gxDepthBits "24"

```

And it still switches resolution, flickers a bit and then says "Unable to start 3D Acceleration" :-(

I have been forced to play in windows to get my warlock to 60, but really want to solve this problem.  It is very strange that it runs at reasonable speed under DirectX (with missing textures) and cannot even get going under OpenGL

---

### Post by SKLP on 2005-11-25
[QUOTE=Burkey]Ok, I actually went all the way to delete my Config.wtf and create a new one with ONLY the lines
```

SET gxApi "opengl"
SET gxColorBits "24"
SET gxDepthBits "24"

```

And it still switches resolution, flickers a bit and then says "Unable to start 3D Acceleration" :-(

I have been forced to play in windows to get my warlock to 60, but really want to solve this problem.  It is very strange that it runs at reasonable speed under DirectX (with missing textures) and cannot even get going under OpenGL[/QUOTE]
:(

can u try and replace the current Config.wtf with this:
```
SET hwDetect "0"
SET gxColorBits "24"
SET gxDepthBits "24"
SET gxResolution "1024x768"
SET gxRefresh "60"
SET gxApi "OpenGL"
SET SoundOutputSystem "1"
SET SoundBufferSize "130"

```
And of course change your proper resolution and refresh rate (same as X is using) before trying ;)

good luck

---

### Post by alynx on 2005-11-25
Very good thread , I cant wait to get home and fix the DAMNED mousebug :razz:

---

### Post by Burkey on 2005-11-25
Ok, I re-installed Ubuntu 5.10 clean.. then installed wine and set my Config.wtf as above, I now get a different error.

```

Your 3D Accelerator is not supported by World of Warcraft. Please install a 3D accelerator card with dual-TMU support.

```

So a kind of progress I guess.. breakfast now but will try some more things when I get back, hope someone might be able to shed some light

---

### Post by apoc on 2005-11-26
Thanks for the howto, however I guess I failed somewhere :(

Heres the error when I do wine WoW.exe

wine: error while loading shared libraries: libwine.so.1: cannot open shared object file: No such file or directory

I've followed the walktrough except the configure wine part. (where do I open regedit?)

Installing wow was copying a full patched game from my NTFS drive

The part for WTF/Config.WTF was added without trouble aswell.

So if you can help me fix it I would be happy :D If not how to I uninstall it as it does not show up in Synaptic anymore. Thanks

---

### Post by trian on 2005-11-26
well. My problem is starting WoW on my Aopen 1557G with a Radeon Mobility 9700 card. It just gets crooked, sound and everything else works great. I dont want to run with -opengl because the performance drop is too great. any ideas?

---

### Post by SKLP on 2005-11-27
> **apoc]Thanks for the howto, however I guess I failed somewhere :(

Heres the error when I do wine WoW.exe

wine: error while loading shared libraries: libwine.so.1: cannot open shared object file: No such file or directory

I've followed the walktrough except the configure wine part. (where do I open regedit?)

Installing wow was copying a full patched game from my NTFS drive

The part for WTF/Config.WTF was added without trouble aswell.

So if you can help me fix it I would be happy :D If not how to I uninstall it as it does not show up in Synaptic anymore. Thanks[/QUOTE]Sorry. I forgot one thing  in my howto...

try this:

```
sudo -s
echo "/usr/local/lib" >> /etc/ld.so.conf
ldconfig

```
then close all terminals said:**
> I dont want to run with -opengl because the performance drop is too great.WoW is not playable in wine without using the opengl mode AFAIK. The howto describes adding ```
SET gxApi "OpenGL"
```which does the same thing as starting WoW.exe -opengl.

---

### Post by SKLP on 2005-11-27
**Just a note**: the 1.9 test patch seems to work in neither wine nor cedega. someone will probably fix soon tho...

---

### Post by SKLP on 2005-11-27
[QUOTE=Burkey]Ok, I re-installed Ubuntu 5.10 clean.. then installed wine and set my Config.wtf as above, I now get a different error.

```

Your 3D Accelerator is not supported by World of Warcraft. Please install a 3D accelerator card with dual-TMU support.

```

So a kind of progress I guess.. breakfast now but will try some more things when I get back, hope someone might be able to shed some light[/QUOTE]That's odd :(

What 3d accelerator are you using? what does "glxinfo | grep direct" give?
what did you install instead of nvidia-glx-dev? 
and finally what does 
glxgears -iacknowledgethatthistoolisnotabenchmark give? :D

---

### Post by SKLP on 2005-11-27
[QUOTE=apoc]If not how to I uninstall it as it does not show up in Synaptic anymore. Thanks[/QUOTE]WoW was not installed through debian tools, hence it can't be removed using Synaptic. The best way to uninstall it is probably to cd into the source directory and type sudo make uninstall

---

### Post by apoc on 2005-11-27
Thanks SKLP, wow starts up fine now :) save for some looping sounds, maybe that was the part with regedit ? maybe you can specify in the guide where that file is ?

---

### Post by Burkey on 2005-11-28
I am on an Intel i915GM integrated video, which does accelerate SDL OpenGL apps and works fine in windows.

```

glxinfo | grep direct
direct rendering: Yes

```

I did not install any specific glx software, I just run with the Breezy defaults

```

glxgears -printfps
5151 frames in 5.0 seconds = 1030.031 FPS
5101 frames in 5.0 seconds = 1020.193 FPS
5084 frames in 5.0 seconds = 1016.682 FPS
5168 frames in 5.0 seconds = 1033.422 FPS

```

That is in 24-bit, in 16 it gives around 1500.

I do wonder about the GLX stuff, and this is not even isolated to just me, everyone I know using a i915 on Breezy has not got it working right, or have not used any 3D apps so don't know (yet)

Sadly I think it is a Breezy bug, since it worked out of the box on Hoary... how do I go about submitting this?

---

### Post by alynx on 2005-11-28
Finally i got it right :p :p 

Now i cant wait to play 

Thanks for a great guide , you helped me alot.

BTW , my windows xp sp 2 cd and w2k sp 4 cds is in my garbage can now.
I love it

---

### Post by GIBson3 on 2005-11-28
[QUOTE=Burkey]I am on an Intel i915GM integrated video, which does accelerate SDL OpenGL apps and works fine in windows.

```

glxinfo | grep direct
direct rendering: Yes

```

I did not install any specific glx software, I just run with the Breezy defaults

```

glxgears -printfps
5151 frames in 5.0 seconds = 1030.031 FPS
5101 frames in 5.0 seconds = 1020.193 FPS
5084 frames in 5.0 seconds = 1016.682 FPS
5168 frames in 5.0 seconds = 1033.422 FPS

```

That is in 24-bit, in 16 it gives around 1500.

I do wonder about the GLX stuff, and this is not even isolated to just me, everyone I know using a i915 on Breezy has not got it working right, or have not used any 3D apps so don't know (yet)

Sadly I think it is a Breezy bug, since it worked out of the box on Hoary... how do I go about submitting this?[/QUOTE]


Just a Guess here, but it sounds like the i915gm driver isn't loading Hardware accel support... (un)fortunately I refuse to use intel's graphics cards as they tend to be pretty flaky, and therefore can't direct you at which driver to throw at it.

[edit]redundant redundancey[/edit]

---

### Post by SKLP on 2005-11-28
[QUOTE=apoc]Thanks SKLP, wow starts up fine now :) save for some looping sounds, maybe that was the part with regedit ? maybe you can specify in the guide where that file is ?[/QUOTE]
You're welcome ;-)

regedit is the windows system registry editor, wine has a "clone" of it launchable from the command line by typing "regedit". 

Looping sounds should be unrelated to the changes in registry that i included in my howto.

Looping sounds is normal at the loading screen but if you are experiencing it during gameplay, try to increase the SET SoundBufferSize value in Config.wtf a bit.

---

### Post by Burkey on 2005-11-28
Sadly, I do not have a choice of what video card to use, it is built into the laptop.

This is just plain stupid, so far I have not been able to get either Enemy Territory (native) or WoW(Wine/Cedega) or HL(Wine/Cedega) to work.

Looks like I have no choice but windows, this is really beginning to jade my view on Ubuntu since other people say they switched distro's simply because Breezy could not use their i915 right.

---

### Post by alynx on 2005-11-29
[QUOTE=SKLP]Sorry. I forgot one thing  in my howto...

try this:

```
sudo -s
echo "/usr/local/lib" >> /etc/ld.so.conf
ldconfig

```


This was why I was failing the second time :cool: 

So now i hope this wil do the trick

---

### Post by apoc on 2005-11-30
Hello SKLP, after playing awile I have some new questions :)

1. Stuff like UI window posistions does save the changes I've made, I figure I have to edit some write permission on some files ? but where ?

2. How to I make a Icon to launch the game instead of open the terminal each time ?

Keep up the good work :D

---

### Post by Zodiac on 2005-11-30
Hey SKLP, when do you think you will have the "Installing WoW" section completed? 

Good work btw!

---

### Post by thegnark on 2005-11-30
i followed the steps on both my desktop and laptop... and it seems that opengl32.dll did not get built/installed/whatever. same error on both machines regarding the same file:


err:module:import_dll Library OPENGL32.dll (which is needed by L"C:\\Program Files\\World of Warcraft\\WoW.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\World of Warcraft\\WoW.exe" failed, status c0000135


even after a `sudo locate -u` and a `locate -i opengl32.dll`, nothing shows up on the system. I didn't install the nvidia-devel stuff since i have an ati chip. i did read that the ati stuff should be available as fglrx-devel, but `apt-cache search fglrx` returns only the restricted modules and xorg driver (yes, multiverse and universe are enables)


any thoughts?

---

### Post by Gordie on 2005-11-30
```
sudo -s
echo "/usr/local/lib" >> /etc/ld.so.conf
ldconfig
```

This was the code that ended up giving me the errors you describe thegnark, I had followed the howto, and ended up not doing the above statement the first time, and wow worked fine...

I just reversed the above changes and the error stopped happening.

You'll have to edit the /etc/ld.so.conf file like so:

sudo gedit /etc/ld.so.conf

Then just remove the line inside the file, save it and re-run ldconfig.

This should get you up and running

---

### Post by Suentis on 2005-12-01
I have gotten WoW working after a couple of bumps.  But the problem I am having is that it is really choppy, both video and sound.  I have an ATI 9800 video card if that helps.  I am not sure what exactly is causing it as I have tried most of the solutions in this thread.  Anyone have any advice?

---

### Post by SKLP on 2005-12-01
[QUOTE=apoc]Hello SKLP, after playing awile I have some new questions :)

1. Stuff like UI window posistions does save the changes I've made, I figure I have to edit some write permission on some files ? but where ?

2. How to I make a Icon to launch the game instead of open the terminal each time ?

Keep up the good work :D[/QUOTE]
Make the whole wow folder writeable...

To make an icon add a custom launcher to the panel in gnome and write something like wine /path/to/worldofwarcraft/WoW.exe as Command.

---

### Post by SKLP on 2005-12-01
[QUOTE=Zodiac]Hey SKLP, when do you think you will have the "Installing WoW" section completed? 

Good work btw![/QUOTE]I posted some instructions for this earlier in the thread. If you want you can try them and if it works tell me so i can add to the howto...

---

### Post by SKLP on 2005-12-01
[QUOTE=thegnark]i followed the steps on both my desktop and laptop... and it seems that opengl32.dll did not get built/installed/whatever. same error on both machines regarding the same file:


err:module:import_dll Library OPENGL32.dll (which is needed by L"C:\\Program Files\\World of Warcraft\\WoW.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\World of Warcraft\\WoW.exe" failed, status c0000135


even after a `sudo locate -u` and a `locate -i opengl32.dll`, nothing shows up on the system. I didn't install the nvidia-devel stuff since i have an ati chip. i did read that the ati stuff should be available as fglrx-devel, but `apt-cache search fglrx` returns only the restricted modules and xorg driver (yes, multiverse and universe are enables)


any thoughts?[/QUOTE]I think the proper package is xorg-driver-fglrx-dev
try to install that and recompile wine

---

### Post by SKLP on 2005-12-01
[QUOTE=Gordie]```
sudo -s
echo "/usr/local/lib" >> /etc/ld.so.conf
ldconfig
```

This was the code that ended up giving me the errors you describe thegnark, I had followed the howto, and ended up not doing the above statement the first time, and wow worked fine...

I just reversed the above changes and the error stopped happening.

You'll have to edit the /etc/ld.so.conf file like so:

sudo gedit /etc/ld.so.conf

Then just remove the line inside the file, save it and re-run ldconfig.

This should get you up and running[/QUOTE]
Why exactly would removing the library path wine is using from the system library path improve anything? it should only give errors like it cant load libwine etc

---

### Post by SKLP on 2005-12-01
Also, i think i will update the howto with wine 0.9.2, install instructions for wow, the ld.so.conf thingie, the fglrx stuff and also clarify how you can uninstall wow installed this way in the weekend.

---

### Post by Naveed on 2005-12-01
Getting the error: "World of Wacraft was unable to start up #3D Acceleration." when trying to run WoW, the screen flickers abit, changes resolution, flickers and back to normal then i get the error.

and config.wtf looks like this:
SET gxApi "opengl"
SET gxColorBits "24"
SET gxDepthBits "24"
SET gxResolution "800x600"
SET gxRefresh "60"
SET hwDetect "0"


Anyone that might know a solution on the problem?

Problem solved!

---

### Post by thegnark on 2005-12-01
[quote=Gordie]```
sudo -s
echo "/usr/local/lib" >> /etc/ld.so.conf
ldconfig
``` 
This was the code that ended up giving me the errors you describe thegnark, I had followed the howto, and ended up not doing the above statement the first time, and wow worked fine...

I just reversed the above changes and the error stopped happening.

You'll have to edit the /etc/ld.so.conf file like so:

sudo gedit /etc/ld.so.conf

Then just remove the line inside the file, save it and re-run ldconfig.

This should get you up and running[/quote]

negative. i tried removing it and got this whenever i ran wine:

wine: error while loading shared libraries: libwine.so.1: cannot open shared object file: No such file or directory

i re-added the line and wine will rune fine, but is still missing opengl32.dll as previous error shows

any other ideas on this one? is there somewhere i can check to see if opengl.dll didn't build and therefore couldn't install ?

---

### Post by apoc on 2005-12-01
[QUOTE=SKLP]Make the whole wow folder writeable...

To make an icon add a custom launcher to the panel in gnome and write something like wine /path/to/worldofwarcraft/WoW.exe as Command.[/QUOTE]

Is there an easy command for this, when I edit a folder, all files in it does not change :/

:edit:
found the command another place on this forum
```
sudo chmod +w -R /path/to/your/folder/*
```
:edit:

I've tried to make that icon alot, and I'm pretty sure the path is /home/apoc/.wine/drive_c/Program Files/Word of Warcraft/WoW.exe , but nomatter what it only works if I type it all into a terminal like this. wine /home/apoc/.wine/drive_c/Progra*/Wor*/WoW.exe . witch doesn't work as a icon either. :(

---

### Post by SKLP on 2005-12-03
[QUOTE=thegnark]i re-added the line and wine will rune fine, but is still missing opengl32.dll as previous error shows

any other ideas on this one? is there somewhere i can check to see if opengl.dll didn't build and therefore couldn't install ?[/QUOTE]That error is probably because wine was installed without OpenGL support due to it not finding OpenGL headers. (like the package nvidia-glx-dev provides for NVIDIA users)

---

### Post by SKLP on 2005-12-03
[QUOTE=apoc]I've tried to make that icon alot, and I'm pretty sure the path is /home/apoc/.wine/drive_c/Program Files/Word of Warcraft/WoW.exe , but nomatter what it only works if I type it all into a terminal like this. wine /home/apoc/.wine/drive_c/Progra*/Wor*/WoW.exe . witch doesn't work as a icon either. :([/QUOTE]Try the same but with quotes like this:
```
wine "/home/apoc/.wine/drive_c/Progra*/Wor*/WoW.exe"
```

---

### Post by moccah on 2005-12-03
Bah, I`ll cant install xorg-driver-fglrx-dev

it says:
```
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  xorg-driver-fglrx-dev: Depends: xorg-driver-fglrx (= 6.8.0-8.16.20-0ubuntu16.1) but 8.19.10-1 is to be installed
E: Broken packages

```

I`ve installed the ATI driver, 8.19.10, anyone have a fix for that?

Great FAQ btw! :D
To bad I`m not able to run WoW because of the ATI dev files...

Regards
Moccah

---

### Post by YokoZar on 2005-12-03
I updated the wiki page.  You really should just install the build dependencies for the Wine package via apt-get build-dep wine -- making a hand list will guarentee you're forgetting some.

---

### Post by moccah on 2005-12-04
> I updated the wiki page. You really should just install the build dependencies for the Wine package via apt-get build-dep wine -- making a hand list will guarentee you're forgetting some.

Can you please link the wiki page ?

---

### Post by moccah on 2005-12-04
I`ve tried to install wine using the src..
but when i:
```
wine WoW.exe
```
I only get an error, and the whole aplication stops..
gah, it worked almost perfect with cedega4.. but now even that doesn`t work..

Switching to Windows is still not an option!!

Any suggestions?:confused:

---

### Post by alynx on 2005-12-05
I have experienced some lag problems , but the game is up and running in every way.

When i get quests and move into a populated area it starts lagging.

I use Gforce 6600 GT BTW , and i have installed the nvidia-glx-dev package.
I have also changed the xorg.conf file and traded nv driver to nvidia.

Am i doing something wrong here? Thinking maybe there would be some Opengl problems that causes this

Or is it something that will fix it in the wine installation? i followed the howto

---

### Post by thegnark on 2005-12-05
what repos have the nvidia and fglrx development stuff? neither show up in apt-cache

---

### Post by SKLP on 2005-12-06
[QUOTE=YokoZar]I updated the wiki page.  You really should just install the build dependencies for the Wine package via apt-get build-dep wine -- making a hand list will guarentee you're forgetting some.[/QUOTE]I know about apt-get build-dep.
The deps i stated in the howto was enough for this to work. Though i suppose that was a cleaner way to do it, but it installs dependencies that are not needed...

Well maybe the howto should be revamped to use apt-get source wine from the winehq repository. And both patches should be merged into a wow.dpatch...
It would be best if someone told me how to make it apply -wow to all libs/executables it installs so we could make wine-wow debs that would be parallell installable with normal ubuntu wine...

---

### Post by SKLP on 2005-12-06
[QUOTE=moccah]I only get an error, and the whole aplication stops..[/QUOTE]
What is the error? Also did you follow the instructions at [https://wiki.ubuntu.com/WorldofWarcraftHowto](https://wiki.ubuntu.com/WorldofWarcraftHowto) and did u read the whole thread?

---

### Post by SKLP on 2005-12-06
[QUOTE=thegnark]what repos have the nvidia and fglrx development stuff? neither show up in apt-cache[/QUOTE]In ubuntu's restricted repository (enabled by default)

---

### Post by SKLP on 2005-12-06
I haven't had time to update the howto, like i wrote earlier i want to revamp the howto but i don't have time ATM...

---

### Post by thegnark on 2005-12-06
[quote=SKLP]In ubuntu's restricted repository (enabled by default)[/quote] 
apt-cache:
```
taylorg@marzipan:~$ apt-cache search fglrx
linux-restricted-modules-2.6.12-10-386 - Non-free Linux 2.6.12 modules on 386
xorg-driver-fglrx - Video driver for ATI graphics accelerators
linux-restricted-modules-2.6.12-10-686 - Non-free Linux 2.6.12 modules on PPro/Celeron/PII/PIII/PIV
xserver-xorg-driver-ati - X.Org X server -- ATI driver

``` 
and my repos:
```

deb-src http://archive.ubuntu.com/ubuntu breezy main restricted
deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy universe
deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted
deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe
deb http://archive.ubuntu.com/ubuntu/ breezy universe main restricted multiverse
deb http://wine.sourceforge.net/apt/ binary/
deb http://people.ubuntu.com/~doko/OOo2 ./
deb http://public.planetmirror.com/pub/plf/ubuntu/plf/ breezy free non-free
deb ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ breezy free non-free
deb-src ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ breezy free non-free

```

:confused:

---

### Post by ShotWeb on 2005-12-06
I copied WoW from my windows partition to my linux partition, i'm running the game on the current version (new patch this morning.. 1.8.4 i believe), the game works up until the login screen. I login and it authenticates then the game crashes and i get the WoW error reporting screen. anyone else have problems like this?

---

### Post by thegnark on 2005-12-06
[quote=ShotWeb]I copied WoW from my windows partition to my linux partition, i'm running the game on the current version (new patch this morning.. 1.8.4 i believe), the game works up until the login screen. I login and it authenticates then the game crashes and i get the WoW error reporting screen. anyone else have problems like this?[/quote]

AFAIK, you should be able to just run it directly off your windows partition. i guess just don't depend on being able to save config options though

---

### Post by Sandlst on 2005-12-07
Hey guys!
First of all, THANK YOU SKLP your guide worked flawlessly for me, but alas I have a problem hehe......Ive installed WoW under wine, updated to lastest patch, but right after I hit the 'ok' to log in my screen goes black for some reason....its just my screen though I think b/c i can hear the sounds of entering what I assume is the realmlist menus by hitting enter, but obviously this doesnt help much...Ive run WoW on this computer through windows, so I know my video card is capable of working....I have an nvidia GeForce Go 6800 with all latest drivers installed, 256 MB.  If any of you can help me I would be very appreciative, thank you in advance :)

---

### Post by YokoZar on 2005-12-08
[QUOTE=Sandlst]Hey guys!
First of all, THANK YOU SKLP your guide worked flawlessly for me, but alas I have a problem hehe......Ive installed WoW under wine, updated to lastest patch, but right after I hit the 'ok' to log in my screen goes black for some reason....its just my screen though I think b/c i can hear the sounds of entering what I assume is the realmlist menus by hitting enter, but obviously this doesnt help much...Ive run WoW on this computer through windows, so I know my video card is capable of working....I have an nvidia GeForce Go 6800 with all latest drivers installed, 256 MB.  If any of you can help me I would be very appreciative, thank you in advance :)[/QUOTE]
Have you enabled the nvidia drivers?  You have to run a command in the terminal after installing them with Synaptic.

---

### Post by Bicky on 2005-12-10
I'm still not able to fix that mouse bug, even with the patch I can't clik on enemies and stuff.

---

### Post by Sandlst on 2005-12-10
[QUOTE=YokoZar]Have you enabled the nvidia drivers?  You have to run a command in the terminal after installing them with Synaptic.[/QUOTE]

Hmm...I followed the directions from the starter guide, so I have done the  ```
sudo nvidia-glx-config enable
```, is that what you mean?

---

### Post by Sandlst on 2005-12-10
[QUOTE=Sandlst]Hey guys!
First of all, THANK YOU SKLP your guide worked flawlessly for me, but alas I have a problem hehe......Ive installed WoW under wine, updated to lastest patch, but right after I hit the 'ok' to log in my screen goes black for some reason....its just my screen though I think b/c i can hear the sounds of entering what I assume is the realmlist menus by hitting enter, but obviously this doesnt help much...Ive run WoW on this computer through windows, so I know my video card is capable of working....I have an nvidia GeForce Go 6800 with all latest drivers installed, 256 MB.  If any of you can help me I would be very appreciative, thank you in advance :)[/QUOTE]

fixed, Ill post here just in case.....I found this in the Gentoo wow forum btw, all you have to do is change the Permissions of the WDB folder to non-writable by anyone.
Pffft now that it works my realm is down :rolleyes:

---

### Post by inthepit on 2005-12-10
Tried to install wine and such...  failed... dont know what went wrong.  here is what i did...

```
alex@inthepit:~$ mkdir ~/temp-winebuild
alex@inthepit:~$ cd ~/temp-winebuild
alex@inthepit:~/temp-winebuild$ wget http://ibiblio.org/pub/linux/system/emulators/wine/wine-0.9.1.tar.bz2
--15:28:47--  http://ibiblio.org/pub/linux/system/emulators/wine/wine-0.9.1.tar.bz2
           => `wine-0.9.1.tar.bz2'
Resolving ibiblio.org... 152.2.210.80
Connecting to ibiblio.org|152.2.210.80|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 10,165,557 (9.7M) [application/x-tar]

100%[====================================>] 10,165,557    46.33K/s    ETA 00:00

15:30:53 (79.05 KB/s) - `wine-0.9.1.tar.bz2' saved [10165557/10165557]

alex@inthepit:~/temp-winebuild$ tar xjf wine-0.9.1.tar.bz2

alex@inthepit:~/temp-winebuild$
alex@inthepit:~/temp-winebuild$ wget http://polynomial-c.homelinux.net/pub/gentoo/portage/app-emulation/wine/files/wine-wow_fixes.patch
--15:31:22--  http://polynomial-c.homelinux.net/pub/gentoo/portage/app-emulation/wine/files/wine-wow_fixes.patch
           => `wine-wow_fixes.patch'
Resolving polynomial-c.homelinux.net... 84.172.69.2
Connecting to polynomial-c.homelinux.net|84.172.69.2|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1,577 (1.5K) [text/plain]

100%[====================================>] 1,577         --.--K/s

15:31:28 (56.98 KB/s) - `wine-wow_fixes.patch' saved [1577/1577]

alex@inthepit:~/temp-winebuild$ cd wine-0.9.1
alex@inthepit:~/temp-winebuild/wine-0.9.1$ patch -p0 < ../wine-wow_fixes.patch
patching file libs/wine/mmap.c
patching file loader/preloader.c
alex@inthepit:~/temp-winebuild/wine-0.9.1$ edit
alex@inthepit:~/temp-winebuild/wine-0.9.1$ sudo gedit dlls/opengl32/opengl_norm.c
alex@inthepit:~/temp-winebuild/wine-0.9.1$ sudo apt-get install build-essential fglrx-driver-dev
Reading package lists... Done
Building dependency tree... Done
Package fglrx-driver-dev is a virtual package provided by:
  xorg-driver-fglrx-dev 6.8.0-8.16.20-0ubuntu16.1
You should explicitly select one to install.
E: Package fglrx-driver-dev has no installation candidate
alex@inthepit:~/temp-winebuild/wine-0.9.1$ sudo apt-get build-dep wine
Reading package lists... Done
Building dependency tree... Done
E: Unable to find a source package for wine
alex@inthepit:~/temp-winebuild/wine-0.9.1$ ./configure && make depend && make
checking build system type... i686-pc-linux-gnuoldld
checking host system type... i686-pc-linux-gnuoldld
checking whether make sets $(MAKE)... no
checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.
alex@inthepit:~/temp-winebuild/wine-0.9.1$
alex@inthepit:~/temp-winebuild/wine-0.9.1$ sudo make install
sudo: make: command not found
alex@inthepit:~/temp-winebuild/wine-0.9.1$

```

could someone please help.  find me on aim: oOinthepitOo

---

### Post by Sandlst on 2005-12-10
AcK! After discovering I couldnt click anything in-game, I eventually figured out that I had previously installed wine from synaptic (ie no mouse patch) before following the HowTo (and missing the part about uninstall heh) so I had to basically do everything again, worked ok until I tried to log in. Attempt ing to log into my two main characters, it crashes after the loading screen is finished-terminal outputs this:
```
sandlst@node-194:~$ wine '/home/sandlst/.wine/drive_c/Program Files/World of Warcraft/WoW.exe'
fixme:advapi:SetSecurityInfo stub
fixme:powrprof:DllMain (0x7cbf0000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 11
fixme:powrprof:DllMain (0x7cbf0000, 0, (nil)) not fully implemented
fixme:win:EnumDisplayDevicesW ((null),0,0x7fb2ef00,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7fb2f16c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7fb2f70c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7fb2f70c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7fb2f674,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)fixme:win:EnumDisplayDevicesW ((null),0,0x7fb2f660,0x00000000), stub!
fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 16 to 32fixme:win:EnumDisplayDevicesW ((null),0,0x7fb2f674,0x00000000), stub!
err:opengl:wglCreatePbufferARB ((nil)): unexpected iPixelFormat(0) <= 0, returns NULL
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)err:opengl:wglCreatePbufferARB ((nil)): unexpected iPixelFormat(0) <= 0, returns NULL
fixme:win:EnumDisplayDevicesW ((null),0,0x7fb2f660,0x00000000), stub!
fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 16 to 32fixme:win:EnumDisplayDevicesW ((null),0,0x7fb2f674,0x00000000), stub!
err:opengl:wglCreatePbufferARB ((nil)): unexpected iPixelFormat(0) <= 0, returns NULL
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)err:opengl:wglCreatePbufferARB ((nil)): unexpected iPixelFormat(0) <= 0, returns NULL
fixme:win:EnumDisplayDevicesW ((null),0,0x7fb2f660,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7fb2ee78,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 112 (SPI_GETMOUSESPEED)fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)fixme:sync:CreateIoCompletionPort (0xffffffff, (nil), 00000000, 00000000): stub.fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_RECEIVE_TIMEOUT: STUB
fixme:wininet:InternetSetOptionW Option 45 STUB
fixme:imm:ImmGetContext (0x30022): stub
fixme:imm:ImmGetContext (0x30022): stub
fixme:imm:ImmGetContext (0x30022): stub
fixme:opengl:wglQueryPbufferARB unsupported WGL_PBUFFER_LOST_ARB (need glXSelectEvent/GLX_DAMAGED work)
fixme:win:EnumDisplayDevicesW ((null),0,0x7fb2e524,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7fb2e57c,0x00000000), stub!
err:opengl:wglGetPixelFormatAttribivARB unexpected RenderType(4)
err:opengl:wglGetPixelFormatAttribivARB unexpected RenderType(4)
err:opengl:wglGetPixelFormatAttribivARB unexpected RenderType(4)
err:opengl:wglGetPixelFormatAttribivARB unexpected RenderType(4)
err:opengl:wglGetPixelFormatAttribivARB unexpected RenderType(4)
err:opengl:wglGetPixelFormatAttribivARB unexpected RenderType(4)
err:opengl:wglGetPixelFormatAttribivARB unexpected RenderType(4)
err:opengl:wglGetPixelFormatAttribivARB unexpected RenderType(4)
err:opengl:wglGetPixelFormatAttribivARB unexpected RenderType(4)
err:opengl:wglGetPixelFormatAttribivARB unexpected RenderType(4)
err:opengl:wglGetPixelFormatAttribivARB unexpected RenderType(4)
err:opengl:wglGetPixelFormatAttribivARB unexpected RenderType(4)
err:opengl:wglGetPixelFormatAttribivARB unexpected RenderType(4)
err:opengl:wglGetPixelFormatAttribivARB unexpected RenderType(4)
err:opengl:wglGetPixelFormatAttribivARB unexpected RenderType(4)
err:opengl:wglGetPixelFormatAttribivARB unexpected RenderType(4)
err:opengl:wglGetPixelFormatAttribivARB unexpected RenderType(4)
err:opengl:wglGetPixelFormatAttribivARB unexpected RenderType(4)
err:opengl:wglGetPixelFormatAttribivARB unexpected RenderType(4)
err:opengl:wglGetPixelFormatAttribivARB unexpected RenderType(4)
err:opengl:wglGetPixelFormatAttribivARB unexpected RenderType(4)
err:opengl:wglGetPixelFormatAttribivARB unexpected RenderType(4)
err:opengl:wglGetPixelFormatAttribivARB unexpected RenderType(4)
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  5 (X_GLXMakeCurrent)
  Serial number of failed request:  523
  Current serial number in output stream:  523

```
just in case it's relevant-my Character is in a 'full' pop. server and is located in Iron Forge-a major lag source at best-and my other char is in Stormwind

Whats strange tho is if I try and make a new char (on the server or any other server) it works fine, any ideas?:confused:
Actually scratch that-playing a new character works fine until I have to enter any kind of building...when that happens I get the same thing.

---

### Post by Bicky on 2005-12-11
I installed wine again, trying to fix this mouse bug.  But it couldn't find the wine packages when I typed 'apt-get build-dep wine'. I hoped it would work without it too. so I continued. But now the bug still isn't gone. and you've said that it would give the message that it wanted to install activex but he didn't asked for that neither... 

Is it this package that I missed caused the mouse bug ?

---

### Post by glaze on 2005-12-12
You don't have the C compiler installed. Do "apt-get install build-essential"

---

### Post by alynx on 2005-12-12
Does anyone actually run Wow without some lag ? 

please help this badger

---

### Post by glaze on 2005-12-12
[QUOTE=alynx]Does anyone actually run Wow without some lag ? 

please help this badger[/QUOTE]

o/ runs fine. AXP 2400+, 1024 MiB RAM, GF5900XT, Wine 0.9.1 (0.9.3 didn't work for me)

---

### Post by alynx on 2005-12-12
i think it comes down to my graphics driver.
I use the 7667 , and they lag , tried to get the nevest ones from nvidia.

But i ended up crashing my whole xserver. 

So i (impatient that i am ) reinnstalled Ubuntu and followed SKLP's guide again and now i am back with the 7667 drivers.

Im trying again tomorrow when my eyes don't bleed

---

### Post by inthepit on 2005-12-13
well i finally got wow running for the most part...  now my problem lies in keeping it running... i'm not even in game after character select for 30 seconds, and it crashes out with Error #132.  something about couldn't write to memory.  pretty sure i patched wine for WoW, and i know my graphics and all are set up.  anyone have this problem?  would like to get it running finally... been workin on this for a few days now.  
*Edit* could it possibly be because of Alsa drivers?  when i went to fix the reg key in wine, Alsa drivers weren't there.

---

### Post by thegnark on 2005-12-14
i finally got WoW running with the patched 0.9.1 wine mentioned in this thread. i would like to see an update for 0.9.3 (basically, a new pathc file) just for giggles

i can walk around, target stuff, etc. it's great, albeit very slow (due mostly to it being run on my underpowered celeron laptop - i imaging my athlon 3000 with 1.5 gig ram and radeon 9700 at home would do much better).

of course, this was under directx (i haven't tried with opengl yet). i definately wouldn't trust it to go raiding bwl (nef's room is horribly laggy on high-end systems), but i supposed it's good enough to go questing for lowbies

one problem i do ntice, is the viewpoint doesn't seem to work perfectly witht he mouse - it's almost like it's extra sensitive - but that doesn't hit it perfectly. the room kind of wildly spins around, and i have little control over looking up/down.

for now, at least i can get on for guild chat and check AH, etc. if i can get the viewpoint problem fixed, i could continue leveling my alts

---

### Post by alynx on 2005-12-14
holy ***** , stupid me , it works really fine when i emulate XP instead of W2k which is default. 

:p :p :p :p :p

---

### Post by arpunk on 2005-12-15
Well, it works great, but its not playable for me :/, i cant see some textures and the ground gets black. I dont see the characters and so on, hehe im a walking weapon :O, ill post a screenshot as soon my realm is up again :P.

---

### Post by Takeshi on 2005-12-17
brian@Brian:~/temp-winebuild/wine-0.9.1$ sudo apt-get install build-essential fglrx-driver-devReading package lists... Done
Building dependency tree... Done
build-essential is already the newest version.
Package fglrx-driver-dev is a virtual package provided by:
  xorg-driver-fglrx-dev 6.8.0-8.16.20-0ubuntu16.1
You should explicitly select one to install.
E: Package fglrx-driver-dev has no installation candidate
brian@Brian:~/temp-winebuild/wine-0.9.1$ sudo apt-get build-dep wine
Reading package lists... Done
Building dependency tree... Done
E: Unable to find a source package for wine


I cant get past these errors [Complete noob] Can somone help me???

---

### Post by Des33 on 2005-12-17
hey all... i can get to the world of warcraft login screen just fine.. but after it restarts and downloads the latest update.. i get this in my terminal..

sorry its a bit lengthy...

```

tpath@ubuntu:~/.wine/drive_c/Program Files/World of Warcraft$ I see 100% - Blizzard Downloader
I see Log
fixme:actctx:CreateActCtxW stub!
wine: Unhandled page fault on read access to 0x7c83b0f4 at address 0x7ee5e809 (thread 0032), starting debugger...
WineDbg starting on pid 0x30
I see Blizzard Updater
I see Blizzard Updater
I see DDE Server Window
I see OleMainThreadWndName
I see 100% - Blizzard Downloader
I see Log
I see Blizzard Updater
I see Blizzard Updater
I see DDE Server Window
I see OleMainThreadWndName
I see 100% - Blizzard Downloader
I see Log
Unhandled exception: page fault on read access to 0x7c83b0f4 in 32-bit code (0x7ee5e809).
In 32 bit mode.
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:1157 GS:0033
 EIP:7ee5e809 ESP:7c82d6f4 EBP:7c82d700 EFLAGS:00210212(   - 00      - RIA1)
 EAX:0000d88c EBX:7eea0bc8 ECX:0000d88c EDX:7c83b0f4
 ESI:7c82d868 EDI:7c82d868
Stack dump:
0x7c82d6f4:  7eea0bc8 7fdffd80 7c82d868 7c82d71c
0x7c82d704:  7ee5e840 7c82d868 7efcdda0 7c82d868
0x7c82d714:  7fdffd80 00000000 7c82d738 7103601a
0x7c82d724:  7c82d868 7fdffd80 00000001 7fdff798
0x7c82d734:  00000000 7c82d754 7108e5d5 7fdffd70
0x7c82d744:  7c82d868 00000001 7fe063a0 7c82d844
022a: sel=1157 base=7ec30000 limit=00001fff 32-bit rw-
Backtrace:
=>1 0x7ee5e809 ILGetSize+0x79 in shell32 (0x7ee5e809)
  2 0x7ee5e840 ILClone+0x20 in shell32 (0x7ee5e840)
fixme:dbghelp:sffip_cb NIY on 'C:\Lego\opt\SHDOCVW.pdb'
  3 0x7103601a in shdocvw (+0x3601a) (0x7103601a)
  4 0x7108e5d5 in shdocvw (+0x8e5d5) (0x7108e5d5)
  5 0x7108bb85 in shdocvw (+0x8bb85) (0x7108bb85)
err:dbghelp:pe_load_dbg_file -Unable to peruse .DBG file MFC42.dbg ("MFC42.dbg")  6 0x5f42c582 2242+0x1da in mfc42 (0x5f42c582)
  7 0x5f42c01b 424+0xecd in mfc42 (0x5f42c01b)
  8 0x5f42b32b 424+0x1dd in mfc42 (0x5f42b32b)
  9 0x5f42ac23 2143+0x20d in mfc42 (0x5f42ac23)
  10 0x5f42a891 451+0xee4 in mfc42 (0x5f42a891)
  11 0x5f42a79e 451+0xdf1 in mfc42 (0x5f42a79e)
  12 0x5f41f3e6 in mfc42 (+0x1f3e6) (0x5f41f3e6)
  13 0x5f40230b 290+0xca0 in mfc42 (0x5f40230b)
  14 0x5f402294 290+0xc29 in mfc42 (0x5f402294)
  15 0x5f40221f 290+0xbb4 in mfc42 (0x5f40221f)
  16 0x5f4021d6 290+0xb6b in mfc42 (0x5f4021d6)
  17 0x7ef8f65a WINPROC_wrapper+0x1a in user32 (0x7ef8f65a)
  18 0x7ef90200 in user32 (+0x80200) (0x7ef90200)
  19 0x7ef951ee CallWindowProcW+0x11e in user32 (0x7ef951ee)
  20 0x7ef653ef in user32 (+0x553ef) (0x7ef653ef)
  21 0x7ef68b06 SendMessageTimeoutW+0x156 in user32 (0x7ef68b06)
  22 0x7ef68b55 SendMessageW+0x35 in user32 (0x7ef68b55)
  23 0x7ef3c562 in user32 (+0x2c562) (0x7ef3c562)
  24 0x7ef3cefd CreateDialogIndirectParamAorW+0x2d in user32 (0x7ef3cefd)
  25 0x7ef3cfdb CreateDialogIndirectParamA+0x2b in user32 (0x7ef3cfdb)
  26 0x5f40bc7b 299+0x411 in mfc42 (0x5f40bc7b)
  27 0x5f404ff4 261+0x14d in mfc42 (0x5f404ff4)
  28 0x7ef90200 in user32 (+0x80200) (0x7ef90200)
  29 0x7ef93595 CallWindowProcA+0x185 in user32 (0x7ef93595)
  30 0x7ef65386 in user32 (+0x55386) (0x7ef65386)
  31 0x7ef6637b in user32 (+0x5637b) (0x7ef6637b)
  32 0x7ef677f2 PeekMessageW+0xa2 in user32 (0x7ef677f2)
  33 0x7ef67967 GetMessageW+0x57 in user32 (0x7ef67967)
  34 0x7ef67b76 GetMessageA+0x26 in user32 (0x7ef67b76)
  35 0x00417327 EntryPoint+0x617 in bnupdate (0x00417327)
  36 0x7bedc34f in ntdll (+0x3c34f) (0x7bedc34f)
I see Blizzard Updater
I see Blizzard Updater
I see DDE Server Window
I see OleMainThreadWndName
I see 100% - Blizzard Downloader
  37 0xb7f60361 start_thread+0x81 in libpthread.so.0 (0xb7f60361)
I see Log
I see Blizzard Updater
I see Blizzard Updater
I see DDE Server Window
I see OleMainThreadWndName
I see 100% - Blizzard Downloader
I see Log
  38 0xb7ef4bde __clone+0x5e in libc.so.6 (0xb7ef4bde)
0x7ee5e809 ILGetSize+0x79 in shell32: movw      0x0(%edx),%ax
Modules:
Module  Address                 Debug info      Name (73 modules)
PE      0x00400000-00491000     Export          bnupdate
PE      0x5a800000-5a80f000     Deferred        pstorec
PE      0x5e380000-5e3a5000     Deferred        msoss
PE      0x5f400000-5f4ed000     Export          mfc42
PE      0x65340000-653d2000     Deferred        oleaut32
PE      0x65f00000-65fc2000     Deferred        ole32
PE      0x70100000-70153000     Deferred        rpcrt4
PE      0x70200000-70295000     Deferred        wininet
PE      0x70bd0000-70c35000     Deferred        shlwapi
PE      0x71000000-71149000     Export          shdocvw
PE      0x71450000-714ae000     Deferred        crypt32
PE      0x78000000-78040000     Deferred        msvcrt
ELF     0x7be8d000-7bf00000     Export          ntdll<elf>
  \-PE  0x7bea0000-7bf00000     \               ntdll
ELF     0x7bf00000-7bf03000     Deferred        <wine-loader>
ELF     0x7c5b3000-7c610000     Deferred        winedos<elf>
  \-PE  0x7c5c0000-7c610000     \               winedos
ELF     0x7c83f000-7c853000     Deferred        vwin32.vxd<elf>
  \-PE  0x7c850000-7c853000     \               vwin32.vxd
ELF     0x7e02c000-7e05d000     Deferred        uxtheme<elf>
  \-PE  0x7e030000-7e05d000     \               uxtheme
ELF     0x7e0dc000-7e0e5000     Deferred        libxcursor.so.1
ELF     0x7e0e5000-7e101000     Deferred        imm32<elf>
  \-PE  0x7e0f0000-7e101000     \               imm32
ELF     0x7e101000-7e11d000     Deferred        ximcp.so.2
ELF     0x7e11d000-7e886000     Deferred        libglcore.so.1
ELF     0x7e886000-7e905000     Deferred        libgl.so.1
ELF     0x7e905000-7e9c5000     Deferred        libx11.so.6
ELF     0x7e9c5000-7e9de000     Deferred        libice.so.6
ELF     0x7e9de000-7ea5a000     Deferred        winex11.drv<elf>
  \-PE  0x7e9f0000-7ea5a000     \               winex11.drv
ELF     0x7ea5a000-7ea79000     Deferred        libexpat.so.1
ELF     0x7ea79000-7eaa7000     Deferred        libfontconfig.so.1
ELF     0x7eaaa000-7eab2000     Deferred        libxrender.so.1
ELF     0x7eab2000-7eac6000     Deferred        libz.so.1
ELF     0x7eac6000-7eb30000     Deferred        libfreetype.so.6
ELF     0x7ec3c000-7ec40000     Deferred        libxdmcp.so.6
ELF     0x7ed51000-7ed65000     Deferred        lz32<elf>
  \-PE  0x7ed60000-7ed65000     \               lz32
ELF     0x7ed65000-7ed7d000     Deferred        version<elf>
  \-PE  0x7ed70000-7ed7d000     \               version
ELF     0x7ed7d000-7ee2b000     Deferred        comctl32<elf>
  \-PE  0x7ed90000-7ee2b000     \               comctl32
ELF     0x7ee2b000-7eeea000     Export          shell32<elf>
  \-PE  0x7ee40000-7eeea000     \               shell32
ELF     0x7eeea000-7f000000     Export          user32<elf>
  \-PE  0x7ef10000-7f000000     \               user32
ELF     0x7f000000-7f03a000     Deferred        advapi32<elf>
  \-PE  0x7f010000-7f03a000     \               advapi32
ELF     0x7f120000-7fa20000     Deferred        gdi32<elf>
  \-PE  0x7f170000-7fa20000     \               gdi32
ELF     0x7fb23000-7fb30000     Deferred        libxext.so.6
ELF     0x7fb32000-7fb37000     Deferred        libxxf86vm.so.1
ELF     0x7fb37000-7fb3c000     Deferred        libxxf86dga.so.1
ELF     0x7fc84000-7fd80000     Deferred        kernel32<elf>
  \-PE  0x7fca0000-7fd80000     \               kernel32
ELF     0x7fd83000-7fd85000     Deferred        libnvidia-tls.so.1
ELF     0x7fd85000-7fd90000     Deferred        libgcc_s.so.1
ELF     0x7fea1000-7fea8000     Deferred        libsm.so.6
ELF     0x7fea8000-7feb2000     Deferred        libnss_files.so.2
ELF     0x7feb2000-7febb000     Deferred        libnss_nis.so.2
ELF     0x7febb000-7fed0000     Deferred        libnsl.so.1
ELF     0x7fed0000-7fed9000     Deferred        libnss_compat.so.2
ELF     0x7fedc000-7fee0000     Deferred        libxfixes.so.3
ELF     0x7fee0000-7fee2000     Deferred        xlcutf8load.so.2
ELF     0x7fee7000-7ff09000     Deferred        libm.so.6
ELF     0x7ff09000-80000000     Deferred        libwine_unicode.so.1
ELF     0xb7e29000-b7e2c000     Deferred        libdl.so.2
ELF     0xb7e2c000-b7f5a000     Export          libc.so.6
ELF     0xb7f5b000-b7f6d000     Export          libpthread.so.0
ELF     0xb7f6d000-b7f87000     Deferred        libwine.so.1
ELF     0xb7f87000-b7f8a000     Deferred        libxau.so.6
ELF     0xb7f95000-b7fab000     Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000030 (D) C:\Program Files\World of Warcraft\BNUpdate.exe
        00000032    0 <==
        00000031    0
00000024
        0000002e    0
        0000002b    0
        0000002a    0
        00000029    0
0000001f
        00000026    0
00000024
        00000025    0
0000001f
        00000023    0
        00000022    0
        00000021    0
        00000020    0
WineDbg terminated on pid 0x30
I see 100% - Blizzard Downloader
I see Log
I see 100% - Blizzard Downloader
I see Log

```

any ideas what could be the problem..

the update/installer just quits after that... nothing happens.. start WoW again.. same process...

my apolgies for the length..

---

### Post by ghost051 on 2005-12-18
im a big fan of the Mac OSX, which i run wow on, but my bro wants to turn to linux instead of windows xp and he gets the error:

err:module:load_builtin_dll failed to load .so lib for builtin L"OPENGL32.dll": libGLU.so.1: cannot open shared object file: No such file or directory
err:module:import_dll Loading library OPENGL32.dll (which is needed by L"D:\\ghost051\\WorldofWarcraft\\wow.exe") failed (error c000007a).
err:module:load_builtin_dll failed to load .so lib for builtin L"GLU32.dll": libGLU.so.1: cannot open shared object file: No such file or directory
err:module:import_dll Loading library GLU32.dll (which is needed by L"D:\\ghost051\\WorldofWarcraft\\wow.exe") failed (error c000007a).
err:module:LdrInitializeThunk Main exe initialization for L"D:\\ghost051\\WorldofWarcraft\\wow.exe" failed, status c0000135

and i have been on it for days, looking at websites and forums and such, any assistance would benefit, ive read the whole thread here and none of the aditional commands did anything.

he used wine to install from all 4 disks, inserted each disk when it asked for it, and when he tried to run 'wine wow.exe' he got the error above.

---

### Post by Niz972 on 2005-12-18
ok.. i followed all instructions in the howto. got to the point to just after i compiled wine. Says now install wine: sudo make install

question is.. now how do i actually install it ? (noob..):confused: Oh. and if someone could actually send me a tell over aim, or just skype me (niz972) thatd be even better. im very.. very new to all this stuff.

---

### Post by mithien on 2005-12-18
Forewarning, this is the first time I've used a *nix system in 6 years. I was never good at it, and you could probably consider me to be a beginner.

chris@ubuntu:~/temp-winebuild/wine-0.9.1$ sudo apt-get build-dep wine
Password:
Reading package lists... Done
Building dependency tree... Done
E: You must put some 'source' URIs in your sources.list
chris@ubuntu:~/temp-winebuild/wine-0.9.1$

I ended up manually installing a few but I must have missed some, the install went for about 3 minutes and crashed. I don't know howto/whether to delete whats been written or to just fix the dependancy sources issue.

I don't know where to get any source URI's, and I'm not 100% what they mean...I'm guessing places to get dependancies.



Any help is greatly appreciated.
Katan1a on AIM if chatting makes help any easier.

---

### Post by thegnark on 2005-12-19
[quote=Niz972]ok.. i followed all instructions in the howto. got to the point to just after i compiled wine. Says now install wine: sudo make install

question is.. now how do i actually install it ? (noob..):confused: Oh. and if someone could actually send me a tell over aim, or just skype me (niz972) thatd be even better. im very.. very new to all this stuff.[/quote]

exactly what it says: **sudo make install**

---

### Post by thegnark on 2005-12-19
[quote=mithien]Forewarning, this is the first time I've used a *nix system in 6 years. I was never good at it, and you could probably consider me to be a beginner.

chris@ubuntu:~/temp-winebuild/wine-0.9.1$ sudo apt-get build-dep wine
Password:
Reading package lists... Done
Building dependency tree... Done
E: You must put some 'source' URIs in your sources.list
chris@ubuntu:~/temp-winebuild/wine-0.9.1$

I ended up manually installing a few but I must have missed some, the install went for about 3 minutes and crashed. I don't know howto/whether to delete whats been written or to just fix the dependancy sources issue.

I don't know where to get any source URI's, and I'm not 100% what they mean...I'm guessing places to get dependancies.



Any help is greatly appreciated.
Katan1a on AIM if chatting makes help any easier.[/quote]

you probably need to turn on the source repositories in apt. the easy way to do this is like so:
alt+f2
sudo synaptic
settings menu
repositories
settings button
check "show disabled software sources"
close button
check the stuff where is says "(source)" on the right of the repository name
OK button

now you can try to **apt-get build-dep wine** again

---

### Post by Niz972 on 2005-12-19
[QUOTE=thegnark]exactly what it says: **sudo make install**[/QUOTE]
well i tried that, but now it acts like its not even installed.. nothing happens when i click on my old ie6 or anything that uses wine.

---

### Post by thegnark on 2005-12-19
[quote=Niz972]well i tried that, but now it acts like its not even installed.. nothing happens when i click on my old ie6 or anything that uses wine.[/quote]

what happens when you type just the command **wine** ? if it's somethign to the effect of *cannot find*, then a simple symlink may fix this. on my system, it's looking for /usr/local/bin/wine, but it's actually located at  /usr/bin/wine, so i simply made a symlink. if this is the case, try this:** sudo ln -s /usr/bin/wine /usr/local/bin/wine**

also, did you make sure to uninstall the wine installed by apt first? if you didn't you'll, probably need to **cd ~/temp-winebuild/wine-0.9.1 && sudo make uninstall && sudo apt-get remove wine && sudo make install**.

---

### Post by Orangecrush on 2005-12-19
[QUOTE=Takeshi]brian@Brian:~/temp-winebuild/wine-0.9.1$ sudo apt-get install build-essential fglrx-driver-devReading package lists... Done
Building dependency tree... Done
build-essential is already the newest version.
Package fglrx-driver-dev is a virtual package provided by:
  xorg-driver-fglrx-dev 6.8.0-8.16.20-0ubuntu16.1
You should explicitly select one to install.
E: Package fglrx-driver-dev has no installation candidate
brian@Brian:~/temp-winebuild/wine-0.9.1$ sudo apt-get build-dep wine
Reading package lists... Done
Building dependency tree... Done
E: Unable to find a source package for wine


I cant get past these errors [Complete noob] Can somone help me???[/QUOTE]


I am getting these as well

```
paul@ubuntu:~/temp-winebuild/wine-0.9.1$ sudo apt-get install build-essential fglrx-driver-dev
Password:
Reading package lists... Done
Building dependency tree... Done
Package fglrx-driver-dev is a virtual package provided by:
  xorg-driver-fglrx-dev 6.8.0-8.16.20-0ubuntu16.1
You should explicitly select one to install.
W: Couldn't stat source package list http://security.ubuntu.com breezy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://security.ubuntu.com breezy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Package fglrx-driver-dev has no installation candidate

```

are the files no longer there?

---

### Post by mithien on 2005-12-19
Never got a chance to repost last night, because I ended up getting it working and playing for quite some time :)

Anyhow the apt-get update just decided to work the last time I tried it. I don't know if its source was down earlier or if it was a fluke, but off it went, I compiled with the modifications listed and bam, WoW on linux.

As for performance, I have a few issues. When the game loads I get a crappy frame rate. Tabbing out and back in fixes this to near XP performance levels. A third tab out will screw up the game window scaling, stretching the the action bar (about 2 inches of the bottom of the screen) off of the display, and overlaying the Gnome UI elements like panels over the top and bottom of the display. Those can be rolled up but it still isn't sufficient IMO. 

First of all I think it's amazing that it running it at all. If it was stable and the performance was suitable for difficult encounters, stability to support multitasking, my windows drive would be history.

Any input on those issues with multitasking mentioned above?

---

### Post by Niz972 on 2005-12-19
[QUOTE=thegnark]what happens when you type just the command **wine** ? if it's somethign to the effect of *cannot find*, then a simple symlink may fix this. on my system, it's looking for /usr/local/bin/wine, but it's actually located at  /usr/bin/wine, so i simply made a symlink. if this is the case, try this:** sudo ln -s /usr/bin/wine /usr/local/bin/wine**

also, did you make sure to uninstall the wine installed by apt first? if you didn't you'll, probably need to **cd ~/temp-winebuild/wine-0.9.1 && sudo make uninstall && sudo apt-get remove wine && sudo make install**.[/QUOTE]

well.. whenever i type in just Wine by itself i get this message. 
>  wine
wine: error while loading shared libraries: libwine.so.1: cannot open shared object file: No such file or directory


---

### Post by mithien on 2005-12-20
Here is whats running through console as I play. The performance is too much of a hinderance to actually do anything terribly important, and I think this console text might have something to do with it.

```
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)fixme:win:EnumDisplayDevicesW ((null),0,0x7fb2e098,0x00000000), stub!
fixme:opengl:wglQueryPbufferARB unsupported WGL_PBUFFER_LOST_ARB (need glXSelectEvent/GLX_DAMAGED work)
fixme:opengl:wglQueryPbufferARB unsupported WGL_PBUFFER_LOST_ARB (need glXSelectEvent/GLX_DAMAGED work)
fixme:imm:ImmGetContext (0x30022): stub
fixme:imm:ImmGetContext (0x30022): stub
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)fixme:win:EnumDisplayDevicesW ((null),0,0x7fb2e098,0x00000000), stub!
fixme:opengl:wglQueryPbufferARB unsupported WGL_PBUFFER_LOST_ARB (need glXSelectEvent/GLX_DAMAGED work)
fixme:opengl:wglQueryPbufferARB unsupported WGL_PBUFFER_LOST_ARB (need glXSelectEvent/GLX_DAMAGED work)
fixme:imm:ImmGetContext (0x30022): stub
fixme:imm:ImmGetContext (0x30022): stub

```


Any ideas folks? The multitasking issue is still there too, but I may have been mistaken in relating the performance issues to it.

---

### Post by alynx on 2005-12-20
[QUOTE=Niz972]well.. whenever i type in just Wine by itself i get this message.  wine
 wine: error while loading shared libraries: libwine.so.1: cannot open shared object file: No such file or directory[/QUOTE]

try typing this :) sudo -s echo "/usr/local/lib" >> /etc/ld.so.conf
then
            ldconfig

tell us how it goes

---

### Post by Niz972 on 2005-12-20
[QUOTE=alynx]try typing this :) sudo -s echo "/usr/local/lib" >> /etc/ld.so.conf
then
            ldconfig

tell us how it goes[/QUOTE]

alright.. just logged onto root in terminal, and typed in exactly that >  sudo -s echo "/usr/local/lib" >> /etc/ld.so.conf/bin/echo: /bin/echo: cannot execute binary file


got that error that you see there.. am i supposed to be doing this from just anywhere when i start in terminal? Anyways, then i type the ldconfig

> ld: config: No such file: No such file or directory


---

### Post by alynx on 2005-12-20
sudo -s should make you root in the console! 

when logged in as root , type echo "/usr/local/lib" >> /etc/ld.so.conf

next command : ldconfig 


did you get root before running the command ?

---

### Post by Niz972 on 2005-12-20
ok, well ityped in what you told me, i guess it worked, it showed no errors.. or anything.. now when i type wine by itself it displays 
> Wine 0.9.1
Usage: wine PROGRAM [ARGUMENTS...]   Run the specified program
       wine --help                   Display this help and exit
       wine --version                Output version information and exit
|

but.. whenever i try to run the warcraft cd to install, it does nothing.. am i missing some other step..?

---

### Post by alynx on 2005-12-20
you will have to copy all 4 cds into a temporary wowinstall directory.

When that is done , you can go into the directory you copied the cd's and type 

wine Installer.exe 

still keep us updated on how it's going ;)

---

### Post by Yuanlong on 2005-12-20
I've just installed Ubuntu and managed to get WoW to run with wine.  However, when I start running WoW, it seems that WoW would suck up all my laptop resources.  Graphics are chopy, mouse is hardly moveable and the whole system become very slow in repond.  My laptop specs are shown in my signature and I don't have any problem to play WoW in windows so I'm sure my laptop is able to handdle WoW.  So is there anything that I can do so that it will run smoothly?  Thanks

---

### Post by arpunk on 2005-12-20
[QUOTE=Yuanlong]I've just installed Ubuntu and managed to get WoW to run with wine.  However, when I start running WoW, it seems that WoW would suck up all my laptop resources.  Graphics are chopy, mouse is hardly moveable and the whole system become very slow in repond.  My laptop specs are shown in my signature and I don't have any problem to play WoW in windows so I'm sure my laptop is able to handdle WoW.  So is there anything that I can do so that it will run smoothly?  Thanks[/QUOTE]
Did you run it with the *--opengl* switch?
```

wine wow.exe --opengl

```

---

### Post by Yuanlong on 2005-12-20
[QUOTE=arpunk]Did you run it with the *--opengl* switch?
```

wine wow.exe --opengl

```[/QUOTE]

Tried that, but it's still the same.  It's loading time after the character selection is so long that I would timeout from the server and get disconnected.

---

### Post by Niz972 on 2005-12-20
> **alynx]you will have to copy all 4 cds into a temporary wowinstall directory.

When that is done , you can go into the directory you copied the cd's and type 

wine Installer.exe 

still keep us updated on how it's going  said:**
> 


ok, typed the wine Installer.exe i got [QUOTE]:~/Desktop/wowinstall$ err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
fixme:font:CreateScalableFontResourceW (1,0x10abe208,0x10aba308,(nil)): stub
Application tries to create a window, but no driver could be loaded.
Make sure that your X server is running and that $DISPLAY is set correctly.

are all cds supposed to be copied into the same file Examplefolder: Wowinstaller
at the same time?

---

### Post by arpunk on 2005-12-20
Did you followed the wiki *step-by-step*? thats usually mean your wine didnt got compiled with X support (happened to me too).

---

### Post by Yuanlong on 2005-12-20
Yes, I followed all the steps in wiki and some additional steps when some problem occur.

---

### Post by Niz972 on 2005-12-20
[QUOTE=arpunk]Did you followed the wiki *step-by-step*? thats usually mean your wine didnt got compiled with X support (happened to me too).[/QUOTE]
talking to me? if so, how do fix wine?

---

### Post by alynx on 2005-12-21
[QUOTE=Niz972]ok, typed the wine Installer.exe i got 

are all cds supposed to be copied into the same file Examplefolder: Wowinstaller
at the same time?[/QUOTE]


every file into the same folder , yes

---

### Post by Sergenten on 2005-12-21
[QUOTE=arpunk]Did you followed the wiki *step-by-step*? thats usually mean your wine didnt got compiled with X support (happened to me too).[/QUOTE]

how do you compile with X support ?

i have been trying to get wow working with wine the last coupple of days, but with no luck. The closet i have bin so far is with wine package included ubuntu badger breezer dist. I can start wow with this but no sound and "mouse-bug". So i decided to try to compile it myself with the patches, but when i try to run 

wine WoW.exe -opengl

i get this error

X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  5 (X_GLXMakeCurrent)
  Serial number of failed request:  375
  Current serial number in output stream:  375

my current wow version is: 1.8.4 and wine is 0.9.3

---

### Post by Niz972 on 2005-12-21
hmm ok copied them all into same folder. i still get this error when i try to wine Installer.exe Alynx.

> err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
fixme:font:CreateScalableFontResourceW (1,0x10abe208,0x10aba308,(nil)): stub
Application tries to create a window, but no driver could be loaded.
Make sure that your X server is running and that $DISPLAY is set correctly.


---

### Post by AnimalMother on 2005-12-22
< Yuanlong
<Ubuntu Newbie Brew
<
<Status:(Offline)
<Posts: 3
<Join Date: Dec 2005
<Location: Malaysia
	
<Default Re: [HOWTO] World of Warcraft - 1 Day Ago
<I've just installed Ubuntu and managed to get WoW to run with wine. However, when I start
<running WoW, it seems that WoW would suck up all my laptop resources. Graphics are chopy,
<mouse is hardly moveable and the whole system become very slow in repond. My laptop specs are
<shown in my signature and I don't have any problem to play WoW in windows so I'm sure my laptop
<is able to handdle WoW. So is there anything that I can do so that it will run smoothly? Thanks

<Acer Aspire 1692WLMI
<Intel Pentium M Processor 740
<15.4" WXGA CrystalBrite TFT LCD
<PCIe ATI Mobility Radeon X700 128MB
<80GB HDD
<Slot-loading DVD-Dual
<1GB DDR2
<802.11b/g wireless Lan
<Bluetooth

<I'm a Pure Newbie in Linux 



fglrx... You need to get this to run WoW with ATI cards.  
My computer without those two things looked like it was very very very slow. the mouse cursor didn't move until a second or two after I moved the mouse.  Thats how long it took for the screan to update.  If that is what your computer is doing then you must download fglrx and set it up and make sure you have the latest ATI drivers.  This is imparative.  I had this problem. Your 3d acceleration will not work properly without those two things.  I cannot remember off the top of my head the "howto" of all of this but it was fairly easy.  The set-up of fglrx and ATI driver is very close to xorg.conf.  Search around I am sure there is a howto because I used one to do it myself.

Now if your WoW is just a little laggy then the above is not what you need.  If your just a little laggy (and you shouldn't be with ATI @ 128mb video ram) that you need to go into your laptop's BIOS and set your AGP aperature size to half your video ram. As a matter of fact do this before you download and set up fglrx and the ATI driver, because you're going to have to do it anyway.

Fglrx you can get via your X package manager or apt-get.  If you have anyother problems after that, like with your mouse clicking (on monsters) just post back here or look for a patch on line called wow-mouse-fixes.patch or something like that. I had to recompile wine(9.3) with the patch applied to get my mouse clicking to work.  Today is 12/22/05 I patched yestarday to make this work. So I know it works with the latest WoW patches  (I think 1.8.4)  the Wine website will tell you how to build wine in ubuntu just go to the download page and you'll see a howto for both debian and ubuntu.  Good luck to you, I know you'll get it, just work through it and you won't be a pure newbie at Linux for very long.
Merry Christmas/HaPpY HoLiDaYs (put a little capitan morgans in your eggnog for me)

---

### Post by alynx on 2005-12-22
[QUOTE=Niz972]hmm ok copied them all into same folder. i still get this error when i try to wine Installer.exe Alynx.[/QUOTE]


hmm , i dont really know , never seen that error before.  But did you get all the packages ? sudo apt-get install build-essential flex bison xlibs-dev libasound2-dev nvidia-glx-dev

---

### Post by Yuanlong on 2005-12-22
Ok, I've tried installing the newest ati driver (took me sometime to get it installed), then I uninstalled wine and fglrx.  Checked the wiki and followed the step by step to reinstall wine and fglrx but I'm still have very choppy grahpics.  My problem is the same as yours which the mouse would only move 1-2 sec after I moved.  Even if I alt+tab to other program, those program are having the same lag as well when wow is open.  Anybody has any other suggestion?

---

### Post by AnimalMother on 2005-12-23
make sure that in you xorg.conf file that "fglrx" is selected as the driver for you video card

---

### Post by AnimalMother on 2005-12-23
This thread helped me out [Click Here]("http://ubuntuforums.org/showthread.php?t=75428")

---

### Post by Yuanlong on 2005-12-23
[QUOTE=AnimalMother]make sure that in you xorg.conf file that "fglrx" is selected as the driver for you video card[/QUOTE]

Thanks, that fixed my problem.  It's kinda later here now so I'm gonna really try to play the game tomorrow.  If everything is going well, I guess it's goodbye to windows:p

---

### Post by AnimalMother on 2005-12-23
I am curious, please let me know how it plays for you.  I personally was willing to deal with it being a little laggy, but it just plays great after I fixed my agp aperature to half my video ram.  I couldn't be happier.
I am also very glad that it is working for you now.

---

### Post by Yuanlong on 2005-12-23
Argg!!! Still no go.  Now that WoW will load into the game but then once inside the game, it will crash after just 3 sec.  I've try creating a new character just to avoid if population is causing the trouble but still it would crash.  

This is wha happening in the terminal up to the point where I have to force quit it.
```
fixme:advapi:SetSecurityInfo stub
fixme:powrprof:DllMain (0x7d0e0000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 11
fixme:powrprof:DllMain (0x7d0e0000, 0, (nil)) not fully implemented
fixme:win:EnumDisplayDevicesW ((null),0,0x7fb2ef00,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7fb2f16c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7fb2f70c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7fb2f70c,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)fixme:win:EnumDisplayDevicesW ((null),0,0x7fb2ee78,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 112 (SPI_GETMOUSESPEED)fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)fixme:sync:CreateIoCompletionPort (0xffffffff, (nil), 00000000, 00000000): stub.fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_RECEIVE_TIMEOUT: STUB
fixme:imm:ImmGetContext (0x10022): stub
fixme:opengl:wglQueryPbufferARB unsupported WGL_PBUFFER_LOST_ARB (need glXSelectEvent/GLX_DAMAGED work)
fixme:wininet:InternetSetOptionW Option 45 STUB
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)fixme:imm:ImmGetContext (0x10022): stub
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)fixme:imm:ImmGetContext (0x10022): stub
fixme:win:EnumDisplayDevicesW ((null),0,0x7fb2e524,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7fb2e57c,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)fixme:imm:ImmGetContext (0x10022): stub
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)fixme:imm:ImmGetContext (0x10022): stub
```

---

### Post by alynx on 2005-12-23
[QUOTE=AnimalMother]I am curious, please let me know how it plays for you.  I personally was willing to deal with it being a little laggy, but it just plays great after I fixed my agp aperature to half my video ram.  I couldn't be happier.
I am also very glad that it is working for you now.[/QUOTE]


how do you do that ?

edit : i have les lag after i turned off vertical sync though :) 

But i still wanna know how you did that! please help me

---

### Post by xjoshuax on 2005-12-23
Hello, 

I finally managed to install the ATI fglrx drivers using this howto: [http://ubuntuforums.org/showpost.php?p=423584](http://ubuntuforums.org/showpost.php?p=423584). 

I've edited the Config.wtf so that the game runs on OpenGL, but when I fire it up it looks very odd:

[http://img373.imageshack.us/img373/4092/wowscreen9or.jpg](http://img373.imageshack.us/img373/4092/wowscreen9or.jpg)

And in the terminal I get these error messages:

```

fglX11AllocateManagedSurface: __FGLTexMgrAllocMem failed!!
fglX11AllocateManagedSurface: __FGLTexMgrAllocMem failed!!
fglX11AllocateManagedSurface: __FGLTexMgrAllocMem failed!!
fglX11AllocateManagedSurface: __FGLTexMgrAllocMem failed!!
fglX11AllocateManagedSurface: __FGLTexMgrAllocMem failed!!

```

I've tried to reconfigure the driver with fglrxconfig, but no luck yet :(

Anyone got the same thing going on or know how to solve it?

EDIT: Thoght the prob was solved but still the same. :(

---

### Post by AnimalMother on 2005-12-24
[QUOTE=alynx]how do you do that ?

edit : i have les lag after i turned off vertical sync though :) 

But i still wanna know how you did that! please help me[/QUOTE]

You have to go into your computers BIOS and look around for something that say "AGP" it may not be called "AGP Aperature" some BOIS call it AGP Memory hole.  Some call it something completely different, but it always says either AGP or Video Card and then has a memory setting(in MB MegaBytes).  Find out how much video ram you card has, and then set the setting to half that.  OpenGL uses the aperature size in its array computing, but the computer needs the rest of the video memory to  perform non-OpenGl funtions.  So you don't want to suck up all your video memory with OpenGL because you computer will fight back.

---

### Post by AnimalMother on 2005-12-24
[QUOTE=Yuanlong]Argg!!! Still no go.  Now that WoW will load into the game but then once inside the game, it will crash after just 3 sec.  I've try creating a new character just to avoid if population is causing the trouble but still it would crash.  
[/QUOTE]
1) I have not seen this, so I don't know what the problem is -  but did you apply the mouse fix patch to the wine source code? 
2) did you fix your AGP Aperature size?
3) do you have the required microsoft DLL's in your "World of Warcraft" directory: mfc42.dll and msvcp60.dll
4)  Here is a copy of my Config.wtf file create a new config.wtf file with it and save *important* CHANGE THE "SET realmName "Dark Iron" TO THE REALM THAT YOU PLAY IN (remember to save your old one under a different name before you do this so that you have a back-up):
```

SET gxApi "openGL"
SET hwDetect "0"
SET gxColorBits "24"
SET gxResolution "1280x1024"
SET gxRefresh "60"
SET gxMultisampleQuality "0.000000"
SET gxFixLag "0"
SET fullAlpha "1"
SET lodDist "100.000000"
SET SmallCull "0.070000"
SET DistCull "450.000000"
SET trilinear "1"
SET frillDensity "12"
SET farclip "300.000000"
SET particleDensity "0.900000"
SET unitDrawDist "300.000000"
SET movie "0"
SET readTOS "1"
SET readEULA "1"
SET ffxDeath "0"
SET gxDepthBits "24"
SET doodadAnim "0"
SET realmName "Dark Iron"
SET gameTip "29"
SET gxCursor "0"
SET mouseSpeed "1"
SET Gamma "1.000000"
SET MusicVolume "0.40000000596046"
SET SoundVolume "1"
SET MasterVolume "1"
SET cameraPitchMoveSpeed "90"
SET cameraYawMoveSpeed "180"
SET cameraPitchSmoothSpeed "45"
SET cameraYawSmoothSpeed "180"
SET cameraDistanceMaxFactor "1"
SET AmbienceVolume "0.60000002384186"
SET uiScale "1"
SET profanityFilter "0"
SET minimapInsideZoom "1"

```
see if that works for you.  If you don't have the wine patch for the mouse fixes here it is (save it in a text file called: wine-wow_fixes.patch):
```

--- libs/wine/mmap.c.old	2005-06-20 13:43:47.000000000 +0200
+++ libs/wine/mmap.c	2005-10-14 21:49:54.794346832 +0200
@@ -161,6 +161,26 @@
 
 #endif  /* (__svr4__ || __NetBSD__) && !MAP_TRYFIXED */
 
+static void *get_anon_mmap_null_address(size_t size)
+{
+    static int got_override = 0;
+    static void *low_alloc_ptr = NULL;
+    void * current_low_alloc_ptr;
+
+    if (!got_override)
+    {
+            low_alloc_ptr = (void*)0x10000000;
+            got_override = 1;
+            //printf("gaak!\n");
+    }
+
+    current_low_alloc_ptr = low_alloc_ptr;
+
+    if (low_alloc_ptr)
+        low_alloc_ptr += size;
+
+    return current_low_alloc_ptr;
+    }
 
 /***********************************************************************
  *		wine_anon_mmap
@@ -209,6 +229,9 @@
             return start;
 #endif
     }
+    if ((start == NULL) && !(flags & MAP_FIXED))
+       start = get_anon_mmap_null_address(size);
+
     return mmap( start, size, prot, flags, fdzero, 0 );
 #else
     return (void *)-1;
--- loader/preloader.c.old	2005-06-02 12:30:08.000000000 +0200
+++ loader/preloader.c	2005-10-14 21:51:16.529921136 +0200
@@ -110,7 +110,7 @@
 {
     { (void *)0x00000000, 0x00110000 },  /* DOS area */
     { (void *)0x80000000, 0x01000000 },  /* shared heap */
-    { (void *)0x00110000, 0x1fef0000 },  /* PE exe range (may be set with WINEPRELOADRESERVE), defaults to 512mb */
+    { (void *)0x10000000, 0x00f00000 },  /* PE exe range (may be set with WINEPRELOADRESERVE), defaults to 512mb */
     { 0, 0 }                             /* end of list */
 };
 

```

save it in your /path/to/wine-0.9.3-winehq/ directory and in a terminal type:
cd /path/to/wine-0.9.3-winehq (hit enter)
"patch -p0 <wine-wow_fixes.patch" (hit enter)

I think that this patch may fix the memory problem that you are having as well as the mouse problem I am not a programmer so I don't exactly know.
 Now before you compile wine again make sure you have all the recomended packages in you system that winehq recomends that you have. If you don't have all of them wine may just exclude the functionality associated with the packages that you do not have rather than spit out compile errors.

One last thing if you haven't done this please do: go to Mozilla.org and download the WINDOWS VERSION OF THE INSTALLER and under wine INSTALL THE WINDOWS VERSION OF MOZILLA.  Then google "Mozilla ActiveX Control v1.7.12" and download "Mozilla ActiveX Control v1.7.12.exe" and install with wine. I know it sounds weird but this is all of the stuff I had to do to get WoW working for me on ubuntu.

I hope some of this helps.

---

### Post by Yuanlong on 2005-12-25
I think I messed up with my xorg.conf.  I've no idea how to fixed it so I think I'll try to reinstall ubuntu after boxing day.

By the way, Merry Christmas

---

### Post by alynx on 2005-12-26
remember to copy the xorg.conf file to a xorg_backup.conf when editing it :) 

In that case nothing can go wrong

---

### Post by Yuanlong on 2005-12-26
[QUOTE=alynx]remember to copy the xorg.conf file to a xorg_backup.conf when editing it :) 

In that case nothing can go wrong[/QUOTE]

lol, lesson learned.  Anyway I've reinstalled Breezy, now in the process of downloading ATI driver.  I'll update with how's everything going on when I've finished all the process.

---

### Post by jcurry on 2005-12-26
I'd appreciate if someone could help me...I am using debian sid, with working nvidia drivers, and I'm running into a problem that I don't think anyone else has seen.

I compiled wine 0.9.3, after patching with 
[http://polynomial-c.homelinux.net/pub/gentoo/portage/app-emulation/wine/files/wine-wow_fixes-2.patch](http://polynomial-c.homelinux.net/pub/gentoo/portage/app-emulation/wine/files/wine-wow_fixes-2.patch)
(is this the correct one?)
and when I try to run WoW with -opengl, I am taken to the character selection screen, and I hit "Enter World".
When it finishes loading, I see one frame of the world, with three weird short golden things on the screen, and then the screen goes black, after maybe ten seconds.  

Direct3D mode (without -opengl) works almost perfectly.  Characters do not have textures, and when I walk around the world, my character is not there, all I see is a huge black patch.

Any way to fix one of these problems (it seems it is better to get OpenGL working) is much appreciated!

Thanks.

---

### Post by Yuanlong on 2005-12-26
I've met with a new problem now.  When I try to compile wine with this command ./configure && make depend && make
this error came out

```
checking build system type... i686-pc-linux-gnuoldld
checking host system type... i686-pc-linux-gnuoldld
checking whether make sets $(MAKE)... no
checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.

```

Here is my config.log
```
This file contains any messages produced by compilers while
running configure, to aid debugging if configure makes a mistake.

It was created by Wine configure 0.9.1, which was
generated by GNU Autoconf 2.59.  Invocation command line was

  $ ./configure 

## --------- ##
## Platform. ##
## --------- ##

hostname = Jimmy
uname -m = i686
uname -r = 2.6.12-10-386
uname -s = Linux
uname -v = #1 Thu Dec 22 11:37:10 UTC 2005

/usr/bin/uname -p = unknown
/bin/uname -X     = unknown

/bin/arch              = i686
/usr/bin/arch -k       = unknown
/usr/convex/getsysinfo = unknown
hostinfo               = unknown
/bin/machine           = unknown
/usr/bin/oslevel       = unknown
/bin/universe          = unknown

PATH: /usr/local/sbin
PATH: /usr/local/bin
PATH: /usr/sbin
PATH: /usr/bin
PATH: /sbin
PATH: /bin
PATH: /usr/X11R6/bin


## ----------- ##
## Core tests. ##
## ----------- ##

configure:1424: checking build system type
configure:1442: result: i686-pc-linux-gnuoldld
configure:1450: checking host system type
configure:1464: result: i686-pc-linux-gnuoldld
configure:1504: checking whether make sets $(MAKE)
configure:1528: result: no
configure:1579: checking for gcc
configure:1608: result: no
configure:1659: checking for cc
configure:1688: result: no
configure:1701: checking for cc
configure:1747: result: no
configure:1800: checking for cl
configure:1829: result: no
configure:1843: error: no acceptable C compiler found in $PATH
See `config.log' for more details.

## ---------------- ##
## Cache variables. ##
## ---------------- ##

ac_cv_build=i686-pc-linux-gnuoldld
ac_cv_build_alias=i686-pc-linux-gnuoldld
ac_cv_env_CC_set=
ac_cv_env_CC_value=
ac_cv_env_CFLAGS_set=
ac_cv_env_CFLAGS_value=
ac_cv_env_CPPFLAGS_set=
ac_cv_env_CPPFLAGS_value=
ac_cv_env_CPP_set=
ac_cv_env_CPP_value=
ac_cv_env_CXXFLAGS_set=
ac_cv_env_CXXFLAGS_value=
ac_cv_env_CXX_set=
ac_cv_env_CXX_value=
ac_cv_env_LDFLAGS_set=
ac_cv_env_LDFLAGS_value=
ac_cv_env_build_alias_set=
ac_cv_env_build_alias_value=
ac_cv_env_host_alias_set=
ac_cv_env_host_alias_value=
ac_cv_env_target_alias_set=
ac_cv_env_target_alias_value=
ac_cv_host=i686-pc-linux-gnuoldld
ac_cv_host_alias=i686-pc-linux-gnuoldld
ac_cv_prog_make_make_set=no

## ----------------- ##
## Output variables. ##
## ----------------- ##

ALSALIBS=''
AR=''
ARTSCCONFIG=''
ARTSINCL=''
ARTSLIBS=''
AS=''
AUDIOIOLIBS=''
BISON=''
BUILTINFLAG=''
CC=''
CFLAGS=''
COREFOUNDATIONLIB=''
CPP=''
CPPBIN=''
CPPFLAGS=''
CROSSCC=''
CROSSTEST=''
CROSSWINDRES=''
CRTLIBS=''
CURSESLIBS=''
CXX=''
CXXFLAGS=''
DEFS=''
DLLDEFS=''
DLLEXT=''
DLLFLAGS=''
DLLIBS=''
DLLTOOL=''
DLLWRAP=''
ECHO_C=''
ECHO_N='-n'
ECHO_T=''
EGREP=''
ESDCONFIG=''
ESDINCL=''
ESDLIBS=''
EXEEXT=''
EXTRACFLAGS=''
FONTFORGE=''
FONTSSUBDIRS=''
FREETYPEINCL=''
FREETYPELIBS=''
GLU32FILES=''
GLUT32FILES=''
GLUT_LIBS=''
ICULIBS=''
IMPLIBEXT=''
INSTALL_DATA=''
INSTALL_PROGRAM=''
INSTALL_SCRIPT=''
IOKITLIB=''
LCMSLIBS=''
LD=''
LDAPLIBS=''
LDCONFIG=''
LDD=''
LDDLLFLAGS=''
LDEXECFLAGS=''
LDFLAGS=''
LDLIBWINEFLAGS=''
LDPATH=''
LDSHARED=''
LEX=''
LEXLIB=''
LEX_OUTPUT_ROOT=''
LIBEXT=''
LIBOBJS=''
LIBPTHREAD=''
LIBS=''
LINT=''
LINTFLAGS=''
LN=''
LN_S=''
LTLIBOBJS=''
MAIN_BINARY=''
NASLIBS=''
OBJEXT=''
OPENGLFILES=''
OPENGL_LIBS=''
PACKAGE_BUGREPORT='wine-devel@winehq.org'
PACKAGE_NAME='Wine'
PACKAGE_STRING='Wine 0.9.1'
PACKAGE_TARNAME='wine'
PACKAGE_VERSION='0.9.1'
PATH_SEPARATOR=':'
PKG_CONFIG=''
PRELINK=''
RANLIB=''
SANEINCL=''
SANELIBS=''
SET_MAKE='MAKE=make'
SHELL='/bin/sh'
SOCKETLIBS=''
STRIP=''
TOOLSDIR=''
WIN16_FILES='$(WIN16_FILES)'
WIN16_INSTALL='$(WIN16_INSTALL)'
WINDRES=''
WINE_BINARIES=''
XFILES=''
XLEX=''
XLIB=''
XML2INCL=''
XML2LIBS=''
XSLTINCL=''
XSLTLIBS=''
X_CFLAGS=''
X_EXTRA_LIBS=''
X_LIBS=''
X_PRE_LIBS=''
ac_ct_AR=''
ac_ct_AS=''
ac_ct_CC=''
ac_ct_CPPBIN=''
ac_ct_CXX=''
ac_ct_DLLTOOL=''
ac_ct_DLLWRAP=''
ac_ct_LD=''
ac_ct_RANLIB=''
ac_ct_STRIP=''
ac_ct_WINDRES=''
bindir='${exec_prefix}/bin'
build='i686-pc-linux-gnuoldld'
build_alias=''
build_cpu='i686'
build_os='linux-gnuoldld'
build_vendor='pc'
datadir='${prefix}/share'
exec_prefix='NONE'
ft_devel2=''
ft_devel=''
host='i686-pc-linux-gnuoldld'
host_alias=''
host_cpu='i686'
host_os='linux-gnuoldld'
host_vendor='pc'
includedir='${prefix}/include'
infodir='${prefix}/info'
libdir='${exec_prefix}/lib'
libexecdir='${exec_prefix}/libexec'
localstatedir='${prefix}/var'
mandir='${prefix}/man'
oldincludedir='/usr/include'
prefix='NONE'
program_transform_name='s,x,x,'
sane_devel=''
sbindir='${exec_prefix}/sbin'
sharedstatedir='${prefix}/com'
sysconfdir='${prefix}/etc'
target_alias=''

## ------------- ##
## Output files. ##
## ------------- ##

MAKE_DLL_RULES=''
MAKE_IMPLIB_RULES=''
MAKE_LIB_RULES=''
MAKE_PROG_RULES=''
MAKE_RULES=''
MAKE_TEST_RULES=''

## ----------- ##
## confdefs.h. ##
## ----------- ##

#define PACKAGE_BUGREPORT "wine-devel@winehq.org"
#define PACKAGE_NAME "Wine"
#define PACKAGE_STRING "Wine 0.9.1"
#define PACKAGE_TARNAME "wine"
#define PACKAGE_VERSION "0.9.1"

configure: exit 1

```

---

### Post by jcurry on 2005-12-27
Oops, update my nvidia drivers, and now it works.   Thanks for the guide!

---

### Post by jcurry on 2005-12-27
Huh.  In Debian, if you install the build-essential package (sudo apt-get install build-essential), you get everything you need to compile stuff, including compilers.

---

### Post by AnimalMother on 2005-12-27
[QUOTE=jcurry]Huh.  In Debian, if you install the build-essential package (sudo apt-get install build-essential), you get everything you need to compile stuff, including compilers.[/QUOTE]

yes, yes, to jcurry you listen.

---

### Post by Yuanlong on 2005-12-27
[QUOTE=AnimalMother]yes, yes, to jcurry you listen.[/QUOTE]

Guess I missed out that step.  Thanks

---

### Post by Yuanlong on 2005-12-28
[QUOTE=AnimalMother]save it in your /path/to/wine-0.9.3-winehq/ directory and in a terminal type:
cd /path/to/wine-0.9.3-winehq (hit enter)
"patch -p0 <wine-wow_fixes.patch" (hit enter)

I think that this patch may fix the memory problem that you are having as well as the mouse problem I am not a programmer so I don't exactly know.
 Now before you compile wine again make sure you have all the recomended packages in you system that winehq recomends that you have. If you don't have all of them wine may just exclude the functionality associated with the packages that you do not have rather than spit out compile errors.
[/QUOTE]

Hmm the activex installer fixed the stalled problem.  Now that I can run around in the game(with about 20+fps) but I'm having the mouse problem.  I can't find where the wine-0.9.3-winehq folder is at so I can't patch it.  Can you give me a idea where usually the installed program will be at?

Edit:  Ok, I manage to find wine in /usr/libs/wine, but I'm having problem to patch it.  The file that are supposed to be patch should be mmap.c.old & mmap.c, but I don't have those file in my wine folder.  Is it that I've did something wrong or did I missed out something?

---

### Post by glaze on 2005-12-28
[QUOTE=Yuanlong]Hmm the activex installer fixed the stalled problem.  Now that I can run around in the game(with about 20+fps) but I'm having the mouse problem.  I can't find where the wine-0.9.3-winehq folder is at so I can't patch it.  Can you give me a idea where usually the installed program will be at?

Edit:  Ok, I manage to find wine in /usr/libs/wine, but I'm having problem to patch it.  The file that are supposed to be patch should be mmap.c.old & mmap.c, but I don't have those file in my wine folder.  Is it that I've did something wrong or did I missed out something?[/QUOTE]

You must install Wine from source and patch it before compiling. If You used Your distro's packet management system to install Wine, it probably was not compiled so You didn't have a change to apply the patch. To get things working, uninstall Wine, get sources from [http://www.winehq.com](http://www.winehq.com), extract them and then You can patch them before compiling. You said You found Wine in /usr/libs/wine but that directory contains only some files Wine uses, and there's nothing to patch there.

---

### Post by Yuanlong on 2005-12-28
Hmm, acording to the new Howto which uses the 0.9.3 version.  It says that we could just install wine using apt-get or synaptic.  So is it that the newest version is patched already and we could installed directly or is there a step missed out in the new Howto??

---

### Post by AnimalMother on 2005-12-29
I had to patch wine and I recompiled the source after I applied the patch, and that was a week ago.  I do not think wine (9.3) has this patch in it.  There is a way to get apt-get to just get soure and unpack it.  Just type: man apt-get (hit enter) that should tell how to just get the source.

*Edit* I believe it is just:
sudo apt-get source wine

do this after you have entered winehq's repository to your list.  This command shoul download and unpack wine source in the directory you are currently in so it (should) be your home directory "~" at the commandline

---

### Post by Disstress on 2005-12-29
I installed exactly as per the Wiki instructions and I have the mouse bug.

Did the wiki change? I installed wow using the wiki a couple of weeks ago, (then I switched to FC4--and back again) and I didn't have the mouse bug then.


EDIT: I just found a foreign language page in the WIKI that is how the 'old' wiki page was.
[https://wiki.ubuntu.com/WoWguideWine-SE?highlight=%28CategoryGames%29](https://wiki.ubuntu.com/WoWguideWine-SE?highlight=%28CategoryGames%29)

I'm going to screenshot it so it doesn't disappear.

---

### Post by Terrasque on 2005-12-29
Someone calling himself *CoreyBurger* merrily ignored the part where you need a specially patched wine to run the game, and linked to the page describing how to install normal wine. Which, as we all know, do not work.

[Here]("https://wiki.ubuntu.com/WorldofWarcraftHowto?action=recall&rev=8") is a link to the page before it got mutilated.

BTW, I've made a .deb of the patched wine after compile, its avaliable [here]("http://80.202.244.48/~terra/wine-wow/"). 
Rev 6 does all the wine patching and configuring steps + setting default audio out to alsa.
[I]**BEWARE**: This is my first .deb ever, and its not tested on other machines.
**YMMV**[/I]

---

### Post by Yuanlong on 2005-12-29
Now that I've uninstalled wine and reinstalled it again, the graphic stalled problem reapear again.  Even after I installed window's firefox and the activex control wouldn't solve the problem.

I'm so sorry to give you guys so many trouble and happy new year to all.

Edit: I've installed wine with patch, currently using the deb version given by Terrasque.  Either the deb version or the old wiki method would give me the same problem.

---

### Post by phil.crissman on 2005-12-30
Terrasque...

Thanks for the link to the old page (with the wine/patching instructions)! -- I was trying to follow the HOWTO the other night, and I was wondering why there were no steps in the HOWTO to patch wine... when everyone was always mentioning the need to patch wine... ;-)

I decided to go ahead and compile wine per the instructions, it's compiling as I write this.

Anyways, thanks again.

---

### Post by AnimalMother on 2005-12-30
[QUOTE=Yuanlong]

Edit: I've installed wine with patch, currently using the deb version given by Terrasque.  Either the deb version or the old wiki method would give me the same problem.[/QUOTE]

Is it still giving you this problem or did terrasque' package fix it? if not, and it is that same stall with the 1 -2 sec screen update, reinstall fglrx and ati stuff and see what happens.

---

### Post by Terrasque on 2005-12-30
If my package dont work, try compiling yourself.

As I said, its my first package, and it havent been tested on any other machine, so hearing that it installs and works at all on another machine is a pleasant suprise.

A bit more info about the package: It's compiled on a system having nvidia-glx-dev, and have these extra registry keys in the default registry:

HKCU,Software\Wine\Drivers,"Audio",,"alsa"
HKCU,Software\Wine\Alsa Driver,"DevicePCM1",,"default" 

these are located in usr/share/wine/wine.inf, under [Misc] 
Wine is also patched according to the page, compiled with no debug messages, and binaries have been stripped.
This is to ensure maximum speed and minimize the size of the package.

It is currently not optimized for any processor, neither mcpu nor march is used.


Any feedback is appreciated.

---

### Post by phil.crissman on 2005-12-31
After I posted, I did wind up using your .deb package; it works great.

For some reason when I compiled it, it failed... I would normally try to figure out why, but since your .deb package worked, I don't think I'll bother.

Thanks again!

---

### Post by gfg on 2005-12-31
Hi! I've got wow up and running but it's very choppy (about 8fps) and I've read it might improve if i turn off vertical sync. The problem is though that I can't turn it off because everytime I press ok at the video options screen, I get an error. So I was wondering if there is any option I can use in the config file to turn it off? Thanks in advance for any help. I use cedega btw.

Regards gfg

---

### Post by Naski on 2005-12-31
Hi, i copied my wow install from windows partition and placed in my home folder, i have installed ati drivers and i can get wow on, but i have these problems.

1. Weak performance (fps is about 10-20, lowest settings), in windows fps all the time 50-70 with best settings.
2. Mouse bug (i cant find my wine folder + i dont have permission to edit anything at / ), i have patched wine.
3. Doesnt save controls.
4. Every second time i try to quit it jams the whole system.

I did installation step by step and i have putted the missing .dll s to wow folder.

---

### Post by inthepit on 2006-01-01
link seems to be down.  can anyone give a working link for the deb.

---

### Post by mrgnash on 2006-01-02
Has anyone tried this with the latest version of Wine? Unlike the previous version, I can load WoW right off the bat.. but what I am then presented with is a static login screen in which I seem to have no mouse and no ability to input my details...

---

### Post by Burgundavia on 2006-01-02
If there are specific tweaks that are still needed for Wine to make WoW work, please add that in a seperate section under the installing Wine section. I apoligize for nuking that.

Cheers,

Corey Burger
Ubuntu Documentation Team

---

### Post by Terrasque on 2006-01-02
Sorry, seems like my server has died. I'll see if I can get a friend of mine to host the deb tomorrow.

As for wine version, last unpatched wine I tried was 0.9.3 and that did not work.

The biggest problem is the "memory bug" part, where if that aint patched in, you cant click on anything.


As for speed. It varies greatly. Most of the time FPS is from 50-75 fps (screen is 75 hz, so it wont go faster than that), but sometimes it drops to horrible speed (1-3 fps). This seem to happen randomly, but have only happened in the big cities for now. I tried the latest nvidia driver, the huge drops seem to be gone, but average fps was halved. Which is even worse in my eyes. 

Also, ALT+rightclick brings up desktop menu. Any way to remove this?

---

### Post by Lord Erik on 2006-01-02
I've just been given a 14 day trial DVD for WoW and thought I'd give it a go.  Before I can even try installing it under wine I have a problem I'm hoping someone can shed some light on.

On a win2k machine I can see the entire DVD contents.  On my laptop currently running ubuntu 5.04 I cant see several files including the Installer.exe, so cant install the game.

I've tried from the file browser (with view hidden files ticked) and from ls -al in a root terminal and by mounting the DVD as iso9660 and udf and get the same results.  The files which are marked as hidded when viewing it on the win2k machine arent visible on my ubuntu laptop.

Any ideas?  I'm baffled, especially with not being able to view everything from a root prompt.

---

### Post by tflovik on 2006-01-03
You have to mount the install cd as root or ls the drive from another directory than the mount point. I'm not shure since it is some time since i installed it.
Hope this can help you!

---

### Post by Terrasque on 2006-01-03
[http://www.x-nett.com/wine-wow_0.9.1-6_i386.deb](http://www.x-nett.com/wine-wow_0.9.1-6_i386.deb)

Wine with wow patches installed.

---

### Post by Lord Erik on 2006-01-04
[QUOTE=tflovik]You have to mount the install cd as root or ls the drive from another directory than the mount point. I'm not shure since it is some time since i installed it.
Hope this can help you![/QUOTE]

Nope, neither worked.  I ended up copying the dvd to my iriver while I still had access to the win2k machine.  I'm now able to get wine to run the installer from the iriver.  Just have to actually get it to install now.

---

### Post by mesilliac on 2006-01-04
[QUOTE=Lord Erik]I've just been given a 14 day trial DVD for WoW and thought I'd give it a go.  Before I can even try installing it under wine I have a problem I'm hoping someone can shed some light on.

On a win2k machine I can see the entire DVD contents.  On my laptop currently running ubuntu 5.04 I cant see several files including the Installer.exe, so cant install the game.[/QUOTE]
You need to mount the dvd with the "unhide" option. Adding this to the mount options in /etc/fstab, then reinserting the dvd worked for me :).

---

### Post by vyktor69 on 2006-01-04
Has the 1.9 patch problem been resolved or is it still a problem? I remember a post saying that the 1.9 test patch will not work with wine or cedega and after I installed the 1.9 patch I can't start the game. I've tried all of the past suggested fixes but to no avail. It was working fine with cedega 4.3 until that patch installed. All I get is a black screen flash up for perhaps 2 seconds then it closes and I get a very long of text.
Anybody have any ideas?

Sempron 1.5 Ghz
512 MB ram
nvidia 5200 - 128mb videocard
Ubuntu 5.10

---

### Post by mesilliac on 2006-01-04
[QUOTE=vyktor69]Has the 1.9 patch problem been resolved or is it still a problem? I remember a post saying that the 1.9 test patch will not work with wine or cedega and after I installed the 1.9 patch I can't start the game. I've tried all of the past suggested fixes but to no avail. It was working fine with cedega 4.3 until that patch installed. All I get is a black screen flash up for perhaps 2 seconds then it closes and I get a very long of text.
Anybody have any ideas?[/QUOTE]
It looks like the 1.9 patch doesn't work with Cedega 4.x. Cedega 5.x appears to work. Check out this thread at the Gentoo forums, a bunch of people are having the same problem.

[http://forums.gentoo.org/viewtopic-t-246098-start-0-postdays-0-postorder-asc-highlight-.html](http://forums.gentoo.org/viewtopic-t-246098-start-0-postdays-0-postorder-asc-highlight-.html)

---

### Post by mesilliac on 2006-01-04
Terrasque,

I tried to download your patched wine .deb but it says "the request is not supported" :(

---

### Post by vyktor69 on 2006-01-04
[QUOTE=mesilliac]It looks like the 1.9 patch doesn't work with Cedega 4.x. Cedega 5.x appears to work. Check out this thread at the Gentoo forums, a bunch of people are having the same problem.

[http://forums.gentoo.org/viewtopic-t-246098-start-0-postdays-0-postorder-asc-highlight-.html](http://forums.gentoo.org/viewtopic-t-246098-start-0-postdays-0-postorder-asc-highlight-.html)[/QUOTE]

I read that. I've even tried the latest version of wine 0.9.4 and I get the same messages. :(

---

### Post by sornen on 2006-01-04
I got wow to work with wine-9.3 following the wiki here:

[https://wiki.ubuntu.com/WorldofWarcraftHowto?action=recall&rev=8](https://wiki.ubuntu.com/WorldofWarcraftHowto?action=recall&rev=8)

For the latest wow patch 1.9 the glPolygonOffset bug appears to be fixed, so there is no need to alter dlls/opengl32/opengl_norm.c

---

### Post by Azerban on 2006-01-05
[QUOTE=sornen]I got wow to work with wine-9.3 following the wiki here:

[https://wiki.ubuntu.com/WorldofWarcraftHowto?action=recall&rev=8](https://wiki.ubuntu.com/WorldofWarcraftHowto?action=recall&rev=8)

For the latest wow patch 1.9 the glPolygonOffset bug appears to be fixed, so there is no need to alter dlls/opengl32/opengl_norm.c[/QUOTE]

I didn't alter that file (most likely because I installed 9.3 from a deb and can't find that file *to* alter), but while it runs fine, I don't have any sound and can't target anything, and wine 9.4 crashes on load. Any fixes?

---

### Post by AnimalMother on 2006-01-05
Azerban look back  to page 12 in this thread I explaine how to patch wine 0.9.3  it fixes the targeting mouse click thing. and I have never had wine crash on the load with 0.9.3.  
The last time I compiled wine I forgot to fix opengl_norm.c's glPolygonOffset problem and it still worked - that was before WOW patch 1.9.

Now I just got WOW patch 1.9 and my working WOW setup was UNEFFECTED.  It works fine with wine 0.9.3 ("wine-wow_fixes.patch" also on pages 12 in this thread) patched.

Can I take just a quick poll?  Who here has WOW working and what setup do you have it on.

Here is mine:

AMD 64 3700+
Ubuntu Breezy 2.6.12-10 i386 (not x64 kernel )
ATI 9700 pro all-in-wonder 128mb (fglrx driver)
wine 0.9.3 patched w/wine-wow_fixes.patch
windows version of mozilla + activex control 1.7.* installed under wine.
wow patch 1.9.*
functional, but I compiled wine with no sound.

---

### Post by vyktor69 on 2006-01-05
Anyone know where I can get wine 0.9.3? Right now the only one on the repository is 0.9.5 (which is the one I'm using) I've tried running with winecfg set to win98 and win2000 modes. This is what I get.
ALSA lib seq_hw.c:455:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
fixme:advapi:SetSecurityInfo stub
fixme:powrprof:DllMain (0x7c320000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 11
fixme:powrprof:DllMain (0x7c320000, 0, (nil)) not fully implemented
fixme:win:EnumDisplayDevicesW ((null),0,0x7fb0eef4,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)fixme:win:EnumDisplayDevicesW ((null),0,0x7fb0ee70,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 112 (SPI_GETMOUSESPEED)fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=18764 < primary_done=30092)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=15340 < primary_done=22572)
fixme:sync:CreateIoCompletionPort (0xffffffff, (nil), 00000000, 00000000): stub.fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=7820 < primary_done=15052)

*I deleted the similiar DSOUND messages for space reasons*

fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_RECEIVE_TIMEOUT: STUB
fixme:wininet:InternetSetOptionW Option 45 STUB
fixme:imm:ImmGetContext (0x10022): stub
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  13 (X_GLXCreateGLXPixmap)
  Serial number of failed request:  386
  Current serial number in output stream:  387


I know it looks like my alsa sound but it's working for the desktop

---

### Post by Des33 on 2006-01-05
yeah i have the identical problem since moving to 0.9.5

worked before that version tho

---

### Post by Terrasque on 2006-01-05
Hello again, folks.. We found the problem with the web server. It didnt like .deb!

So we renamed it to .zip, and it works perfectly.. 
Here's a new link : [http://www.x-nett.com/wow%2Dwine/wine-wow_0.9.1-6_i386.zip](http://www.x-nett.com/wow%2Dwine/wine-wow_0.9.1-6_i386.zip)
Remember: this is NOT a zip file ;) Also, I got to try it on a new install today. Worka like a charm :) This was one of my big worries earlier.

If anyone else can host it, I'd be grateful! Here is the MD5 of the original:
8ad9bbab1ef9f1569315124918351f36  wine-wow_0.9.1-6_i386.deb


Now, for patch 1.9 - Nothing major breakage. The sound is a bit more unstable (this is with alsa), and I needed mfc42.dll to run the update. Apart from that, no problems at all with the new patch.

If I get time, I might try out 0.9.3 - but 0.9.1 seems to work fine as it is. (I have tried 0.9.4 and cvs... deb packages makes it easy to go back if the new one's not working :D )

EDIT: The target bug is fixed in 1.9 it seems, making the offset patch bugged. I didnt notice that until now ;) And I am compiling 0.9.3 rev 2 (without the offset patch) right now. Does anyone have a place I can host it?

---

### Post by Terrasque on 2006-01-05
[http://www.stud.ntnu.no/~jensadne/files/wine-wow_0.9.3-2_i386.deb](http://www.stud.ntnu.no/~jensadne/files/wine-wow_0.9.3-2_i386.deb)

Lights! Camera! Action!

This have the target cursor patch removed (it was there to work around a bug in opengl WoW that was fixed in 1.9), and it use alsa default for audio, which means it play nice with all the other apps in ubuntu playing sound. It have been tested to work with 1.9 - and have been tested installed on a clean ubuntu install with no apparent problems. Unless something big turns up this will be the last deb for a while.

---

### Post by vyktor69 on 2006-01-05
[QUOTE=Terrasque][http://www.stud.ntnu.no/~jensadne/files/wine-wow_0.9.3-2_i386.deb](http://www.stud.ntnu.no/~jensadne/files/wine-wow_0.9.3-2_i386.deb)

Lights! Camera! Action!

This have the target cursor patch removed (it was there to work around a bug in opengl WoW that was fixed in 1.9), and it use alsa default for audio, which means it play nice with all the other apps in ubuntu playing sound. It have been tested to work with 1.9 - and have been tested installed on a clean ubuntu install with no apparent problems. Unless something big turns up this will be the last deb for a while.[/QUOTE]

I just got the 0.9.1 package installed and WoW is playing better than ever. I tried using Cedega 5.0.3 and it crashed everytime I tried to change the graphics settings in game. I don't have the problem with wine-wow_0.9.1.
Is there any advantage to going to the 0.9.3 package?

---

### Post by Terrasque on 2006-01-05
I've only tried it for an hour now. I dont see any reason not to use it, to put it that way. Some error messages in console are gone, and this gets the targeting circles back (which was broken pre-1.9, and wine patched accordingly, and now fixed, and now latest wine package unpatched accordingly :p)
Also, sound seem to be a bit more stable.

---

### Post by vyktor69 on 2006-01-05
Ok, since I know the 0.9.1 is working for me I may try the 0.9.3 one and if it doesn't work I can alway go back to the other one. :)

---

### Post by Terrasque on 2006-01-05
That's the part I especially liked about compiling and then making debs :)

If it dont work, it only takes a few seconds to go back to a version I know works.

Combined with the compile shell script I've written it makes it dead easy to experiment :D Truly a blessing.

---

### Post by malkaven on 2006-01-05
How do i uninstall wine that I compiled from the source files?
Do i just delete out the directory ~/.wine ?

I'm going to try the prepatched one that Terrasque was nice enough to up.

---

### Post by mesilliac on 2006-01-05
Wohoo, thanks Terrasque! WoW is now working flawlessly on my amd64 system, without a 32 bit chroot in sight.

For the record, this is how I got it working nicely: (wine-wow_0.9.3 and WoW 1.9)

***(amd64 only - x86 users just install terrasque's .deb from page 16)*** Follow RAOF's instructions, buried in **[this thread](http://www.ubuntuforums.org/showthread.php?t=96620)**, except using terrasque's wine-wow deb from page 16. amd64 users will need to find some extra 32bit libraries and put them in /lib32, but wine tells you what's missing when you try to run it.

***(all architectures)*** Find some native windows dlls: *msvcp60.dll* and *mfc42.dll*, and put them in your fake windows/system directory. You might have to add them as overrides using "winecfg".
Install the *windows version* of mozilla using wine, and the *mozilla activeX control* (I used version 1.7.12 for both.) This allows WoW to automatically download and install patches. I followed the instructions from **[here](http://gentoo-wiki.com/HOWTO_Install_and_update_World_Of_Warcraft_with_wine)**.

To install WoW I had to make sure my dvd drive was mounted with the "unhide" option (adding it to the options in /etc/fstab worked okay). Then just "wine /cdrom/installer.exe" worked.

Finally, add some options to the config.wtf file in the "Program Files\World of Warcraft\WTF" directory:
```
SET SoundOutputSystem "1"
SET SoundBufferSize "130"
SET gxApi "OpenGL"
```

Start "regedit" then set the following
```
[HKEY_CURRENT_USER\Software\Wine\Alsa Driver] "DevicePCM1"="default"
```

now..... ```
wine "C:\Programs Files\World of Warcraft\WoW.exe"
```

or click on the icon wine put on your desktop ;).

Hooray! WoW!


My cpu: amd64 athlon 3200
my gpu: nvidia geforce 6600 gt
my kernel: 2.6.12-10-amd64-k8

---

### Post by mesilliac on 2006-01-06
[QUOTE=malkaven]How do i uninstall wine that I compiled from the source files?
Do i just delete out the directory ~/.wine ?

I'm going to try the prepatched one that Terrasque was nice enough to up.[/QUOTE]
Go to the wine source directory (same place you typed "make && make install") and type "sudo make uninstall" :).

You can keep your settings and your fake windows drive... they're what's in ~/.wine, so you probably *don't* want to delete it.

---

### Post by Niamor on 2006-01-06
Thanks a lot Terrasque.

It's much easier with a deb than to compile wine and add the patch, I had a problem with opengl.dll....

It's working great, just need to find a way to improve the fps a bit, maybe by starting wine with startx instead of kde.

---

### Post by Des33 on 2006-01-06
> [HKEY_CURRENT_USER\Software\Wine\Alsa Driver] "DevicePCM1"="default"

thats not there on mine... what i need to do to fix that prob?

---

### Post by fine_young_misanthrope on 2006-01-06
I installed wine using the apt-get method and i dont remember where i made and configured it.  Is there any way to uninstall the latest version of wine and install the version on this forum with the patch and start from scratch with wine?  Ive got other games to work like Doom3 (for linux) so I know my graphic card is up to date.


For more fun, ive started another thread about my two sound cards and no sound in some games and programs but sound in other games and programs.  Im new to ubuntu and need all the help i can get.

---

### Post by Azerban on 2006-01-07
When installing that wine-wow, and trying to run WoW with it, I get the following error message:

```
wine: failed to initialize: /usr/lib/wine/ntdll.dll.so: symbol gnu_dev_minor, version GLIBC_2.3.3 not defined in file libc.so.6 with link time reference
```

What does it mean and how can I fix it?

---

### Post by souled on 2006-01-07
Okay, everything is working except for the sound. I hear sound, but it's all distorted and what not. When I run winecfg and go into the audio tab, it crashes. What's the problem here?

---

### Post by tafsen on 2006-01-07
I got this error:
> fixme:advapi:SetSecurityInfo stub
fixme:powrprof:DllMain (0x7c630000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 11
fixme:powrprof:DllMain (0x7c630000, 0, (nil)) not fully implemented
fixme:win:EnumDisplayDevicesW ((null),0,0x7faeeef4,0x00000000), stub!
fixme:d3d:IWineD3DImpl_GetDeviceCaps Caps support for directx9 is nonexistent at the moment!
fixme:win:EnumDisplayDevicesW ((null),0,0x7faef160,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7faef700,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7faef700,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7faef668,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7faef654,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)fixme:win:EnumDisplayDevicesW ((null),0,0x7faeee70,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 112 (SPI_GETMOUSESPEED)fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)fixme:sync:CreateIoCompletionPort (0xffffffff, (nil), 00000000, 00000000): stub.fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_RECEIVE_TIMEOUT: STUB
fixme:wininet:InternetSetOptionW Option 45 STUB
fixme:imm:ImmGetContext (0x10022): stub
fixme:dbghelp:sffip_cb NIY on 'C:\build\buildWoW\WoW\bin\Wow.pdb'
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)

Can anyone help me?

---

### Post by glaze on 2006-01-09
I'm having problems after trying WoW 1.9 compatible mods (CTMod and Titan), so I deleted WTF and Interface, but it still doesn't work. WoW crashes on entering the world with dreaded #132 and gives an error about GUARD_PAGE which is new to me. I had WoW 1.9 working before trying new versions of mods. Repair.exe doesn't find anything odd. Also, WINE 0.9.1 is the newest that has ever worked for me, no luck with 0.9.5 for example even with OpenGL regression patch. I run on AthlonXP 2400+, 1 GiB RAM, Ubuntu 5.10, Geforce FX5900XT with patched 1.0-8178 drivers and kernel 2.6.15ck1. dmesg shows "can't create port" when trying to play WoW.

edit: Got it working again with Wine 0.9.1 + polynomial-c's patch like before, but fps is a lot lower than before. Maybe related to the new Nvidia driver.

---

### Post by Terrasque on 2006-01-10
0.9.4 added some stuff that breaks WoW. My latest wine-wow use 0.9.3

As for you others that have problems running wow, first check that you have 3d acceleration enabled ("glxinfo | grep direct" in console). If you still cant get it to run, try deleting your ~/.wine folder, or even make a new user to try from. The WoW folder itself can be copied to someplace else, and run directly from there. It does not have to be installed.

And, just to repeat myself, my prepatched wine .deb is avaliable on [http://www.stud.ntnu.no/~jensadne/files/wine-wow_0.9.3-2_i386.deb](http://www.stud.ntnu.no/~jensadne/files/wine-wow_0.9.3-2_i386.deb)

---

### Post by jackie_brown on 2006-01-10
hi guys

im running the wine-wow-0.9.3 under kde. ATI card with correct drivers i think.

i got wow installed, set the needed parameters in Config.wtf (where btw are a lot more statements than just these 3 which i had to add, right?)
the two dll's which are needed are in /windows/system/ (btw they are the only one which are in there, right?) i moved them into system32/ but nothing changed...

i have 2 problems:

1. in winecfg i can't click at the audio section, because then my winecfg hangs and nothing happens anymore. i guess sound is not configured right, but xmms for example works. anywhere a possibility to config the output device of wine in textmode or sth equal?

2. the performance of wow is just inacceptable. fps are round about 7-10 and WoW runs maximum some minutes. then it crashes with an wow error and an "ACCESS VIOLATION". after that some memory addresses and so on...

did is miss sth ?

[ i try to copy/paste the error msg...]

---

### Post by Damburger on 2006-01-11
[QUOTE=Burkey]Ok, I re-installed Ubuntu 5.10 clean.. then installed wine and set my Config.wtf as above, I now get a different error.

```

Your 3D Accelerator is not supported by World of Warcraft. Please install a 3D accelerator card with dual-TMU support.

```

So a kind of progress I guess.. breakfast now but will try some more things when I get back, hope someone might be able to shed some light[/QUOTE]

I have the exact same prolem, but I'm not using an onboard Intel graphics card, I'm using a Geforce 6800.

To begin with, it did work, then I installed nvidia-glx and copied over my xorg.conf, and the error turned up.

---

### Post by mesilliac on 2006-01-12
[QUOTE=jackie_brown]i have 2 problems:

1. in winecfg i can't click at the audio section, because then my winecfg hangs and nothing happens anymore. i guess sound is not configured right, but xmms for example works. anywhere a possibility to config the output device of wine in textmode or sth equal?[/QUOTE]

This happens for me too.... but if I wait for a minute, it's okay. For me it hangs because it can't find the drivers for arts and esd (don't have arts, haven't installed 32 bit esd drivers on my 64bit system). Try waiting for a bit after clicking on audio and see if it unhangs?

I think you can set the output device to alsa using "regedit". Add/change this key:
```
HKEY_CURRENT_USER/Software/Wine/Drivers/"Audio"="alsa"
```

Yes there should be a lot more stuff in config.wtf (it's WoW's main config file), and yes those 2 dlls should be the only ones in your windows/system directory (the others are emulated by wine).


Just to confirm, the new 1.9.1 patch with it's annoying loader screen is working for me with the method I posted before ;). The display of the loader screen is glitchy, but it works fine.

---

### Post by akurashy on 2006-01-12
is it true that WoW have private servers?

---

### Post by mesilliac on 2006-01-12
[QUOTE=Des33]thats not there on mine... what i need to do to fix that prob?[/QUOTE]
right-click -> new key.

I don't actually know if it does anything, but it doesn't seem to break anything either ;).

---

### Post by Mr_Grieves on 2006-01-12
[QUOTE=Burkey]
```

glxgears -printfps
5151 frames in 5.0 seconds = 1030.031 FPS
5101 frames in 5.0 seconds = 1020.193 FPS
5084 frames in 5.0 seconds = 1016.682 FPS
5168 frames in 5.0 seconds = 1033.422 FPS

```

That is in 24-bit, in 16 it gives around 1500.
[/QUOTE]
That surly looks very low..

I got (Nvidia 6800GT)
```

glxgears -printfps
50027 frames in 5.0 seconds = 10005.327 FPS
57984 frames in 5.0 seconds = 11596.625 FPS
58529 frames in 5.0 seconds = 11705.744 FPS
59006 frames in 5.0 seconds = 11801.144 FPS
58356 frames in 5.0 seconds = 11671.091 FPS

```
but you might have figured that yourself.. seems weird that my box is handling 10 times more frames per second.

---

### Post by Des33 on 2006-01-12
works brilliantly.. fps can be some what erratic.. generally hold ups around 40-50 most of the times..

people tend to be very laggy to me.. jolting all over the show.. even when my connection to the server is grand..

---

### Post by jackie_brown on 2006-01-12
[QUOTE=mesilliac]This happens for me too.... but if I wait for a minute, it's okay. For me it hangs because it can't find the drivers for arts and esd (don't have arts, haven't installed 32 bit esd drivers on my 64bit system). Try waiting for a bit after clicking on audio and see if it unhangs?

I think you can set the output device to alsa using "regedit". Add/change this key:
```
HKEY_CURRENT_USER/Software/Wine/Drivers/"Audio"="alsa"
```

Yes there should be a lot more stuff in config.wtf (it's WoW's main config file), and yes those 2 dlls should be the only ones in your windows/system directory (the others are emulated by wine).


Just to confirm, the new 1.9.1 patch with it's annoying loader screen is working for me with the method I posted before ;). The display of the loader screen is glitchy, but it works fine.[/QUOTE]


ok, the problem is that there is no section like "drivers" or equal in the regedit :( so i assume that soemthing went completely wrong with my sound installation? if i remember right, the alsa configuration went right, no errors. everything that uses sound works fine except wine&WoW. For example Warcraft 3 the sound is possible, even it is stuttering like hell. in Quake 3 there is also no sound possible. even setting the snddevice in the quake console didn't help much. everytime a sound should be played there is the message "sound dropped" -> huh?

but thank u for ur help :)

---

### Post by tafsen on 2006-01-12
Does this guide only work with Nvidia and ATI cards?

---

### Post by dragge on 2006-01-12
I got performance issues i cant solve.
Wine : 0.9.1, mousebug patched

glxgears show

```
68351 frames in 5.0 seconds = 13670.022 FPS
68774 frames in 5.0 seconds = 13754.758 FPS
68773 frames in 5.0 seconds = 13754.545 FPS
64624 frames in 5.0 seconds = 12924.625 FPS
67502 frames in 5.0 seconds = 13500.356 FPS

```

I get huge fps drops both in IF/OGR and out in the world.
-> City fps ~ 10-18fps
-> World ~ 30-40fps

Im running ubuntu 5.10, last time i tried wow in ubuntu i was runing 5.04. that time i got around 10-15fps more than in windows.

"standard" opengl config.wtf.

Even att all graphic setting turned to low i get this crappy fps. anyone got any ideas or hacks for speed increase?

My box
```
P4 3,4Ghz 533Mhz
2048Mb DDR 400Mhz
SATA Discs all the way
Geforce 6800 Ultra PCI-Express 256
```

---

### Post by MadHatter on 2006-01-13
Just thought I'd add my 5 cents to this, or maybe it's more like 1c or 2c :P

I just managed to get WoW running, on an Acer Aspire 1804WSMi. Started out with just installing winex through Synaptic, it worked after updating the config file with 'SET gfxApi ="Opengl"'. At least as far as starting it up and getting to the loginscreen, although it ran extremely slow. It took WoW about 3-4 seconds to react to mouse movement/keyboard.

At that point, I got the latest drivers from the ATI webpage and installed them. When I tried to start 'wine wow.exe' at that point, it failed to start with the PixlMap error. So I went searching here in the forums and found Terrasque's 0.9.3 build with the patches installed. This got me all the way through the login, character create/select. But as I clicked Enter Realm, it loaded up as it should and then when the game started up, it would crash out to the Desktop with a fatal exception.

Didn't really now what to do, as I hadn't seen that before here on the forums so I just tried to remove the 'SET gfxApi = "OpenGL"' line from the config.wtf file, and started wow with 'wine wow.exe' and it works great. Just one minor flaw, the small facial icons next to the health bars are corrupted. But I can live with that :)

---

### Post by jackie_brown on 2006-01-13
LOL in the meanwhile i removed all my wine's and the .wine dir. installed terrasques 0.9.3 version and treid to install WoW, but when it asks for the 2nd cd and I am inserting it into the drive, mounting it, he don't recognizes that the 2nd one is inserted.... just my 3 ½ cents ^^

---> ok i copied my WOW from the windos partition. in my regedit is also a 

"HKEY_CURRENT_USER/Software/Wine/Alsa Driver/DevicePSM1   REG_SZ   default

the sound still is not working right. in the WoW menu it stutters still awesome. in winecfg it is still not possible to enter the audio section -> hangs. and wine says 

```

err:wave:DSDB_MapBuffer Please run winecfg, open "Audio" page and set
"Hardware Acceleration" to "Emulation".

```

what is not possible ... *cry*

---> my error message when i'm starting it:
```

ALSA lib pcm_dmix.c:762:(snd_pcm_dmix_open) The dmix plugin supports only playback stream
ALSA lib seq_hw.c:455:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
*** glibc detected *** free(): invalid pointer: 0x7c03bf60 ***
wine: Assertion failed at address 0xb7dc67a7 (thread 0009), starting debugger...
err:seh:EXC_DefaultHandling Unhandled exception code c000013a flags 0 addr 0xb7e7b469
err:seh:EXC_DefaultHandling Unhandled exception code c000013a flags 0 addr 0xb7e7b469

```

---

### Post by Terrasque on 2006-01-14
I would guess its something wrong with your audio setup, jackie_brown..

You could try to make a new user, so you're sure its not any of your user settings thats wrong. 

BTW, do you have ati or nvidia? and did you add the lines from [https://wiki.ubuntu.com/WorldofWarcraft](https://wiki.ubuntu.com/WorldofWarcraft) to Config.WTF ?

---

### Post by jackie_brown on 2006-01-14
yes i added these lines with no success... but i will try the new user - after that night ;) 

gn8

---

### Post by mesilliac on 2006-01-14
Hmm, this is just a note to say I've had much better framerates ever since I *disabled* vertex animation shaders in the WoW video options menu. I'd say I've had a 50% increase, and a couple graphical glitches disappeared entirely. And to think it says "Enable to maximize performance".

So now I'm running at 1280*1024 full graphical detail on everything ;). Wow, WoW is pretty.

I have experienced the strange 7-10 fps issue a couple times, and the only way I can seem to fix it is to reboot. And they say it's not a windows emulator!


[QUOTE=jackie_brown]ok, the problem is that there is no section like "drivers" or equal in the regedit :( so i assume that soemthing went completely wrong with my sound installation?[/QUOTE]
Hmm, you could try creating the key. In regedit, right-click on wine -> new key.

Don't know if it will help, but you can try setting hardware acceleration to emulation by changing / adding this in regedit ;)
```
[HKEY_CURRENT_USER/Software/Wine/DirectSound] "HardwareAcceleration" = "Emulation"
```

---

### Post by Damburger on 2006-01-15
I can load WoW until the character selection screen, then when I try and actually connect to the game, it freezes when the progress bar is around two thirds done. The computer doesn't seem to actually crash though (I can recover by shutting down wine and the x server).

Anybody recognise this bug (I'm running a 64 bit install if it helps)

---

### Post by jackie_brown on 2006-01-15
i have nearly the same problem, just when the progress bar is at 100% - nothing happens anymore.

---

### Post by RavenndudE on 2006-01-15
I was able to login and then restart and download the patches. But now when I
$wine WoW.exe
I hear the music, but notthing shows up, not even in the task bar. But if I alt-tab I see the wow icon but it won't show up when I open it, but it does show in the task bar.

I am using the latest version of wine without any tweaks to the source.
I am using Breezy
I am trying to install on a Gateway laptop with a 1.4ghz Celeron M, 512 of DDR and an intigrated GPU

---

### Post by tafsen on 2006-01-15
Trying once more: Does this guide only work for ATI/Nvidia? 
I have an intel integrated Graphich Card. Can I make it work on that?

---

### Post by mesilliac on 2006-01-16
[QUOTE=tafsen]Trying once more: Does this guide only work for ATI/Nvidia? 
I have an intel integrated Graphich Card. Can I make it work on that?[/QUOTE]
try it and see :). If your onboard graphics meet the game specs I see no reason it shouldn't work.


To everyone having problems - are you using terrasque's .deb from page 16 of this thread?

Can you run WoW from a terminal and post any error messages wine is giving you?


You can also try following the vague instructions I posted on page 17 of this thread (especially amd64 users) if they differ from what you've done.

---

### Post by RavenndudE on 2006-01-16
[QUOTE=mesilliac]
To everyone having problems - are you using terrasque's .deb from page 16 of this thread?

Can you run WoW from a terminal and post any error messages wine is giving you?


You can also try following the vague instructions I posted on page 17 of this thread (especially amd64 users) if they differ from what you've done.[/QUOTE]

ok, I installed the tweaked wine from page 16 and I followed the psudo-instructions on page 17. This doesn't start at all... here's what the console puts out:
```
ravenndude@pirateship:~/World of Warcraft$ wine WoW.exe
X Error of failed request:  GLXUnsupportedPrivateRequest
  Major opcode of failed request:  144 (GLX)
  Minor opcode of failed request:  17 (X_GLXVendorPrivateWithReply)
  Serial number of failed request:  354
  Current serial number in output stream:  354

```

---

### Post by tafsen on 2006-01-16
wine WoW.exe
X Error of failed request:  GLXUnsupportedPrivateRequest
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  17 (X_GLXVendorPrivateWithReply)
  Serial number of failed request:  630
  Current serial number in output stream:  630

What's wrong?

glxinfo | grep direct
direct rendering: Yes

---

### Post by glaze on 2006-01-16
[QUOTE=tafsen]wine WoW.exe
X Error of failed request:  GLXUnsupportedPrivateRequest
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  17 (X_GLXVendorPrivateWithReply)
  Serial number of failed request:  630
  Current serial number in output stream:  630

What's wrong?

glxinfo | grep direct
direct rendering: Yes[/QUOTE]

You have to apply a patch that downgrades Wine's OpenGL implementation, because the new implementation doesn't work with WoW, or you can also use older Wine.

---

### Post by tafsen on 2006-01-16
How do i do that? I installed the deb from page 16

---

### Post by Crovax2000 on 2006-01-16
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  13 (X_GLXCreateGLXPixmap)
  Serial number of failed request:  469
  Current serial number in output stream:  470

I'm getting this error, do i need to d/l a patch to downgrade Wine's OpenGL Implementation?

---

### Post by Burkey on 2006-01-16
Hmm, a fresh install on a Dell laptop with an i915 and WoW starts up ok but has LOTS of missing textures, most things in game are just white.

This is with wine 0.9.5 straight out of Automatix BTW.. I will have a shot at the deb posted here but when I tried last night could not get to the server it is on.

Will try again.

---

### Post by Burkey on 2006-01-16
Ok, I get the same on the .deb from page 16, however it only works using DX, if I use OpenGL I get the same error as above..

```
X Error of failed request: GLXUnsupportedPrivateRequest
```

---

### Post by tafsen on 2006-01-17
Can't anyone help us??? =\

---

### Post by RavenndudE on 2006-01-17
Doesn't look like it, I may have to make a small XP partition on my laptop just to play WoW

=(

---

### Post by hiltunen on 2006-01-17
Having a problem and no idea what to do about it.

Trying to start World of Warcraft and only thing that I get is next problem:

 ./bin/cvscedega /home/hiltunen/.cvscedega/drive_c/Program\ Files/world/WoW.exe --winver win2000
fixme:cdrom:CDROM_GetIdeInterface not implemented for true scsi drives
err:win32:PE_fixup_imports No implementation for ADVAPI32.dll.563(SetSecurityInfo) imported from C:\Program Files\world\WoW.exe, setting to 0xdeadbeef
fixme:keyboard:X11DRV_KEYBOARD_DetectLayout Your keyboard layout was not found!
Using closest match instead (Latin American keyboard layout) for scancode mapping.
Please define your layout in windows/x11drv/keyboard.c and submit them
to us for inclusion into future Wine releases.
See the Wine User Guide, chapter "Keyboard" for more information.
fixme:debug:FlushInstructionCache (0x00400000,0x82c800,0x00000004): stub
fixme:ntdll:NtQueryInformationToken (00002088,1,(nil),0,0xb7a8222c): stub
fixme:ntdll:NtQueryInformationToken (00002088,1,0xb7a82008,20,0xb7a8222c): stub
fixme:ntdll:RtlValidAcl stub
fixme:ntdll:RtlValidAcl stub
err:seh:EXC_RtlRaiseException possibly COM stub exception at 0xdeadbeef
./bin/cvscedega: line 108: 12206 Segmentation fault      "$ConfigurePrefix/bin/$WineExecName" "$@"

If somebody could just tell me what to do. Been googling for couple of days already. And please. Quite specific instructions would be nice. Funniest thing was that I installed WoW and even patched it. And now it does that... So please. Pimp my ri... no not that one. So please help me out here.

---

### Post by mesilliac on 2006-01-18
To those who installed the .deb from page 16 and are getting the GLXUnsupportedPrivateRequest error - did you make sure to uninstall wine before installing wine-wow?

I'm afraid I can't help much except for with the problems I had before I got it to work :(. Haven't had that one...

> Hmm, a fresh install on a Dell laptop with an i915 and WoW starts up ok but has LOTS of missing textures, most things in game are just white.
Wine's DirectX implementation isn't fully functional. using DirectX works, but many textures seem to be missing, which is why OpenGL is recommended.


Apparently something in wine 0.9.4 broke openGL for WoW. I've heard that there's an extra / diferent patch for wine that needs to be compiled in if you want to use 0.9.4 or 0.9.5. The 0.9.3 deb seems to work fine though, so I haven't tried it (compiling 32 bit is a chore on my amd64 system).

Using the 0.9.3 wine-wow deb you shouldn't need to patch anything...

---

### Post by tafsen on 2006-01-18
Yes I un-installed Wine with the package manager before I installed wow wine.

Is it a way that I can check that there's only one wine installed?

---

### Post by glaze on 2006-01-21
I got WoW working again, by downgrading NVIDIA driver to 7676 and kernel to 2.6.13.5, and using Wine 0.9.1. Has anyone tried Wine 0.9.6 yet?

---

### Post by moccah on 2006-01-25
I`ve tried wine 0.9.6 but with no luck. Wow starts up fine, but when i enter the game it hangs and displays a "Memory could not be read" error.. I`ll keep on trying, and will post if i can get it to work.

---

### Post by alinuxfan on 2006-01-25
if you guys are having trouble...
try following kidcharles' post [here]("http://ubuntuforums.org/showthread.php?t=120615")
i know both he and i got it working this way and not sure how many others
i am not trying to discredit this howto i just know the other thread worked for me
amd xp 1700
nvidia geforce fx5200 128agp
1gig ddr ram

---

### Post by Yob on 2006-02-27
Hi,

I finished reinstalling my ADM64 and wanted to get WOW going again, but the links to the wow-wine deb are no longer working. Since i'm on an 64bit installation I can't compile it myself, so if anyone can supply it I would be very happy ;)

---

### Post by derekd on 2006-03-09
How do I copy the data from the discs for easier install with Cedega 5.1?

---

### Post by shade73 on 2006-03-10
Hey all, I've had great luck having wine work with WoW right out of the box.  The only thing I have left is the "mouse-bug".  THe one where you can't target copper NPC's etc.  I saw a guy on the first page say we have "wine_wowfixes" for that, but I can't find anything on it at all. I'm really hesitant to uninstall the ubuntu package of wine and compile from the 0.9.6 source with the patches because I'm not positive it will work (and I know aside from the mouse bug this one works).  Is there a way to fix the mouse bug without compiling back from source?  If i *have* to compile from source can you recommend what version I use for best results (is 0.9.6 fine, or something else?)  I thought i saw some posts about 0.9.1 & 0.9.3 working, but those are older so I'd rather use new packages if possible.  I also tried to grab the deb packages with it pre-compiled and none of the links worked.  I'm using opengl

---

### Post by shade73 on 2006-03-10
OK so i broke down and followed the howto with 0.9.1 and everything compiled and such.  I ran it and I still have the same bug.  The first thing I did was uninstall wine by using apt-get remove wine or something like that.  The only patch I applied was the wow-fix.patch.  Did I miss something?

---

### Post by gdoyel on 2006-03-16
Install went peachy...

Having a problem with loading WoW with OpenGL. It says "Your 3D Accelerator Card is not supported by World of Warcraft. Please install a 3D accelerator card with dual-TMU support."

If I run without opengl, I get strange colors. I know my card will work, as I used it before in Windows XP. Any guidance here?

I'm thinking new driver, but I'm not sure how to go about that in Ubuntu (breezy)

edit:
If it helps, i'm running a Intel ThinkPad.

---

### Post by thegnark on 2006-03-16
[quote=gdoyel]Install went peachy...

Having a problem with loading WoW with OpenGL. It says "Your 3D Accelerator Card is not supported by World of Warcraft. Please install a 3D accelerator card with dual-TMU support."

If I run without opengl, I get strange colors. I know my card will work, as I used it before in Windows XP. Any guidance here?

I'm thinking new driver, but I'm not sure how to go about that in Ubuntu (breezy)

edit:
If it helps, i'm running a Intel ThinkPad.[/quote]


Sounds like you don't have the right driver installed. I would get this error on WinXP if I didn't yet have the video driver installed (and was instead running graphics off the CPU.).

Try searching around for instructions on updating your video card driver

---

### Post by SKLP on 2006-03-16
Hello,

I'm not maintaining this howto anymore. Feel free to change it to contain any recent hacks to make wow work :)

Also, you should probably read [http://ubuntuforums.org/showthread.php?t=144928](http://ubuntuforums.org/showthread.php?t=144928) ...

Have fun,

// 
   sklp

---

### Post by Lushlie on 2006-03-16
Error when I try wine wow.exe  Very new to ubuntu, also getting the 3d accelerator error.

err:module:import_dll Library DivxDecoder.dll (which is needed by L"C:\\windows\\system32\\wow.exe") not found
err:module:import_dll Library fmod.dll (which is needed by L"C:\\windows\\system32\\wow.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\windows\\system32\\wow.exe" failed, status c0000135

:confused:

---

### Post by EX0S on 2006-03-16
Very nice. I have a level 48 warrior on Burning Blade. I never knew linux can run WoW.

---

### Post by markfra on 2006-03-30
Hello,

I am also running wow on Linux and i am fairly happy with it :) No more windows and the good thing is: It works like a charm.

This al is running for less than a month and so i got suprised yesterday when i wanted to apply patch 1.10.
The download works good, only when i want to start the patch it tells me:

```

markfra@orion:~/.wine/drive_c/World of Warcraft$ wine WoW-1.9.4.5086-to-1.10.0.5195-enGB-patch.exe
err:module:import_dll Loading library MFC42.DLL (which is needed by L"C:\\World of Warcraft\\BNUpdate.exe") failed (error c0000020).
err:module:LdrInitializeThunk Main exe initialization for L"C:\\World of Warcraft\\BNUpdate.exe" failed, status c0000135

```

I have been searching on google and some ppl said that you had to change form builtin to native dlls
At this moment the mfc42.dll is in .wine/drive_c/windows/system32 but it still complains, i have tried to copy the files to the patch directory itself, and many other directories but i keep on getting this error.

Starting wow is no problem though.

Can someone help me?

---

### Post by justleen on 2006-03-30
[QUOTE=markfra]Hello,
I have been searching on google and some ppl said that you had to change form builtin to native dlls
At this moment the mfc42.dll is in .wine/drive_c/windows/system32 but it still complains, i have tried to copy the files to the patch directory itself, and many other directories but i keep on getting this error.

Starting wow is no problem though.

Can someone help me?[/QUOTE]
I had exactly the same problem yesterday.. make sure _both _.dll files (see first post HOWTO) are in the system32 dir.
After that you should  be able to run the update

---

### Post by markfra on 2006-03-30
I have and i am very sure about that, i even moved the system32 to system and then it complained that it could not find system32.
It was obviously that i had to put the dll files in that directory.

This morning however i came to a new idea:

I put the dll in /usr/local/lib/wine/ and added that to override library part in winecfg with "Load Order" as Native selected.

This worked so it's patched (at work :)) now i only have to wait untill i come home ^^

---

### Post by Zer0d on 2006-04-03
I have installed wine 0.9.11 from deb files.
What path should i follow when i comes to the mouse problem?
Wine runs much better than cedega, so it would be fun to get the mouse problem fixed =D
I've tried alot of ways but i just seem to get nowere. The normal mouse problem output :

```
fixme:advapi:SetSecurityInfo stub
fixme:powrprof:DllMain (0x7ca80000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 11
fixme:powrprof:DllMain (0x7ca80000, 0, (nil)) not fully implemented
fixme:win:EnumDisplayDevicesW ((null),0,0x7fb9eedc,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7fb9f448,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7fb9f6e8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7fb9f6e8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7fb9f650,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7fb9f63c,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:win:EnumDisplayDevicesW ((null),0,0x7fb9f158,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 112 (SPI_GETMOUSESPEED)
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:sync:CreateIoCompletionPort (0xffffffff, (nil), 00000000, 00000000): stub.
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 4
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:imm:ImmAssociateContextEx (0x10024, (nil), 16): stub

```

---

### Post by microthorne on 2006-04-24
Hi,

I can get to the login screen, but when I try to login authentication fails with an "unable to connect" error message.  My internet connection is obviously fine.  If I boot into windows I can login.

I apologize if this was covered in a previous post already.

---

### Post by microthorne on 2006-04-24
[QUOTE=microthorne]Hi,

I can get to the login screen, but when I try to login authentication fails with an "unable to connect" error message.  My internet connection is obviously fine.  If I boot into windows I can login.

I apologize if this was covered in a previous post already.[/QUOTE]

Nevermind.  Blizzard just posted "Breaking News" stating they are having authentication issues O_o

---

### Post by glaze on 2006-04-26
I updated from kernel 2.6.13 to 2.6.16ck7 and nvidia 1.0-7676 to 1.0-8756. Before I was getting fps like 30-40, now only 15-25 :-(

---

### Post by Rafinator on 2006-04-26
Do games lag when using wine?

---

### Post by tafsen on 2006-04-27
Is it still not possible to play WoW in linux if you not got either a nvidia or ATI gpu?

---

### Post by Binny45 on 2006-04-27
Aye, I'm still searching for a driver for my ATI X800 GTO Fireblade.  Once I accomplish that, then I'll need to learn how to install it LMAO!

Once I'm at that point, I at least have this thread to come to , so that I can install my precious WoW!

---

### Post by Andrew-buntu on 2006-04-27
[QUOTE=Rafinator]Do games lag when using wine?[/QUOTE] 

No, WoW doesn't lag any more than it would if you were playing on windows.  Works great if you have a decent video card (I recommend nvidia) and play in opengl.

[QUOTE=tafsen]Is it still not possible to play WoW in linux if you not got either a nvidia or ATI gpu?[/QUOTE]

I think some people have configured Intel graphic chipsets to play.  The important thing is having hardware rendering.  Look around and I'm sure you'll find some Intel-owning posters.

Zer0d, I coudn't quote your post for some reason.  But if you want to get rid of the mouse bug, you need to patch wine before you install it.  You can still do that with .debs.  You just download the source .deb with "apt-get source wine", then patch, then "apt-get --build source wine".  You'll have wine in a nice package and you'll be able to uninstall with apt-get or synaptic.  Just look around this forum for the patches - the newest ones (0.9.12 at the moment) are usually linked on the first post.

---

### Post by Grog140 on 2006-05-02
Thanks for the wiki, I got it up and running but I cant change the video settings./

When I try running it in D3D I only get far enough to see my character on screen and it then freezes before I can change the settings to lower. Any advice would be appretiated.

EDIT: I got it working, I just need to figure out how to click on things. I remember reading about a patch but cant find it. If anyone could steer me in the right direction it would be cool.

EDIT2: Ok, I am good now, I got the mouse thing fixed. Well the patch included int he wiki would have done it but I went [Here]("http://appdb.winehq.org/appview.php?versionId=4031") and it did the trick for me.

---

### Post by Alexeon Lanar on 2006-05-19
Hello. I was going to install wine, but decided against it after I had downloaded the apt-get build-dep wine files. What do I have to do to get rid of them?
BTW, I downloaded these while following a different guide, also on installing WoW through wine.
Please help. No one answered my question on the other thread...
Thank you.

---

### Post by eqisow on 2006-06-09
The WoW version of Wine on the Wine wiki has been updated to 0.9.15. Enjoy. :)

[https://wiki.ubuntu.com/Wine](https://wiki.ubuntu.com/Wine)

P.S. - If somebody could let me know if the installer still hangs with 0.9.15 that would be fantastic.

---

### Post by zachtib on 2006-06-09
it appears to, right after i click on 'install' right?
also, no text shows up on the buttons in the installer, is this normal?

---

### Post by eqisow on 2006-06-10
It would be normal if you didn't have the right fonts installed. I, personally, installed from the disk with no issues at all. But I also think I had a lot of fonts installed already.

Just to clarify, the locking up should resolve itself after awhile. At least it did in 0.9.14. You just have to be patient. :)

---

### Post by basse1989 on 2006-06-11
My fps really suck, way below what I get in windows.
Im using a geforce 6600 with nvidia-glx 1.0.8762+2.6.15.11-1
I used my old config from windows and fixed it as the guides say and got crappy fps, so I deleted it and let wow make a new one but my fps still suck :(
Anyone know what might fix it?

---

### Post by groggyboy on 2006-06-11
So I used to get the dreaded error 132, until I read that basse1989 in the post above had deleted his windows config file and finally had success getting WoW to run.

I backed up my Config.wtf file, and deleted the original.  Now I have a different problem: WoW starts, but I have no cursor control.  I can watch the opening cutscene, but clicking does nothing.  Hitting escape crashes the game.  Letting the cutscene finish also results in the game crashing.  At least the error 132 doesn't happen anymore!

I also noticed that there is no new Config.wtf file.  Any ideas?

groggyboy

---

### Post by zachtib on 2006-06-11
[QUOTE=eqisow]It would be normal if you didn't have the right fonts installed. I, personally, installed from the disk with no issues at all. But I also think I had a lot of fonts installed already.

Just to clarify, the locking up should resolve itself after awhile. At least it did in 0.9.14. You just have to be patient. :)[/QUOTE]

ok, it installed.  now i get no fonts in the game with opengl, but i do with d3d, what should i do from here?

---

### Post by milamber on 2006-06-12
Recently installed Ubuntu 6.06 and very pleased so far. The last thing i need now is to get my WoW working on Ubuntu so i can leave Windows behind. So far i got a long way with the guides from:

[https://wiki.ubuntu.com/WorldofWarcraft](https://wiki.ubuntu.com/WorldofWarcraft)
and
[https://wiki.ubuntu.com/Wine](https://wiki.ubuntu.com/Wine)

I managed to get the log in screen and char selection screen of WoW with sound and perfect graphics (i was very pleased with myself about thios :D  )

When i got to the actual game however i was (and still am) faced with a problem. The screen keeps flickering at a very annoying rate so that the game becomes unplayable. I tried to play around with the video setting some but that does not seem to help.

I think its something with my video card (nvidia Geforce 2). I installed the drivers and my 3d rendering is ok. I also tried to run the game with: wine WoW -d3d
but then i get black areas everywhere where an object is on the ground.

Does anyone have any suggestions? Else i still have to go to windows everytime to be able to play WoW :S

---

### Post by sadscientist on 2006-07-24
```
andrew@deimos:/$ sudo apt-get build-dep wine
Reading package lists... Done
Building dependency tree... Done
Note, selecting libicu34-dev instead of libicu-dev
Note, selecting libfontconfig1-dev instead of libfontconfig-dev
E: Build-dependencies for wine could not be satisfied.

```

:(  Any ideas why?

---

### Post by ilmorris on 2006-07-24
Is there a way to stop the update notifications and synaptic trying to upgrade wine if I am using the wine w/WoW patches .deb package?

---

### Post by Anivair on 2006-08-05
Any chance anyone knows how to make this play nice with XGL?  

I've got WoW running perfectly on ubuntu 6.06 (thank you very muchm, I can now never log into windows again) but in an XGL session I get an error saying that WoW can't start graphics acceleration.  Clearly acceleration works, so it's probably a config issue.  thoughts?

---

### Post by eqisow on 2006-09-16
Updated the wiki to Wine 0.9.21. This one should fix the ATI crashes. Hooray!

---

### Post by vinnie on 2006-09-23
> **Anivair said:**
> Any chance anyone knows how to make this play nice with XGL?  

I've got WoW running perfectly on ubuntu 6.06 (thank you very muchm, I can now never log into windows again) but in an XGL session I get an error saying that WoW can't start graphics acceleration.  Clearly acceleration works, so it's probably a config issue.  thoughts?

[http://ubuntuforums.org/showthread.php?t=176636](http://ubuntuforums.org/showthread.php?t=176636)

---

### Post by lazyron on 2006-09-29
> **Burkey said:**
> Ok, I re-installed Ubuntu 5.10 clean.. then installed wine and set my Config.wtf as above, I now get a different error.

```

Your 3D Accelerator is not supported by World of Warcraft. Please install a 3D accelerator card with dual-TMU support.

```

So a kind of progress I guess.. breakfast now but will try some more things when I get back, hope someone might be able to shed some light

> **SKLP said:**
> That's odd :(

What 3d accelerator are you using? what does "glxinfo | grep direct" give?
what did you install instead of nvidia-glx-dev? 
and finally what does 
glxgears -iacknowledgethatthistoolisnotabenchmark give? :D

I'm having this same problem, but with the updated version of Intel's onboard graphic chip, the 950. This is the same chipset that is in the MacBooks, which *can* play WoW, so I'm hoping that some solution has been found to this. I'm having the same (or very similar problems). I get the message above if I try to load the game with -opengl. In -d3d, i can run around in enclosed spaces (like UC), but if I try to go outside, the textures tear and I can't tell up from down, left from right... through the looking glass :P And if I load the game in -d3d and I'm outside, my laptop just crashes very hard. FWIW, I have a Dell E1405.

Any suggestions?

---

### Post by Gioutsaman on 2006-10-06
yo :D i also have a small problem with WoW. I installed it sucessfully with wine 0.9.6 (i applied the patches before compiling) and when i start the game after the intro is finished it crashes ](*,) ](*,) .the message i get:


fixme:advapi:SetSecurityInfo stub
fixme:powrprof:DllMain (0x7c220000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 11
fixme:powrprof:DllMain (0x7c220000, 0, (nil)) not fully implemented
fixme:win:EnumDisplayDevicesW ((null),0,0x7fb9eee8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7fb9f158,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7fb9f6f4,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7fb9f6f4,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7fb9ee60,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7fb9f65c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7fb9f648,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:win:EnumDisplayDevicesW ((null),0,0x7fb9ee60,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 112 (SPI_GETMOUSESPEED)
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:sync:CreateIoCompletionPort (0xffffffff, (nil), 00000000, 00000000): stub.
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_RECEIVE_TIMEOUT: STUB
fixme:wininet:InternetSetOptionW Option 45 STUB
fixme:imm:ImmGetContext (0x20022): stub
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  13 (X_GLXCreateGLXPixmap)
  Serial number of failed request:  386
  Current serial number in output stream:  387


help please...i have an nvidia 4800 ti.

---

### Post by groggyboy on 2006-10-10
> I'm having this same problem, but with the updated version of Intel's onboard graphic chip, the 950. This is the same chipset that is in the MacBooks, which *can* play WoW, so I'm hoping that some solution has been found to this. I'm having the same (or very similar problems). I get the message above if I try to load the game with -opengl. In -d3d, i can run around in enclosed spaces (like UC), but if I try to go outside, the textures tear and I can't tell up from down, left from right... through the looking glass :P And if I load the game in -d3d and I'm outside, my laptop just crashes very hard. FWIW, I have a Dell E1405.


I feel your pain lazyron.  I've got a Dell Inspiron 6000 with onboard i915 graphics.  And I have identical symptoms.  Running with opengl results in a message about my hardware.  Running with d3d produces exactly the same effects you describe.  I hope this gets fixed in a future edition of wine.  Any idea if wine 0.9.22 has been patched for WoW yet?

---

### Post by Ferrat on 2006-10-10
> **groggyboy said:**
> I feel your pain lazyron.  I've got a Dell Inspiron 6000 with onboard i915 graphics.  And I have identical symptoms.  Running with opengl results in a message about my hardware.  Running with d3d produces exactly the same effects you describe.  I hope this gets fixed in a future edition of wine.  Any idea if wine 0.9.22 has been patched for WoW yet?

wine 0.9.22 doesn't need to be patched for wow except for some nVIDIA users and that patch is listed in the appdb at winehq =)

---

### Post by larsne on 2006-10-14
Hi, i couldnt find any post in this thread with the same problem as i have, but hopefully some of you are skilled enough to give me a few pointers :) 
If i run WoW using -opengl, i get the regular WoW-errormessage (blue thing), but if i run it without opengl everything works fine, except the 3d is upside-down, GUI is the correct way. I'm also rather new to linux, so im not sure what information you need to be able to help me, feel free to send me a  message or an email.  

I'm using Wine 0.9.21
ATi Mobility Radeon 9700
Ubuntu 6.06 

Thanks in advance

---

### Post by larsne on 2006-10-14
I figured it out, i just had to disable fullscreen glow effects in WoW. So hopefully this will help someone else with the same problem :)

---

### Post by simplyw00x on 2006-10-14
With a Radeon 9200 SE, it runs fine with D3D (but slowly) with wine 0.9.22, but gets the error #132 on starting if run with opengl. It has been working with opengl in previous versions of wine. Any ideas?

---

### Post by Castar on 2006-10-19
Hi, I used to be able to run WoW with Kubuntu Dapper's wine, albeit the sound problem.

Now, I have updated to Edgy and the wine included and also the wine I manually compiled (0.9.22 and 0.9.23) do actually work, but the game is unplayable to say the least. 

I'm using the i810 driver for my Intel i915.

Any suggestions please? :confused: I really want to dump windows :(

---

### Post by exp0zed on 2006-11-07
I am suffering from one slight problem, whenever I enter a building with my minimap open my screen seems to refresh or flash rapidly until I resize the screen (with the actual panel of WoW). It makes it hard to enter dungeons and what not since my minimap must be closed whenever I enter any buildings. 

Anyone have any clues on the issue, if so feel free to PM or leave a reponse here.

Regards,

Peer

---

### Post by Castar on 2006-11-07
So, I've installed Crossover and it finally works! No problems with the graphics anymore, but notably slower than windows on my PC :(.

Still, I have decided to stop playing. For now at least. :)

---

### Post by doktor_p on 2006-11-08
hi folks!
i installed wine from the patched .deb in found in the howto (version 0.9.21_wow_i386.deb), then copied the content of all wow cds in a dir on my HD and installed it from there.
although i couldn't read properly the eula and other writings during the installation process it worked just fine, with no error messages.
anyway when launching wow with the command

```
wine WoW.exe
```

once inthe wow directory i get this reply:

```

fixme:advapi:SetSecurityInfo stub fixme:powrprof:DllMain (0x7d350000, 1, (nil)) not fully implemented fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 11 fixme:powrprof:DllMain (0x7d350000, 0, (nil)) not fully implemented fixme:win:EnumDisplayDevicesW ((null),0,0x33eeec,0x00000000), stub! fixme:win:EnumDisplayDevicesW ((null),0,0x33f458,0x00000000), stub! fixme:win:EnumDisplayDevicesW ((null),0,0x33f6f8,0x00000000), stub! fixme:win:EnumDisplayDevicesW ((null),0,0x33f6f8,0x00000000), stub! fixme:win:EnumDisplayDevicesW ((null),0,0x33f660,0x00000000), stub! fixme:win:EnumDisplayDevicesW ((null),0,0x33f64c,0x00000000), stub! fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)fixme:win:EnumDisplayDevicesW ((null),0,0x33f168,0x00000000), stub! fixme:system:SystemParametersInfoW Unimplemented action: 112 (SPI_GETMOUSESPEED)fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)fixme:sync:CreateIoCompletionPort (0xffffffff, (nil), 00000000, 00000000): stub.fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 4 fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
```

if you want to have a look this is my config.wtf:
```

SET gxColorBits "24" 
SET gxDepthBits "24" 
SET gxResolution "800x600" 
SET gxRefresh "60" 
SET hwDetect "0" 
SET fullAlpha "1" 
SET lodDist "100.000000" 
SET SmallCull "0.040000" 
SET DistCull "500.000000" 
SET trilinear "1" 
SET frillDensity "24" 
SET farclip "500.000000" 
SET particleDensity "1.000000" 
SET unitDrawDist "300.000000" 
SET movie "0" 
SET readTOS "1" 
SET realmList "eu.logon.worldofwarcraft.com" 
SET SoundOutputSystem "2" 
SET SoundBufferSize "150" 
SET gxApi "OpenGL"
```

i also tried soundoutputsystem "1" and "-1" and soundbufersize "100"
what's wrong???
i'm on dapper, with a radeon igp 340m (64MB ram) with mesa/DRI drivers and direct rendering enabled.
please help obi wan kenobi, you're my last hope...

---

### Post by msnider on 2006-11-14
Is there an advantage to playing on ubuntu or?

just wondering if its worth the time for a n00b to put ubuntu on a laptop and dual boot to play WoW in linux?

---

### Post by doktor_p on 2006-11-14
no, i don't think is a good idea setting up a dual boot system to play wow on ubuntu.
actually wow is the only software i run on win on my notebook...

---

### Post by msnider on 2006-11-14
So basically if my wife uses Office and I basically do Firefox and WoW, there isn't much of a need of installing ubuntu besides something new,fresh, and better of an OS ?

---

### Post by reiki on 2006-11-14
DEpends, I guess on how much you're willing to pay. How much does Office cost? How much was your operating system? How much to upgrade?

Ubuntu... free
OpenOffice (installed by default) ... free (and it opens MS Office docs and can save them BACK as MS Office docs)

I can go on, but basically I have escaped Microsoft (no I'm not an MS basher but I can play one if you like), escaped the cost of upgrading software, my PC RUNS BETTER... yup... really, and I haven't lost any functionality at all. I play WoW under Wine and it seems smoother than it ever did in Windows and I know that's a rather subjective description and I have no hard data to back up my claim, but there it is nonetheless. :)

---

### Post by Sammi on 2006-12-03
Seems that the vannila deb file of version 0.9.26 works out of the box for most users, so therefor I have updated the helpfile.

I have deleted the instructions on the patched deb file and added instructions on installing Wine directly from WineHQ's unofficial repositories.

---

### Post by LeChuckThePirate on 2007-03-06
I've finally made WoW work in Ubuntu 6.10 x86 with my new ATI X1950PRO card using the latest ATI drivers (8.34¿?)

I've done all the tricks I've found in several forums, including the OpenGL settings in registry, all the gxXXXXX options in the config.wtf file, changing settings in xorg.conf to avoid WoW freezes :

```
Option "Capabilities" "0x00000800" 
Option "UseFastTLS" "off" 
Option "KernelModuleParm" "locked-userpages=0"
```

Yet still, the only way to get an acceptable framerate is looking at the floor, or getting inside a little building, the FPS raise to 42/50 (in Windows I get about 100fps in those situations) and drop dramatically in outdoors (at Terokkar they drop to 10-15fps with choppy sound, rendering the game unplayable...

Do you have any advice/tip/trick I could try to boost FPS ?

I'll try to update this post when I get home with my xorg.conf and config.wtf to make it easier for the gurus ;)

My system specs:

AMD64 3000+
Motherboard Asus A8R-MVP Crossfire
1GB RAM
120GB IDE + 160GB SATA2 HD (linux on SATA2 drive)
ATI Radeon X1950PRO single (not crossfire)
Dual Screen setup Acer AL1922 19" (1280x1024) / Acer AL1916W 19" (1440x900)
Ubuntu 6.10 (Efty Edge) x86 Spanish with Gnome Desktop (dual head) DRI enabled

Thanks in advance ;)

---

### Post by Sammi on 2007-03-06
This is an old and dead tread. I made a new one here: [http://www.ubuntuforums.org/showthread.php?t=312482](http://www.ubuntuforums.org/showthread.php?t=312482)

---

### Post by Perfect Storm on 2007-03-06
Thread Closed.

---

