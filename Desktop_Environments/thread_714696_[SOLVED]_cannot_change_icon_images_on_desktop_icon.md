---
title: "[SOLVED] cannot change icon images on desktop icons."
date: 2008-03-04
forum: Desktop Environments
---

### Post by keratos on 2008-03-04
If I right click on an icon on the desktop and select "Properties", the property tab appears. If I then click on the icon image (to select a different icon) the icon browser dialog appears. For the most, the icon path is usually something like /usr/share/icons/tango/48x48/apps/... and the available icons are displayed in the dialog box.

However, if I change the path to /usr/icons/<anything>... then no icons are displayed. No matter what path I enter, the icons are never displayed, just a blank dialog box.

So the icon chooser only works if I never "Browse" to another path.

Pointless really...

Any ideas good folk?

---

### Post by erginemr on 2008-03-04
I believe there are no icons in the directories you have been looking at. Please refer to the following single posts of mine for a few places which pack a good deal of icons:
[http://ubuntuforums.org/showpost.php?p=4353715&postcount=5](http://ubuntuforums.org/showpost.php?p=4353715&postcount=5)
[http://ubuntuforums.org/showpost.php?p=4189630&postcount=2](http://ubuntuforums.org/showpost.php?p=4189630&postcount=2)
[http://ubuntuforums.org/showpost.php?p=4180851&postcount=2](http://ubuntuforums.org/showpost.php?p=4180851&postcount=2)

---

### Post by keratos on 2008-03-04
there are icons there, and in the other directories I am browsing.

I PUT THE ICON THEMES THERE MYSELF. They came from tar balls.

I've checked permissions etc.

No joy!

---

### Post by erginemr on 2008-03-04
But did you try visiting the directories I gave to you? Can you still not see or select any icons in those folders either?

---

### Post by keratos on 2008-03-04
YES!

i tried them all

just a blank in the browser window that allows me to select an icon (screenshot)

and I CAN see the files in a terminal:

```
daz@daz-desktop:~$ ls -l /usr/share/app-install/icons/|more
total 9776
-rw-r--r-- 1 root root   3949 2007-10-06 11:50 abiword.png
-rw-r--r-- 1 root root    642 2007-10-06 14:30 abuse.png
-rw-r--r-- 1 root root   3602 2007-10-06 12:30 accerciser.png
-rw-r--r-- 1 root root   5702 2007-10-06 14:30 achilles.svg
-rw-r--r-- 1 root root   4061 2007-10-06 13:24 acidrip.png
-rw-r--r-- 1 root root   6820 2007-10-06 14:18 adept_manager.png
-rw-r--r-- 1 root root   2319 2007-10-06 14:31 agave-icon.png
-rw-r--r-- 1 root root    878 2007-10-06 14:30 agistudio.xpm
-rw-r--r-- 1 root root   7961 2007-10-06 14:30 airstrike.xpm
-rw-r--r-- 1 root root   2861 2007-10-06 14:22 akregator.png
-rw-r--r-- 1 root root   1036 2007-10-06 11:50 alacarte.png
-rw-r--r-- 1 root root   1488 2007-10-06 14:30 alc.xpm
-rw-r--r-- 1 root root   5762 2007-10-06 15:00 alien-arena.xpm
-rw-r--r-- 1 root root   5215 2007-10-06 14:31 alltray.png
-rw-r--r-- 1 root root   4018 2007-10-06 14:17 amarok.png
-rw-r--r-- 1 root root   6267 2007-10-06 12:28 amaya-9.54.png
-rw-r--r-- 1 root root   4595 2007-10-06 14:22 amor.png
-rw-r--r-- 1 root root   7160 2007-10-06 14:30 amulegui.xpm
-rw-r--r-- 1 root root   7861 2007-10-06 14:30 amule.xpm
-rw-r--r-- 1 root root   6702 2007-10-06 14:30 anjuta.xpm
-rw-r--r-- 1 root root   5160 2007-10-06 14:31 anymeal.png
-rw-r--r-- 1 root root   3793 2007-10-06 12:30 aptoncd.png
-rw-r--r-- 1 root root   5435 2007-10-06 14:31 aqualung.xpm
-rw-r--r-- 1 root root   3778 2007-10-06 14:22 ark.png
-rw-r--r-- 1 root root   4274 2007-10-06 14:30 arson.png
-rw-r--r-- 1 root root   2758 2007-10-06 14:22 artsbuilder.xpm
-rw-r--r-- 1 root root   2642 2007-10-06 14:22 artscontrol.png
-rw-r--r-- 1 root root   2827 2007-10-06 14:31 assogiate.png
-rw-r--r-- 1 root root   4649 2007-10-06 14:21 atlantikdesigner.xpm
-rw-r--r-- 1 root root   3791 2007-10-06 14:21 atlantik.png
-rw-r--r-- 1 root root   4295 2007-10-06 11:50 atomix-icon.png
-rw-r--r-- 1 root root   1373 2007-10-06 14:31 audacious.png
-rw-r--r-- 1 root root  10776 2007-10-06 14:30 audacity.xpm
-rw-r--r-- 1 root root   7601 2007-10-06 14:31 audio-x-generic.xpm
-rw-r--r-- 1 root root   1200 2007-10-06 12:30 authtool.png
-rw-r--r-- 1 root root    527 2007-10-06 14:55 aven.png
-rw-r--r-- 1 root root  11486 2007-10-06 14:31 avida.xpm
-rw-r--r-- 1 root root   4891 2007-10-06 15:00 avidemux.png
-rw-r--r-- 1 root root  16722 2007-10-06 12:30 Azureus.png
-rw-r--r-- 1 root root   1311 2007-10-06 14:32 balder2d.xpm
-rw-r--r-- 1 root root   7041 2007-10-06 14:20 baobab.xpm
-rw-r--r-- 1 root root   4519 2007-10-06 14:32 barrage.xpm
-rw-r--r-- 1 root root    825 2007-10-06 14:32 basket.png
..etc..
```

?? what gives ??

---

### Post by keratos on 2008-03-04
..and yet I can see them in a "normal" file browser (screenshot)

---

### Post by keratos on 2008-03-05
Has that stumped you my friend?

Anyone else have any clues please?

Its certinaly no showstopper - but help would be appreciated.

---

### Post by erginemr on 2008-03-05
> **keratos said:**
> Has that stumped you my friend?

Anyone else have any clues please?

Its certinaly no showstopper - but help would be appreciated.

Sure it did, pal. :confused: and ](*,)

I will try to look for it on the net though...

---

### Post by erginemr on 2008-03-05
Following this example:
[http://ubuntuforums.org/showthread.php?t=68473](http://ubuntuforums.org/showthread.php?t=68473)

and until someone comes up with a solution, I have a nice trick / workaround for you to try. In the respective order of the attached screenshots:

1- Make sure that the picture preview is active from Nautilus settings.

2- Open a folder which contains icons. For a better view of all icons, you may reduce the zoom level from the toolbar above. And to reach your icon folder(s) faster, you may drag the icon folder(s) to the places side bar to create a shortcut.

3- Right-click on an icon on the desktop and select "properties".

4- Now drag the icon you deem appropriate just onto the box where the generic icon for the file is shown.

5- Kudos! Your file has a brand-new icon.

In fact, this workaround is even faster than the normal way of selecting icons and I am planning to use it 24/7. This trick will also work for any application launchers on the Gnome panels. I hope it will work for you, too.

---

### Post by keratos on 2008-03-05
Hi

Thanks ever so much for the help.

I did what you suggest and it works.

Strange!!

Clearly a bug in the desktop.

I also changed the settings (screenshot) in file manager (or whatever the app is called). Not sure it is Nautilus?? Think its called Thunar. When I changed the settings (screenshot) from "Local" to "Always" then that seemed to work, as now the icons are accessible just by clicking on the icon button - as it should be. I think this is a bug but wouldnt have found it without your help.

Massive thanks and cheers for all your hard net scouring.

:-)

---

### Post by erginemr on 2008-03-05
Wonderful! You are welcome. I am also glad that you have successfully overcome this nuisance. :D

Take care yourself. :popcorn:

As a quick reminder:
**To close a thread **-> Select **"mark this thread as solved"** from the thread tools menu. 
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by keratos on 2008-03-05
ThreadTools->Mark as Solved.

Done.

(wondered how you marked as solved)

thanks again and you take care also :-)

---

