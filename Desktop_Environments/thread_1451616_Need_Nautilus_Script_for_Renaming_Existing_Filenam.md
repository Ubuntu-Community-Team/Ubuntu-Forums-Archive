---
title: "Need Nautilus Script for Renaming Existing Filenames"
date: 2010-04-10
forum: Desktop Environments
---

### Post by BadServo on 2010-04-10
I'm hoping someone can point me in the right direction on this as I'm not that great at scripting.

One of the features that I liked from Vista/Win7 is that when you move a set of files into another folder that already contains different but identically named files, you are given the option of leaving the source files where they are, replacing the existing files with the source files or moving the files anyway, but renaming the source files so that their filenames do not clash with the existing ones.  This is achieved by adding a (1), (2), etc to the end of the existing filename.

Since I often merge folders with large numbers of similarly named files, this was a very useful feature.  Sadly, Nautilus has no such option, it's either skip or cancel.

Instead, I thought of this scenario:

Attempt the move operation, when asked about a conflicting file, simply skip it.  Nautilus moves the non-conflicting files.  At this point, I'd like to use a Nautilus script on the conflicting files that would simply append an "a" to the end of the files.  If the file already ends with an "a", I'd like it to append a "b" instead, and so on.  I could then copy these newly named files.

Alternatively, if that is impossible to achieve, have it simply add an "a" to the end of the filename regardless.

Sadly, I have no idea where to begin to write such a script.  Any insight would be greatly appreciated.

---

### Post by new_tolinux on 2010-04-10
I don't know about Nautilus, but I do know a way in the terminal
```

cd /path/to/folder
mv * *\ (1)
```where "/path/to/folder" the "source"-folder is. The second command will put [space](1) after every filename.
You might run in trouble there, since the * mask includes the extension (e.g. everything after the dot).
Using *.* (and *.*\ (1)) instead of * will solve that problem, but won't work for files without an extension.
The \ before the space is to escape the space. If you don't put a \ in front of a space, Linux will think you're providing the next option for the command.

Edit: never mind..... I just read your joindate :oops:

---

### Post by BadServo on 2010-04-10
Thanks for the reply.  Although I must be doing something incorrectly.  The command:


```
mv * *\ (1)
```

Give me the error:

```
bash: syntax error near unexpected token `('
```

---

### Post by new_tolinux on 2010-04-10
> **BadServo said:**
> Thanks for the reply.  Although I must be doing something incorrectly.  The command:


```
mv * *\ (1)
```Give me the error:

```
bash: syntax error near unexpected token `('
```
I wrote that without testing.

I think I found some solution [here]("http://www.24hourapps.com/2009/03/linux-tips-10-rename-multiple-files.html")

The command I tested to rename "all" files to "all (1)" is:
```
for f in *; do mv "${f}" "${f} (1)"; done;[code]
which renamed
[code]test.a
test.b
test.c
```into
```
test.a (1)
test.b (1)
test.c (1)
```This is another page I found: [http://aplawrence.com/Linux/rename.html](http://aplawrence.com/Linux/rename.html)

Edit:
I wonder why something that was so simple (even in MS-DOS) is so unsuccesful implemented in Linux.

---

### Post by bear24rw on 2010-04-10
> **BadServo said:**
> Thanks for the reply.  Although I must be doing something incorrectly.  The command:


```
mv * *\ (1)
```

Give me the error:

```
bash: syntax error near unexpected token `('
```

try

```
mv * *\ \(1\)
```

i think  you need to escape the ()

---

### Post by new_tolinux on 2010-04-10
> **bear24rw said:**
> try

```
mv * *\ \(1\)
```i think  you need to escape the ()
Doesn't work, tested that one before my previous message.

With 1 file it renames the file to "* (1)" instead of "theoldfilename (1)"
With more files it produces an error like
```
mv: target `* (1)' is not a folder
```
(I'm not using the English version of Ubuntu)

---

### Post by 2hot6ft2 on 2010-04-10
Since I have krename and krusader installed. I would just synchronize the folders in one or both directions with krusader and make name changes on the fly if the same name existed and the files were not =.

I always hated windows doing just what you're missing. What you considered a feature I considered a flaw.

---

### Post by new_tolinux on 2010-04-10
> **2hot6ft2 said:**
> Since I have krename and krusader installed. I would just synchronize the folders in one or both directions with krusader and make name changes on the fly if the same name existed and the files were not =.

I always hated windows doing just what you're missing. What you considered a feature I considered a flaw.
I consider it a basic to have a simple command like "rename *.some *add.some", which renames anyfile.some to anyfileadd.some. Lack of this I consider a major flaw.

I consider it a feature if it gives you the option (while moving) to rename the "moving" file if the filename is already present, or rename the "present" file if the "moving" file has the same name.
That said, Windows doesn't present the option to rename the "moved" file. Therefore I moved to some Norton Commander-alike tool long time ago. Maybe there's something like that for Linux too.

---

### Post by kaibob on 2010-04-10
This is not exactly what the OP requested, but the cp and mv commands have a backup option that appends a number in the format of ~1~ to any file that already exists. For example,

```
cp --backup=numbered *.txt /home/kaibob/documents
```

Unfortunately, the duplicate renamed files are hidden due to the ~ at the end of their file name. You can remove the ~ by use of the rename command:

```
rename -n 's/~//g' *~
```

The -n option does a dry run and reports proposed changed. Substitute -v for -n to actually rename the files. Anyways, a bit of a kludge but does work. 

I don't know of a way to write a Nautilus script that will do what the OP wants in the manner he specifies. You could write a Nautilus script that does it all--copy where there are no duplicates and copy and rename where there are duplicates.

---

### Post by 2hot6ft2 on 2010-04-10
> **new_tolinux said:**
> Therefore I moved to some Norton Commander-alike tool long time ago. Maybe there's something like that for Linux too.
](*,)](*,)](*,)](*,)](*,)](*,)Yes and it's called krusader, like I said.
> Krusader is a simple, easy, powerful, twin-panel (commander-style) file
manager, similar to Midnight Commander (C) or Total Commander (C).

