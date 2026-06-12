---
title: "Custom environment variable: &quot;My Documents&quot;-ish"
date: 2010-06-21
forum: Desktop Environments
---

### Post by miyalys on 2010-06-21
Hi,

I've been wanting to improve, personalise and optimise my OS,
so I've been thinking about ways to do that, and one thing I'd really like to do is a custom search path for documents, so I don't have to CD to my documents directory each time I want to edit a document, which is all the time.
My idea is a custom $path-like environment variable, that searches a specific (or more) directory and subdirectories for files. 
Either it could be a setting in vi, like instead of (ALT+F2) Run: vi /media/s1/documents/awesome.txt or sth., it could be simply Run: vi awesome.txt  (I'd make sure that I don't have two identically named documents in any of my document folder's subdirectories.) 
Alternately it could be a non-vi-specific command, like a home made command called edt, that takes the current $EDITOR and searches a unique $PATH for whatever files are in there.
As far as I know though, $PATH itself searches for executables, not ANY file.

To me it sounds fairly simple, but I still can't seem to find out how to do it.
Can anyone help me? I run debian lxde.

Thanks!

---

### Post by wojox on 2010-06-21
If your editing documents in you're /home directory open Nautilus and click the document.

---

### Post by miyalys on 2010-06-21
Thanks, but I'd like to be able to do it from a terminal and a runner-app, and direct it to directories like "/media/s1/Documents and settings/Application data/Biowaste/Microsoft/Internet explorer/Quick launch" and to "/media/data/various/documents" fx.

---

### Post by wojox on 2010-06-21
Double Post

---

### Post by wojox on 2010-06-21
Oh I understand know. You may want to use aliases. Like alias quick=&#8217;data/Biowaste/Microsoft/Internet explorer/Quick launch&#8217; Look at the man page [http://manpages.ubuntu.com/manpages/intrepid/man1/alias.1posix.html](http://manpages.ubuntu.com/manpages/intrepid/man1/alias.1posix.html)

---

### Post by miyalys on 2010-06-21
From what I understand your example would be the same as a system-wide symlink, like typing "cd quick/textfile" instead of the long path there(?) which is also what a custom made env like $documents would do? ....But that would still require me to either make many different aliases for each subfolder, or manually cd further into my documents, which has many subfolders, and the command would be longer than simply "vi textfile" a sort of vi-specific $PATH that accepts any filetype and includes subfolders. And that concept could be extended to give gimp it's own search directory (incl. subdirectories) and one for gpicview and one for vlc etc.

---

### Post by untana on 2010-06-21
Sorry brother!!!! this is not the environment which we were talking about,this is the background environment of the desktop of the computer.so no relevant reply to it.






[]("http://www.MSDScompliance.com")

---

### Post by miyalys on 2010-06-21
I'm not sure I understand what you mean? It isn't shell but desktop specific?

---

### Post by potat on 2010-06-21
Could this work?

Make a bash script (call it "q" (or something  short and sweet like that)) and get it to do the expansion for you:

```

FPATH="/home/$(whoami)/Documents  /home/$(whoami)/foo/bar/docs /etc/grumblecakes"
find $FPATH -name $1  | head -n1

```

make a ~/bin and put the script in there.  Then add it to your $PATH for each bash session.

make or edit  ~/.bash_profile 
```

PATH=$PATH:/home/$(whoami)/bin
export  PATH

```

and add to the end of .bashrc
```

# use  .bash_profile
if [ -f ~/.bash_profile ]; then
    .  ~/.bash_profile
fi

```

Then
```

vim `q  foo.txt`

```
will edit the first file in the directories  matched by the filename. It's recursive, but you can change the options  to "find" to change that.

I'm sure there's a better way, but this  is the first thing I thought of. Hope it helps or is interesting.

---

### Post by potat on 2010-06-21
Alternately, you could use a script that runs in the background, every 30 seconds or so, and symlinks all new files in the directories to a ~/mydocs folder. The ~/mydocs could even be linked to a "quick" name such as "/q/" on the root dir. Then the tab-completion in bash would still work.

EDIT: This is the basic idea:
```

#!/bin/bash
# This script will check for changes in a list of directories DIRARR and symlink
# changes to LNDIR, so that a user can more easily access often-used document 
# directories from the command line. Only the top levels of the listed 
# directories are checked and linked. Only use with versions of bash that
# support arrays.

# To have this script run at startup in Ubuntu (assume we call it docsync):
#   chmod +x docsync
#   mv docsync /etc/init.d/
#   update-rc.d docsync defaults

# Author: Stephen Albert
# Free to use, copy, modify, distribute


# List of directories to be watched. Each directory in which you have documents
# should be explicitly stated.
DIRARR=("/home/$(whoami)/Documents"     \
        "/home/$(whoami)/foo/bar")

LNDIR="/home/$(whoami)/mydocs" #directory in which to put symlinked files
NAPTIME="30" #Time to wait between checks (seconds)


mkdir -p $LNDIR

#OLDARR=$DIRARR 

while true
do
    echo "Waiting..."
    
    for (( i = 0 ; i < ${#DIRARR[@]} ; i++ ))
    do
        DIR=${DIRARR[$i]}
        # take a new snapshot of stats
        NEWARR[$i]=$( stat -c "%y" $DIR )
        # compare it with old
        if [ "${NEWARR[$i]}" != "${OLDARR[$i]}" ]; then
            echo "Files changed in ${DIR}"
            
            echo "Checking for new files"
            for FP in $( find $DIR -maxdepth 1 -type f)
            do
                #echo "${LNDIR}/$(basename ${FP})"
                if ! [ -h "${LNDIR}/$(basename ${FP})" ]; then
                    echo "linking ${LNDIR}/$(basename ${FP})"
                    ln -s $FP $LNDIR
                fi
                #echo "ln -s $FP $LNDIR"
            done
            
            echo "Checking for broken links"
            for LK in $( find $LNDIR -type l)
            do
                if ! [ -e $LK ]; then
                    echo "Removing broken link $LK"
                    rm $LK
                fi
            done
        fi        
        OLDARR[$i]=${NEWARR[$i]}
    done 
sleep $NAPTIME
done

```

Not sure if the install method I described works in Debian, but I think it should. Also, I don't know how to make it recursive (checking subdirectories automatically) because stat just checks the data for the elements in a folder.

---

### Post by miyalys on 2010-06-22
Thx a lot, potat! I got the first one to work! Nifty.
How to incorporate tab-completion into that though? Regardless I'm guessing it will be useful.

The second solution sounds more resource intensive(?), but I guess I'd just lower the file update frequency to once per session or something

Do you btw. happen to know what I'd do with a path that has spaces in it? This is one of my path's in the script:
```
/media/s1/Documents\ and\ Settings
```
but then it says:
```
find: `/media/s1/Documents\\': No such file or directory
find: `and\\': No such file or directory
``` 
..and so on.

---

### Post by potat on 2010-06-24
I believe I have the script now working for files with spaces. The code is below.

Thanks to stat, it actually runs quite quickly. If nothing has been modified, it doesn't do anything (stat just checks the modification time of the folder's inode). And the actual search should take less than a second (except for the first time). So if you set NAPTIME to something like 300 (5 minutes), you'll still get fairly quick syncing and won't have to worry about performance issues.

