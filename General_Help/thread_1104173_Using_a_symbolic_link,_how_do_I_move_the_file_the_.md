---
title: "Using a symbolic link, how do I move the file the symbolic link is pointing to?"
date: 2009-03-23
forum: General Help
---

### Post by nattugglan on 2009-03-23
Hi!

Is there a way on the command line/in a bash script to find out what file a symbolic link is pointing to, and move that original file and not the symbolic link?

Example:

I want to move mythtv recordings from /media/recordings to another drive (i.e. /media/nfs_01/recordings) by using the "human readable" filenames/symbolic links created by mythrename.pl. But I want the recordings to still be named the original way so that mythtv will find them in their new location.

If one simply uses the mv command on the symbolic link only the symbolic link is moved, and not the original recording file - it remains where it is.

---

### Post by shankru85 on 2009-03-23
I am sorry. I am not sure if I understood ur question completely. just in case u want to move an original file that a link is pointing to, do an ls -l. It should give you the path where original file is stored. just use mv command. Now dont bash me if you knew what i am telling here and were looking out for something else.

 
shankar@shankar-desktop:~$ ls -l templink 
lrwxrwxrwx 1 shankar shankar 9 2009-03-23 22:51 templink -> /tmp/temp
shankar@shankar-desktop:~$ mv -v /tmp/temp /media/disk
`/tmp/temp' -> `/media/disk/temp'
removed `/tmp/temp'
shankar@shankar-desktop:~$

---

### Post by unutbu on 2009-03-23
To "redirect" the symbolic link, you could simply "remake" the symbolic link to point it somewhere else:

Using shankru85's example, the command
```

