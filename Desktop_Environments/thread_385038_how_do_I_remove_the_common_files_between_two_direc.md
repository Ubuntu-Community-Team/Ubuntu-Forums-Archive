---
title: "how do I remove the common files between two directories?"
date: 2007-03-15
forum: Desktop Environments
---

### Post by pmark on 2007-03-15
I have two directories: *dir1* and *dir2*. *dir2* contains all that *dir1* contains but has some additional files. I want to delete the common files between the two and keep only the additional ones. It would be really nice to have MD5 confirmation (to see whether two files are indeed identical), but it's not necessary. I have tried with rsync but I to no avail.

I can phrase the same problem in a different way:

I have three directories: *dir1*, *dir2*, and *dir3*. *dir1* and *dir2* share some common files. *dir3* is empty. I want to find which files are **not** common between *dir1* and *dir2* and place them in *dir3*.

In fact, the second approach is more convinent, but both will satisfy my needs at this point.

It is really important, so any help or hint would be great!

---

### Post by ComplexNumber on 2007-03-15
there's probbaly an application that will allow you to do that easily, but the ony way i can think of is to briefly use the commandline. here are the stages you would perform.

1) get a list of those files found in dir1 and send them to a text file. to do this, fire up the terminal ad go to dir1 and execute the command:
**find > ~/Dir1_list.txt**
then sort them into alphabetical order with:
**sort Dir1_list.txt**

2) do the same for dir2, but send them to a text file called Dir2_list.txt

3) use an application called meld(you can download it via synaptic or via apt-get) to compare the 2 text files to see the differences. those differences will be the files that are not common to both directories. just remove those files and place them in dir3,  and then delete the others because the others will be common files.


NOTE: without any parameters, the 'find' command will simply list all those files in the current directory. 'meld' is a GUI application to find the differences between 2 or 3 files.
EDIT2: there's an application called gnome-commander which may do what you want to do more effortlessly and in a GUI.

---

### Post by Dritzen on 2007-03-15
No need to download anything extra, you can just run diff

diff file1 file2

This will show the differences between file1 and file2.

---

### Post by ComplexNumber on 2007-03-15
> **Dritzen said:**
> No need to download anything extra, you can just run diff

diff file1 file2

This will show the differences between file1 and file2.
yes, but meld is a useful tool to have lying around. so thats why i suggested that option. a lot of the time, its handy to have the differences between files  highlighted in a GUI.

---

### Post by pmark on 2007-03-15
> **Dritzen said:**
> No need to download anything extra, you can just run diff

diff file1 file2

This will show the differences between file1 and file2.

That's what I tought at first, but Meld uses a GUI and it's kind of neat.

> **ComplexNumber said:**
> there's probbaly an application that will allow you to do that easily, but the ony way i can think of is to briefly use the commandline. here are the stages you would perform.

1) get a list of those files found in dir1 and send them to a text file. to do this, fire up the terminal ad go to dir1 and execute the command:
**find > ~/Dir1_list.txt**
then sort them into alphabetical order with:
**sort Dir1_list.txt**

2) do the same for dir2, but send them to a text file called Dir2_list.txt

3) use an application called meld(you can download it via synaptic or via apt-get) to compare the 2 text files to see the differences. those differences will be the files that are not common to both directories. just remove those files and place them in dir3,  and then delete the others because the others will be common files.


NOTE: without any parameters, the 'find' command will simply list all those files in the current directory. 'meld' is a GUI application to find the differences between 2 or 3 files.
EDIT2: there's an application called gnome-commander which may do what you want to do more effortlessly and in a GUI.

I have the two lists, and I have a third list with all the non-common files. Now, what do I do next?

The list counts in thousands of files, I can't possibly edit the list by hand and make it a script by adding a "cp" or "mv" at the beginning of every new line. Is there a way to automate the process of moving/copying the files on the list?

---

### Post by misterlizard on 2007-03-15
You could give this short Tcl script a try. Paste the code into a file, save it somewhere, make it executable (chmod u+x whatever_you_call_it) and try running it. The first 2 arguments are your 2 directories and the 3rd argument is the output directory (which must already exist).

The script gets directory listings for both directories, then goes through each file and copies it to the output directory if it is NOT found in the other directory. Hope this is OK. Let us know otherwise.


