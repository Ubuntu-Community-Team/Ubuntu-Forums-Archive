---
title: "Recursively cut and paste files in subdir to &quot;root&quot;"
date: 2006-02-02
forum: Desktop Environments
---

### Post by mschievano on 2006-02-02
Hello,
i've a dir whit other 200 dir inside.
On every dir there're about 20 files.
Q: Are there ways to cut and paste every 20 files in this dir without enering every dir and do it "by hand"?

---

### Post by vruum on 2006-02-02
Not totally sure what you're trying to do, but it sounds like it could be done in nautilus, just run gsudo nautilus, an move the top dir, subdirs should follow

---

### Post by mschievano on 2006-02-02
i have to cut all files from the 200 subdir (every subdir contains 20 files) and paste all in "father" dir

---

### Post by audax321 on 2006-02-02
You need to write a script... Something like this should do it:

```

#!/bin/sh

# Copy files out of sub-directories in source folder to destination folder

source="ENTER_SOURCE_DIRECTORY_HERE"
destination="ENTER_DESTINATION_DIRECTORY_HERE"

for directory in "$source"/*
do
	if [ -d "$directory" ]; then
		cp "$directory"/* "$destination"
	fi
done


```

Now, if you don't have write permissions to the destination folder, this script needs to be run as root. Also, this does no checking to see if filenames conflict.. you can set up some options for backups, etc by modifying the cp command (see cp --help OR man cp).  Also if you want to move the files change cp to mv... BUT that is probably not a good idea if you want to make sure the move went right... I would use cp, check if the files have all copied, and then just delete the sub-directories by hand.

---

### Post by vruum on 2006-02-02
oh, sorry bout that then, I think I get it now, you want all the files that are now in seperate folders, in the same folder? (if thats not what you want just ignore me) the way I would do that would be: 
```
sudo cp -v /$topdir/*/* /$destinationdir/
```
assuming that non of the files are hidden, you could use "mv" instead of "cp" but this way, if anything goes wrong, you can try again, if everything works out, then just delete the old dirs.

---

### Post by audax321 on 2006-02-02
Ahhh, yeah.. vruum's method is easier and much more direct than my script. As you can see I really like my scripts... the one reason I can't move to KDE is because I love the scripts menu in Nautilus :)


<raises hand> hi my name is audax321 and I'm a script junkie :(

---

### Post by mschievano on 2006-02-04
thanks to all.
Do you think that the script work in a situation near like this?

Top dir= /media/hdb2/img

Subdir = alk, saf, sfw, rrw, aq, rwe , .... -> till 200 subdir

and whit subdir nested on top dir in this way
/media/hdb2/img/alk
/media/hdb2/img/saf
....

thanks again

---

### Post by audax321 on 2006-02-05
It should, but vruum's method does the same thing minus the complicated script in one line. All the script does is loop through all the items in the source directory and determine if the item is a directory and then copy all the contents of that directory to a destination directory. When its done copying it goes to the next item in the loop and does it with that.

Vruum's command is doing the same thing but the cp command is handling everything.

For example to adapt the command to your case you would use:


sudo cp -v /media/hb2/img/*/* /destination_folder_somewhere
(but I wouldn't use sudo unless you don't have write access to the destination folder).

---

### Post by mschievano on 2006-02-05
mschievano@uainex:~$ cp -v /media/hdb2/backgrounds/img/*/* /media/hdb2/backgrounds/img
bash: /bin/cp: Lista degli argomenti troppo lunga

It say that the command is too long!

also if i substitute cp with mv, and also if symlink the directory to pass a shorter line (and also changing the destination dir)

---

### Post by vruum on 2006-02-05
hmm, it seems that the core-utils has a limit on the amount of memory they can use in a single command. [see this]("http://www.gnu.org/software/fileutils/doc/faq/#Argument%20list%20too%20long"). As far as I can tell Audax321's script should still work though. so if you haven't already, try that.
EDIT: [this]("http://www.linuxjournal.com/article/6060") might also be interesting

---

### Post by mschievano on 2006-02-06
Done!

in this way:

```

#!/bin/sh

# Copy files out of sub-directories in source folder to destination folder
SOURCE="/media/hdb2/backgrounds/img"
DEST="/media/hdb2/backgrounds/imgnews"

for i in $SOURCE/*; do
     [ -d $i ] && cp -v $i/* $DEST/
done

```

---

