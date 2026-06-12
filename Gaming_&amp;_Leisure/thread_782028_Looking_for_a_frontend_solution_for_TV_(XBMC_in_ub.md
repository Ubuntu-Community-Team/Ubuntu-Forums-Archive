---
title: "Looking for a frontend solution for TV (XBMC in ubuntu?)"
date: 2008-05-04
forum: Gaming &amp; Leisure
---

### Post by KamakazieX on 2008-05-04
I am looking to eliminate the need for a keyboard and mouse on the ubuntu desktop. Basically its here to replace my PS2, and I am keeping the controllers as the HIDs for the box. (I will also have VNC) Heres the important stuff:

*MythTV could work though its a waste of resources due to the SQL backend. Plus its a **** to setup!
*Will utilize some sort of interfacing to convert a ps2/usb controller to the mouse and arrows for the frontend
*Like to have mythtv like "watch a movie" menu to a shared resource on a windows box with divx
*Like to have mythtv like "listen to music" menu to a shared resource on a windows box with mp3's and ogg's
*I have tons of SNES, NES, Genesis, MAME, you name it, and I am looking for it all integrated into one frontend solution along with the movies and music playing

**The machine does not currently have a TV tuner in it.


-I hear XBMC got ported, would that be my best choice? Has anyone installed it on an Ubuntu box?

---

### Post by Topfs on 2008-05-23
XBMC for linux is quite far along and we actually have a repository for you so it's very easy to install and test it. [Here]("http://xbmc.org/forum/showpost.php?p=185738&postcount=1") are the URL's needed for sources.list after these it's only > sudo apt-get update
sudo apt-get install xbmc You can install skins aswell from this by sudo apt-get install xbmc-skin*
I'm not familiar with the PS2 controllers but everything that is supported through SDL's joystick is supported and just needs to be mapped.
The emulator is not currently working IIRC as python scripts is abit shaky, although this should hopefully be remedied somewere down the line, most problems stems from the fact that linux have casesensetive paths were xbox/windows does not which some scripts missuse.

PS: XBMC for linux is developed on Ubuntu so it's the prefered distro.

Sincerely Topfs2

---

