---
title: "bash script that moves all jpg files into one dir"
date: 2005-12-25
forum: General Help
---

### Post by gert cuykens on 2005-12-25
this gives me the files i need

gert@F53:~$ ls -all recup_dir.* | grep .jpg

now how do i move the files in one folder ?

ps we are talking about allot of jpg files :)

---

### Post by Sutekh on 2005-12-26
Wouldn't this work?
```
cd <folder_with_jpgs>
cp *.jpg <destination_folder>
```

---

### Post by &#1055;&#1054;&#1055;&#1058;&#1054;&#1053;&#1046; on 2005-12-26
What happens when 100 of them have the same filename? 

Oh well.. here ya go.

for ALL in `find jpg recup_dir.*`;do mv ${ALL} ${ALL##*/};done

You might want to replace mv with cp until you're sure it's what you want to do...

---

### Post by gert cuykens on 2005-12-26
[QUOTE=Sutekh]Wouldn't this work?
```
cd <folder_with_jpgs>
cp *.jpg <destination_folder>
```[/QUOTE]

no because we are talking about 214 folders containing 106885 files of recoverd data

example:

recup_dir.156
recup_dir.157
recup_dir.158
recup_dir.159

---

### Post by gert cuykens on 2005-12-26
> **&#1055 said:**
> What happens when 100 of them have the same filename? 

Oh well.. here ya go.

for ALL in `find jpg recup_dir.*`;do mv ${ALL} ${ALL##*/};done

You might want to replace mv with cp until you're sure it's what you want to do...

no they all have different filenames numbert from 1 to 106885 divided into seperate recup_dir.* folders 

I canot cp them because of the size hd to small

---

### Post by gert cuykens on 2005-12-26
So i asume this would be a solution ?
Please confirm ?

for ALL in 'find recup_dir.* -name *.jpg';do mv ${ALL} very_big_jpg_folder;done

---

### Post by gert cuykens on 2005-12-26
gert@F53:~$ for ALL in 'find t* -name *.jpg';do mv -u ${ALL} bigj/;done
mv: invalid option -- n
Try `mv --help' for more information.
gert@F53:~$

i made a few test folders and jpgs but it doesnt work ?

---

### Post by oscartheduck on 2005-12-26
I don't have the syntax with me yet, but the easiest route looks like using xargs to do a mv in batches of twenty or so jpgs.

Are you wanting to preserve the directory structure? Or just move all the jpegs into one huge directory?

---

### Post by gert cuykens on 2005-12-26
one huge directory so i can scroll trough it to find the needle in the haystack :)

---

### Post by lcg on 2005-12-26
[QUOTE=gert cuykens]this gives me the files i need

gert@F53:~$ ls -all recup_dir.* | grep .jpg

now how do i move the files in one folder ?[/QUOTE]
'find' should do the trick:

```
find -name '*.jpg' -exec mv -i {} /target/dir \;
```

This command moves all *.jpg in a directory or anywhere in a subdirectory to the target directory, asking for confirmation if any filename exists twice or more. If there are other JPGs you don't want to move, just make sure you move all the recup_dir.* to an empty folder first and 'cd' to that folder before running the 'find' command.

HTH,
Lars

---

### Post by gert cuykens on 2005-12-26
thx it worked

Wondering how long it going to take for gnome to create tumbnails of 20 gb of jpegs lol :)

---

