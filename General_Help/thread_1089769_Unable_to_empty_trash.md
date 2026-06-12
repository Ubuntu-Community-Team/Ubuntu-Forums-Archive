---
title: "Unable to empty trash"
date: 2009-03-07
forum: General Help
---

### Post by kalamityjane on 2009-03-07
There is a folder in my trash that refuses to be deleted. 

I have access to the files, but I am unable to change the file permissions.

Any suggestions?

---

### Post by taurus on 2009-03-07
Who owns that file?

Open a terminal and post the output of this command.

Applications -> Accessories -> Terminal
```
ls -la ~/.local/share/Trash/files
```

---

### Post by abhilashm86 on 2009-03-07
hey even i'm not able to delete some files in trash
here it goes
abhilash@abhi:~$ ls -la ~/.local/share/Trash/files
total 24
drwx------ 6 abhilash abhilash 4096 2009-03-08 01:57 .
drwx------ 4 abhilash abhilash 4096 2009-02-20 00:47 ..
drwxr-xr-x 3 abhilash abhilash 4096 2009-02-20 00:47 pidgin-2.2.3.1
drwxr-xr-x 3 abhilash abhilash 4096 2009-01-19 14:31 pidgin-2.3.1
drwxrwxrwx 3 abhilash abhilash 4096 2009-01-19 14:31 pidgin-rhythmbox-2.0
drwxr-xr-x 3 abhilash abhilash 4096 2009-02-03 18:33 yoga

i tried becoming superuser and also tried nautilus, din't work...........

---

### Post by taurus on 2009-03-07
> **abhilashm86 said:**
> hey even i'm not able to delete some files in trash
here it goes
abhilash@abhi:~$ ls -la ~/.local/share/Trash/files
total 24
drwx------ 6 abhilash abhilash 4096 2009-03-08 01:57 .
drwx------ 4 abhilash abhilash 4096 2009-02-20 00:47 ..
drwxr-xr-x 3 abhilash abhilash 4096 2009-02-20 00:47 pidgin-2.2.3.1
drwxr-xr-x 3 abhilash abhilash 4096 2009-01-19 14:31 pidgin-2.3.1
drwxrwxrwx 3 abhilash abhilash 4096 2009-01-19 14:31 pidgin-rhythmbox-2.0
drwxr-xr-x 3 abhilash abhilash 4096 2009-02-03 18:33 yoga

i tried becoming superuser and also tried nautilus, din't work...........

Those four are all directories.  Which one(s) do you want to remove from a terminal?

---

### Post by abhilashm86 on 2009-03-07
> **taurus said:**
> Those four are all directories.  Which one(s) do you want to remove from a terminal?

drwxr-xr-x 3 abhilash abhilash 4096 2009-02-20 00:47 pidgin-2.2.3.1
drwxr-xr-x 3 abhilash abhilash 4096 2009-01-19 14:31 pidgin-2.3.1
drwxrwxrwx 3 abhilash abhilash 4096 2009-01-19 14:31 pidgin-rhythmbox-2.0
drwxr-xr-x 3 abhilash abhilash 4096 2009-02-03 18:33 yoga

these are the ones i need to remove, everytime they just sit in trash!!!!

tale goes like this.
pidgin i went on installing from scratch, so messed up a little in middle, so don't know why i can't delete......

i got a original yoga dvd, a license version, i made a .bin file using some cd software, then something happened, i'm unable to delete?

---

### Post by taurus on 2009-03-07
> **abhilashm86 said:**
> drwxr-xr-x 3 abhilash abhilash 4096 2009-02-20 00:47 pidgin-2.2.3.1
drwxr-xr-x 3 abhilash abhilash 4096 2009-01-19 14:31 pidgin-2.3.1
drwxrwxrwx 3 abhilash abhilash 4096 2009-01-19 14:31 pidgin-rhythmbox-2.0
drwxr-xr-x 3 abhilash abhilash 4096 2009-02-03 18:33 yoga

these are the ones i need to remove, everytime they just sit in trash!!!!

tale goes like this.
pidgin i went on installing from scratch, so messed up a little in middle, so don't know why i can't delete......

i got a original yoga dvd, a license version, i made a .bin file using some cd software, then something happened, i'm unable to delete?

If you want to remove those directories, try 

```
rm -rf pidgin-2.2.3.1 pidgin-2.3.1 pidgin-rhythmbox-2.0 yoga
ls -la
```
And if you encounter permissions or ownership issue, then put sudo in front of it.

```
sudo rm -rf pidgin-2.2.3.1 pidgin-2.3.1 pidgin-rhythmbox-2.0 yoga
ls -la
```

---

### Post by charkoal on 2009-03-09
I tried that code and it comes up with rm: invalid option - - l

What have i done wrong ?

---

