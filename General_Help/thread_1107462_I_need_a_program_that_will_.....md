---
title: "I need a program that will ...."
date: 2009-03-26
forum: General Help
---

### Post by accooper on 2009-03-26
I need a program that will allow me to print out the contents of a folder.  Anyone know of one?

:guitar:

TIA
Andrew

---

### Post by mb_webguy on 2009-03-26
What about the terminal command "ls > dir_listing.txt"?  This will write the contents of the current directory to the file dir_listing.txt.  If you wanted to do this from Nautilus, you could write a Nautilus script for it, or using the Nautilus Actions extension.

---

### Post by Shpongle on 2009-03-26
id say you could do it in cpp, and have the output file set as the printer or just print the output file or just print the terminal command result that was said above

---

### Post by mb_webguy on 2009-03-26
Save the following script to the ~/.gnome2/nautilus-scripts directory as "Create directory listing".```
#! /bin/sh

pwd > dir_listing.txt
ls -lsah >> dir_listing.txt

```
Make it executable with the following command:```
chmod +x "~/.gnome2/nautilus-scripts/Create directory listing"
```
Now you'll have a new submenu called "Scripts" in your Nautilus context menu, with a "Create directory listing" option.  Right-click and select this option in any directory, and it will create a text file called "dir_listing.txt" in that directory containing the path of the directory and a detailed list of its contents.

A slightly more elaborate script might be able to send the file directly to the printer, then clean up after itself.

---

### Post by mb_webguy on 2009-03-26
Ok, here's that slightly more elaborate version.```
#! /bin/sh

pwd > ~/dir_listing.txt
ls -lsah >> ~/dir_listing.txt
lpr ~/dir_listing.txt
rm ~/dir_listing.txt
```

This will create the directory listing file in your home folder (which allows you to make a directory listing for directories to which you don't have write permission), prints the file using the system default printer, then deletes the file.  You'd probably want to call this script "Print directory listing".

---

### Post by accooper on 2009-03-26
Thanks for the suggestions.  I will try them.

:guitar:

Andrew

---

