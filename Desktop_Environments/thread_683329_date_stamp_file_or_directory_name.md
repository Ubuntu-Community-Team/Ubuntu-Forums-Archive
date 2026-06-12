---
title: "date stamp file or directory name"
date: 2008-01-30
forum: Desktop Environments
---

### Post by dgermann on 2008-01-30
Hi--

How can this be done?

I want to set up a script to copy files and directory structures and have the new files or at least the directories named with a date and time stamp in the file/directory name itself.

I have a crontab file which does something similar by creating an hourly10.tgz file and an hourly11.tgz file, etc., but I do not know how to do this with whole directories, so that it automatically adds time and date.

The script file for creating those files says: 
```
set $(date)
  filename="/backups2/hourly`date +'%H'`.tgz"

```
But I do not know how to read what it is doing, nor even what to search for to find the right syntax.

I think what I need it to do is to use the cp command with something like what is in that script. I see that doing "date --help" produces a list of these things--am I in the correct area?

Can anybody point me in the right direction?

Many thanks!q

---

### Post by kidders on 2008-02-01
Hi there,

If you were to copy dir1, which of these would you like to have happen to it?

```
dir1
  |
  +- file1
  +- file2
  +- dir2
      |
      +- file3
      +- file4
```Suggestion 1...```
dir1-20080201
  |
  +- file1
  +- file2
  +- dir2
      |
      +- file3
      +- file4
```Suggestion 2...```
dir1-20080201
  |
  +- file1-20080201
  +- file2-20080201
  +- dir2-20080201
      |
      +- file3-20080201
      +- file4-20080201
```

Hopefully my little ASCII pictures turn out okay on your end hehe. Basically, I'm not clear on whether you just want top level directories to get a new name, or want to descend into directories & datestamp *everything* you copy.

One is trivial ... the other is a little more complex ... but both can be done.

---

### Post by dgermann on 2008-02-01
kidders--

Thanks!

Yes the pix turned out brilliantly!

Suggestion 1 with just the first level directory renamed is acceptable, I think, but suggestion 2 is better.

If you can say how to do each, that would give me some flexibility if one does not fulfill my needs.... :)

Thanks kidders!

---

### Post by kidders on 2008-02-02
Hey again,

The first one is the easy one ...```
cp -dpR "dir1/" "dir1-`date +'**%Y**'`"
```That would recursively copy the contents of "dir1" to "dir1-2008". (The format of the datestamp is controlled by the "%Y" ... it can be anything you want.) The names of any files/directories inside dir1 would remain unchanged.

