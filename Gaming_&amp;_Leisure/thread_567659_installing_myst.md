---
title: "installing myst"
date: 2007-10-04
forum: Gaming &amp; Leisure
---

### Post by 99bluefoxx on 2007-10-04
hi
i have a number of old dos/win9x games i dont want to let go of and have spent the morning installing them
however i have found that a few will not install, or even run the installer. the one that will run the installer is an old one called myst, made by broaderbund. it runs the installer but terminates with a dialog box exclaining "could not find shell.dll. setup will now terminate."
how can i fix this?any  suggestion?

---

### Post by 99bluefoxx on 2007-10-04
anything???

---

### Post by yabbadabbadont on 2007-10-04
WINE application database entry for Myst:
[http://appdb.winehq.org/objectManager.php?sClass=application&iId=91](http://appdb.winehq.org/objectManager.php?sClass=application&iId=91)

Read through the entry and comments for the version you are trying to install and see if anything there can help.

Edit: It looks like you are trying to install the 16-bit, original version for windows 3.1.  That isn't supported by WINE.  What you can probably do though, is to install either DosBox or DosEmu and then install Windows 3.x in there and then the game.  I know that one of the two will run Windows 3.x, but I don't remember which one.

---

### Post by 99bluefoxx on 2007-10-04
kay il try that thanks
*gives you a cookie*

---

### Post by yabbadabbadont on 2007-10-04
Please read the edit I made to my post if you haven't already.

---

### Post by 99bluefoxx on 2007-10-04
after checking out the link it turns out that the original dos 3.1 cd release doesnt work
:0
is there anything for any other games i own?
i have got in addition to myst for dos 3.1:
azreals tear[msdos, made by mindscape]
sim city 200 special edition[95, 98se, by maxis]
the dig[ibm and compatible, lucas arts]
rollercoaster tycoon[win 9x, atari]
monopoly tycoon[9x, atari]
none of these work for me in wine and i would like to get tham going, as gaming is something i miss from windows[i havent played anything in over six months]
any help is greatly appreciated!

---

### Post by yabbadabbadont on 2007-10-04
As I stated in the edit to my first post, you will probably be able to play those games using DosBox/DosEmu (with Windows 3.x installed for the games that require it).

There is a good DosBox howto thread around here somewhere.

---

### Post by marlowe650 on 2007-10-04
scummvm will run the dig

  scummvm.org

---

### Post by 99bluefoxx on 2007-10-05
anything for the others?
i especially would like to install myst, i never got to finish it D:

---

### Post by 99bluefoxx on 2007-10-05
ok
installed dosbox and tryed to run azrael in it
however when it runs it starts to load, then quits, saying no suitable drive present, then terminates to cmdline
i tried to mount a folder as drive d, but it still dosnt work
any suggestions?
also, im trying to run the dig in dosbox, but ittl grab my cursor, freez and terminate leaving my cursor stranded and forcing me to restart x

---

### Post by Perfect Storm on 2007-10-05
Try with this dosbox: [http://gaming.gwos.org/doku.php/guides:dosbox](http://gaming.gwos.org/doku.php/guides:dosbox)
A good idea is to copy the dos games to the harddrive to run it.

---

### Post by 99bluefoxx on 2007-10-05
do i copy them as iso or into folders named the same as teh cds?

---

### Post by Perfect Storm on 2007-10-05
Try as folders as first.

---

### Post by 99bluefoxx on 2007-10-05
ok thanks, will try in morning[its 1 in the morning now, i need to sleep>.>]then post results
thanks for all teh help^^

---

### Post by 99bluefoxx on 2007-10-08
ok, found this by accident after wow stopped connecting to the internet, but if you download [http://www.dll-files.com/dllindex/dll-files.shtml?shell](http://www.dll-files.com/dllindex/dll-files.shtml?shell) and [http://www.dll-files.com/dllindex/dll-files.shtml?shell16x](http://www.dll-files.com/dllindex/dll-files.shtml?shell16x) as well as [http://www.dll-files.com/dllindex/dll-files.shtml?shell32](http://www.dll-files.com/dllindex/dll-files.shtml?shell32)
and extract them into /home/<username>/.wine/drive_c/windows and /home/<username>/.wine/drive_c/windows/system32 then the 16bit installer will run :) hope it works for others too^^
now to fix [fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB] from world of warcraft...
EDIT: i got the installer to run but myst itself wont yet, it comlains that it needs a 256 colorized pallette and then aborts once the "okay" button is clicked D= any got a way to fix wine up with a "256 color mode" somehow?

---

### Post by yabbadabbadont on 2007-10-08
You would need to edit your /etc/X11/xorg.conf and configure an 8-bit color depth display mode.  If one is already configured, you would need to set it to be the "DefaultDepth".  ;)

That's a bit of a hassle to go through though.  I forget where, but I've read about starting games in their own X session on a different TTY for better performance.  If you did that, you would be able to specify the color depth to be used.  You might also see if the xrandr utility can change the active color depth in a running Xsession.

Edit: It doesn't look like the xrandr utility can change color depth.

---

