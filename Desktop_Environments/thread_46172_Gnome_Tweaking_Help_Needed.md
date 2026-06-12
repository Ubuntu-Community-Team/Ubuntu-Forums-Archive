---
title: "Gnome Tweaking Help Needed"
date: 2005-07-03
forum: Desktop Environments
---

### Post by jlacroix on 2005-07-03
Hello all, I was hoping to "fix" some very minor things in Gnome that I would like to work a bit better.

First of all, I'd like to have **Multiple Desktops with Multiple Wallpapers**.
Maybe I am just blind, but a friend at work has a different wallpaper for each of his multiple desktops, and I don't see that option anywhere. I really like it.

**Annoying *.WMV File Warning**
This very annoying warning message comes up when I try to play a WMV file by left clicking on it. It will play when I rightclick and then Open with > Totem, but I'd rather have them be clickable like the rest of the files I have. (MPG, AVI, etc, those work fine).
```
The filename "file_name.wmv" indicates that this file is of type "Microsoft WMV
video". The contents of the file indicate that the file is of type "Microsoft ASF video". 
If you open this file, the file might present a security risk to your system.

Do not open the file unless you created the file yourself, or received the file from a 
trusted source. To open the file, rename the file to the correct extension for 
"Microsoft ASF video", then open the file normally. Alternatively, use the Open With 
menu to choose a specific application for the file.
```

Alternatively, I can rename the WMV files to have an ASF extension and they will work, so I probably could rename them all, but that seems kind of odd that I would have to lie about the file type to get them to play. Something must be wrong somewhere.

**3D Desktop, And Effects**
I really would like to set up a 3D desktop like I've been seeing pictures of on the net for a while. (I have 3ddesktop set up, but that is only for the pager, I'd like to have other cool 3d effects).

Also, I've heard that Xorg now supports transparent window manager windows, is that true? If so, I would like to have that too.

**Linphoto and Lsongs**
I don't like Linspire much (I've tried it) but I really like these two programs. Is there a way to set them up in Ubuntu?

**Nautilus Video Preview/Thumbnails**
I really like how Nautilus shows a preview image of video files, however only some of them have preview files. I wonder why? Is there a way to make it show a preview icon for all videos?

**Rhythmbox Radio**
Is there a way to add some more radio stations to Rhythmbox?[/b]

I have other questions but these will do for now.

---

### Post by sethmahoney on 2005-07-03
Most of these issues are covered in HOWTOs on this forum.  Do a few searches and you should find all the info you're looking for.  I know for sure that the multiple wallpapers thing is covered, along with X.org transparency (though it only seems to work well with nVdia cards), and I think I've seen adding radio stations to Rhythmbox too.

---

### Post by jlacroix on 2005-07-03
I already searched and didn't find anything that will help me...

---

### Post by sethmahoney on 2005-07-03
That's strange.  I just did a search for "wallpaper" and it pulled up this thread: [http://ubuntuforums.org/showthread.php?t=6980&highlight=wallpaper](http://ubuntuforums.org/showthread.php?t=6980&highlight=wallpaper)
which talks about exactly what it sounds like you're looking for.  Maybe you need to try less restrictive searches?

---

### Post by jlacroix on 2005-07-03
Nope, thats not what I need. That's the hard (unofficial) way of doing it, when I used Redhat, the old Gnome releases have that option so I just need to enable it within Gnome.

---

### Post by C.B. on 2005-07-04
[QUOTE=jlacroix]**3D Desktop, And Effects**
I really would like to set up a 3D desktop like I've been seeing pictures of on the net for a while. (I have 3ddesktop set up, but that is only for the pager, I'd like to have other cool 3d effects).

Also, I've heard that Xorg now supports transparent window manager windows, is that true? If so, I would like to have that too.
[/QUOTE]

There's an excellent (i.e., works) HOWTO on "Making your windows look super sweet in Hoary (compositing)" at [http://www.ubuntuforums.org/showthread.php?t=20769&page=1&pp=10&highlight=transparent](http://www.ubuntuforums.org/showthread.php?t=20769&page=1&pp=10&highlight=transparent) . Just did it myself. Check it out.

Bogs the system down, but I'm running it on an old PII with only 90M ram . . . slow but beautiful. I think it can be tweaked a bit. And I have gDesklets going in background.

---

### Post by sethmahoney on 2005-07-05
[QUOTE=jlacroix]Nope, thats not what I need. That's the hard (unofficial) way of doing it, when I used Redhat, the old Gnome releases have that option so I just need to enable it within Gnome.[/QUOTE]

Right, the option has been disabled in the newer versions of Gnome.  That's why you need to do it the hard way now.

---

### Post by C.B. on 2005-07-05
Seth,

Just out of curiosity, do you know why it was disabled . . . too unstable for universal distribution? Seems like a pretty neat feature that lots of people want. I wonder if it will find its way back in any time soon.

---

### Post by sethmahoney on 2005-07-05
[QUOTE=C.B.]Seth,

Just out of curiosity, do you know why it was disabled . . . too unstable for universal distribution? Seems like a pretty neat feature that lots of people want. I wonder if it will find its way back in any time soon.[/QUOTE]

I don't know why for sure, but if you're really curious you could probably find out at gnome.org.  I do know, though, that several features (including the ability to edit the Applications menu) were removed in the latest Gnome and will be added to some future release.  I'm assuming that, like these other features, the multiple wallpapers feature will find its way back in in a future release (again, if you're curious gnome.org might have a plan somewhere on the site that shows just when you can expect it back - you can also probably find lists of new features that you can expect in future releases).

---

