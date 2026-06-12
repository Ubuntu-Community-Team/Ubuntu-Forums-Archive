---
title: "Filenames Disappearing"
date: 2006-06-20
forum: Desktop Environments
---

### Post by Admiral Valdemar on 2006-06-20
I've noticed that since the infamous recent update, my files in Gnome aren't showing up right. Unless I zoom out so the icons are tiny (about 25% or so), they won't show the filenames underneath a folder or thumbnail image. The same happens in gThumb, but not in Konqueror, so it has to be a Gnome bug. The files essentially stop having their names being correctly displayed around a quarter of a way down the directory and then names distort into folder or file images and just disappear.

Anyone else noticed this bug? Is it GDM or something to do with the new FGLRX driver for instance?

---

### Post by Admiral Valdemar on 2006-06-20
*Bump*

---

### Post by Admiral Valdemar on 2006-06-21
Someone has to know something about this. Having files view corrupted isn't exactly a good way to run a system if you want to know what you're viewing.

---

### Post by Admiral Valdemar on 2006-06-23
So nothing then? Well this upgrade to Dapper was a big damn mistake. I'll be holding back next time until all the bugs are worked out, because I've had nothing but crap since upgrading here from printing to display artufacts.

---

### Post by ifokkema on 2006-06-23
[QUOTE=Admiral Valdemar]Someone has to know something about this. Having files view corrupted isn't exactly a good way to run a system if you want to know what you're viewing.[/QUOTE]
I'm not sure if I understand correctly. Could you post a screenshot please?

---

### Post by Admiral Valdemar on 2006-06-23
Thank you! At least one person has noticed.

[IMG]http://img.photobucket.com/albums/v88/Admiral_Valdemar/Screenshot-4.png[/IMG]

That's what I get with Nautilus when browsing the Music folder I have, it's a small image, but you can clearly see the filenames distort halfway and then disappear altogether. The same result comes about when using gThumb on My Pictures. This only started occurring when Dapper was installed.

---

### Post by keith whitehouse on 2006-06-23
hi admiral veldemar,

it is not that only one person has noticed, it is more likely to be that only one person has  replied.

I am runner Dapper Drake, which is fully updated and I do NOT have your problem.

best regards keith

---

### Post by Admiral Valdemar on 2006-06-23
I'm pretty sure it's down to either me being the only one to have this problem (doubtful), or there simply isn't a solution yet. I have no idea why this has started happening now, but I'm going to try installing Xgl and seeing if that can maybe sort it out. I've been meaning to get Compiz running now anyway, so I have a better reason than not just for the eye candy. I can only assume this is GNOME, since KDE shows no problems when I use Konqueror.

---

### Post by ifokkema on 2006-06-23
[QUOTE=Admiral Valdemar]That's what I get with Nautilus when browsing the Music folder I have, it's a small image, but you can clearly see the filenames distort halfway and then disappear altogether. The same result comes about when using gThumb on My Pictures. This only started occurring when Dapper was installed.[/QUOTE]
I can see how this bugs you. This really is irritating. Did you try messing with the Gnome themes or fonts, while you have that folder open, to see if that changes anything?

---

### Post by Admiral Valdemar on 2006-06-23
[QUOTE=ifokkema]I can see how this bugs you. This really is irritating. Did you try messing with the Gnome themes or fonts, while you have that folder open, to see if that changes anything?[/QUOTE]

The only way lessen the problem is to zoom right out in file manager, but that makes icons tiny and squashes the filenames and makes it generally annoying to look at. There's nothing I can do to really change this in gThumb.

---

### Post by ifokkema on 2006-06-23
Just to confirm - you have tried picking a different font as the 'application font' in the Gnome font preferences?

---

### Post by Admiral Valdemar on 2006-06-23
Yes, though I'll try again later when I have time to see if it's different on a selection of different fonts.

---

### Post by ohgod on 2006-06-23
Did you upgrade from a previous version of Ubuntu, or is this a clean install?  If you did an upgrade, could you try doing a clean install instead?

---

### Post by Admiral Valdemar on 2006-06-23
It's an upgrade. I'm not too keen on the idea of a total clean install when I've spent months getting this system as I want it. I shouldn't *have* to do a Windows procedure when it's evident this is something that got messed about in an upgrade. It's not like I'm alone in the whole Dapper problems thing.

---

### Post by dpm on 2006-06-23
You need to give more information so people can help you:

1. Does this only happen on your Music folder? Are the filenames in other folders ok?

2. Is there anything particular about the Music folder? What type of partition is it mounted on (ext2/3, vfat, ntfs,...)?

3. If you open a terminal, cd to the Music folder and type 'ls' are the filenames displayed correctly?

4. Are you using the default GNOME fonts? Have you installed the msttcore package by any chance?

5. Posting a bigger screnshot of only Nautilus would help. What are the file names that are not shown like? Do they contain any special characters? How long are they?

---

### Post by Admiral Valdemar on 2006-06-25
1. It happens on any folder with enough contents such as My Music and My Pictures which have numerous files.

2. All partitions are Ext3 and working optimally.

3. All filenames are displayed correctly.

4. Default GNOME fonts are used (Sans, 12 point) though the MS font package from Automatix was installed in Breezy.

