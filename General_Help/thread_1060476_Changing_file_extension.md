---
title: "Changing file extension"
date: 2009-02-04
forum: General Help
---

### Post by pikabuntu on 2009-02-04
I am trying to learn all I can about linux commands and to practice, I am creating simple shell scripts to automate some of the things I do a lot in nautilus.  

I have a folder full of flash videos that I would like to give the .flv extension to, and this is the best I could come up with to do this, but it does not work...

cd ~/Videos
mv * ~/Videos/*.flv

---

### Post by kaibob on 2009-02-04
This will do it:

```
rename -n 's/.swf$/.flv/' *.swf
```

It assumes that the existing extension is .swf. The -n option directs rename to do a dry run and report proposed changes; substitute -v for -n to actually rename the files.

The following thread gives a lot of great info on the use of the rename utility:

[http://ubuntuforums.org/showthread.php?p=5210531](http://ubuntuforums.org/showthread.php?p=5210531)

---

### Post by pikabuntu on 2009-02-04
Could you break that down for me? :)

EDIT

None of the files already have an extension.

Thank you! that thread looks useful!

---

### Post by pikabuntu on 2009-02-04
Ok, this command is supposed to *remove *a file extension... Is there any way that I can change it to *create* one?

rename -n 's/\.tmp$//' *.tmp

---

### Post by kaibob on 2009-02-04
This will add the flv extension to all files in the current directory:

```
rename -n 's/$/.flv/' *
```

Rename is actually quite easy. The general format is:

```
rename 's/old/new/' files
```

S means substitute. Old is the string that will be replaced. New is the string that will be substituted. Files are the files that will be renamed. 

The following are refinements:

Change only at beginning of name: 's/^old/new/'
Change only at end of name: 's/old$/new/'
Change all instances of old: 's/old/new/g'

Have a look at the following page which provides additional detail:

[http://tips.webdesign10.com/how-to-bulk-rename-files-in-linux-in-the-terminal](http://tips.webdesign10.com/how-to-bulk-rename-files-in-linux-in-the-terminal)

---

### Post by pikabuntu on 2009-02-04
> **kaibob said:**
> This will add the flv extension to all files in the current directory:

```
rename -n 's/$/.flv/' *
```

Thanks sooo much! That's exactly what I needed.

---

### Post by pikabuntu on 2009-02-04
Hold on... How could I use this to rename only the files with no extension and not have it rename directories?

---

### Post by kaibob on 2009-02-04
There is probably an easier way to do this but the following works:

```
find /directory/name -maxdepth 1 -type f -exec rename -n 's/$/.flv/' '{}' ';'
```

You have to change /directory/name. You can read about the find command at:

[http://content.hccfl.edu/pollock/Unix/FindCmd.htm](http://content.hccfl.edu/pollock/Unix/FindCmd.htm)

---

