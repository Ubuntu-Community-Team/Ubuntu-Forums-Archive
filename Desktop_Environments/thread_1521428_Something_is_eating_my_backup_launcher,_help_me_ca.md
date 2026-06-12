---
title: "Something is eating my backup launcher, help me catch it!"
date: 2010-06-30
forum: Desktop Environments
---

### Post by Simon Cropper on 2010-06-30
Hi,

I have created a launcher than runs a backup script that uses rsync. Once and a while I notice (usually when I come into work the next day) that the launcher is gone.

All the scripts are still present but the launcher is nowhere to be seen (not even in the trash). The file is not in the directory either - that is, present but not seen. By all intensive purposes the file is gone.

I have tried to pin down the sequence leading to this happening but have not been able. I am confused!

Something is eating my launcher. Only this one though. How do I catch the culprit. Is there a watcher program that will log what deletes a file. If I can narrow down a cause then I can submit a bug or get rid of the program causing the problem. Not sure if this is a X11, Gnome Desktop or Rsync problem.

Any help would be appreciated.

Note: rsync does backup the home directory, and therefore the ~/Desktop directory, that the launcher resides. The launcher runs the script ~/.scripts/RunBackup.sh. When I ran this script directly from the desktop it to use to disappear, as the launcher now does.

Simon

---

