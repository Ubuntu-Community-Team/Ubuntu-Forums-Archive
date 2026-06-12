---
title: "Howto:Collapse Folders into one"
date: 2009-03-31
forum: General Help
---

### Post by blackest_knight on 2009-03-31
This is a very powerful and dangerous script but useful script
this is a nice little script I made for nautilus very simple

It searches subfolders and brings all the files into the current folder all with a rightclick to run the script.

To be honest I didnt figure out the command line but did figure out how to add it to nautilus. 

The problem 
you have been using a program like music brains picard to correct the tags on some mp3's you used the file rename and move options 
and now you have 
originalfolder\artist\album\artist\album\artist\one-mp3-here.mp3
...repeat for the rest of the tracks

now you could manually move each file and then delete the unneeded folders
but its a slow tedious job.
or issue the following command in the shell from the base directory

find . -type f -exec mv '{}' . \;

or try this (open a shell)

nano collapsefolders.sh (add these three lines and save)

#!/bin/bash
#move all files in subfolders below this dir to the current dir
find . -type f -exec mv '{}' . \;

(ctrl x Y to save)

chmod +x collapsefolders.sh
mv collapsefolders.sh .gnome2/nautilus-scripts/collapsefolders.sh

This script is now available for nautilus to use 
so open the folder you want to collapse  and 
right click select scripts and 
collapsefolders
 after about a second all the files will be out the subfolders and in the current folder 

now all you need do is delete the now empty sub folders
I did consider adding a line to delete the subfolders but its very dangerous with wild cards so easier just to delete by hand

Warning-this does not check for duplicate entries!!

theres no checking for duplicates so if you have two files with the same name you will finish up with only one in the current directory it looks like the files in the subfolder will disappear in preference to the existing files in the current directory

This script could probably do with some more development to make it safer 
but its good enough for me

---

