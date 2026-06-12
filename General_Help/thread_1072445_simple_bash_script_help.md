---
title: "simple bash script help"
date: 2009-02-17
forum: General Help
---

### Post by mishkin on 2009-02-17
okay I have a little script I found that extracts season packs in that it puts each episode avi into the folder it came from

then I want to get them out of those folders and all into one folder for easy viewing purposes

So i made up a command that I can run to do the seccond part but it's a bit annoying as I have to navigate to the main folder through terminal and then paste it from a text-pad to run it.

Is there a simple way to have them all extract to a specific folder instead of "e" (current  dirrectory)

OR

A way to add the move command to the first script?

here are the script and command:

> 
#!/bin/bash
for i in $(find $(pwd) -name '*.rar')
do
cd $(dirname $i)
unrar e $i
done


>  find $pwd -name *.avi -a -size +100M -exec mv {} /home/mishkin/dump/ \; 

the size is there so samples don't get moved



parts of the man for unrar is as follows

>  SYNOPSIS
unrar  <command> [-<switch 1> -<switch N>] archive [files...] [path...]
...
options:   e      Extract files to current directory.

       l      List archive content.

       p      Print file to stdout.

       t      Test archive files.

       v      Verbosely list archive.

...
switches:
       -av-   Disable Authenticity Verification check.

       -c-    Disable comments show.

       -f     Freshen files.

       -kb    Keep broken extracted files.

       -ierr  Send all messages to stderr.

       -inul  Disable all messages.

       -o+    Overwrite existing files.
-o-    Do not overwrite existing files.

       -p<password>
              Set password.

       -p-    Do not query password.

       -r     Recurse subdirectories.

       -u     Update files.

       -v     List all volumes.

       -x<file>
              Exclude specified file.

       -x@<list>
              Exclude files in specified list file
       -x@    Read file names to exclude from stdin.

       -y     Assume Yes on all queries.




thanks for any help

it's very annoying to manually extract 12-100 episodes at once lol

what I have atm works... but It would be nice if it were even simpler (one step just double click script and hit run in terminal)

---

### Post by mikewu on 2009-02-17
The last optional argument to a unrar command is also the path to extract to. 

I imagine the final script would end up something like this.

```
#!/bin/bash
for i in $(find $(pwd) -name '*.rar')
do
cd $(dirname $i)
unrar e $i /home/mishkin/dump/ #Extract to folder
done 

find /home/mishkin/dump -name *avi -a -size -100M -exec rm {} \; #Remove all samples
```

I don't know if you wanted to mv or rm all the samples, but that's easily changed.

---

### Post by mishkin on 2009-02-17
but e is a switch to extract to the current dirrectory (Look at the man I posted)\

I did try just putting the path as I recall but it wouldn't work... could try again

---

### Post by mishkin on 2009-02-18
hmm keeping the e and just adding the filepath seems to have done it

no need to remove or stop samples from moving

after it extracts and moves the avi's I can just delete the origonal season folder

thx :)

---

