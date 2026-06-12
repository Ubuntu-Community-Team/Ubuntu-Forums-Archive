---
title: "run executables anywhere"
date: 2009-02-28
forum: General Help
---

### Post by bigrockcrasher on 2009-02-28
is there a way to have an executable run in any folder with out having that file in the folder. i have this program i wrote in c++. i have to copy this executable in to folders where i would like to use them. i got this program i wrote called convert and i would like it so that it is located in one spot and i can call it in any folder and have it act like it is that folder like when it makes files it will put it in the same directory. does anyone know how to do this.
aaron tanenbaum

---

### Post by Rinzwind on 2009-02-28
If you add the command to a directory that is inside your PATH it will work.
Put it in /usr/bin/. That to me is the most obvious candidate.

BTW: convert is already a command in Linux (in the package imagemagick) so you might want to rename it ;)

---

### Post by lha on 2009-02-28
You shouldn't (atleast in principle) add custom files to /usr/bin, it is supposed to contain binary files that are maintained by your distribution. The standard place for other programs is /usr/local/bin. It is easier to stay in control of your own programs when they are in a dedicated place.

---

### Post by snova on 2009-02-28
**/usr/bin** is for the package manager, and **/usr/local** is for locally installed programs.

Although it might do well in /usr/local, you need root access to move files there- so I suggest creating a private ~/bin folder, and copying your programs in there.

Then, add this directory to your PATH variable in .bashrc:

```
PATH=~/bin:$PATH
```

And you should be able to run files in ~/bin from anywhere.

---

### Post by bodhi.zazen on 2009-02-28
> **lha said:**
> you shouldn't (atleast in principle) add custom files to /usr/bin, it is supposed to contain binary files that are maintained by your distribution. The standard place for other programs is /usr/local/bin. It is easier to stay in control of your own programs when they are in a dedicated place.

+1

---

