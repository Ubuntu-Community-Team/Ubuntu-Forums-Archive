---
title: "How to search for words in unkown documents"
date: 2012-06-21
forum: Desktop Environments
---

### Post by Man with Hat on 2012-06-21
Sorry if this is clearly explained somewhere else, I have spent the best part of my day trying to fix this and think I must look like Doc Brown about now. I recently lost a document (thanks Libre) for no apparent reason. I have been using recovery software that has found lots and lots and lots of documents that of course are now labelled 000001, 000002, 213583, or whatever. As I am looking for a specific word document I wanted to know how to search all of the recovered files for a certain word that is not likely to appear in other documents. 

I am of the understanding that I can use either "find" or "grep" or a combination of the two, but every command I have found on the net either makes my computer complain or me complain. Could someone please tell me the code (exact code) that I will need to:

- search a specific directory (and sub directories)
- for file type *.odt
- containing the word "fence" in the file itself (not the title)
- edited within the last week (created in the last week would be better)

Much appreciated!!!!

---

### Post by black veils on 2012-06-21
read through this:

[http://askubuntu.com/questions/39200/how-to-search-for-files-containing-specific-word](http://askubuntu.com/questions/39200/how-to-search-for-files-containing-specific-word)

---

### Post by Man with Hat on 2012-06-21
Thanks for the reply, if you are referring to DemonWareXT's answer of 

```
grep -R hello /home
```This is the style of grep code that I have tried that returns 0 joy. If you (or someone) really understands grep, please could you give me the code I need for my EXACT problem? I have been tearing my hair out reading other threads, trying to alter codes to fit my problem. The most likely I have tried (that doesn't work) is 

```
grep -i -r fence Downloads/testdisk-6.14-WIP/recovered/
```which tells me there is no such directory, alternatively

```
grep -i -r fence *.odt
```sits there and blinks at me. I have even tried this code by moving a file into it's own directory, putting a word into that file that I want. Running this code and it still blinks :(

PLEASE PLEASE PLEASE what am I doing wrong?

EDIT: Also please answer the question, I can't keep reading other threads. Sending me links will more than likely send me to a thread I have read/tried/failed to understand already

---

### Post by drmrgd on 2012-06-21
I don't believe that you can use 'grep' to do this, as the files are not in standard ASCII format or whatever when read in BASH.  So, for example, if you just do:

```
more somefile.odt
```

You'll find that there is some human readable header information followed by gibberish.   So, I think searching for the word "fence" in the document may not be possible unless someone has a really clever trick.

With the appropriate find command, you can at least narrow the search down to files based on creation and / or last access date.  I'm not sure if these dates would help, as I wonder if the recovery software puts a new stamp on them.  A quick check would tell you if this is true:

```
stat *.odt #in the directory where your recovered files are
```

You'll see the access, modify and change times of the files and know whether the recovery software restamped them or not.

If all of the above seems to be fitting the mold, then you could try:

```
find /path_to_folder_with_odt_docs/*.odt -type f -mtime -7
```

This should recursively search through the folder and subfolders with the .odt docs and give you anything modified in the last 7 days.  

Hope that helps at least a little

---

### Post by steeldriver on 2012-06-21
iirc the newer .odt file format is a zipped archive of xml files - one of which (content.xml) contains the text of your document - it's a bit of a pita but you can do something like:

```
find Documents -name "*.odt" -print -exec unzip -c "{}" content.xml \; | tee >(grep "Archive: ") >(grep -o "brown fox") 1>/dev/null
```where the 2nd grep contains the text you're looking for

---

### Post by LewisTM on 2012-06-21
While not as geeky, you could try **Recoll** to index your files. It will extract the text from your odt files and make everything easily searchable. It also has an advanced search feature for date, file path, name, etc.

Cheers!

---

### Post by David Andersson on 2012-06-21
Do your recovered files have file name extension? (Are they called "213583.odt" or just "213583" ?) If not, you can find which files are .odt with the file command, and filter out those of type "OpenDocument Text". Go to the directory of recovered files.

Exercise: List type of all files
```
file *
```

Exercise: List file names of .odt-files only
```
file * | awk -F: '$2~/OpenDocument Text/{print $1}'
```

To use grep to search for words in .odt files will not work reliably since the text may be compressed. Recoll mentioned above might work (have not tried it). Otherwise try odt2txt (in package odt2txt in the repository).

Exercise: See text of one .odt-file
```
odt2txt 213583.odt
```

Final solution: Search in all .odt-files for the text "hello world", ignoring case, and list file names where it is found.
```
file * | awk -F: '$2~/OpenDocument Text/{print $1}' | while read f; do if odt2txt "$f" | grep -iq "hello world"; then echo "Found: $f"; fi; done
```

---

### Post by Man with Hat on 2012-06-22
Wow that's a lot of info, thanks all :) Gonna go through this one by one and will post the results!!

---

### Post by Man with Hat on 2012-06-22
> **steeldriver said:**
> iirc the newer .odt file format is a zipped archive of xml files - one of which (content.xml) contains the text of your document - it's a bit of a pita but you can do something like:

```
find Documents -name "*.odt" -print -exec unzip -c "{}" content.xml \; | tee >(grep "Archive: ") >(grep -o "brown fox") 1>/dev/null
```where the 2nd grep contains the text you're looking for


This is a great code! :)
It located all of the odt files without a problem (ignoring the word in the 2nd grep command) and lists them, ordering them in.... Relevance to search? The first file that shows (the one that is 0 bytes) has this error message:
```
Documents/Fencing/The_letter_that_ is_annoying_me.odt
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
unzip:  cannot find zipfile directory in one of Documents/Fencing/The_letter_that_ is_annoying_me.odt or
  Documents/Fencing/The_letter_that_ is_annoying_me.odt.zip, and cannot find 
Documents/Fencing/The_letter_that_ is_annoying_me.odt.ZIP, period.
```I ran this command from within my home directory. None of the recovered files appeared in results at all. I used "photorec" to recover the files which seems to put them all in padlocked (read-only maybe?) folders that I can't delete.

---

### Post by Man with Hat on 2012-06-22
> **drmrgd said:**
> I don't believe that you can use 'grep' to do this, as the files are not in standard ASCII format or whatever when read in BASH.  So, for example, if you just do:

```
more somefile.odt
```You'll find that there is some human readable header information followed by gibberish.   So, I think searching for the word "fence" in the document may not be possible unless someone has a really clever trick.

With the appropriate find command, you can at least narrow the search down to files based on creation and / or last access date.  I'm not sure if these dates would help, as I wonder if the recovery software puts a new stamp on them.  A quick check would tell you if this is true:

```
stat *.odt #in the directory where your recovered files are
```You'll see the access, modify and change times of the files and know whether the recovery software restamped them or not.

If all of the above seems to be fitting the mold, then you could try:

```
find /path_to_folder_with_odt_docs/*.odt -type f -mtime -7
```This should recursively search through the folder and subfolders with the .odt docs and give you anything modified in the last 7 days.  

Hope that helps at least a little
Thanks for that info, yes the "more" command is loaded with fun gibberish to read :)