The second option is a bit fiddly, not least because of all the nested quoting (which I hope I've gotten right!). The way I chose to do it was to construct a list of commands to individually copy every source file to its destination...```
find dir1/ -type f -exec sh -c '
DIRNAME="/tmp/`echo $(dirname "{}") | sed "s_/\([^/]*\)_/\1-'`date +'%Y'`'_g"`";
FILENAME="`basename "{}"`-`date +'%Y'`";
**echo** mkdir -p "$DIRNAME";
**echo** cp -dp "{}" "$DIRNAME/$FILENAME"' \;
```[LIST]
[*]**find dir1/ -type f -exec sh -c** - Searches "dir1" for files (as opposed to directories, etc.), and spawns new shells for each one.
[*]** DIRNAME=...** - Performs a substitution to append the date to each part of the destination directory name. Basically, "dir1/dir2/dir3" becomes "dir1-2008/dir2-2008/dir3-2008". The modified path is preceded by "/tmp/", which is the place you want your files to be copied to (and can, of course, be anything you want).
[*]**FILENAME=...** - Constructs a new name for each copied file, by sticking the date on the end.
[*]** echo mkdir** - Ensures the target directories exist.
[*]** echo cp** - Copies the source files to the target directories.[/LIST]Not quite as straightforward ... but doable. You might notice the extra 'echo's in "echo mkdir" and "echo cp". These prevent the command actually doing anything, and make it spit out what it *would* do, instead. Because the damn thing is so complicated, I thought a dry run would be smart ... to actually perform the copy, change "echo mkdir" to "mkdir", and "echo cp" to "cp".

Just like the simplier first suggestion, you can write the second one all on one line, if you want to ... I just broke it up to make it easier to read. In both cases, be careful to match my quoting _precisely_.

---

### Post by dgermann on 2008-02-02
kidders--

Fantastic! And there is progress to report.

Here is the script file I made based upon what you suggested:
```
#!/bin/sh

#cp -av "/sam/doug2/" "/media/sdb1/backups/two/doug2-`date +'%Y%m%d%H%M'`"


find /sam/doug2/ -type f -exec sh -c '
DIRNAME="/media/sdb1/backups/two/`echo $(dirname "{}") | sed "s_/\([^/]*\)_/\1-'`date +'%Y%m%d%H%M'`'_g"`";
FILENAME="`/sam/doug2/ "{}"`-`date +'%Y%m%d%H%M'`";
mkdir -p "$DIRNAME";
cp -dpv "{}" "$DIRNAME/$FILENAME"' \;


```

The first command, currently commented out, worked fine to create the main directory name that I was looking for. Thank you!

Emboldened by that success, I tested the second one. Using your echo trick, I could see no errors, so I removed echo from each place it appeared (3 places). That did not produce the correct main file name--it just had the date and time stamp with a dash in front of it. So I put back the first echo. That gave me a whole bunch of these:

```
doug@doug2:/media/sdb1/backups$ sudo ./dirn
sh: /sam/doug2/: Permission denied
`/sam/doug2/dl-2007/wordpress-2.2.2.tar.gz' -> `/media/sdb1/backups/two//sam-200802021717/doug2-200802021717/dl-2007-200802021717/-200802021717'
sh: /sam/doug2/: Permission denied
`/sam/doug2/dl-2007/OOoPassword1-0.zip' -> `/media/sdb1/backups/two//sam-200802021717/doug2-200802021717/dl-2007-200802021717/-200802021717'

```

It did seem to be making a series of directories with the date and time stamp as I expected, and then it saved, or tried to save the first actual file with "-200802021717", that is, only the date and time stamp with a dash in front.

I notice a whole bunch of double forward slashes in the output--is that telling us anything? I do not understand all the slashes and backslashes in the command you gave, so perhaps there is an extra?

---

### Post by kidders on 2008-02-03
> **dgermann said:**
> I removed echo from each place it appeared (3 places).Only remove the two I mentioned in my last post. If you remove all three, the datestamp substitution (performed by "sed") will screw up.

> **dgermann said:**
> I do not understand all the slashes and backslashes in the command you gaveBackslashes are used to escape things (ie strip special meanings they might otherwise have. Compare...```
$ echo "Price: $1"
Price: 
$ echo "Price: \$1"
Price: $1
```...or...```
$ ls My Documents
ls: cannot access My: No such file or directory
ls: cannot access Documents: No such file or directory
$ ls My\ Documents
...
...
```Forwardslashes are path separators, similar to '\' in Windows.

It's also worth noting that including a path in...```
FILENAME="`/sam/doug2/ "{}"`-`date +'%Y%m%d%H%M'`";
```...is not a good idea. It'll probably cause lots of errors. In the command I posted originally, the source directory name (dir1/) is defined in line 1, and the destination (/tmp/) in line 2. You should change those to meet your needs.

---

### Post by dgermann on 2008-02-03
kidders--

As advertised! You are a wonder worker!

You are really a top rate teacher! Thank you for helping me to understand better!

Yes, I put the third echo back in, before I posted to you in # 5.

I replaced "basename" into the "FILENAME" line like you said, and it worked as I wanted! Great!

Now why did it work? I don't see any definition of "basename" in the script you came up with....

Thank you, thank you, thank you, kidders! :popcorn::KS

---

### Post by kidders on 2008-02-04
> **dgermann said:**
> You are a wonder worker!Lol ... not quite!

"basename" lives in /bin or /usr/bin ... it turns "/home/dgermann/file.txt" into "file.txt". The other commands I used are...
[LIST]
[*]**find** - Searches for files.
[*]**sh** - A shell (like bash).
[*]**echo** - Parrots things back to you.
[*]**dirname** - Like basename, except it extracts directory paths.
[*]**sed** - A stream editor.
[*]**date** - You know that one!
[*]**mkdir** - Makes directories.
[*]**cp** - You know that one too.[/LIST]... just in case you weren't aware of some of them. They're all part of the base Linux system, and have man pages, in case you need more info.

"Why did it work" is a bit long-winded. Briefly, "find" searches "dir1/" for things of type 'f' (files), and executes "sh" once for each result. From that point forward, "{}" takes the place of the discovered file's relative path.

Then, much as you might do **http_proxy="whatever" apt-get update** to set an environment variable for a command you want to run, I defined "DIRNAME" and "FILENAME", the target path and filename for the discovered source file. Defining those two variables makes the last two lines easier to read.

I hope that helps.

---

### Post by dgermann on 2008-02-06
kidders--

Wow! So much I did not know! Like an author I read a couple days ago said: It feels like chopping down a forest from the inside out--once I clear this circle of trees, there is an even larger ring of trees just outside that, and beyond that is.... 

For instance I did not know that basename nor dirname existed, and just tonight for the first time (I have been using linux since 2003) I did man bash and man glob and can see the second row of trees!

Thank you very much for your help, kidders! You have made my experience much more useful.

---

### Post by kidders on 2008-02-07
No problem. :-)

---

