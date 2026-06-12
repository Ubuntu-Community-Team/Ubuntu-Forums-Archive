---
title: "Trash directory in the wrong location"
date: 2009-02-26
forum: Desktop Environments
---

### Post by yannos on 2009-02-26
I’m not sure what happened, but my trash directory is under my music directory. I can only see *some* files in it from nautilus, but when I dig into the folder in a terminal, I see that there is much more stuff. Emptying the trash trough nautilus doesn’t delete them. I’m not sure why there is a trash folder there, but some clues might include:
 
- I just migrate from gentoo (but I was using kde back then).
- A machine running macosx was mounting my whole home directory (nfs, then sshfs).
- the files in my music folder are in fact there because of a mount -o bind of a another partition.
- Its name is .Trash-1000

I don’t have a .trash in my home directory. Now, I don’t want to screw things up, so does anybody knows how thrashes works in gnome? Can I just move mine to my home dir?

---

### Post by dbbolton on 2009-02-26
> **yannos said:**
> I’m not sure what happened, but my trash directory is under my music directory. I can only see *some* files in it from nautilus, but when I dig into the folder in a terminal, I see that there is much more stuff. Emptying the trash trough nautilus doesn’t delete them. I’m not sure why there is a trash folder there, but some clues might include:
 
- I just migrate from gentoo (but I was using kde back then).
- A machine running macosx was mounting my whole home directory (nfs, then sshfs).
- the files in my music folder are in fact there because of a mount -o bind of a another partition.
- Its name is .Trash-1000

I don’t have a .trash in my home directory. Now, I don’t want to screw things up, so does anybody knows how thrashes works in gnome? Can I just move mine to my home dir?
Nautilus does not uses .Trash anymore. It uses the URI "trash:// ". You can see this by launching the command ```
nautilus --no-desktop trash://
```

I don't know what your .Trash-1000 folder is from, but it's a safe bet that Nautilus isn't using it for anything important.

---

### Post by yannos on 2009-02-26
It seems the files I'm deleting from my music dir is put into ~/home/Music/.Trash-1000 (and they do not appear in trash:///). If I delete it, it'll get recreated once I trash some more music files. If I trash files elsewhere on my system, everything behaves normally. Weird.

---

### Post by dbbolton on 2009-02-26
> **yannos said:**
> It seems the files I'm deleting from my music dir is put into ~/home/Music/.Trash-1000 (and they do not appear in trash:///). If I delete it, it'll get recreated once I trash some more music files. If I trash files elsewhere on my system, everything behaves normally. Weird.
Can you paste the output of these two commands:

```

apt-cache policy nautilus

nautilus --version

```

---

### Post by yannos on 2009-02-26
```
yanos@musaraigne:~$ apt-cache policy nautilus
nautilus:
  Installed: 1:2.24.1-0ubuntu2
  Candidate: 1:2.24.1-0ubuntu2
  Version table:
 *** 1:2.24.1-0ubuntu2 0
        500 http://mirrors.ccs.neu.edu intrepid-updates/main Packages
        100 /var/lib/dpkg/status
     1:2.24.1-0ubuntu1 0
        500 http://mirrors.ccs.neu.edu intrepid/main Packages

yanos@musaraigne:~$ nautilus --version
GNOME nautilus 2.24.1
```

---

### Post by dbbolton on 2009-02-26
> **yannos said:**
> ```
yanos@musaraigne:~$ apt-cache policy nautilus
nautilus:
  Installed: 1:2.24.1-0ubuntu2
  Candidate: 1:2.24.1-0ubuntu2
  Version table:
 *** 1:2.24.1-0ubuntu2 0
        500 http://mirrors.ccs.neu.edu intrepid-updates/main Packages
        100 /var/lib/dpkg/status
     1:2.24.1-0ubuntu1 0
        500 http://mirrors.ccs.neu.edu intrepid/main Packages

yanos@musaraigne:~$ nautilus --version
GNOME nautilus 2.24.1
```
Exact same version as the one I'm using. Quick question, what happens when you open ~/home/Music/.Trash-1000 and delete the files that are in that folder? Are they sent to the Trash?

