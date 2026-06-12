---
title: "Finding file types?"
date: 2009-06-23
forum: General Help
---

### Post by UncleMonty on 2009-06-23
Is there a program I can install which will find all the photos on my computer?

---

### Post by muteXe on 2009-06-23
You can use grep and find at the command line.
Check out the example at the bottom of this: [http://www.crazysquirrel.com/computing/debian/general-commands/grep.jspx](http://www.crazysquirrel.com/computing/debian/general-commands/grep.jspx)

---

### Post by sedawk on 2009-06-23
Let's assume all images are in /home/user, then you can do this:

find /home/user -name \*jpg -name \*.JPG -print

This works as long as you know the suffix of all image files.

If you have messed up file names and you cannot use the suffix
you need a more advanced search.

* The command "file" tries to detect the file type of a given file.
  You can use it to scan every file if you are in doubt.
  But that would require a small shell script to examine all files and
  output the matching files.
  (it might be useful to limit to files of a certain range of size, e.g.
   bigger than 1 MB but smaller than 10 MB. I do not know of a better
   way to do this than to use "du" command.)

---

### Post by geirha on 2009-06-23
You can use the find or locate commands. Locate is much faster since it searches through a database that is updated daily, but it only searches through the / and /home, not external drives and ntfs partitions etc..

```
locate '*.jpg'
```

The find command will take a bit longer, but can search through all files.
```

find $HOME -iname "*.jpg"   # Find all jpegs in your homedir
find / -iname "*.jpg"       # Find all jpegs in the entire system.

```
The latter will likely give a few warnings as it will encounter files/folders you do not have access to. You can ignore those messages by adding 2>/dev/null at the end
```
find / -iname "*.jpg" 2>/dev/null
```

Lastly, in case there are a lot of files, it may be best to write the list to a file, you do that by adding at the end of the command: >~/jpglist.txt

When it's done, you'll find the new file jpglist.txt in your homefolder. Open it in a regular text editor.

---