```
#!/usr/bin/tclsh


if {$argc < 3} {
    puts stderr "Not enough arguments\n"
    puts stderr "Usage:\n    [file tail $argv0] <dirA> <dirB> <dirOut>"
    exit
}

set dirA [lindex $argv 0]
set dirB [lindex $argv 1]
set dirOut [lindex $argv 2]

set dirAContents [glob -tails -directory $dirA -types f *]
set dirBContents [glob -tails -directory $dirB -types f *]

foreach f $dirAContents {
    if {[lsearch -exact $dirBContents $f] == -1} {
        file copy [file join $dirA $f] $dirOut
    }
}

foreach f $dirBContents {
    if {[lsearch -exact $dirAContents $f] == -1} {
        file copy [file join $dirB $f] $dirOut
    }
}

```

Best back everything up first just in case. I've only given this a quick check, so it should work OK.

(And yes, I'm sure there are much more elegant ways to do this, probably in one line of Perl or something)

---

### Post by pmark on 2007-03-15
> **misterlizard said:**
> You could give this short Tcl script a try. Paste the code into a file, save it somewhere, make it executable (chmod u+x whatever_you_call_it) and try running it. The first 2 arguments are your 2 directories and the 3rd argument is the output directory (which must already exist).

The script gets directory listings for both directories, then goes through each file and copies it to the output directory if it is NOT found in the other directory. Hope this is OK. Let us know otherwise.

```
...
```

Best back everything up first just in case. I've only given this a quick check, so it should work OK.

(And yes, I'm sure there are much more elegant ways to do this, probably in one line of Perl or something)

First of, thanks a lot for getting into the trouble writing a script :) Second... I can't get it to work.

I named the file "test.tcl" and executed like this:

```
./test.tcl dir1 dir2 dir3
```

Then, I got this error message:

```
no files matched glob pattern "*"
    while executing
"glob -tails -directory $dirA -types f *"
    invoked from within
"set dirAContents [glob -tails -directory $dirA -types f *]"
    (file "./test.tcl" line 14)
```

What am I doing wrong?

---

### Post by misterlizard on 2007-03-16
Hi,
What this (slightly cryptic) error means is that the script couldn't find any files in dir1 or that the directory doesn't actually exist where the script is looking for it.

If you've a directory structure like the one below, where your two input directories (dir1 and dir2) and your empty output directory (dirOut) reside, then put your script in 'some_dir' (i.e. the same level as your directories of interest) and run it using './test.tcl dir1 dir2 dirOut'

some_dir
|
+--dir1
|
+--dir2
|
+--dirOut


Anyway, here's some updated code with some error checking in that should catch most obvious problems. Give this a try and let me know if you're still having troubles.

```

#!/usr/bin/tclsh


if {$argc < 3} {
    puts stderr "Not enough arguments\n"
    puts stderr "Usage:\n    [file tail $argv0] <dirA> <dirB> <dirOut>"
    exit
}

set dirA [lindex $argv 0]
set dirB [lindex $argv 1]
set dirOut [lindex $argv 2]

# check that the directories exist
if {![file isdirectory $dirA]} {
    puts stderr "Couldn't find 1st input directory: $dirA, current directory=[pwd]"
    exit
}
if {![file isdirectory $dirB]} {
    puts stderr "Couldn't find 2nd input directory: $dirB, current directory=[pwd]"
    exit
}
if {![file isdirectory $dirOut]} {
    puts stderr "Couldn't find output directory: $dirOut, current directory=[pwd]"
    exit
}

# get lists of the files within the input directories
set dirAContents [glob -nocomplain -tails -directory $dirA -types f *]
set dirBContents [glob -nocomplain -tails -directory $dirB -types f *]

# check that the directories contain some files, else this is pointless
if {[llength $dirAContents] == 0} {
    puts stderr "1st directory contains no files. Aborting"
}
if {[llength $dirBContents] == 0} {
    puts stderr "2nd directory contains no files. Aborting"
}

# copy the files
foreach f $dirAContents {
    if {[lsearch -exact $dirBContents $f] == -1} {
        puts "Copying file from dirA: $f"
        file copy [file join $dirA $f] $dirOut
    }
}

foreach f $dirBContents {
    if {[lsearch -exact $dirAContents $f] == -1} {
        puts "Copying file from dirB: $f"
        file copy [file join $dirB $f] $dirOut
    }
}

puts "Finished"

```

---

### Post by pmark on 2007-03-16
I have placed dir1, dir2, and dirOut inside /home/pmark/test. I have saved the new script as test2.tcl and executed it with:

```
./test2.tcl dir1 dir2 dirOut
```

But I got this message:

```
1st directory contains no files. Aborting
2nd directory contains no files. Aborting
```

Then I realised that the problem is that there is a number of sub-directories that I am interested in. And there are directories in those directories too. All my files are inside sub-directories.

So, I created some text files that reside on the root of dir1 and dir2, and the script worked perfectly:

```
Copying file from dirA: moka
Copying file from dirB: totem
Finished
```

I hope thar the fact that my files are placed in multiple sub-directories doesn't mean that I am out of luck.

---

### Post by misterlizard on 2007-03-17
Well, it's a bit more work :) The script as it is won't go through any subdirectories, it just looks for files at the top-level. I can have a look at doing this. Does the output directory need to have the same directory structure as the input directories? Or do you just want the files to be output into one directory with no hierarchy?

---

### Post by pmark on 2007-03-18
> **misterlizard said:**
> Well, it's a bit more work :) The script as it is won't go through any subdirectories, it just looks for files at the top-level. I can have a look at doing this. Does the output directory need to have the same directory structure as the input directories? Or do you just want the files to be output into one directory with no hierarchy?

Yes, the output directory needs to have the same directory sctructure as the input directories.

Perhaps there is an easier way...

ComplexNumber suggested to make two lists with the command *find*, then pass them though Meld (or diff) and then edit that file to create a bash script that will copy all  the files into the output directory.

The two collection of files that need to go through this procedure count in hundrends of thousands of files. So as not to waste time and risk harming files, I have been experimenting with two small directories (that contain some .deb files I downloaded with apt-get). 

I executed this simple bash script (at the parent directory that dir1 and dir2 reside):

```
cd dir1
find > ../list1.txt
cd ..
cd dir2
find > ../list2.txt
cd ..
diff -u list1.txt list2.txt > list3.txt
```

The diff result (although Meld produces a more nice output, I'd rather go with something that exists on every Linux setup) is this:

```
--- list1.txt	2007-03-18 19:05:40.000000000 +0200
+++ list2.txt	2007-03-18 19:05:40.000000000 +0200
@@ -1,18 +1,4 @@
 .
-./build-essential
-./build-essential/build-essential_11.3_i386.deb
-./build-essential/dpkg-dev_1.13.22ubuntu7_all.deb
-./build-essential/g++-4.1_4.1.1-13ubuntu5_i386.deb
-./build-essential/g++_4%3a4.1.1-6ubuntu3_i386.deb
-./build-essential/libc6-dev_2.4-1ubuntu12.3_i386.deb
-./build-essential/libstdc++6-4.1-dev_4.1.1-13ubuntu5_i386.deb
-./build-essential/linux-libc-dev_2.6.17.1-50.50_i386.deb
 ./filezilla
 ./filezilla/filezilla_3.0.0~beta2-2~edgy1_i386.deb
 ./filezilla/filezilla-common_3.0.0~beta2-2~edgy1_all.deb
-./unison
-./unison/unison_2.13.16-4ubuntu1_i386.deb
-./unison-gtk
-./unison-gtk/unison-gtk_2.13.16-4ubuntu1_i386.deb
-./xinetd
-./xinetd/xinetd_1%3a2.3.14-1_i386.deb
```

Now... if there was a way to edit this diff file and do the following things:
1. remove all lines that do not start with a dash ("-").
2. remove beginning dashes from all lines
3. place a "cp " at the beginning of each line
4. place a " dir3" at the end of each line

After than, I can just execute it like a bash script.

However, a TCL script that would do all this is just as fine :)

---

### Post by misterlizard on 2007-03-18
OK, here's another script to do this. Put your diffed lines into a file caled 'inFile' which should be where this script should be (at the level just above your directories of interest) and run it. If it all works OK (I did check it a bit) you should get a copyFiles bash script as the output.

Make this executable, run it and you should be good to go.

You'll also need to remove that line starting with '---'. Let me know if this works.



```
#!/usr/bin/tclsh

set outDir outDir

set inFileHandle [open inFile r]
set outFileHandle [open copyFiles w]

puts $outFileHandle "#!/bin/bash\n\n"

while {![eof $inFileHandle]} {
    set line [gets $inFileHandle]
    
    # skip lines that don't start with a -
    if {![regexp {^-(.*$)} $line dummy filePath]} {
        continue
    }
    
    puts $outFileHandle "cp $filePath $outDir"
}



close $inFileHandle
close $outFileHandle

```

---

### Post by pmark on 2007-03-20
The TCL script needs some adjustments which I am trying to make myself. I have never programmed before in TCL but I find it an interesting challenge.

I would like to work on it for a few days before I ask your help to give a final solution to the problem.

Thank you for your help so far. I just need to work on this myself for a while.

---