Also, are you pressing the delete key or doing  Right-click > Move to Trash ?

---

### Post by yannos on 2009-02-26
> **dbbolton said:**
> Exact same version as the one I'm using. Quick question, what happens when you open ~/home/Music/.Trash-1000 and delete the files that are in that folder? Are they sent to the Trash?

No, they disappear and them come right back with ".2" appended to the filename. 

> **dbbolton said:**
> 
Also, are you pressing the delete key or doing  Right-click > Move to Trash ?

I tried both and there doesn't seem to be any difference.

---

### Post by dbbolton on 2009-02-26
That is really strange. You might think about filing a bug report or looking through the existing ones on Launchpad: [https://bugs.launchpad.net/nautilus/+bugs?field.searchtext=trash&search=Search+Bug+Reports&field.scope=project&field.scope.target=nautilus](https://bugs.launchpad.net/nautilus/+bugs?field.searchtext=trash&search=Search+Bug+Reports&field.scope=project&field.scope.target=nautilus)

---

### Post by yannos on 2009-02-27
Ok I'll file a bug report. I just noticed that there is a .Trash-1000 directory on my usb stick. I think it's used to store files you delete from it, instead of transferring them to the local filesystem just to put them in the proper trash. Could it be that nautilus thinks that my music dir, witch is on a different filesytem, somehow think that this FS is not local?

---

### Post by dbbolton on 2009-02-27
> **yannos said:**
> Ok I'll file a bug report. I just noticed that there is a .Trash-1000 directory on my usb stick. I think it's used to store files you delete from it, instead of transferring them to the local filesystem just to put them in the proper trash. Could it be that nautilus thinks that my music dir, witch is on a different filesytem, somehow think that this FS is not local?
Hmm, that could be. I have noticed the creation of hidden "trash" directories on USB drives too.

---

### Post by heindsight on 2010-05-20
Hi yannos,

Did you ever manage to find a solution to this?

I just installed Lucid, after using Hardy for 2 years, and as usual I created a Data partition to store all my documents, music, pictures etc. However, where in the past I mounted this partition at /home/heindsight/data I now mounted it at /mnt/data and created a bind mount from /mnt/data/heindsight to /home/heindsight/data.

I now have the same problem you described with trashing files under /home/heindsight/data. Interestingly, when I navigate (in nautilus) to /mnt/data/heindsight/... and move a file to trash, the file gets placed under /mnt/data/.Trash/1000/, it shows up in the trash applet and emptying the trash permanently deletes the file. However if I point nautilus to /home/heindsight/data/... and move a file there to trash, the file gets placed under /home/heindsight/data/.Trash-1000 and doesn't show up in the trash applet.

It would appear that the bind mount is confusing nautilus (or probably actually gvfs).

I tried to work around this by making /home/heindsight/data/.Trash-1000 a symlink to /mnt/data/.Trash/1000, but that doesn't work - when I try to move a file to trash from /home/heindsight/data/... I get an error stating that the file cannot be moved to trash and asking if I want to permanently delete it instead.

I also tried creating /home/heindsight/data/.Trash/1000 with the same ownerships and permissions as /mnt/data/.Trash/1000, but that doesn't seem to work either - when I move files from /home/heindsight/data/... to the trash, they do get placed under /home/heindsight/data/.Trash/1000, but they still don't show up in the trash applet.

For now, it seems the only solutions are to either mount my data partition at /home/heindsight/data again as in the past (but I don't want to do this, because I plan on creating at least one other user account on this system, which should also be able to use that partition) or to use a symlink instead of a bind mount (which has its own set of problems associated with it).

Does anybody else have any ideas?

---