As far as the time stamp goes, I did try the mtime -7 command, but for some reason (this is probably where my problem starts) I can't actually read the recovered files using these commands. Apparently they don't exists:
```
find *.odt
No such file or directory

```
](*,) THEN WHY CAN I ACCESS THEM FROM THE GUI Mr. COMPUTER?!>?! WHY CAN I DO THAT?!?!

---

### Post by Man with Hat on 2012-06-22
> **David Andersson said:**
> Do your recovered files have file name extension? (Are they called "213583.odt" or just "213583" ?) If not, you can find which files are .odt with the file command, and filter out those of type "OpenDocument Text". Go to the directory of recovered files.

Exercise: List type of all files
```
file *
```Exercise: List file names of .odt-files only
```
file * | awk -F: '$2~/OpenDocument Text/{print $1}'
```To use grep to search for words in .odt files will not work reliably since the text may be compressed. Recoll mentioned above might work (have not tried it). Otherwise try odt2txt (in package odt2txt in the repository).

Exercise: See text of one .odt-file
```
odt2txt 213583.odt
```Final solution: Search in all .odt-files for the text "hello world", ignoring case, and list file names where it is found.
```
file * | awk -F: '$2~/OpenDocument Text/{print $1}' | while read f; do if odt2txt "$f" | grep -iq "hello world"; then echo "Found: $f"; fi; done
```

