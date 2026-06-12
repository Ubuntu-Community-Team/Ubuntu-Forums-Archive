---
title: "copying a list of files"
date: 2009-05-16
forum: General Help
---

### Post by synthesist on 2009-05-16
I'm doing some maintenance on my dad's Ubuntu box and he seems to have made a huge mess of the files he has. 

He has split his files into two folders. 
/media/KINGSTON_ is his backup folder.
/home/alex/ is his home folder on the machine.

everything that exists in /media/KINGSTON_ also exists in /home/alex/. /home/alex/ has some files which do not exist in /media/KINGSTON_.

I ran the following command to compare the two folders and output to a file what exists only in folder2:
```
diff /home/alex/ /media/KINGSTON_ | grep "Only in /home/alex/: >> /home/alex/Desktop/diff.txt"

```

I removed the "Only in .." part of every file from the list. I also removed all the directories that start with . from the list.

I now have a list of files and directories which i need to copy to /media/KINGSTON_

**_My problem is_**:
I try to run:
```
for i in `cat /home/alex/Desktop/diff.txt`; do cp $i /media/KINGSTON_; done

```

It gives me:
```
cp: cannot stat `What': No such file or directory
cp: cannot stat `are': No such file or directory
cp: cannot stat `(Main).doc': No such file or directory
```

**It also seems to be omitting directories, which I also need copied.**

---

### Post by FIONEX on 2009-05-16
Try messing around with something like this

cp `cat diff.txt` /media/Kingston_"

If you also want directories and their contents to be copied, then do "cp -r".  This tells it to do a recursive copy, which goes into each subdirectory and copy the files under it.

---

### Post by synthesist on 2009-05-16
Same result. It splits up filenames with spaces and thinks they're different files.

---

### Post by FIONEX on 2009-05-16
I would do this in perl if I was you.  Maybe a language you're more comfortable with.


Run this first:
sudo apt-get install libfile-copy-recursive-perl


Create a file called copyover.sh using gedit and paste this in it:
```

#!/usr/bin/perl -w

use File::Copy::Recursive qw(fcopy rcopy dircopy fmove rmove dirmove);

while (<STDIN>){
	chomp;
	print "Copied over: " . $_ . "\n";
	rcopy("/home/alex/" . $_, "/media/Kingston_");
}

```
Save it.  Then use the terminal and do this:
chmod +x copyover.sh


Then run the command like this:
cat test | ./copyover.pl

---