It provides all the file management features you could possibly want.

Plus: extensive archive handling, mounted filesystem support, FTP,
advanced search module, viewer/editor, directory synchronisation,
file content comparisons, powerful batch renaming and much more.

It supports archive formats: ace, arj, bzip2, deb, iso, lha, rar, rpm, tar,
zip and 7-zip.

It handles KIOSlaves such as smb:// or fish://.

Almost completely customizable, Krusader is very user friendly, fast and looks
great on your desktop.

But have it your way. I was trying to help.
):P

---

### Post by BadServo on 2010-04-10
Thanks for the input, 2hot6ft2.

I am unfamiliar with krusader.  Although as a gnome user I generally don't fool with many KDE-centric apps (amarok is the exception).  Also, I've tended to avoid 3rd part file managers as there's new perfect way to integrate them into the shell (i.e. open desktop folders etc).  Otherwise, I'd likely have switched to dolphin for most day to day usage.  I'd personally also disagree with the opinion that it's an undesirable feature under Windows.  I'd always rather have the option.  Nontheless, I'll give krusader a go.

And kaibob, that's not a bad idea.  It's a lil "around your elbow", but one can't argue with success.  May experiment with that and see if I can make those command work as a Nautilus script.

I'm a lil surprised this is proving to be as challenging as it appears.  I know this could prolly be done easily enough in python, but that's way outtuv my depth.

Thanks again for the input, gents.  Any other insight is welcome.

---

### Post by new_tolinux on 2010-04-11
> **2hot6ft2 said:**
> ](*,)](*,)](*,)](*,)](*,)](*,)Yes and it's called krusader, like I said.

But have it your way. I was trying to help.
):P
I was talking about using a NC-clone I use in Windows. Not linux. ;)
But krusader is a nice hint for what I read, thanks anyway.

---

### Post by overlordchin on 2010-04-13
Ok you wanted it in bash form for your nautilus script. Here is exactly what you were asking for. You can add file extensions into the regex as you see fit. There is probably a way to make the ext case insensitive so the regex comparison doesnt get unweildly. Note that if you run this subsequent times on the same file it will add an additional ".a." before the extension so a text file would end up as sometext.a.a.txt. To me this makes more sense than changing the a to a b and so on down the line (It is a lot less code). Hope it helps you out champ


```

#!/bin/bash
for thing in "$@"
do
   substring=${thing}
   # push out the current file value to a temp file for searching
   echo $substring > listoffiles
   # compare file against regex to only change the ext and not every "."
   # note that the $& usually denotes $(regexmatch) but in this case it is just "&"
   sed "s/\.[(jpg|JPG|gif|GIF|doc|DOC|pdf|PDF|txt|TXT|avi|AVI)]/\.a&/g" listoffiles > temp.txt
   for file in `cat temp.txt`
   do
      # do the actual renaming here
      mv $substring $file
   done
done

# clean up temp files used in rename
rm listoffiles temp.txt


```

---

### Post by BadServo on 2010-04-13
A couple modifications and this should be jsut what the doctor ordered.

Cheers!

---

### Post by bmfc187 on 2011-11-26
> **BadServo said:**
> A couple modifications and this should be jsut what the doctor ordered.

Cheers!

hi i just came across this script and for some reason it didnt work for me.  could i trouble you for your modified files?  i am trying to get this to work, i hate not having this functionality!  any insight would be appreciated.
running ubuntu lucid.

---

### Post by BadServo on 2011-11-29
Sorry to say it, but this approach also failed to meet my needs.  I ultimately had to use 3rd party tools under windows to complete my sorting.

---

