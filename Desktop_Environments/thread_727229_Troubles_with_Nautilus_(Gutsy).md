---
title: "Troubles with Nautilus (Gutsy)"
date: 2008-03-17
forum: Desktop Environments
---

### Post by Ghost|BTFH on 2008-03-17
Okay, anyone who can help with this Nautilus problem: 

I can't click on anything on my desktop, nor right click the desktop for a menu. I can open Nautilus (75% of the time) and I can go from one folder to another, but if the folder contains anything OTHER than more folders, it locks up tight and I have to kill it. 

Any suggestions on where to start to fix this? 

I have attempted: removing nautilus and reinstalling it, removing ~/.nautilus and even ~/.gnome2 to no avail. Creating a new user account gives the same issue in the new account. I'm running Gutsy with all current updates.

---

### Post by WarMonkey on 2008-03-17
Try purging/reinstalling the ubuntu-desktop package

```

sudo aptitude purge ubuntu-desktop
sudo aptitude install ubuntu-desktop

```

---

### Post by Ghost|BTFH on 2008-03-17
I've tried purging nautilus, but oddly, I didn't try purging the desktop...I will do so and see if I have the same issue and will post back.

---

### Post by Ghost|BTFH on 2008-03-17
Interesting update. After getting curious and running several attempts at browsing my file structure with nautilus...I have found an odd thing:

The lockup only occurs in a folder that has an .mp3 file in it.

I can go into my documents (multi levels of folders) and click on, and interact with my files.

I can go into my pictures, or video, same thing.

Only when I go into folders containing .mp3s (which, ironically, my desktop happens to have as well) does the lockup occur.

Ideas?

---

### Post by WarMonkey on 2008-03-17
Hmm, that's odd, I have tons of mp3 files in my folders but I have no problems. When did this start happening: was it right after you installed Ubuntu, or is it a recent thing?

Is the mime type "audio/mpeg" (check by rightclick then properties).

---

### Post by Ghost|BTFH on 2008-03-17
Semi-solution has been found.

It appears to be an issue with the audio preview. Turning that off in Nautilus allows me to go everywhere with it, with zero lockups.

Now the only question is, how to fix the previews. :)

---

### Post by WarMonkey on 2008-03-17
Check 
[http://ubuntuforums.org/showthread.php?p=4383973](http://ubuntuforums.org/showthread.php?p=4383973)

and

[http://ubuntuforums.org/showthread.php?t=598231](http://ubuntuforums.org/showthread.php?t=598231)

---

