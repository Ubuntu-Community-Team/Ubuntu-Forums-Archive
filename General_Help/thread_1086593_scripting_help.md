---
title: "scripting help"
date: 2009-03-04
forum: General Help
---

### Post by porchrat on 2009-03-04
I've made a script that locates files of type 'data' (when the file command is used on them) from a directory recursively, and places the filepath in a log file (which I need).

How could I get the script to hand that log file line by line to 'rm' to remove those files?

```
find /foo -type f -name "example_string" -exec file '{}' > ~/Desktop/list.txt \;

grep ": data" ~/Desktop/list.txt > binlist.txt

sed 's/: data//g' binfilelist.txt > binlist2.txt
```

I've looked into using 'while read' and it looks like that will do what I need, but I can't find a tutorial that can adequately explain the basics of this function. Could anyone provide an example of how this would work or perhaps a guide to understanding this function?

---

### Post by Chandler258 on 2009-03-04
Hi,

if you type your command in ` quotes it executes first.

Example:

```
dude@ferdo:~/ls
nekiXorg.txt  nvidiaCrap.txt  xorg.conf.new

```

```
dude@ferdo:~/rm `ls *.txt`
dude@ferdo:~/temp$ ls
xorg.conf.new

```

On my QWERTZ keybord I have to press altgr+7 to get that char.

Hope this helps.

---

### Post by porchrat on 2009-03-04
> **Chandler258 said:**
> Hi,

if you type your command in ` quotes it executes first.

Example:

```
dude@ferdo:~/ls
nekiXorg.txt  nvidiaCrap.txt  xorg.conf.new

```

```
dude@ferdo:~/rm `ls *.txt`
dude@ferdo:~/temp$ ls
xorg.conf.new

```

On my QWERTZ keybord I have to press altgr+7 to get that char.

Hope this helps.

You misunderstand.  I don't want to remove the log file, I want to read the contents of that log file line by line and hand each line to the 'rm' command in order to remove each file in that log.

This is what I have come up with so far:

```
find /foo -type f -name "example_string" -exec file '{}' > ~/Desktop/filelist.txt \;

grep ": data" ~/Desktop/list.txt > binlist.txt

sed 's/: data//g' binlist.txt > binlist2.txt

cat binlist2.txt | while read line
	do rm $line
done
```

I will test it and see what happens.

---

### Post by Chandler258 on 2009-03-04
```
rm `find /foo -type f -name "example_string"`
```

or

```
rm `cat binlist2.txt`
```

---

### Post by porchrat on 2009-03-04
OK tried my script out and it worked just fine.  And on the plus side I now understand a little more about the 'while' loop in bash.

> **Chandler258 said:**
> ```
rm `find /foo -type f -name "example_string"`
```

or

```
rm `cat binlist2.txt`
```

Problem with the first one is that I can only remove files with filetype 'data', meaning i need the "-exec file '{}' " part, otherwise I would've just done that.

I must admit I hadn't thought about the second option.  That is a lot simpler than the 'while' loop, but now that I've done it I'm too impressed to ruin it.  I hadn't considered that 'rm' can handle more than one argument at a time.  However there are over 3000 files in that log file and I doubt it could handle that sort of scale, at least with the 'while' loop it doesn't matter how large that log file becomes (sizes will vary) as rm will only need to handle one file for each loop.

Thanks Chandler258, I am once again blown away by the rapid responses and willingness to help of our forumites

---

### Post by vanadium on 2009-03-04
Chandler did properly understand your question. The issue with the approach suggested is that it will not work if there are too many files: you might exceed the allowed command length.

This problem can be solved simply by running the same find command with "-exec rm '{}', though.

You can also combine -exec options in one find command, which would work here as well:

[edit]This solution is not correct as it would delete all found files, not only these that are identified as "data" by the "file" command.
```

find /foo -type f -name "example_string" -exec file '{}' \; -exec rm '{}' \;  > ~/Desktop/filelist.txt

```

---

### Post by heindsight on 2009-03-04
> **porchrat said:**
> You misunderstand.  I don't want to remove the log file, I want to read the contents of that log file line by line and hand each line to the 'rm' command in order to remove each file in that log.

This is what I have come up with so far:

```
find /foo -type f -name "example_string" -exec file '{}' > ~/Desktop/filelist.txt \;

grep ": data" ~/Desktop/list.txt > binlist.txt

sed 's/: data//g' binlist.txt > binlist2.txt

cat binlist2.txt | while read line
	do rm $line
done
```

I will test it and see what happens.

It would probably be much simpler to do something like:
```

find foo -type f -name "bar" | while read name; do
    type=$(file -b $name)
    if [ "$type" = "data" ]; then
        echo $name >> filelist.txt;
        rm "$name";
    fi
done

```

---

### Post by heindsight on 2009-03-04
> **vanadium said:**
> 
```

find /foo -type f -name "example_string" -exec file '{}' \; -exec rm '{}' \;  > ~/Desktop/filelist.txt

```
But this would delete all the files with names matching "example_string", you need something a bit more complicated if you want to look at the output of **file** and decide whether to delete based on that.

---

### Post by porchrat on 2009-03-04
Hi guys I solved it no worries. Feel free to keep the suggestions coming though as I am keen to learn how others would approach this.

I hadn't considered doing it in a if statement and I really liked this one as it is less complicated:

> **heindsight said:**
> It would probably be much simpler to do something like:
```

find foo -type f -name "bar" | while read name; do
    type=$(file -b $name)
    if [ "$type" = "data" ]; then
        echo $name >> filelist.txt;
        rm "$name";
    fi
done

```

---

### Post by vanadium on 2009-03-04
Nice approach indeed. I missed a part of the problem, for which I apologize.

---

### Post by porchrat on 2009-03-04
> **vanadium said:**
> Nice approach indeed. I missed a part of the problem, for which I apologize.

No worries, as I mentioned before it is nice to learn of new ways to use bash even if it isn't related to my particular problem.  It is all interesting and important. Thank you for your input :D

---

