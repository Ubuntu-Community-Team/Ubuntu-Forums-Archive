---
title: "Change folder icon of symbolic link"
date: 2009-10-30
forum: Desktop Environments
---

### Post by davexunit on 2009-10-30
I would like to know how I can change the icon of a symbolic link. I have changed my music folder into a symbolic link that points to music on another hard drive. The problem is, I want to use the music folder icon with the little music note on it. When I try to set it to that in properties, nothing happens. It just keeps the default. Is there anyway to change this? Thanks in advance.

---

### Post by Pabster on 2009-11-01
Hi there,

I've been struggling with the same problem as yours since I first installed Karmic Koala several days ago!  I found your post while looking for an answer myself.  I thought this might be a Karmic 9.10 or nautilus bug since I have had several symbolic links to folders with custom icons on my desktop since Feisty without any problem.  However, it's possible I did some hack a long time ago that I have since forgotten that carried over when upgrading from Feisty-Gutsy-Hardy-Intrepid-Jaunty.  This Karmic install is my first clean build in all that time due to moving to 64 bit so maybe it has always been this way, I don't know.  Anyway, it's annoying.  When I copied over my old Desktop files, to my surprise the symbolic links to folders didn't bring over their icons and any attempt to set them manually was ignored with no error message!

I just figured out a way to achieve the same end result that will probably help you as well.  Try this.  Delete the symbolic link to your music folder that you already have and follow these steps to create a desktop launcher with an icon.  At the end of the day, it will be the same end result:

1. Right-Click on an open space on the desktop
2. Click Create Launcher
3. Change the Type to "Location"
4. Set the Name to whatever you like
5. Type the full path to your folder in the Location field i.e. /home/myname/myfolder/whatever (Note - for some reason the Browse button doesn't seem to work properly here so type it in manually)
6. Enter a comment if you like or leave it blank
7. Click the square "Spring" icon in the upper left
8. Choose the icon you would like to use
9. Click OK and OK again
10. You should now have a working "shortcut" to your folder with icon
11. You can cut and paste this from your desktop to any folder in Nautilus if that's where you want to use the shortcut.

I just finished converting all of my symbolic links to folders on my desktop with the above method and now have my desktop looking like I prefer it to be.  I hope this helps you as well.  If anyone else reads this and knows of a better way to get icons back on symbolic links to folders, please let us know.

Pabster

---

### Post by iruel on 2009-11-01
> **Pabster said:**
> Hi there,

I've been struggling with the same problem as yours since I first installed Karmic Koala several days ago!  I found your post while looking for an answer myself.  I thought this might be a Karmic 9.10 or nautilus bug since I have had several symbolic links to folders with custom icons on my desktop since Feisty without any problem.  However, it's possible I did some hack a long time ago that I have since forgotten that carried over when upgrading from Feisty-Gutsy-Hardy-Intrepid-Jaunty.  This Karmic install is my first clean build in all that time due to moving to 64 bit so maybe it has always been this way, I don't know.  Anyway, it's annoying.  When I copied over my old Desktop files, to my surprise the symbolic links to folders didn't bring over their icons and any attempt to set them manually was ignored with no error message!

I just figured out a way to achieve the same end result that will probably help you as well.  Try this.  Delete the symbolic link to your music folder that you already have and follow these steps to create a desktop launcher with an icon.  At the end of the day, it will be the same end result:

1. Right-Click on an open space on the desktop
2. Click Create Launcher
3. Change the Type to "Location"
4. Set the Name to whatever you like
5. Type the full path to your folder in the Location field i.e. /home/myname/myfolder/whatever (Note - for some reason the Browse button doesn't seem to work properly here so type it in manually)
6. Enter a comment if you like or leave it blank
7. Click the square "Spring" icon in the upper left
8. Choose the icon you would like to use
9. Click OK and OK again
10. You should now have a working "shortcut" to your folder with icon
11. You can cut and paste this from your desktop to any folder in Nautilus if that's where you want to use the shortcut.

I just finished converting all of my symbolic links to folders on my desktop with the above method and now have my desktop looking like I prefer it to be.  I hope this helps you as well.  If anyone else reads this and knows of a better way to get icons back on symbolic links to folders, please let us know.

Pabster

your suggestion is good,but you can't make it as bookmark folder,;)

---

### Post by davexunit on 2009-11-01
Thank for the idea, but I need symbolic links so they can be treated as a folder by the operating system. Not having pretty icons for my symbolic links won't be a huge deal. Although I also wish I could get rid of the little arrow emblem as well so it really looks like a folder.

---

### Post by Pabster on 2009-11-01
Oh well, I'm sorry my suggestion won't solve your issue, davexunit.  It sounds like you are using these folder symlinks for more than I am -- just a quick way to open the folder in question.  I hope you do eventually find a proper fix, though.

Does anyone know if this is an actual bug that should be reported or if this is intentional behavior?  I'm also curious if it worked for other people in older releases as it did for me.

Pabster

---

### Post by Mithrandir95 on 2009-11-01
My problem was related.  Not only does it not keep customised icons, it doesn't keep the location of the icon on the desktop (after a reboot it always defaults back to top left).  And call me anal but I have "links" on top right (and they wouldn't stay there).

Pabster your solution works for me, Thanks!

Also, don't really know if this should be considered a bug, but it'd make my list for a "paper cut".

---

### Post by wayneox on 2009-11-05
symbolic links link directly to the folder in question...

ie: 

/Windows

link is at /home/user/desktop/windows-disk

you have to change the icon on the dir /Windows and it updates the "windows-disk" icon also...

- took me ten mins to find that out yesterday :D

hth :)


