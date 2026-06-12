---
title: "(Newbie Question) Trailing tilda (&quot;~&quot;) in filename in a terminal Window -"
date: 2009-05-05
forum: General Help
---

### Post by wklang on 2009-05-05
I looking at the /etc/X11 directory in my Ubuntu installation, I see three xorg.conf files: the backup of the original, the one I just edited, and one with a trailing "~".


```

wes@kashgar-ubuntu:/etc/X11$ pwd
/etc/X11
wes@kashgar-ubuntu:/etc/X11$ ls -al xorg*
-rw-r--r-- 1 root root 1716 2009-05-05 16:27 xorg.conf
-rw-r--r-- 1 root root 1037 2009-04-28 12:35 xorg.conf~
-rw-r--r-- 1 root root 1137 2009-05-05 16:26 xorg.conf_backup
wes@kashgar-ubuntu:/etc/X11$ 

```

My suspicions are that the one with the trailing "~" was left over from a failed attempt to edit the file with NVIDIA X Server Settings utility, but I'm not sure. (I installed 9.04 on or about April 28, 2009)

Can anyone shed some light on this form!

---

### Post by SentientFluid on 2009-05-05
The trailing ~ is a backup file.  Gedit does this by default, for example.  If you had the file open in Gedit for x minutes, then it automatically create the backup in case somethign went wrong.

---

### Post by Agent ME on 2009-05-05
You can disable backups in gedit under one of its menus if you don't want them.

To get rid of all backups in a directory, simply doing "rm *~" works for me. (Be careful you type that exactly, because if you forgot the ~ it will simply delete all files in the directory.)

---

### Post by andrew.46 on 2009-05-06
Hi wklang,

> **wklang said:**
> My suspicions are that the one with the trailing "~" was left over from a failed attempt to edit the file with NVIDIA X Server Settings utility, but I'm not sure.

Have a look at your whole system and you may be a little shocked to see the number of backup files you have accumulated:

```
sudo find / \( -name '*~' -o -iname '*.bak' \)
```

The safest thing to do is of course to leave them all alone, or you can live a little closer to the edge and judiciously prune them :-).

Andrew

---

### Post by SentientFluid on 2009-05-06
> **Agent ME said:**
> You can disable backups in gedit under one of its menus if you don't want them.

To get rid of all backups in a directory, simply doing "rm *~" works for me. (Be careful you type that exactly, because if you forgot the ~ it will simply delete all files in the directory.)

Or show hidden files in Nautilus and delete from there. That way if you accidentally delete the wrong thing, you can recover from your trash.

Using rm in Terminal just deletes and makes it incredibly hard to recover from mistakes.

---

