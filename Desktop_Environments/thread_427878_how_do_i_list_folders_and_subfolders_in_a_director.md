---
title: "how do i list folders and subfolders in a directory?"
date: 2007-04-29
forum: Desktop Environments
---

### Post by super.rad on 2007-04-29
In my home directory i've created a folder called "My Music" how do i create a list of all the folders and sub-folders in this directory? Thanks

---

### Post by super.rad on 2007-04-29
sorry just realised where i posted this, it was supposed to be in general help, please move it

---

### Post by bashologist on 2007-04-29
#Maybe something like this? How would you like your directory's displayed?
find ~/My\ Music -type d

---

### Post by brian.smith on 2007-04-29
perhaps you are looking for "tree" command? tree lists contents of directories in a tree-like format.

tree <directory name>

If you don't have the package already installed:

# apt-get install tree

---

### Post by DarkN00b on 2007-04-29
Try this, it worked for me:

In a terminal, type

```
ls -R list.txt
```

That will create a text file in the current directory containing a recursive list of all files as well as all files in all directories within. Except hidden files though..

This is great for creating .m3u playlists, all you have to do is open the file and remove the directory names.

---

### Post by dunomous on 2007-05-05
> **DarkN00b said:**
> Try this, it worked for me:

In a terminal, type

```
ls -R list.txt
```

That will create a text file in the current directory containing a recursive list of all files as well as all files in all directories within. Except hidden files though..

This is great for creating .m3u playlists, all you have to do is open the file and remove the directory names.


[color=green]Don't you mean:

```
ls -R > list.txt
```

and then renaming the file with a .m3u extension?[/color]

---

### Post by DarkN00b on 2007-05-05
[img]http://graphics.gaiaonline.com/images/template/smiles/icon_sweatdrop.gif[/img] Ehheh heh, you're right. I was in a hurry when I posted that. Sorry.

---

### Post by dunomous on 2007-05-05
> **DarkN00b said:**
> [img]http://graphics.gaiaonline.com/images/template/smiles/icon_sweatdrop.gif[/img] Ehheh heh, you're right. I was in a hurry when I posted that. Sorry.

I see, treating the forums like a fast food worker at a busy drive through. =D>  :D

Oh well, it was a simple mistake, a typo.

I'm curious as to why the original poster never posted back about it not working and asking for a fix though...

---

### Post by Impulse666 on 2007-09-22
I was looking for something to do just this. 
```
ls -R > list.txt
```
worked great. Thanks!

---

### Post by olavjunior on 2007-11-21
Great!! Thanks

And if you're in a directory you want to make a playlist of, just use
```
ls > playlist.m3u
```

---

### Post by super.rad on 2007-12-03
is there anyway to do this without showing the files, so it makes a list of the folders and subfolders?

---

### Post by Chas_E_Erath on 2007-12-03
If the directory you're interested in is called 'My Music':

```
find ./My\ Music -type d
```

If you want to redirect the output to a file called 'directory.names', then:

```
find ./My\ Music  -type d > directory.names
```

'find' searches recursively from a specified location.  You can tell it what type of thing to look for (the default is everything), in this case the 'd' tells it to look for directory type things.

---

### Post by super.rad on 2007-12-03
thanks worked perfectly

---

