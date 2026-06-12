---
title: "No .avi thumbnails"
date: 2006-07-02
forum: Desktop Environments
---

### Post by pt78 on 2006-07-02
Hallo,
Afer upgrade to Dapper nautilus (ok, I know, it's thumnailer) no longer makes thumbnails of .avi files. Anybody else having the same problem? How can I fix it? Where can I find thumnailer log or something that will help me solve this problem?

Thanks.

---

### Post by jimbob on 2006-07-02
I don't know if there is a thumbnail log as such but if you go to the file .thumbnails in yout home directory there are two subdirectories, normal and fail.

In a system where all the codecs are installed and all thumbnail file types are working there should be nothing at all in the fail subdirectory.

Unfortunately, once a thumbnail fails it remains in that directory and won't be attempted again.

The cure is to delete the directory (not to worry, the system always recreates it) and try again once you have fixed the cause of the .avi failure.

I guess I have danced around your problem without giving you a specific fix but that is all I know.  Just make sure all the codecs are installed and working.  Perhaps someone will reply with a specific fix for the .avi files.
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by pt78 on 2006-07-03
Well,
thank you for hints. I checked fail subdir (lots of entried - removed everything), no effect. Codecs should be fine, mplayer is able to play every file, which thumbnailer fails to process. I'll check what package thumbnailer comes from and reinstall it. (After upgrade from 5.10 to 6.06 i had to reinstal e.g. mplayer plugins - mplayer was not working.) 
Anyway, thanks.

---

### Post by psychicdragon on 2006-07-03
Do you have totem installed? Nautilus uses totem-video-thumbnailer to generate thumbnails for video files.

---

### Post by Denis on 2006-07-03
I noticed this problem too a few days ago. I also found the solution: 

Nautilus uses gstreamer to read the avi files (the same system used for totem - gstreamer). This means it doens't matter whether your movie player (mplayer) plays the file or not. 

You need to have the necessary plugins for gstreamer to decode mpeg, divx and others. Look for the "gstreamer" packages and install plugins-good, plugins-bad and plugins-ugly. Try to play the movie with Totem. 

If Totem can play it, delete the .thumbnails directory to rebuild all the thumbnails. 

(*you may also want to delete the older gstreamer packages from breezy (0.8.x) that are no longer used)

---

### Post by pt78 on 2006-07-04
So here is what i had to do: uninstall totem-xine, install totem-gstreamer, reinstall all gstreamer plugins and add gstreamer0.10-ffmpeg and voila - thumbailer works again for all .avi files. Thanks for suggestions!

---

