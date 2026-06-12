---
title: "aMule Incoming directory?"
date: 2006-08-21
forum: Desktop Environments
---

### Post by mengfei on 2006-08-21
Hi there!

I'm using aMule, and by its default settings.

And I downloaded one pdf file, but I cannot seem to find it.

The preferences tell me the Incoming directory should be in a folder called ".amule" in the home directory.

However, I see no such folder, and also, doing a file search for the file doesn't get me anything either.

How do I get to it?!!

Sincerely yours,
Mengfei

---

### Post by mengfei on 2006-08-21
Gagh.

I changed in the preferences the ".aMule" folder to just "aMule"

and now whenever I try to run aMule, it gives me: "Bad permissions on Temp directory"

---

### Post by zhopudey on 2006-08-29
Hey! I got the same error! Someone please help me.


Edit: Ok, got it :D   Edited the amule.conf file. Its in the home folder, ".amule" dir. ( its hidden). Set the dirs back to default. Everythings working now :D

Though the question remains. Why can't I set my own dirs?

---

### Post by buddah3618 on 2007-07-23
Re: changing amule download folder
The .amule directory is hidden. Hit Ctrl+h to unhide it. You can change it from Preferences>Directories

You can easily unhide it permanently by renaming .amule to amule in both amule and your home folder. The files you download can be seen it amule's window.

You can also just change the download directory to something like /home/amuledownloads to make everything visible in your home directory.


Here you guys. I found these entries that should help you out. I had a similar issue, this resolved it for me. Just a little WARNING !! If you choose to rename the directories you will be required to restart aMule. When you do that, any & all downloads that are listed will be cleared from the list. You will have to re-search them & start downloading them again.

buddah3618 :)

---

