---
title: "[SOLVED] Loading ZSNES Windows originated save files in Gutsy"
date: 2008-01-11
forum: Gaming &amp; Leisure
---

### Post by Saghaulor on 2008-01-11
I'm starting this thread because the other thread I've been posting to is labeled solved, however, I'm still having trouble.

Here's where I'm at.

I was playing Final Fantasy III in Windows Xp on ZSNES v1.42.

I backup up my data, formated and took the plunge into Gutsy. (A happy move I might add.)

I had some trouble installing ZSNES but found working instructions on the ubuntuguide. I have an AMD64 chipset, so this was part of the problem. ([http://ubuntuguide.org/wiki/Ubuntu:Gutsy](http://ubuntuguide.org/wiki/Ubuntu:Gutsy))

I've tried to load the files by setting the path. I'm aware that UNIX based systems are case sensitive and that ZSNES is not, so I even edited the config files to point to the proper case sensitive path. 

I've tried dumping the files into ./znses folder, as well as any other location that had anything to do with ZSNES. I still cannot load the save files.

I've started a new game, saved, and then closed the program and tried to load my data, only to discover that there was no save. 

I'm lead to believe the issue is a rights issue, but I'm not sure. 

Please help me.

Thank you in advance.

-Stephen

---

### Post by acoustibop on 2008-01-11
Case sensitivity is not the only issue, Stephen.  If there are spaces in the paths, you should also enclose these paths in inverted commas ("path") or prefix the spaces in the paths in ZSNES' configuration with backslashes (\).

I've been sharing saves in this way between Windows and Ubuntu without problems, as long as paths are sorted out, so I can confirm that there's no essential reason why this won't work.  What I do now, to avoid problems, is make sure that any paths ZSNES may need to use are all lower case and without spaces.

---

### Post by Saghaulor on 2008-01-11
That would resolve loading the save files, but what are your thoughts on saving the game from a fresh load, and then the saved game is no longer present after I reload ZSNES?

The aforementioned scenario is why I suspected a rights issue.

---

### Post by acoustibop on 2008-01-11
Yes, that would be my first conclusion as well, Saghaulor.

---

### Post by Saghaulor on 2008-01-13
Do you know how to modify the rights permissions so that I can test our hypothesis?

---

### Post by acoustibop on 2008-01-13
Try ```
sudo chmod -R <path to saves folder> 666
``` Saghaulor.

---

### Post by Saghaulor on 2008-01-15
> **acoustibop said:**
> Try ```
sudo chmod -R <path to saves folder> 666
``` Saghaulor.

I'm not sure how to use that command. What is the relevance of "666"? Also, if I'm going to be saving to the save files, don't I want the permissions to be read and write?

---

### Post by acoustibop on 2008-01-15
That's exactly what that command does, Saghaulor: sets the specified folder and its contents to be readable and writeable by the owner (the first 6), the group (the second 6) and others (the third 6).

See the Ubuntu documentation [here]("https://help.ubuntu.com/community/FilePermissions#head-7a62fafd9fc7ac32bf05041e413852400abe42bd").

To use the command, enter it in a terminal, replacing <path to saves folder> with the actual path to your saves folder.

You'll need to use sudo if the folder is not in your Home folder, as your system probably won't regard you as the owner, although if your saves folder is in ~/.ZSNES, you can probably omit sudo, since you'll be its owner.

---

### Post by Saghaulor on 2008-03-06
After chatting with a friend who also uses linux, I told him that I was using Xubuntu, and he thought that I was crazy. He swore by Gnome. At this point I had royally screwed up quite a bit in the OS and I had no clue on how to fix it. So I decided to load Ubuntu. Things seems a bit easier, and won't you know, I can load my save files to ZSNES. I don't know of it was the XFCE desktop or Thunar, but something was blocking me from loading my save files.

Anyways, I thought I would post this in case someone else is having similar issues.

---