Brilliant, getting so close now!! That odt2txt thing works great on the one file and on the multiple files. Now how to I get it to recursive search subdirectories? So far photorec has created literally hundreds of subdirectories with numbers for names. I'd rather search them simultaneously if possible.  I'm going to play around with adding an -r in different places unless an answer comes quicker ;)

Ok tried these variations:
```
file * | awk -F: '$2~/OpenDocument Text/{print $1}' | while read f; do  if odt2txt "$f" | grep -iqr "hello world"; then echo "Found: $f"; fi;  done
file * | awk -F: '$2~/OpenDocument Text/{print $1}' | while read f; do  if odt2txt "$f" | grep -irq "hello world"; then echo "Found: $f"; fi;  done
file * | awk -F: '$2~/OpenDocument Text/{print $1}' | while read f; do  if odt2txt "$f" | grep -r -iq "hello world"; then echo "Found: $f"; fi;  done
file * | awk -F: '$2~/OpenDocument Text/{print $1}' | while read f; do  if odt2txt "$f" | grep -iq -r "hello world"; then echo "Found: $f"; fi;  done
file * | awk -F: '$2~/OpenDocument Text/{print $1}' | while read f; do  if odt2txt "$f" | grep -d recurse -iq "hello world"; then echo "Found: $f"; fi;  done
file * | awk -F: '$2~/OpenDocument Text/{print $1}' | while read f; do  if odt2txt "$f" | grep -iq -d recurse "hello world"; then echo "Found: $f"; fi;  done

```

Plus I don't know how many others. All return 0 search results. I am doing this search from within my "Documents" but trying to locate the words/files in a subdirectory called "Fencing." The code works great if I am in the "Fencing" directory, but I want to search subs :(

---

### Post by Man with Hat on 2012-06-22
> **LewisTM said:**
> While not as geeky, you could try **Recoll** to index your files. It will extract the text from your odt files and make everything easily searchable. It also has an advanced search feature for date, file path, name, etc.

Cheers!
Thanks very much for this too Lewis. I'll give this a go if the command lines for odt2txt don't work the way I want. BTW, does the sudo sandwich command work with your wife? :p

---

### Post by David Andersson on 2012-06-22
> **Man with Hat said:**
>  That odt2txt thing works great on the one file and on the multiple files. Now how to I get it to recursive search subdirectories? So far photorec has created literally hundreds of subdirectories with numbers for names. I'd rather search them simultaneously if possible.  I'm going to play around with adding an -r in different places unless an answer comes quicker ;)


You placed the -r in the wrong places. Actually it's not about -r at all. The first two commands in the pipe chain is for finding .odt:s. The first ("file *") list filenames and their types. The second ("awk...") filters on type and list only the right filenames.

If you change the first command to
```
file * */* */*/*
```
it will list filenames and types for all files in current folder, all sub-folders and all sub-sub-folders. The rest of the pipe chain will do its work as usual but with all the new filenames it is given. It there are sub-sub-sub- and sub-sub-sub-sub-folders, I am sure you figure it out how to cover them.

(There surely is a way to handle *infinitely* many levels of sub-folders, many ways actually, and they may or may not involve -r, but I think it will be unnecessary complicated for this problem.)

---

### Post by Man with Hat on 2012-06-24
Thanks for your continued help David. I tried changing the command as you suggested, but either get the error message:

bash: /usr/bin/file: Argument list too long

Or else no output and I am back with a new prompt. I have tried these variations with marked results:

* *   no output
* */ no output
* */* Argument list too long
* */* * Argument list too long
* */* */ Argument list too long
* */* */* Argument list too long
* */* */*/ Argument list too long
* */* */*/* Argument list too long

I ran the command from the folder marked "recovered." inside this folder is where there are over 600 folders marked numerically, but only contain files, no more subs.

---

### Post by David Andersson on 2012-06-24
> **Man with Hat said:**
> 
bash: /usr/bin/file: Argument list too long


Sweet. Probably more than 100,000 files then.

Let's try give the file command one directory at a time and see if it can handle that. This mean you replace

**file */***