5. [[IMG]http://img324.imageshack.us/img324/9061/screenshot55yg.th.png[/IMG]](http://img324.imageshack.us/my.php?image=screenshot55yg.png)

---

### Post by ifokkema on 2006-06-25
[QUOTE=Admiral Valdemar]1. It happens on any folder with enough contents such as My Music and My Pictures which have numerous files.

2. All partitions are Ext3 and working optimally.

3. All filenames are displayed correctly.

4. Default GNOME fonts are used (Sans, 12 point) though the MS font package from Automatix was installed in Breezy.

5. [[IMG]http://img324.imageshack.us/img324/9061/screenshot55yg.th.png[/IMG]](http://img324.imageshack.us/my.php?image=screenshot55yg.png)[/QUOTE]


Interesting... You're in genetics? :)

This screenshot is slightly different than the first in that this time, the file names are put right on top of the file previews on one row. After that, they're gone. Not a suggestion for a fix, but merely interested: what happens when you highlight one of the files with a 'lost' file name, and press F2? What's different when doing this for a file with the name right on top of the icon, and a file with it's name is the correct position?

Also, does this only happen in folders with files with long names, or specific types of files?

---

### Post by dpm on 2006-06-25
Hmmm...

Weird, but I've got a feeling this may have something to do with the gnome-thumbnailer generating the thumbnails. Have you tried deleting the ~/.thumbnails folder?

Another question: are the file names correctly displayed when you choose "View as List" instead of "View as Icons" in Nautilus?

---

### Post by Admiral Valdemar on 2006-06-26
[QUOTE=desp]Hmmm...

Weird, but I've got a feeling this may have something to do with the gnome-thumbnailer generating the thumbnails. Have you tried deleting the ~/.thumbnails folder?

Another question: are the file names correctly displayed when you choose "View as List" instead of "View as Icons" in Nautilus?[/QUOTE]

It must be that, because as soon as I tried listing all the contents in My Music via terminal, the folder showed up fine in Nautilus. I'll try the deleting the thumbnails file and see if that works.

[QUOTE=ifokkema]Interesting... You're in genetics? :)[/quote]

Was part of my studies, though I confess to being more a microbiology guy nowadays (genetics is damn hard when you get into it).

> This screenshot is slightly different than the first in that this time, the file names are put right on top of the file previews on one row. After that, they're gone. Not a suggestion for a fix, but merely interested: what happens when you highlight one of the files with a 'lost' file name, and press F2? What's different when doing this for a file with the name right on top of the icon, and a file with it's name is the correct position?

Also, does this only happen in folders with files with long names, or specific types of files?

It should be the same in the other image, but it wasn't as clear. The filenames just merge into the icons of the row above usually around a third way through the directory, then vanish and there's also dodgy rendering of the icons after that. So far, this has only happened in directories with many files, but I think the thumbnail preview file just got borked during the upgrade to Dapper, so that should be all that needs sorting.

---

### Post by ifokkema on 2006-06-26
[QUOTE=Admiral Valdemar]It must be that, because as soon as I tried listing all the contents in My Music via terminal, the folder showed up fine in Nautilus. I'll try the deleting the thumbnails file and see if that works.[/QUOTE]
I believe that emptying the ~/.thumbnails folder just forces nautilus into generating new thumbnails for the files. Anyway, if that doesn't work, and when you log in through a newly generated user it suddenly does work, we've established it's something in your home dir messing it up.

[QUOTE=Admiral Valdemar]Was part of my studies, though I confess to being more a microbiology guy nowadays (genetics is damn hard when you get into it).[/QUOTE]
Man, I got really annoyed during my studies by all the specific lab work that comes with microbiology. And that smell in the large 37 degree rooms... LOL
I guess you can get really used to that :)

---

### Post by Admiral Valdemar on 2006-06-26
[QUOTE=ifokkema]I believe that emptying the ~/.thumbnails folder just forces nautilus into generating new thumbnails for the files. Anyway, if that doesn't work, and when you log in through a newly generated user it suddenly does work, we've established it's something in your home dir messing it up.
[/quote]

Seems the problem persists. Now I'm stumped.

> Man, I got really annoyed during my studies by all the specific lab work that comes with microbiology. And that smell in the large 37 degree rooms... LOL
I guess you can get really used to that :)

Ah, the smell of a good day's work growing your perfect bioweapon... I mean, uh...

---

### Post by ifokkema on 2006-06-26
[QUOTE=Admiral Valdemar]Seems the problem persists. Now I'm stumped.[/QUOTE]
If even a new user, with a fresh home directory, has these problems, it's most likely a bug in an app. I assume you're up to date, but what versions are you running for packages like nautilus, gthumb, libpango1.0-0 (pango handles text flow in GTK, I believe)?

[QUOTE=Admiral Valdemar]Ah, the smell of a good day's work growing your perfect bioweapon... I mean, uh...[/QUOTE]
:twisted: LOL :twisted:

---

### Post by dpm on 2006-06-26
Hmmm, what about switching temporarily to the default Human theme, or Crux, for example? Does your problem also happen with those themes?

Otherwise if this also fails, I'd just look/ask at the usual places:

[https://launchpad.net/distros/ubuntu/+source/nautilus/+bugs](https://launchpad.net/distros/ubuntu/+source/nautilus/+bugs)
[http://mail.gnome.org/archives/nautilus-list/]("http://mail.gnome.org/archives/nautilus-list/")
[http://bugzilla.gnome.org/browse.cgi?product=nautilus]("http://bugzilla.gnome.org/browse.cgi?product=nautilus")
The #nautilus IRC channel at irc.gimp.org

Cheers.

---

