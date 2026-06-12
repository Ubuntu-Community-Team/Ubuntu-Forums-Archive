---
title: "Desktop and Konqueror do not update directory contents"
date: 2006-06-10
forum: Desktop Environments
---

### Post by gspr on 2006-06-10
Hi.

I've recently moved from Gentoo to Kubuntu Dapper, and so far I very much like what I see.

I'm experiencing only one problem, which seems to be related to the file alternation monitor. I haven't actually installed FAM, as it suggested removing half my system, so I've just stuck with Gamin, Ubuntu's default file alternation monitor.
Here's my problem, though: If I open a directory in Konqueror, and then use a terminal to create or remove a file in it, I have to explicitly refresh Konqueror for it to take notice of this. On my Gentoo system, Konqueror would be aware about a second after the alternation had happened.
A worse problem than that of Konqueror, is that of my (KDE) desktop. If I create a file in ~/Desktop, it doesn't show up even after I've hit refresh desktop. I have to create another file on my desktop using KDE for the other file to show up.

Has anybody experienced this before? I'm sure it's easily fixed, but things like this could really disappoint people coming to (K)ubuntu for the first time.

Thanks.

---

### Post by mark_g on 2006-06-10
Yes, I have also had this a couple of times. I think it's a bug, so hopefully it'll be fixed in the next release.

---

### Post by gspr on 2006-06-10
Hmm... this sure isn't good!

---

### Post by GeneralZod on 2006-06-10
Please post *and* vote here :)

[https://bugs.kde.org/show_bug.cgi?id=106394](https://bugs.kde.org/show_bug.cgi?id=106394)

If you're comfortable with re-compiling and installing kdelibs, you might want to try applying the patch I created (it's mentioned in the bug report) - I haven't tried it on KDE3.5.x, yet.

gamin isn't at fault, here, and is really better in practically every way than famd.

---

### Post by chavo on 2006-06-10
Hmm, works for me. I'm on a clean dapper install now. I do have another partition with an install that was updated from breezy and I do remember this breaking at time to time throughout the daily dapper upgrades I did.

---

### Post by GeneralZod on 2006-06-11
[QUOTE=chavo]Hmm, works for me. I'm on a clean dapper install now. I do have another partition with an install that was updated from breezy and I do remember this breaking at time to time throughout the daily dapper upgrades I did.[/QUOTE]

Adding and deleting files works for me, too, but any other operation that would change the file size or modification time of a file does not.  Can you try a quick experiment - start downloading a large file (via wget, firefox, konqueror - whatever :)) and open a separate konqueror file manager instance to the target directory.  On my machine, the file is registered in konqueror as being created, but its size and modification time are never updated so it will say the file size is 760k (or whatever) even when it really should be 100's of MB or so.  What should happen is an update to the file size every second or so throughout the duration of the download.  Thanks!

---

### Post by gspr on 2006-06-11
I restarted KDE, and now files that are created/removed are updated, but the thing that GeneralZod describes is still happening. At least the current situation is livable.

---

### Post by gspr on 2006-06-12
That's weird. The problem returned. Very very odd. I hope the KDE people fix this soon, and I especially hope Ubuntu applies the update. Having a desktop like this is unbearable.

---

### Post by GeneralZod on 2006-06-12
[QUOTE=gspr]That's weird. The problem returned. Very very odd. I hope the KDE people fix this soon, and I especially hope Ubuntu applies the update. Having a desktop like this is unbearable.[/QUOTE]

The more people who post/ vote in the bug report, the more likely it is to get fixed - you know what to do! :)

---

### Post by gspr on 2006-06-14
OK. Commented on bug 36581.

---

### Post by msak007 on 2006-06-21
I'm not sure when this started happening to me (probably after the 3.5.3 upgrade), but I'm having the same problem. If I download a file to my Desktop, it doesn't show up unless I create a file / directory first. Also, another weird problem I've been having is deleting some files / folders. When I download and compile something from source, when I'm done with it and try to delete the original source file or folder I get an error that permission is denied (even though it's MY Desktop). Even though I get the error, the folder / file "disappears" - I can no longer see it if I look for it using a terminal and double-clicking it gives me an error that the file no longer exists. But the weird part is that there's still an icon on my Desktop for that file / folder, and now it has a padlock symbol on it! This also won't go away unless I create a file / folder.

---

### Post by brandon-san on 2006-06-29
I am also having this issue and as a web developer it is pretty annoying.  If I create a new file in kate, it will not even show up until I refresh in konqueror.  More annoying is when I download something from my browser direct to the desktop and it does not show up until I refresh.

It was not doing it when I started with dapper, it all the sudden started last week.

---

### Post by Pekkalainen on 2006-07-02
Confirmed here too :(

---

### Post by Bigglez on 2006-08-16
Done and voted too. Please fix this, it's nasty.

Funny thing is Windows does this all the time in Explorer. It will simply stop reflecting new or removed icons. I always felt so superior on my Fedora KDE (which, ironically, has this same desktop bug).
Then I came to Kubuntu ...

;(

---

