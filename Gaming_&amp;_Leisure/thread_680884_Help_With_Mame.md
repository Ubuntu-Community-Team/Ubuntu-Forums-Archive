---
title: "Help With Mame?"
date: 2008-01-28
forum: Gaming &amp; Leisure
---

### Post by CarlosinFL on 2008-01-28
I have installed mame and gxmame on Ubuntu 7.10. I also downloaded one ROM (Street Fighter Alpha 3) and am unable to understand how I can play this ROM. When I launch gxmame - it loads fine but how to I tell it to play the ROM file that is located on my Desktop? How do I import the ROM into gxmame so I can play the game???

---

### Post by frenchn00b on 2008-01-28
I use kxmame since it has less bugs:[http://sourceforge.net/projects/kxmame/](http://sourceforge.net/projects/kxmame/)
[http://ubuntuforums.org/showthread.php?p=4179576#post4179576](http://ubuntuforums.org/showthread.php?p=4179576#post4179576)
 
Here is for xmame with console.
[http://ubuntuforums.org/showthread.php?t=342543&highlight=howto+xmame](http://ubuntuforums.org/showthread.php?t=342543&highlight=howto+xmame)

---

### Post by CarlosinFL on 2008-01-28
I don't have any problems running gxmame - I just don't see how I import my game. I don't use KDE so no need for kxmame. :confused:

---

### Post by disturbedite on 2008-01-28
yeah, i'd recommend kxmame over gxmame.  for one thing, its faster.
but don't install the kxmame package from the ubuntu repo nor any form of xmame.
see my post here please:
[http://ubuntuforums.org/showthread.php?p=4179576#post4179576](http://ubuntuforums.org/showthread.php?p=4179576#post4179576)

---

### Post by DoktorSeven on 2008-01-28
Plus gxmame is much buggier.  Either one, though, adds ROMs in the same way if you're using plain xmame -- in Settings, there should be a Directories or similar option that you set all of the paths your ROMs and other things are in.  This should be a setting called Mame ROM Paths or similar.  Point that to your desktop (/home/(your user name)/Desktop) and it should find the ROM.

If you set up SDLmame and kxmame as shown in the thread above, however, you'll need to edit the mame.ini configuration file to point to your ROMs.  See that thread and others for more information.

---

### Post by chochem on 2008-02-04
In GXMame enter Options | Directories | XMame basic paths. In the 'ROMs paths' section, enter (or browse your way to) the path of your directory with zipped ROMs (e.g. /home/[username]/.mameroms - probably a better place than the desktop). Be sure to click 'Add' so that the path appears in the list. Click OK.

Now click 'Rebuild games list' in the Options menu. Switch the sidebar view to 'Available' and click the 'Refresh' button. Your game should appear.

If it does not, check that a) your directory does appear in the 'ROMs paths' list and that there truly are zip-files in it, e.g. dkong.zip for Donkey Kong and b) verify that the file names match what GXMame expects. Enter the 'All games' view in the sidebar (topmost) and find your game, e.g. 'Donkey Kong (US set 1)' in the list and note the name in the 'Directory' pane, which is 'dkong'. This should be the name of the zip file and **bear in mind** that linux file names are case sensitive. DKONG.ZIP will not be detected (and some ahem distributions of such files are in all capitals). Rename such file(s) to all-lowercase names and start over on the rebuild routine (see [this thread]("http://ubuntuforums.org/showthread.php?t=127491") for advice on mass renaming uppercase-lowercase).

---

