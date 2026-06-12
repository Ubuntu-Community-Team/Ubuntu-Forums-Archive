---
title: "Rhythmbox ignores id3 tags"
date: 2005-04-01
forum: Desktop Environments
---

### Post by condorloco on 2005-04-01
Hi,

today I upgraded from Warty to Hoary and everything's working fine except one thing: Rhythmbox isn't really usable any more. It ignores all the id3 tags of my mp3 files, just listing the filename. And some of the files are listed as 'invalid file name' and Rhythmbox crashes if I try to play them. Renaming all files (and checking that the id3 tags are still there!) with Easytag didn't help. Does anybody has any idea what might be the cause of this? Thanks.

---

### Post by mostwanted on 2005-04-01
[QUOTE=condorloco]Hi,

today I upgraded from Warty to Hoary and everything's working fine except one thing: Rhythmbox isn't really usable any more. It ignores all the id3 tags of my mp3 files, just listing the filename. And some of the files are listed as 'invalid file name' and Rhythmbox crashes if I try to play them. Renaming all files (and checking that the id3 tags are still there!) with Easytag didn't help. Does anybody has any idea what might be the cause of this? Thanks.[/QUOTE]

This is a very long shot, but I have had some problems with Rhythmbox and packages from the marillat depository - try disabling that if it's enabled, delete all local packages that have anything to do with Rhythmbox and reinstall them from other repositories instead.

---

### Post by condorloco on 2005-04-01
Hi, thanks for the help, but i use the rhythmbox 0.8.8-7ubuntu3 (hoary) package from the official repository. De- and reinstalling the package doesn't change a thing.

---

### Post by cannibalbob on 2005-04-18
same problem.

---

### Post by Alexander Kirillov on 2005-04-18
[QUOTE=condorloco]Hi,

today I upgraded from Warty to Hoary and everything's working fine except one thing: Rhythmbox isn't really usable any more. It ignores all the id3 tags of my mp3 files, just listing the filename. And some of the files are listed as 'invalid file name' and Rhythmbox crashes if I try to play them. Renaming all files (and checking that the id3 tags are still there!) with Easytag didn't help. Does anybody has any idea what might be the cause of this? Thanks.[/QUOTE]
  1. Default Ubuntu packages do not have mp3 support - you would need marillat for that.

2. Do you tags contain non-Latin-1 symbols? This can cause no end of problems...

---

### Post by condorloco on 2005-04-18
After some research and trying I resolved the problem a few days ago. When I used the utf8-migration-tool it said that some of my mp3 files had to be renamed. When I told it to do so, it crashed, saying 'files not found'. Looking into those directories, they actually seemed to be empty. After deleting the directories, Rhythmbox worked fine, just as in Warty. It seems as if the upgrade to utf8 somehow completely corrupted a few of my files.

@Alexander
Why do I need Marillat? Mp3 works fine with universe and multiverse.

---

### Post by Alexander Kirillov on 2005-04-18
[QUOTE=condorloco]After some research and trying I resolved the problem a few days ago. When I used the utf8-migration-tool it said that some of my mp3 files had to be renamed. When I told it to do so, it crashed, saying 'files not found'. Looking into those directories, they actually seemed to be empty. After deleting the directories, Rhythmbox worked fine, just as in Warty. It seems as if the upgrade to utf8 somehow completely corrupted a few of my files.

@Alexander
Why do I need Marillat? Mp3 works fine with universe and multiverse.[/QUOTE]
 You are right - mp3 playing plugins are  is in multiverse. My mistake.

---

