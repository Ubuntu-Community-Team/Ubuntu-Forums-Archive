---
title: "A very simple problem.. but rply"
date: 2009-06-24
forum: General Help
---

### Post by babbar.ankit on 2009-06-24
When a write in terminal cd~/Dekstop 
It says no such directory found
How to move to different directories:confused:

---

### Post by pedro_orange on 2009-06-24
Try a space between cd and the folder you wish to move to.

```
cd ~/Desktop
```

---

### Post by babbar.ankit on 2009-06-24
it didnt worked

---

### Post by nice_like_rice on 2009-06-24
If you type "cd" on its own, this will take you to your home directory. Then type "ls" to list the files there. You can then type "cd Desktop" to change into that directory.

---

### Post by pedro_orange on 2009-06-24
I just did this.

Open terminal

```

pedro@pedro-desktop:~$ cd ~/Desktop
pedro@pedro-desktop:~/Desktop$

```

Remember it's case-sensitive.

---

### Post by geirha on 2009-06-24
If you are running Ubuntu in a non-english language, those standard folders may be localized. To see what the directory is called for you, run ```
xdg-user-dir DESKTOP
```

Then pass the directory it prints to the cd command. You can do it directly with command substitution as well
```
cd "`xdg-user-dir DESKTOP`"
# or
cd "$(xdg-user-dir DESKTOP)"
```

---

### Post by babbar.ankit on 2009-06-24
Thank You all Resolved !

---

### Post by snek on 2009-06-24
Remember you can press TAB to autocomplete, even for directories..
So in my case I could type:
```

cd ~/D

```
and then press TAB 2x and it will list all possible directories/files which start with D.
It saves from having to cd to a dir and using ls to view the contents..

So in this case you could have used:
```

cd ~/

```
and then pressed TAB 2x to list all files & directories in your home dir.

Hope this helps you in the future :)

---