- addition

symbolic links [as far as i know] will always av the little arrow, but say if you put a "disk drive" image it isnt so noticeable...

I use launchers on my desktop to put my "computer, network, trash" icons... i then put sym links to /WinC [my media drive] and /WinD [my Windows install] (when i installed windows i created my large media partition first, so it messed the C: up ;) lol couldnt be arsed to fix it lol] 
- not sure if you know this - but if a partition is mounted outside of /media/ it doesnt show the "unmount" option and doesnt display in "computer://" (what i chose the path for) - i auto mount the partitions :D - not much else i can add here so once again... hope it helps

---

### Post by rpotter28 on 2009-11-05
> **Mithrandir95 said:**
> My problem was related.  Not only does it not keep customised icons, it doesn't keep the location of the icon on the desktop (after a reboot it always defaults back to top left).  And call me anal but I have "links" on top right (and they wouldn't stay there).

This is a known bug in Karmic. See post 13 at:

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/399974](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/399974)

---

### Post by iruel on 2009-11-05
it was **glibc / libglib2** not nautilus,because Desktop _not connected_ with nautilus library,

---

### Post by surfinmdq on 2009-11-29
> **Pabster said:**
> Hi there,

I've been struggling with the same problem as yours since I first installed Karmic Koala several days ago!  I found your post while looking for an answer myself.  I thought this might be a Karmic 9.10 or nautilus bug since I have had several symbolic links to folders with custom icons on my desktop since Feisty without any problem.  However, it's possible I did some hack a long time ago that I have since forgotten that carried over when upgrading from Feisty-Gutsy-Hardy-Intrepid-Jaunty.  This Karmic install is my first clean build in all that time due to moving to 64 bit so maybe it has always been this way, I don't know.  Anyway, it's annoying.  When I copied over my old Desktop files, to my surprise the symbolic links to folders didn't bring over their icons and any attempt to set them manually was ignored with no error message!

I just figured out a way to achieve the same end result that will probably help you as well.  Try this.  Delete the symbolic link to your music folder that you already have and follow these steps to create a desktop launcher with an icon.  At the end of the day, it will be the same end result:

1. Right-Click on an open space on the desktop
2. Click Create Launcher
3. Change the Type to "Location"
4. Set the Name to whatever you like
5. Type the full path to your folder in the Location field i.e. /home/myname/myfolder/whatever (Note - for some reason the Browse button doesn't seem to work properly here so type it in manually)
6. Enter a comment if you like or leave it blank
7. Click the square "Spring" icon in the upper left
8. Choose the icon you would like to use
9. Click OK and OK again
10. You should now have a working "shortcut" to your folder with icon
11. You can cut and paste this from your desktop to any folder in Nautilus if that's where you want to use the shortcut.

I just finished converting all of my symbolic links to folders on my desktop with the above method and now have my desktop looking like I prefer it to be.  I hope this helps you as well.  If anyone else reads this and knows of a better way to get icons back on symbolic links to folders, please let us know.

Pabster

Good idea.

FOR MODS CONSIDERATION:

This thread should be marked **STICKY** as it's a useful one for solving a release **bug**.

---

### Post by michael18 on 2009-12-08
me too...the same problem..=(

can explain how to change it back? after i read this post i still not understand..

ps: i juz start using LINUX from yesterday...the 1st time using LINUX...and i'm using the Ubuntu 9.10 Karmic Koala...xD

---

