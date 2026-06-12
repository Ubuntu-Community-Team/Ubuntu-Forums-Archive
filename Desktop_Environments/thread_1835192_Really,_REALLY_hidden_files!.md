---
title: "Really, REALLY hidden files!"
date: 2011-08-28
forum: Desktop Environments
---

### Post by llanitedave on 2011-08-28
I'm developing an application that will rely on data files that are created from within it.  In order to ensure that there won't be any confusion with other file types, I give my data files the extension ".evo", because that one doesn't seem to be used anywhere else.  There's nothing fancy about them, they're essentially just sqlite3 files with a particular table setup.

However, when I open the folder that contains those files from inside the classic Gnome desktop, those files are invisible!  I also cannot see them from the file dialogs in Firefox or Libre Office.

I CAN see them from the terminal, I can see them in Dolphin, and I can see them from the file dialog in my own application, as well as a couple of other apps that I've tried.  

I'm assuming there's some kind of preferences setting that limits the file types or extensions that a particular application can detect.  However, I don't know where to look for it.

Can somebody give a clueless guy a clue?

Thanks!

---

### Post by papibe on 2011-08-28
The standard in Linux is to hidden files based in its names. Files that start with a dot (.) will be hidden (or not shown by default) to most applications.

Do your filenames start with a dot? If not, could you post how you see them in the terminal?

BTW, if you press Ctrl+H, you can 'see' the hidden files on the Nautilus (file browser).

Hope it helps,
Regards.

---

### Post by llanitedave on 2011-08-29
No, the filenames take the form "testdb1.evo", so there's not a period preceding anything.  Interestingly, once I logged out of "Classic" mode and into Unity, the files became visible, temporarily, but with the next login they seem to have toggled into invisibility again -- but never do show up on the Firefox or Libre Office dialogs.  Maybe the act of logging out and in cleared something up?

Here's the appearance in Dolphin -- a portion of a screenshot with the two icons at the bottom representing the "*.evo" files.


eta:  CTRL + H has no effect on these files in Nautilus.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=201021&d=1314590708[/IMG]

---

### Post by papibe on 2011-08-29
Could you show them on the terminal?
```
$ ls -l
```

---

### Post by llanitedave on 2011-08-29
> **papibe said:**
> Could you show them on the terminal?
```
$ ls -l
```

Ah, I think I see what you're getting at now.  Here it is.  I still don't see anything that would hide the files.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=201024&d=1314596951[/IMG]

---

### Post by papibe on 2011-08-29
Interesting... Are those files on a NTFS partition?

Regards.

---

### Post by Anirab on 2011-08-29
havnt tried this but is it possible to boot up from a live cd and explore the HD while in live mode .hope thats a help .

---

### Post by fdrake on 2011-08-29
can you post the ls -l of the folder containing those files:
eg
```
ls -l /home/dave/Desktop/folder
```

---

### Post by llanitedave on 2011-08-29
> **papibe said:**
> Interesting... Are those files on a NTFS partition?

Regards.

No, it's ext4.

As of this morning, all the files are visible again on Nautilus, or whatever the Unity file browser is.  Weird.

---

### Post by matchett808 on 2011-08-29
You mentioned something about icons have you tried to make a custom icon or something?? this sounds (although I am guessing) that this is specifically something nautilus related - It almost sounds like because nautilus doesn't know what they are or theres an incorrect setting in terms of the thumbnail - maybe its that nautilus is simply skipping these files because it doesn't know what to do??

Its just a bit of a guess because from what you posted (the terminal output) the other users are right, there is no reason for it not to show up!

One thing I would try is maybe bunging it all on a usb stick and running it on another machine??? see what happens?

Also I would try renaming one to be extension-less ie. "testdata1" instead of "testdata1.evo" see if that has an effect?

---

### Post by llanitedave on 2011-08-29
> **fdrake said:**
> can you post the ls -l of the folder containing those files:
eg
```
ls -l /home/dave/Desktop/folder
```

The directory permissions are drwxrwxrwx. 
I'm not sure what else is on there that could be helpful, just a group of *.py, *.pyc, and *.png files -- all of which have never given me this trouble.

---

### Post by llanitedave on 2011-08-29
> **matchett808 said:**
> You mentioned something about icons have you tried to make a custom icon or something?? this sounds (although I am guessing) that this is specifically something nautilus related - It almost sounds like because nautilus doesn't know what they are or theres an incorrect setting in terms of the thumbnail - maybe its that nautilus is simply skipping these files because it doesn't know what to do??

Its just a bit of a guess because from what you posted (the terminal output) the other users are right, there is no reason for it not to show up!

One thing I would try is maybe bunging it all on a usb stick and running it on another machine??? see what happens?

Also I would try renaming one to be extension-less ie. "testdata1" instead of "testdata1.evo" see if that has an effect?

I've only made one custom icon, for the rest just copied some generic *.png icons from the Gnome collection and renamed the copies.  Those haven't given me any trouble.  As I said, the *.evo files are visible on Nautilus as of this morning, but still invisible on the Firefox/Libre Office dialogs.

I suppose that's not really a problem operationally -- They DO show up on my own app's dialog, and the appear on my two sqlite database management apps -- Sqliteman and SQLite Database Browser, which are the main things that can read them anyway.  They also are visible on Kate's and Geany's dialogs, but again, a mere text editor can't read them anyway.

At this point, it's just more of a "hhhhmmmmm" issue, but one that I'm hoping doesn't have troubling implications down the road.

---

### Post by matchett808 on 2011-08-29
In those dialogues are you searching for all file types?

---

### Post by llanitedave on 2011-08-29
> **matchett808 said:**
> In those dialogues are you searching for all file types?

Good question, but yes!    [IMG]http://t2.gstatic.com/images?q=tbn:ANd9GcRx08HzzBvQQyNsJbC_OtSpGCx3ykgrH7gcIXzi_uuCrh2hoOxsVg[/IMG]

---

### Post by Slim Odds on 2011-08-29
I'm not sure what you're finding so surprising. Linux files systems (ext2/3/4) do not have a "hidden" attribute like some others.

Applications like LibreOffice typically (as the default) show only their OWN document file types.

What most applications do if the want to hid files is to create a directory with a . (period) as the first character and then put all their files in there.

---

