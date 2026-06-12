---
title: "Desktop &quot;move to&quot; operation gives me a strange error."
date: 2018-10-20
forum: Desktop Environments
---

### Post by cajones on 2018-10-20
When I perform a right click on a file and select the 'move to' or 'copy to' operation, I get an error saying folder contents cannot be displayed. It doesn't seem to remember the last folder I used or go to a default folder. This happens on both of my Ubuntu computers, and has done it since 18.04, I figured it was a bug that would be fixed in 18.10, so now that I've upgrade, it's still there, I'm puzzled.  Does this happen to anyone else, how to I fix it?

[ATTACH=CONFIG]281394[/ATTACH]

---

### Post by dino99 on 2018-10-21
You might find some error into 'journalctl -b' that will help to understand that problem.
Note that you only can move a file if: it is yours, it is not in use.

---

### Post by mc4man on 2018-10-21
If this is just happening to files on the Desktop then it's par for the course, Gnome doesn't support the Desktop & Ubuntu does as little as possible to keep producing Ubuntu for desktop installs.

---

### Post by cajones on 2018-10-21
The files are all mine but this problem only occurs with files on the Desktop, but I have the same issue on multiple computers, weird huh? not sure what I'm looking for but only found one thing that might indicate something.

: open pipe file /run/rpc_pipefs/nfs/blocklayout failed: No such file or directory

---

### Post by cajones on 2018-10-21
Since I'm the only one having this issue apparently, it has to be something specific to my setup.  Maybe it has to do with my home network? NFS file sharing or something? It doesn't make any sense to me.

---

### Post by mc4man on 2018-10-21
> **cajones said:**
> Since I'm the only one having this issue apparently, it has to be something specific to my setup.  Maybe it has to do with my home network? NFS file sharing or something? It doesn't make any sense to me.
No, anyone you tries this with files on the Desktop will see the same. (with nautilus..

---

### Post by cajones on 2018-10-21
Yes, any folder or file that I try to 'move to' or 'copy to' gives me the same pop-up when the nautilus window opens. I can select a folder and proceed, but its annoying and something I would like to figure out.

---

### Post by mc4man on 2018-10-21
> **cajones said:**
> Yes, any folder or file that I try to 'move to' or 'copy to' gives me the same pop-up when the nautilus window opens. I can select a folder and proceed, but its annoying and something I would like to figure out.

I thought this post was explanatory, if not I'll reiterate 
[https://ubuntuforums.org/showthread.php?t=2404167&p=13810325#post13810325](https://ubuntuforums.org/showthread.php?t=2404167&p=13810325#post13810325)

---

### Post by cajones on 2018-10-21
I got this...  open pipe file /run/rpc_pipefs/nfs/blocklayout failed: No such file or directory

but I don't know what it means or if it could be related.

---

