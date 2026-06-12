---
title: "&quot;permission denied&quot; in directory folders (pcmanfm)"
date: 2012-01-28
forum: Desktop Environments
---

### Post by scubscub on 2012-01-28
Hello all, 

Suddenly pcmanfm will not allow me into sub-folders of my home directory. I opened pcmanfm in lxterminal as shown [on this thread]("http://ubuntuforums.org/showpost.php?p=11619219&postcount=406"), and got the following error:

(pcmanfm:2917): Gtk-CRITICAL **: IA__gtk_window_present_with_time: assertion `GTK_IS_WINDOW (window)' failed
** (pcmanfm:2917): DEBUG: unable to load icon . GThemedIcon application-octet-stream gnome-mime-application-octet-stream application-x-generic
** (pcmanfm:2917): DEBUG: FmJob error: Permission denied
** (pcmanfm:2917): DEBUG: FmJob error: Permission denied


What does it all mean?  For the record, I can get to the said folders as root, and I have marked all the permissions as read and write for owner, group, and other. I have lubuntu 11.10.

---

### Post by scubscub on 2012-01-28
More details:


This happens two folder levels inside my home folder.  So, my computer's name being Severian, I can open /home/Severian/Documents/ but not /home/Severian/Documents/Audio/.  I get separate "permission denied" dialogues to click through for every file in the denied folder.

To make sure there wasn't something wrong with the partition, I booted xubuntu from a livecd, and everything worked fine.

---

### Post by SteveDee on 2012-01-28
> **scubscub said:**
> ...I can open /home/Severian/Documents/ but not /home/Severian/Documents/Audio/. ...

Open LXTerminal and inspect your file permissions in the Documents folder like this:-
```

cd Documents
ls -l

```

If you can't see any problems, post the output here.

---

### Post by scubscub on 2012-01-28
Thanks, SteveDee.  What am I looking for?  This gave me a list of the contents of the Documents folder, with the folders highlighted.  Trying to cd to the folders inside Documents predictably came back "permission denied".

---

### Post by scubscub on 2012-01-28
Oops, sorry.  I tried it again and now see that all the folders are marked:

drw-rwxrwx

while the files which I can access are marked:

-rw-rw-rw-

---

### Post by scubscub on 2012-01-28
Okay, so the owner does not have execute rights on the subfolders.  I was able to change this from terminal within ~/Documents/ for one of the subfolders, with:

chmod u+x folder/

That worked.

But I can't imagine doing this for every single affected folder.  What I need is a way to back up to the home directory and give a chmod which affects all subdirectories of the home folder.  Of course, the home folder itself and its immediate subfolders are drwxrwxrwx, it's only the sub-subfolders which are drw-rwxrwx...

And I'm still wondering how all this happened...

---

### Post by scubscub on 2012-01-28
Sorry to keep posting this in bits and pieces.

Anyway, the solution was to go back to the home/ directory and in terminal:

chmod u+x /Severian -R

Everything is now accessible, though it is still unclear how it all happened.


SteveDee, this is the second time in a week or so you have helped me out, many thanks!

---