ln -sf /tmp/new_destination templink
```

would redirect templink to point to /tmp/new_destination.

ln is the command used to make (symbolic) links.
The -s flag tells ln to make a symbolic link.
The -f flag "forces" ln to create the symbolic link, even if templink already exists.

---

### Post by prshah on 2009-03-23
> **nattugglan said:**
> 
Is there a way on the command line/in a bash script to find out what file a symbolic link is pointing to, and move that original file and not the symbolic link?

The "cp" (copy) command carries a "dereference" switch (-L) that will perform the command on the link target; perhaps the mv command also has such a switch? (Not listed in man mv, though).

EDIT: Nope mv does not have a "dereference" switch; if you have the space, you can consider using a cp -L command and then the rm command. But you will have to recreate the link to make it point to the new location. Eg:```
cp -L -R /media/recordings /media/nfs_01/recordings && rm -rf /media/recordings \
&& ln -s /media/nfs_01/recordings /media/recordings
``` (Example only, please perform sanity check).

---

### Post by nattugglan on 2009-03-23
Here's info on the file I'm testing with. What it looks like:

**[FONT="Courier New"]ls -lh /home/USERNAME/mythrename/Movies\ -\ Happy\ Feet\ -\ Untitled\ -\ 2008-11-02\ 1810.mpg[/FONT]**

Gives:

**lrwxrwxrwx 1 USERNAME USERNAME 58 2009-03-23 17:28 /home/USERNAME/mythrename/Movies - Happy Feet - Untitled - 2008-11-02 1810.mpg -> /media/SEAGATE_1TB_NS01/recordings/1011_20081102181000.mpg**


@shankru85

Yes, the symbolic links point to the original filename, and it is this original filename I want the recordings to have in their new location as well.
But I want to use the symbolic links created by mythrename.pl when choosing which files to move. I.e. move all movies at once to a new location by using **/home/USERNAME/mythrename/Movies*** as the selection.


@PRShah
 
I tried "cp" with **-L** and also with **-H**, but both use the name of the symbolic link as the name for the new copy..
 
According to "man cp":
-H     follow command-line symbolic links

-L, --dereference
              always follow symbolic links


Trying:

**[FONT="Courier New"]cp -vL '/home/USERNAME/mythrename/Movies - Happy Feet - Untitled - 2008-11-02 1810.mpg' test/[/FONT]**

Gives:

**"/home/USERNAME/mythrename/Movies - Happy Feet - Untitled - 2008-11-02 1810.mpg" -> "test/Movies - Happy Feet - Untitled - 2008-11-02 1810.mpg"**

In the example above, I want the result to be **"test/1011_20081102181000.mpg"**.

---

### Post by ilrudie on 2009-03-23
```
LN="link.txt"; NEWTARGET="somefile.txt"; LNTARGET=`ls -l "$LN" | grep ^l | grep "$LN" | awk -F "-> " '{print $2}'`; if [[ -e "$LNTARGET" ]]; then; mv "$LNTARGET" "$NEWTARGET"; ln -sf "$NEWTARGET" "$LN"; else; echo "Specified link ($LN) does not exist, is not a link or does not point to an existing file"; fi
```

This should be what you are looking for it I understand your question correctly.  
LN should be set to the link you want to move the target of (or the full path if its not in the current working directory)
NEWTARGET should be set to the new name you want the link's target to have (or the full path if the new target is not in the current working directory

If you want to use it a lot it might be worth making into a script and adding all the proper checking.

Note: This one-liner does only minimal error and permission checking.  Test it to ensure its working the way you think its working and as always: Use at your own risk.

---

### Post by bodhi.zazen on 2009-03-23
I did not all of your post, but the problem is you have spaces in your file names.

So you either need to quote them or escape them.

Method 1, quotes :

"file name with spaces"

Method 2, escape (use the \ to escape spaces)
file\ name\ with\ spaces

Or use tab completion on existing files.

---

### Post by ilrudie on 2009-03-23
```
LN="link.txt"; NEWPATH="/usr/local/bin/"; LNTARGET=`ls -l "$LN" | grep ^l | grep "$LN" | awk -F "-> " '{print $2}'`; if [[ -e "$LNTARGET" ]]; then; LNTARGETF=$(basename "$LNTARGET"); mv "$LNTARGET" "${NEWPATH}${LNTARGETF}"; ln -sf "${NEWPATH}${LNTARGETF}" "$LN"; else; echo "Specified link ($LN) does not exist, is not a link or does not point to an existing file"; fi
```

Just saw the post with further explanation of what you are looking for.  This is more along the lines of what you want.  It preserves the name of the link target but moves it to a new path specified by NEWPATH.  All the above warnings and instructions apply plus: [COLOR=Red]Make sure newpath ends in a / character or else you will have unwanted results.[/COLOR]

Hope that helps more.

---

### Post by nattugglan on 2009-03-24
@ilrudie,

Thank you! To use **ls** and **grep** to get the original filename was my first thought, but I thought that perhaps there was an easier way - or a special command for it that I didn't know about.

I used your suggestions from your first post and did some tests, and the following works just the way I want it to (for one file, and without error checking so far).

**[FONT="Courier New"]SYMLINK="/home/USERNAME/mythrename/Crime - Beck - i guds namn - Untitled - 2009-03-22 2057.mpg"; RECORDING=`ls -l "$SYMLINK" | grep ^l | grep "$SYMLINK" | awk -F "-> " '{print $2}'`; mv -v "$RECORDING" /media/NFS_SHARE/recordings/[/FONT]**

The original file is moved to the nfs share.

[B]"/media/recordings/1004_20090322205700.mpg" -> "/media/NFS_SHARE/recordings/1004_20090322205700.mpg"
tog bort "/media/recordings/1004_20090322205700.mpg"[/B]

Now I need a nice way to select the symlink(s).

Is it possible to select multiple symlinks with **dialog --fselect**? I would like to be able to do everything over a ssh session in a terminal.

There is a basic example in **/usr/share/doc/dialog/examples/fselect**:

[B][FONT="Courier New"]#!/bin/sh
# $Id: fselect,v 1.6 2005/12/07 01:55:53 tom Exp $
: ${DIALOG=dialog}

exec 3>&1
FILE=`$DIALOG --title "Please choose a file" --fselect $HOME/ 14 48 2>&1 1>&3`
code=$?
exec 3>&-

case $code in
  0)
    echo "\"$FILE\" chosen";;
  1)
    echo "Button 1 (Cancel) pressed";;
  2)
    echo "Button 2 (Help) pressed";;
  3)
    echo "Button 3 (Extra) pressed";;
  255)
    echo "Box closed.";;
esac[/FONT][/B]

I would like to build on this to select all the recordings I want to move. To have the script create a list (i.e. in /tmp) of the chosen symlinks that the script then automatically goes through until all chosen recordings are moved. If it's not possible to choose multiple files at once, one could choose them one by one - and have each added to the list - by repeating the selection step/dialog. It would be nice to be able to i.e. choose all movies by using **/home/USERNAME/mythrename/Movies*** (or **Crime*** as in the example above).

I'm also thinking of a function/dialog that allows me to choose the target directory (as this will change depending on if it is i.e. a TV show or movies I want to move) and that the script checks and only tries to move recordings that are not already in that target directory - by feeding the target directory chosen to a TARGET variable and using **grep** to check that the chosen symlinks doesn't point to a recording that is already in the target directory.

The last piece would be to use **gauge** to show the progress as the recordings are move to their new location.

---

### Post by nattugglan on 2009-03-24
I now have a basic dialog selection in place (for one file).

I created the following script in /usr/local/bin/moverec:

[B][FONT="Courier New"]/home/USERNAME/mythrename.pl --link /home/USERNAME/mythrename/ --verbose --format "%C - %T - %S - %Y-%m-%d %H%i"

SYMLINK=`dialog --backtitle "Move recordings" --stdout --title "Please choose a file." --fselect /home/USERNAME/mythrename/ 14 48`

DESTINATION=`dialog --backtitle "Move recordings" --stdout --title "Please choose a destination." --fselect /media/ 14 48`

RECORDING=`ls -l "$SYMLINK" | grep ^l | grep "$SYMLINK" | awk -F "-> " '{print $2}'`;

mv -v "$RECORDING" "$DESTINATION"[/FONT][/B]

First mythrename.pl does its thing to create the "human readable" symlinks.
Then a dialog to choose a symlink is shown:

[IMG]http://dl.getdropbox.com/u/614009/mythtv/scripts/moverec_dialog_01.png[/IMG]

Followed by a dialog to choose the destination:

[IMG]http://dl.getdropbox.com/u/614009/mythtv/scripts/moverec_dialog_02.png[/IMG]

And when the destination has been chosen, the verbose output from the **mv** command is shown:

[IMG]http://dl.getdropbox.com/u/614009/mythtv/scripts/moverec_dialog_03.png[/IMG]

---