with

**for d in */; do file $d/*; done**

The whole command chain then becomes
```
for d in */; do file $d/*; done | awk -F: '$2~/OpenDocument Text/{print $1}' | while read f; do if odt2txt "$f" | grep -iq "hello world"; then echo "Found: $f"; fi; done
```

That's quite long, even on a wide screen. Let's divide it into smaller parts and save intermediate data in temporary files.

1) Find .odt-files
```
for d in */; do file $d/*; done | awk -F: '$2~/OpenDocument Text/{print $1}' >/tmp/myodtfiles.list
```
2) Search .odt files for "hello world", ignoring case
```
cat /tmp/myodtfiles.list | while read f; do odt2txt "$f" | grep -H --label="$f" --color=auto -i "hello world"; done
```

(The grep command is not exactly as before. Now it will show not only the filename where the word is found, but also the line of text, and in colours if output is to a terminal.)

---

### Post by Man with Hat on 2012-06-25
Sooooooooooooooo close now :) Thanks for all of this help, I'm actually having a bit of fun learning about this... Even if I don't 100% understand what is happening. 

I ran a test of this in the Documents folder and it worked great!

I'm having diffculty with this one as it has created 2 types of files in the list. There are odt files and sxw files (whatever they are). When I run command 2, it tries about 4 of these sxw files and then complains. I obviously can manually delete them from the list, but is there an easier way?

---

### Post by ubu2008 on 2012-07-15
[1] It really should as easy as using ubuntu search tool (main | places | search files)
 -- but it is not. 
The trouble is that people do not understand the specifications of your problem
and so they will give you solutions that work for one directory or one file
but not a general purpose solution.
The general purpose specifications are:
1. given a files system (not one directory) containing many odt files.
2. given a searchstr. (and maybe other criteria like dates)
3. find and report all files (and their paths) that contain searchstr.
4. report the list of paths (possibly many) in a nice gui that allows you to click on the
path and open the file and to confirm if it is the one that you want.

[2] Welcome to the club of people who need this tool -- but there is no such tool. (The Recoll tool runs on Windows but there is no Linux version.)
You even find other people asking for it and some get funny answers
like this one:  [http://answers.yahoo.com/question/index?qid=20120105000528AA0DsKk](http://answers.yahoo.com/question/index?qid=20120105000528AA0DsKk)
In reality, you can easily take single odt file and unzip it and find if it contains
the text you looking for. But to find an odt file one of many in your file system (haystack)
should be handled by ubuntu search (main | places| search for files), but it is not.
The grep dumps list of files on you (say 2000) and you can then go and open
them one by one using vi by giving it manually the path. This is as friendly as unix was in 1985.
The grep based solution are forcing you to get a list of files that than you need to
write another program, call it searchodt, that will show you nice gui interface
like ubuntu search where you can click and open file. (see requirement 4)
Here are more funny answers:
[http://in.answers.yahoo.com/question/index?qid=20100128220440AAapYRd](http://in.answers.yahoo.com/question/index?qid=20100128220440AAapYRd)
So far the only good workaround is to convert your odt files to doc and then the 
ubuntu search tool will find those. Yes it is heresy, but it does work until we have a searchodt tool.

[3] I have a solution for requirements 1,2,3 but not 4. If I you get 2000 or even 20 hits, it is difficult to do requirement (4) manually. :( :( :(

---

### Post by LewisTM on 2012-07-15
> **ubu2008 said:**
> [1]
[2] Welcome to the club of people who need this tool -- but there is no such tool. (The Recoll tool runs on Windows but there is no Linux version.(
What are you talking about?? Recoll run on Linux, it's in the official repos. You can even add a [PPA]("http://www.webupd8.org/2012/03/recoll-lens-full-text-search-unity-lens.html") that offers, in addition to the latest version, a Unity lens. Meaning you can do full text searches from the dash. Just run recoll for the first time, configure the indexing and let it run. It doesn't get any easier than this.

---

