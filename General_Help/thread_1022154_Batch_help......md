---
title: "Batch help....."
date: 2008-12-26
forum: General Help
---

### Post by chadwit on 2008-12-26
I have several thousand files that start with a 4 digit number followed by a space, then a dash, another space, filename and then extension, like this:

#### - filename.xxx

I need to just remove the 4 digits, the dash and the spaces from all of the files so I just have "filename.xxx". 

I assume the quickest easiest way to do this would be via some command line syntax in a batch as opposed to doing each file individually, which would take several hours (or days). Unfortunately my command line experience and knowledge isn't there yet. Could someone please tell me what the command would be? 

Thanks....

---

### Post by dagnabit dang doohickey on 2008-12-26
Yes, you can write a command. Or, you can use a rename utility.

[gprename]("http://gprename.sourceforge.net/") - simple
[Métamorphose]("http://file-folder-ren.sourceforge.net/") - powerful

---

### Post by kaibob on 2008-12-26
The following will remove the first {n} characters from a file name:

rename -n 's/^.{n}//' *

As written, this command does a dry run and reports proposed changes. Substitute -v for -n to make the actual changes. Be careful with this command--it renames every file and subdirectory in the current directory. 

[http://ubuntuforums.org/showthread.php?p=5210531](http://ubuntuforums.org/showthread.php?p=5210531)

---

