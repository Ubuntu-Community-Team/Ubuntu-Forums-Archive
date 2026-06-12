---
title: "Help with file sorting"
date: 2009-04-10
forum: General Help
---

### Post by lazychris2000 on 2009-04-10
I am hoping that someone will be able to give me a hand with a problem that I am running into.  I have been using Ubuntu for years and I consider myself to be pretty proficient as a user, but coding is not at all my strong point.  In my work, I do a fair number of data recoveries using photorec, which for those who do not know, leave you with tens of thousands of folders labeled recup_dir.xxxxx.  I found a quick little script on the internet (I can no longer remember from where) and modified it a little to sort the files. This may not be the most efficient method of doing it, but it gets the job done.  Recently, I have noticed that every time I sort files from a recovery, there are several file types that I have missed.  Then I have to go back into the scripts and add them, then run them all over again.  This becomes pretty time consuming after I re-edit and rerun each script several times.  I am also trying to find a way to limit each folder to 25000 files a piece.  This helps when you open the folder to see if any of the data is useful and your file explorer has to catalog 200000+ files.
Currently, I have a few scripts for each kind of file (sort-docs, sort-music, sort-video, etc, etc) which repeats this basic command for each file type:
```

cd photorec
mkdir Music
mkdir Music/mp3
for i in `ls`;do
	for j in `ls $i/*.mp3`; do
		mv -v $j "Music/mp3"
	done
done

```

What I am trying to do is this: have a single script that will do something like the following made-up scripting language:
```

1 n=0
2 d=0
3 mkdir <fileextension>.d
4 while n<25000, do
5    for i in `ls`;do
6        for j in `ls $i/*.mp3`; do
7             mv -v *.<fileextension> <fileextension>.d
8             n=n+1
9        done
10   done
11 when n=25000, do
12    n=0
13    d=d+1
14   goto 3

```

As you can see, I have a very, very basic knowledge of programming, but hopefully someone understands what I am talking about.  I dont really know what would go into this, maybe there is a way for it to read a file, set <fileextension> to whatever is after the . then start moving it. The data being recovered is from windows machines, so almost all of the files have a file extension...the ones that dont could be thrown into their own folder or something.
Im not looking for anything terribly fancy and Im not asking someone to dedicate a large amount of time to this, I'm just trying to get something that works so it will save me alot of time and aggravation.  Any help would be greatly appreciated!

---

### Post by lavinog on 2009-04-10
Fun stuff. My drive crashed last week, unfortunately it looks like the onboard circuitry is the issue.

You may find that the **find** command should do everything for you.

this code:
```

for i in `ls`;do
	for j in `ls $i/*.mp3`; do
		mv -v $j "Music/mp3"
	done
done

```
can be replaced with
```

find ./ -iname "*.mp3" -exec mv -v {} Music/mp3 \;

```
./ is the root folder to search from
the \; is required

---

### Post by soltanis on 2009-04-10
Let me see if I can stamp out a perl script to your specs.

Wait, no, that won't work.

---

### Post by lavinog on 2009-04-10
```

#!/bin/bash

for d in recup_dir.*
do

 for f in ${d}/*
 do

  bf=$(basename "$f")

  ext=$(echo $bf|cut -d '.' -f 2)

  sortpath="sorted/"$ext
  [[ -d $sortpath ]]||mkdir -p $sortpath

  cp -v $f $sortpath
  #mv -v $f $sortpath
 done
done

```
It will copy every file to ./sorted/<extention>
if you want it to move the file put a # in front of cp and remove the one infront of mv

Note: this will only be useful for the files that photorec creates, it wont handle filenames like *file.with.more.period.txt* nor will it be able to handle spaces in the file names.

---

### Post by ghostdog74 on 2009-04-10
> **lavinog said:**
> ```

  bf=$(basename "$f")

```

no need to call basename. 
```

bf=${f##*/}

```

> 
```

  ext=$(echo $bf|cut -d '.' -f 2)

```


no need to call external cut.
```

ext=${bf##*.}

```

---

### Post by lavinog on 2009-04-10
> **ghostdog74 said:**
> no need to call basename. 
```

bf=${f##*/}

```

no need to call external cut.
```

ext=${bf##*.}

```

Hey thanks, thats good to know...I use the {%.ext} and knew about the #, but never knew you can use the * with it.

---

