---
title: "find: unknown predicate `-E' error on Bash Script"
date: 2010-10-22
forum: Desktop Environments
---

### Post by juliushibert63 on 2010-10-22
I've chopped together a bash script that I've been using for the last 6 months on my mac. It basically parses through a directory supplied via the Terminal and then search each sub directory running a script called tvrenamer.pl. This renames all the TV episodes in each directory based on the info on TVdb.

I've just setup an Ubunutu 10.4 64bit system and tried to use the script but get an error;


```
gil@gil-htpc:~/Scripts$ sudo ./clean_tv_names.sh ~/Videos/TV/
[sudo] password for gil: 
\n
The directory we're going to try and rename TV files in is /home/gil/Videos/TV/
Is this correct Y/N?
Y
find: unknown predicate `-E'
\n
Finished renaming all the files and closing up shop
gil@gil-htpc:~/Scripts$ 
```


I would of though as both Mac OS X and Ubuntu both use the same Terminal it would all run the same. But evidently not. Any ideas what's causing the error?

Here's the contents of the bash script that's running. As I said works absolutely fine on my OS X 10.6 system.


```
#!/bin/sh
######################################
#
#
# Script source: http://www.robmeerman.co.uk/coding/file_renamer
# Author: Adrian
#> I have a script that I run regularly to scan through the TV Shows
#> directory on my NAS. The script runs tvrenamer.pl on any likely
#> looking directory (assuming a directory structure such as
#> "Programme/Series x" or "Programme/Season x" where x is a numeric
#> value). The script is very rough and ready and looks like this:
#
#
# Commented and mods by: Gil Cocker
#
#Date:21/02/2010
#######################################

# Setup the dir/vars that the script will work on

TV_DIR=$1
#This is directory we want the script to run on

TVRENAMER_SCRIPT=~/Scripts/tvrenamer.pl
#Where the tvreanmer.pl script is


echo "\n"
echo "The directory we're going to try and rename TV files in is $TV_DIR"
echo "Is this correct Y/N?"
read choice

if [ $choice = "Y" ]; then
 cd "$TV_DIR"
 IFS=$'\n'
 for dir in `find -E . -type d -iregex "./[^/]*/S(eason|eries)[[:space:]]+[0-9]+"`; do
       ( cd "$dir"; rm -f ._*; "$TVRENAMER_SCRIPT"  --reversible --scheme=SXXEYY --pad=2 $
done
        echo "\n"
        echo "Finished renaming all the files and closing up shop"
else
        echo "\n"
        echo "Quiting....."
fi
```

---

### Post by DaithiF on 2010-10-22
[QUOTE=juliushibert63;10010220]
I would of though as both Mac OS X and Ubuntu both use the same Terminal it would all run the same. But evidently not. Any ideas what's causing the error?
[\QUOTE]

Mac OSX is based off BSD, whereas Ubuntu is linux.  Although the default choice of shell is bash for both, there are still differences in certain commands between the 2 environments.  find is one such command -- BSD command has the -E flag to enable modern regex support, but GNU / linux find does not.  I don't know if there will be any actual difference in the behaviour of the regex matching for you, so as a first step just remove the -E from your find command and see if that works.

---

### Post by juliushibert63 on 2010-10-23
> 
Mac OSX is based off BSD, whereas Ubuntu is linux. Although the default choice of shell is bash for both, there are still differences in certain commands between the 2 environments. find is one such command -- BSD command has the -E flag to enable modern regex support, but GNU / linux find does not. I don't know if there will be any actual difference in the behaviour of the regex matching for you, so as a first step just remove the -E from your find command and see if that works.


Thanks for the clarification.

Removing the -E flag on find removed the error, the script doesn't look like it's working correctly. I'm guessing it's not finding any directories even though they exist. Any ideas what might be happening;

```
./clean_tv_names.sh ~/Videos/TV/
\n
The directory we're going to try and rename TV files in is /home/gil/Videos/TV/
Is this correct Y/N?
Y
\n
Finished renaming all the files and closing

```

---

### Post by DaithiF on 2010-10-23
Looks like the default regex behaviour in gnu find doesn't support [[:space:]] or (a|b) alternatives.

add 
```
-regextype posix-extended
```
to your find command and it should work I think.

Also, to avoid guess work, add an echo statement to show the directories which are being found by the find command:

```
 ( echo "$dir"; cd "$dir"; rm -f ._*; "$TVRENAMER_SCRIPT"  etc...

```

---