If you do decide to run the script only once per session, set LOOP to false.

```

#!/bin/bash
# This script will check for changes in a list of directories DIRARR and symlink
# changes to LNDIR, so that a user can more easily access often-used document 
# directories from the command line. Only the top levels of the listed 
# directories are checked and linked. Only use with versions of bash that
# support arrays.

# To have this script run at startup in Ubuntu (assume we call it docsync):
#   chmod +x docsync
#   mv docsync /etc/init.d/
#   update-rc.d docsync defaults

# Author: Stephen Albert
# Free to use, copy, modify, distribute
# ------------------------------------------------------------------------------

# List of directories to be watched. Each directory in which you have documents
# should be explicitly stated. Use the line continuation "\" character as shown.
DIRARR=("/home/$(whoami)/Documents"     \
        "/home/$(whoami)/foo/bar"       \
        "/home/$(whoami)/Documents and Settings")

# Directory in which to put symlinked files
LNDIR="/home/$(whoami)/mydocs" 

# Only set to "false" if you run this script yourself periodically,
# or if you run it via cron
LOOP="true"

# Time to wait between checks (seconds)
# Meaningless if LOOP is false.
NAPTIME="5"


# Creates link dir if it doesn't already exist
mkdir -p $LNDIR
# Cleans out link dir
$LOOP && rm ${LNDIR}/*

# Main loop: these commands will execute every $NAPTIME seconds.
while true
do
    echo "Waiting..."
    
    # for each directory in our list...
    for (( i = 0 ; i < ${#DIRARR[@]} ; i++ ))
    do
        DIR="${DIRARR[$i]}"
        
        # get new modification time
        NEWARR[$i]=$( stat -c "%y" "${DIR}" )
        
        # compare it with old
        if [ "${NEWARR[$i]}" != "${OLDARR[$i]}" ]; then
       
            echo "Files changed in ${DIR}"
            
            echo "Checking for new files..."   
            FPLIST=$( find "${DIR}" -maxdepth 1 -type f )
            FPNUM=$( echo "${FPLIST}" | wc -l )
            for (( j = 1 ; j <= ${FPNUM} ; j++ ))
            do
                FP=$( echo "${FPLIST}" | head -n $j | tail -n1 )
                LFP="${LNDIR}/$(basename "${FP}")"
                if ! [ -h "${LFP}" ]; then
                    echo "Linking ${LFP}"
                    ln -s "${FP}" "$LNDIR"
                fi
            done
            
            echo "Checking for broken links..."
            LKLIST=$( find "${LNDIR}" -maxdepth 1 -type l )
            LKNUM=$( echo "${LKLIST}" | wc -l )
            
            for (( j = 1 ; j <= ${LKNUM} ; j++ ))
            do
                LK=$( echo "${LKLIST}" | head -n $j | tail -n1 )
                if ! [ -e "$LK" ]; then
                    echo "Removing broken link $LK"
                    rm "$LK"
                fi
            done
            echo "done."
        fi        
        OLDARR[$i]="${NEWARR[$i]}"
    done

# Break if we are not looping 
! ${LOOP} && break

sleep $NAPTIME
done

```

---

