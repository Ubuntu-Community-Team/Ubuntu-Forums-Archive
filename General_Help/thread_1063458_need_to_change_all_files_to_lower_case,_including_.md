---
title: "need to change all files to lower case, including subdirectories"
date: 2009-02-07
forum: General Help
---

### Post by beatgeek on 2009-02-07
Here's the problem: I've got this old CD-ROM full of HTML pages that all link to each other. The HTML assumes the filenames will be considered case-insensitive. The filenames are all uppercase, while the HTML code is looking for lowercase. I have to change the filenames to some 13,000 files several directories deep, to match the HTML code. 

Searching on google told me how to do it with one file, and with one folder, but not several folders deep. The other workaround is to force linux to be case-insensitive, but the only google results I got for that called for creating a new partition, which is ridiculous.

Help me, codemonkeys!

---

### Post by mb_webguy on 2009-02-07
Install the package krename.  It allows you to easily change the case of filenames, and it has the ability to do it recursively.

---

### Post by paddydd on 2009-02-08
If you don't want to install the package here's a shell script that I think would do the trick.

This will get you started. You should check the script out and TEST it in a small set of files. I built a set of directories 3 levels deep to test.  

The Script does the following:

1. Ask if its ok to run.
2. Using the find command it produces a list of relative path names to all files based on your current directory. Note the syntax in the find command. You can modify this search criteria if desired. This is the command the works down the tree.
3. Eliminates the "." directory and the program name which is p.sh from the list using grep -v. It feeds the rest of the list into a loop.
4. The value returned by the find command is checked to see it is actually a file and not a directory. Directory names are skipped.
5. The relative path name of the file is broken down into FILE NAME and DIR NAME parts.
6. The FILE NAME part is lowercased with the tr command.
7. The New File Name is pasted back together using the original DIR NAME and the newly lower cased file name parts.
8. The mv command is used to rename the file.
   note that if the mv command tries to name a file the same name the mv command will report an error but the script will continue.

There are various echo commands that I used for debugging. You can comment out as you see fit.
Even though I have tested this you should as well. I had to cut and paste the script into this interface so you should certainly test it.

I certainly hope this helps.

Paddy

' There are old pilots and bold pilots but there are no old bold pilots'

# p.sh
# Script to lowercase file names in directory tree.
# This script is very dangerous in that it moves down a directory tree and
# renames all of the files to lower case.
# It should be use with extreme caution.

echo ""
echo "This script will rename all files in this directory to lowercase"
echo "This means that all files no matter how deep in the directory will "
echo "be changed."
echo "Do you wish to proceed?  "
echo "enter y for yes or n for no."

read YN

VAR_YN=`echo $YN | tr '[A-Z]' '[a-z]' `

if [ "$VAR_YN" !=  "y" ]
  then
    echo "Program Stopped"
    exit 1
fi


find . -name "*"  -print | grep -v '^.$' | grep -v 'p.sh' |

   (
      while read OLD_FILE_NAME
        do
         echo "OFN: " $OLD_FILE_NAME

         if [ -f "$OLD_FILE_NAME" ]
          then
            FILE_NAME_PART=`basename $OLD_FILE_NAME`
            DIR_NAME_PART=`dirname $OLD_FILE_NAME`

            echo "FNP: " $FILE_NAME_PART
            echo "DNP: " $DIR_NAME_PART

            FILE_NAME_PART_LOWER=`echo $FILE_NAME_PART | tr '[A-Z]' '[a-z]' `

            NEW_FILE_NAME=$DIR_NAME_PART/$FILE_NAME_PART_LOWER

            echo "NFN: " $NEW_FILE_NAME

            mv $OLD_FILE_NAME $NEW_FILE_NAME
         fi
        done
   )

---

### Post by beatgeek on 2009-02-08
Ah, thank you for the script, but I'd already started using the krename. It took 2197 seconds to do the job, plus almost that long just to change settings in the GUI!

I think next time I'll try the script and see if it can do better!

---

### Post by mb_webguy on 2009-02-08
I'm not sure why it took so long to use KRename.  Using the Wizard interface, it took me eight mouse clicks to do what you were talking about, and that included navigating the file browser to pick my test directory.  Of course, I *have* used the app before, but only about twice over the course of a year...

All but the most complex scripts tend to do only one thing, but do that thing very well.  The script paddydd posted might be a bit faster than KRename (in fact, there's a good chance it would be, at least by a bit), but it's nowhere near as flexible.  If you have some other need for batch renaming in the future, you can either use KRename or you can write a new script.  I think I could figure out the options I need to change in KRename faster than writing a new script, even though I'm fairly comfortable writing scripts.

Personally, I use GPRename for batch renaming (which is a bit simpler, and designed for Gnome), but I suggested KRename because GPRename doesn't to my knowledge do recursion.

---

### Post by geirha on 2009-02-09
You may also be able to mount the cd with only small letters, by disabling rockridge and joliet extensions. Filenames larger than 8+3 characters may appear with partial names though.

```
umount /media/cdrom
mount -o norock,nojoliet /media/cdrom

```

---

