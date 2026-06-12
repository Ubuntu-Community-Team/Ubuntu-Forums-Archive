---
title: "List view shuts down nautilus"
date: 2009-12-11
forum: Desktop Environments
---

### Post by chaitanya.andhare on 2009-12-11
Hi all, I use Ubuntu 9.10 64-bit. Whenever I change the view in nautilus to list view, nautilus shuts down and I'm unable to open that folder again. I can open any other folder (as long as I don't change its view to list view). This happened to my home folder so I'm forced to open all my folders (inside home folder) via bookmarks. :(
My nautilus version is 1:2.28.1-0ubuntu3 but nautilus-data is 1:2.28-1-0ubuntu2 and it fails to upgrade to the 0ubuntu3 version citing this error:

E: /var/cache/apt/archives/nautilus-data_1%3a2.28.1-0ubuntu3_all.deb: subprocess new post-removal script returned error exit status 1

Please help.

---

### Post by madverb on 2009-12-11
Run nautilus from a terminal and paste output on failure.

---

### Post by chaitanya.andhare on 2009-12-11
Nautilus fails to start from terminal (for any folder)

This is what I got for my home folder:

chaitanya@Castle:~$ nautilus

(nautilus:16520): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed

** (nautilus:16520): WARNING **: No marshaller for signature of signal 'UploadFinished'

** (nautilus:16520): WARNING **: No marshaller for signature of signal 'DownloadFinished'

** (nautilus:16520): WARNING **: No marshaller for signature of signal 'ShareCreateError'
Initializing nautilus-gdu extension
**
Eel:ERROR:eel-preferences.c:687:update_auto_string_array: assertion failed: (callback_data != NULL)
Aborted
chaitanya@Castle:~$

---

### Post by chaitanya.andhare on 2009-12-11
Help, anyone?

---

### Post by The Bright Side on 2009-12-11
Hey it seems like Nautilus has gotten quite buggy in the latest kernel. I don't have the same problem as you, but mine is very similar:

Since I updated to the latest Karmic 64-bit kernel yesterday (2.6.31-16-generic), Nautilus freezes whenever I open a folder in my (vast) CD collection. It seems like there's too much stuff in that CD collection folder for Nautilus to handle. Strangely enough, it had no problem handling it before I upgraded the kernel, and it also has no trouble handling it when I switch to any other view or make the side pane disappear altogether.

The folder that holds digital copies of all my CDs currently has 587 subfolders. When the Folders sidebar is set to Tree view and I enter any of these 587 subfolders, the parent folder's contents (i.e. the 587 subfolders) start to expand in the tree view, and Nautilus freezes.

Now here's the thing: I thought perhaps it was indexing stuff or something, so I let it run for like an hour, and lo and behold, it was fine when I came back. However, the next time I tried, the same thing happened again.

And the killer: when I press F9 to make the Folder pane disappear, THEN enter one of the subfolders, and THEN bring the pane back by pressing F9 again, everything is expanded and fine within the blink of an eye!

Does anybody else have this issue? It didn't happen with the last kernel, so I would guess it's a bug, but perhaps you can think of some things to try here. Also, how do I file a bug report with the devs? I'm kind of new-ish to Ubuntu.

I took a screenshot... It's in this thread, which I originally opened for the problem:

[http://ubuntuforums.org/showthread.php?t=1352073](http://ubuntuforums.org/showthread.php?t=1352073)

---

### Post by The Bright Side on 2009-12-11
Hey, did you try sudo or gksudo for Nautilus? Probably won't do anything, but who knows.

---

### Post by The Bright Side on 2009-12-11
You could also reinstall Nautilus (possible from Synaptic? I don't have Ubuntu here, am at work right now) or use Konqueror.

---

### Post by chaitanya.andhare on 2009-12-11
Reinstalling nautilus from synaptic didn't help, but sudo nautilus doesn't have that problem so thanks for the tip :)
Does anyone know how to fix the list view problem?

---

