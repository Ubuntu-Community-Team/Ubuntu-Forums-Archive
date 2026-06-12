---
title: "[SOLVED] Egads!  Why do I have all these hundreds of Nautilus saved-session-CCCCC fil"
date: 2008-01-18
forum: Desktop Environments
---

### Post by Phrawm48 on 2008-01-18
Feisty (7.04), Gnome 2.18.1

In my home directory's *~/.nautilus* sub-directory, I have several hundred files of the form *saved-session-CCCCC*, where *CCCCC* is an upper-case alphanumeric character presumably used to uniquely identify each saved session file.

These files in turn contain what appears to be a usage history for each invocation of of Nautilus(?).  For example:

> <?xml version="1.0"?>
<session>
  <history>
    <bookmark name="ric" icon="user-home" uri="file:///home/rbv"/>
    <bookmark name="Serial &amp; Card Numbers" icon="gnome-fs-directory" uri="file:///media/sda8/Tweener/Junk_Drawer/Serial%20%26%20Card%20Numbers"/>
    <bookmark name="Junk_Drawer" icon="gnome-fs-directory" uri="file:///media/sda8/Tweener/Junk_Drawer"/>
    <bookmark name="Tweener" icon="gnome-fs-directory" uri="file:///media/sda8/Tweener"/>
    <bookmark name="sda8" icon="gnome-fs-directory" uri="file:///media/sda8"/>
*...[a long list of similar entries continues here]...*
  </history>
</session>
Of what possible use is all this garbage?  (I ran a couple of Web searches and a couple of forum searches but didn't get any answers there...)

More to the point, can I safely run a periodically scheduled *chron* process or something to purge these files?  They seem useless, at best...

Cheers & thanks,
Ric
SFO

---

### Post by Phrawm48 on 2008-01-23
I 7-zip'ed all the files up a couple of days ago, deleted them and then used Nautilus without ill effects.  So there's evidently no problem deleting these files.

But I won't mark this **Solved** until I understand *why* Nautilus needs to create all this crap.  Hundreds of apparently useless(?) files -- worse than Windows for Heaven's sake!

Cheers & hope this somehow helps,
Ric
SFO

---

### Post by Jittoku on 2008-01-27
I noticed the same thing.  Tried deleting the contents, and I noticed that files I had on the desktop had lost their arrangment, and been stacked along the left edge of the screen.  It appears that's something that the files in the "metafiles" folder keep track of.  But why keep the old ones?  It does seem sloppy, and windoze-like.  

I'm guessing this is something done to restore a lost session.  It couldn't be part of the file system check, could it?  That wouldn't be happening in nautilus, would it?

---

### Post by Phrawm48 on 2008-01-28
> **Jittoku said:**
> ...Tried deleting the contents, and I noticed that files I had on the desktop had lost their arrangement, and been stacked along the left edge of the screen.  It appears that's something that the files in the "metafiles" folder keep track of.  But why keep the old ones? 

When I get an extra minute I think I'll create a little script that deletes all but the most recent version of the files and use chron or anachron to periodically run the script.

My theory, yet to be proven, is that such a script will provide me with any notional benefits of the most recently created file while eliminating the clutter caused by Nautilus's sloppy retention of every file it ever created...

Cheers, thanks, & hope this helps,
Ric

---

### Post by HDave on 2008-03-03
Same question here....anyone?

---

### Post by Phrawm48 on 2008-03-12
Okay, first I finally got around to writing myself a little script that purges all but some number of *retained_files* (I decided on four):

```
#!/bin/bash
# Script to purge all but most recently created "retained_files" in Nautilus history directory.

# Specify the target directory and file names to operate on.
target_files=~/.nautilus/saved-session-*

# Calculate the total number of files matching the target criteria. 
total_files=$(ls -t1 $target_files | wc --lines)

# Specify the number of files to retain.
retained_files=4

# If there are surplus files, delete them.
if [ $total_files -gt $retained_files ]
  then
  rm $(ls -t1 $target_files | tail --lines=$((total_files-retained_files)))
fi
```I use **System** > **Administration** > **Sessions** to run this script during startup.  *chron* or *anachron* are other ways to periodically run the script.

I also discovered that the *.xml* files in *~/.nautilus/metafiles* maintain the state of the desktop, etc.  Deleting these results in, to cite but one example, the placement of one's desktop icons to be reset.

Finally, I still have no idea why Nautilus wants to retain so many of these files...

Cheers,
Ric
SFO

---

### Post by soumo on 2008-05-27
Thanks a ton!  You may want to do the same for your .thumbnails folder as well from time to time.

I appreciate your script, but suggest you put in some contact info for your credit, -or in case of blame ;)

---

