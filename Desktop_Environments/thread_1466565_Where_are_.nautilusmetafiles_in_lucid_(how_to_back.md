---
title: "Where are .nautilus/metafiles in lucid (how to backup nautilus' emblem-assignment)"
date: 2010-04-30
forum: Desktop Environments
---

### Post by produnis on 2010-04-30
Hi folks,

I would like to backup my files and folders. This is very easy - but just copying the files to another HD loses all the emblems I attached to files/folder with nautilus.

So, I would like to backup/restore not only my data, but additionally the emblems I assigned to them in nautilus

At least in Jaunty, there was a xml-file in ~/.nautilus/metafiles/
that contains all emblem-assignments I did with nautilus. So restoring this folder brought back all my emblems

In Lucid (and in Karmic), this folder is empty.

Does anyone know where nautilus stores these information now?

I read somewhere in the internet, that the new folder is 
~/.local/share/gvfs-metadata

But that does not seem to be true.
I assigned a emblem to a new folder, but there are no changes in ~/.local/share/gvfs-metadata and subfolders
So...
I still stuck with my question....

---

### Post by produnis on 2010-05-01
bump

---

### Post by Solid One on 2010-05-31
probably here:

~/.gconf/apps/nautilus/desktop-metadata

---

### Post by morrigu76 on 2010-07-11
I can't find where the metadata on emblems is stored either. Emblems, without the possibility to back them up when doing a fresh install, seem pretty useless to me.
Any suggestions?

---

### Post by libssd on 2010-07-11
I suspect that I have run into another symptom of the same basic question. 

See thread: [http://ubuntuforums.org/showthread.php?t=1528520](http://ubuntuforums.org/showthread.php?t=1528520)

I use Remastersys to create restorable system backups, and I'm 99% certain that emblems are preserved, but that doesn't do you any good with a fresh install.

---

### Post by morrigu76 on 2010-07-11
Actually I didn't want to backup the emblem-images themselves, but the information on which folders/files have emblems "attached" to them.
It seems the other thread is just about restoring a certain set of emblems, but doesn't mention where the data on emblem-assignment is stored.

---

### Post by bn127 on 2010-09-05
I don't know about the emblems matter but the images I've assigned to my folders (Pictures and Music folders) are kept at ~/.local/share/gvfs-metadata. Backing this folder up and overwriting the same name's folder of a new system install I can re-gain the previous Pictures and Music folders' look.
I hope this can help you.

---

### Post by isync on 2010-12-01
Let's revive this thread:

Can anyone tell where Nautilus on 10.04 and up stores the data for which emblems are assigned to files?? As said on this thread, the mentioned dirs don't carry that information...

I  did a bit of digging in the source-code without luck, still [this thread]("http://mail.gnome.org/archives/gvfs-list/2008-July/msg00011.html") indicates emblems are now read from a common API exposed by GNOME to all applications, one user being Nautilus. So, where does GNOME commonly store the emblem metadata??

---

### Post by isync on 2010-12-02
Anyone know this??

---

### Post by hellork on 2010-12-12
On fedora, harvesting the file
~/.local/share/gvfs-metadata/home
brought about the miraculous bestowal of notes upon my desktop.
May its blessings extend to you this holiday season and to the emblems themselves, **but...** loggest thou out to witness the manefestation thereof...

---

### Post by HendyIrawan on 2011-05-26
> **hellork said:**
> On fedora, harvesting the file
~/.local/share/gvfs-metadata/home
brought about the miraculous bestowal of notes upon my desktop.
May its blessings extend to you this holiday season and to the emblems themselves, **but...** loggest thou out to witness the manefestation thereof...

Thank you............!!! :popcorn:

---

