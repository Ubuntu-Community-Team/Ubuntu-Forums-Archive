---
title: "Supreme Commander Forged Alliance patch questions"
date: 2009-06-12
forum: Gaming &amp; Leisure
---

### Post by lheinemann on 2009-06-12
I have tinkered around with linux for years so I am familiar with it but def not a power user.  Just installed 9.04 and ran install of Forged Alliance through wine 1.0.1 yesterday but i get an error saying something about a security exception every time I try to run the game.  I know I need to patch the game from .3596 to .3599 but not sure how to do it.  Someone suggested using the "virtual machine" method and I have no clue what that means.  Any thoughts?

This is not a wine question cause the patch won't run through wine either gui or terminal or right-clicking and "run with wine".  Thanks

---

### Post by Bölvaður on 2009-06-12
> **lheinemann said:**
> This is not a wine question cause the patch won't run through wine either gui or terminal or right-clicking and "run with wine".  Thanks

Yes this is a wine question.


Virtual machine is a program that allows you to run other operating systems, google "virtual box" or install it from add/remove. you'll need an .iso or a cd to install an operating systems on the virtual machine you can create.

But be aware that this will not work to run supreme commander, you will need wine for that.

Check out what people did to make it work:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=7038](http://appdb.winehq.org/objectManager.php?sClass=version&iId=7038)
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=9728](http://appdb.winehq.org/objectManager.php?sClass=version&iId=9728)

---

### Post by lheinemann on 2009-06-12
I know what a virtual machine is I even use Vbox and have msdn.  I dont want to install windows on a VM and then SupCom on that cause i have two drives 1 vista and 1 ubuntu already.  I got that "virtual machine" mode thing from the wine website I just am not sure what it means.

---

### Post by clw3388 on 2009-06-13
hes not telling you to install vm and run supreme commander from it.. He was just explaining what a VM is. some people, believe it or not, really don't know :) 

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=9728](http://appdb.winehq.org/objectManager.php?sClass=version&iId=9728)
points out

********************************************************************	
Working pretty well in 1.0...
by Charles Huber on Saturday June 21st 2008, 22:21
Debian lenny (amd64), 8800GTS, using Wine 1.0 from the Winehq repo and a clean ~/.wine:

$ wget [www.kegel.com/wine/winetricks](www.kegel.com/wine/winetricks)
$ sh winetricks gdiplus dotnet20 vcrun2005 mono19
$ wine /path/to/FA/DVD/setup.exe
$ wget thq.vo.llnwd.net/o10/SC/live/supcom_fa_patch_1.5.3596_to_1.5.3599.exe
$ wine supcom_fa_patch_1.5.3596_to_1.5.3599.exe

Make sure to set OffscreenRenderingMode to FBO in the Registry.

Sound worked fine out-of-the-box using ALSA, 44100/16, and Emulation.

For mostly glitch-free graphics, set in ~/.wine/drive_c/windows/profiles/`whoami`/Local\ Settings/Application\ Data/Gas\ Powered\ Games/Supreme\ Commander\ Forged\ Alliance/Game.prefs:
antialiasing = 0
fidelity_presets = 4
texture_level = 0
level_of_detail = 2
shadow_quality = 0
fidelity = 1
bloom_render = 0
*********************************************************************
 Might give that a try..
Also according the the wine website more people are having luck with supreme commander under 1.1.22.. I hate to update wine unless i have to cause crap breaks.. but then again yours is a new install so what's gonna break?

---

### Post by Zenki on 2009-10-20
Finally! The forum i was looking for.
So I get the same error...
 
 
I need to get VM, patch the game, then use wine to run it?  And the patch will solve the error message?

---

