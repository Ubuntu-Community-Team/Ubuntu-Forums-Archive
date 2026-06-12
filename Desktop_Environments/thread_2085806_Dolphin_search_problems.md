---
title: "Dolphin search problems"
date: 2012-11-19
forum: Desktop Environments
---

### Post by oygle on 2012-11-19
I used to use Nautilus in Ubuntu, but now use Dolpin in Kubuntu 12.04

I can't find the (full) search features in Dolphin, the 'find' for 'content' doesn't seem to work.

All I want to do is a recursive search through various folders, looking for a string in each file, and return the results

Any Clues ??

Oygle

---

### Post by mparillo on 2012-11-19
> **oygle said:**
> I used to use Nautilus in Ubuntu, but now use Dolpin in Kubuntu 12.04

I can't find the (full) search features in Dolphin, the 'find' for 'content' doesn't seem to work.

All I want to do is a recursive search through various folders, looking for a string in each file, and return the results

Any Clues ??

Oygle

I am on Dolphin Version 2.1 Using KDE Development Platform 4.9.3, but this should be available for you also.
I have both an icon looking like binoculars, and have set my Control Settings to Show the Menu Bar.
So, I can either click on the binoculars, or click though Edit > Find.
In the Find entry box, enter a string (there may be a way to enter a regular expression)
Underneath, change Filename to Content, and I leave Search from here alone, as that is by default searching recursively through my home directory.
The results are Filenames.

---

### Post by ankspo71 on 2012-11-19
Are you trying to search hidden directories? If so I believe there is a bug that prevents searching hidden directories using dolphin. [http://forum.kde.org/viewtopic.php?f=22&t=94849](http://forum.kde.org/viewtopic.php?f=22&t=94849)

I can't search hidden directories using dolphin's find feature, but searching for unhidden files and directories is working well. Dolphin 2.1, KDE 4.9.3 

'Kfind' is a good alternative to search hidden directories.

PS. The Nepomuk/Strigi also defaults to not searching hidden directories (probably for performance and organisation reasons). Individual hidden directories can be added for indexing at System Settings > Desktop Search > Desktop Query > Customize Index Folders > Show Hidden Folders.

---

### Post by oygle on 2012-11-20
> **mparillo said:**
> I have both an icon looking like binoculars, and have set my Control Settings to Show the Menu Bar.

I didn't have menu bar showing, but have now. I'm using Dolphin 2.0

> **mparillo said:**
> So, I can either click on the binoculars, or click though Edit > Find.
In the Find entry box, enter a string (there may be a way to enter a regular expression)
Underneath, change Filename to Content, and I leave Search from here alone, as that is by default searching recursively through my home directory.
The results are Filenames.

Results are no filenames for me, even if I go to the exact path, and try one filename, no results. Dolphin uses Nepomuk, maybe that is where the problem is ??

Thanks,

Oygle

---

### Post by oygle on 2012-11-20
> **ankspo71 said:**
> Are you trying to search hidden directories? If so I believe there is a bug that prevents searching hidden directories using dolphin. [http://forum.kde.org/viewtopic.php?f=22&t=94849](http://forum.kde.org/viewtopic.php?f=22&t=94849)

Yes, it is in a lot of paths for KMail, which have hidden directories. I then went and tried in a path with no hidden and the search worked.

I'm using Dolphin 2.0 and KDE 4.8.5

> **ankspo71 said:**
> 'Kfind' is a good alternative to search hidden directories.

Thanks, I will try Kfind.  :)

> **ankspo71 said:**
> PS. The Nepomuk/Strigi also defaults to not searching hidden directories (probably for performance and organisation reasons). Individual hidden directories can be added for indexing at System Settings > Desktop Search > Desktop Query > Customize Index Folders > Show Hidden Folders.

I went and changed that setting here, thanks. Then I went and tried a search in KMail, because it hadn't been working, now it seems to be working, as it uses Nepomuk, so searching. Not entirely sure though ??

Tried Dolphin again, same problem.

Thanks,

Oygle

---

### Post by oygle on 2012-11-20
KFind is great, lots of options.

---

