---
title: "Copy directory and make files empty"
date: 2009-03-13
forum: General Help
---

### Post by RageAgainstThis on 2009-03-13
I would like to copy a directory with subfolders and files.  The catch is I would like to copy all the folders, but when I copy the files I would like them to be empty (0 bytes).  I have done some searching in these forums and on the web, but I may not have the right search terms, so this may have been answered before.  

Thanks

---

### Post by kaibob on 2009-03-14
I was able to do what you want with the commands shown below. My home directory contains a directory named templates. I made a copy of the templates directory structure in my temp directory, which is also in my home directory. Then, I created the empty files with the touch command. I tried this and it worked.

> cd /home/kaibob
find templates/ -type d -exec mkdir -p '/home/kaibob/temp/{}' ';' 
find templates/ -type f -exec touch '/home/kaibob/temp/{}' ';'

You will, of course, have to change the source and target directories. There's probably an easier way to do this, but this is all I could come up with. 

I guess an alternative is to create a copy of the source directory including all subdirectories and files with the cp command and then create empty files with the touch command.

---

### Post by RageAgainstThis on 2009-03-15
Kaibob,

Thanks the above commands worked great, looks like I will have to read up on the power of the find command.  Seems like a very powerful tool in CLI.

Thanks again 

Branden

---

