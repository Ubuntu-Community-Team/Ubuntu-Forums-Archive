---
title: "Rename &quot;Desktop&quot; to &quot;desktop&quot;"
date: 2009-05-17
forum: General Help
---

### Post by heitjer on 2009-05-17
Hi Y'all!
I just did a fresh install of Jaunty and I played around enough to like it. Before I move my backup 'home' folder over again I like to see if I can get rid of some default folders. I saw a few weeks back a thread that showed me how to do this but I did not bookmark it and I can not find it anymore. 

Anyhow - it has to do with '**user-dirs.dirs**' but I looked at it and don't want to mess anything up in there. I like to do a few changes:

a) rename "Desktop" to "desktop"
b) create a folder "photos" in addition to "pictures" that shows up as a default and is the main one for photos, I store a bunch of clip arts that reside in "pictures'. So "photos" should be the main one that gets accessed by F-Spot etc. 
c) place the folder "templates" and "examples" out of sight, i.e. into "documents"

---

### Post by mc4man on 2009-05-17
> .......can not find it anymore.

Possibly

[http://ubuntuforums.org/showthread.php?t=1117448&highlight=user-dirs.dirs](http://ubuntuforums.org/showthread.php?t=1117448&highlight=user-dirs.dirs)

---

### Post by heitjer on 2009-05-18
Thanks - but this does not solve my problem. I tested this by renaming my folder "Video" to "video" and rebooted but still the folder was only accessible with a capital "V".

---

### Post by mc4man on 2009-05-19
Wasn't offering as a solution, only that it may be the "thread" you couldn't find.

I don't see the point of attempting to make Desktop lowercase.

As far as fspot you can set any folder you wish to be it's default.

If your specifically meaning the "Pictures" dir. that listed in the  "Places" top area, then rename it to Photos or photos or whatever you wish (right click -> rename

---

### Post by mcduck on 2009-05-19
If you really want, you could symlink the directories to new ones using the names you want, and then hide the originals using a .hidden file.

For example, Pictures into Photos:
ln -s ~/Pictures ~/Photos, then create a file called ~/.hidden, and add "Pictures" into it.

You can use .hidden file to hide any file/directory without changing it's name. Just put a file called .hidden into the directory containing stuff you wish to hide, and then add all the things to hide each on their own line. At least Nautilus will respect this setting and hide those files/directories.

---

