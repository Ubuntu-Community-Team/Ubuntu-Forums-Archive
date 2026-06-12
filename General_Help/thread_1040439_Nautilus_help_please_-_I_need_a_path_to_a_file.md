---
title: "Nautilus help please - I need a path to a file"
date: 2009-01-15
forum: General Help
---

### Post by 3pinner on 2009-01-15
I am searching for a file that is somewhere in the File System. Its a database (mdb file) for an application I am using.
The file is not in the application's  folder, so I went looking for it by Sudo Nautilus. 
I did a search for it, and Nautilus found it, but it doesn't really tell me where it is located in the File System.

How do I get Nautilus to display the path to the items I am searching for?

Thanks!

---

### Post by wolfen69 on 2009-01-15
do ```
sudo updatedb
``` and wait. then
```
locate name_of _file
``` it will show all instances of it and show the path.

---

### Post by 3pinner on 2009-01-15
Thank You Wolfen I found the file with no problems.
Seems to me that Nautilus would display that information by default dont you think?

---

### Post by adult swim on 2009-01-15
in nautilus, right above the places sidebar, there is an icon that looks like a pen and paper.  if you click that it will display where you are at in a path format, ie /usr/local/bin

---

### Post by 3pinner on 2009-01-15
> **adult swim said:**
> in nautilus, right above the places sidebar, there is an icon that looks like a pen and paper.  if you click that it will display where you are at in a path format, ie /usr/local/bin

Thank you, I know about that, and if I am looking for a single item in a single place, it will give me the complete path.
But in this case I was looking for all mdb files, because there are 3 that I needed in this case; so when the search function finished, all it gave me was /System Files listing- all the mdb files it found.

What would be nice is, as you click on each item in the list, the path would show in that address bar.
But that's why I need to learn Terminal eh? :P

---

### Post by adult swim on 2009-01-15
that would be nice. i guess you could right click and select properties, it has the path in there.

---

### Post by dcstar on 2009-01-15
> **3pinner said:**
> 
........
How do i get nautilus to display the path to the items i am searching for?


Ctrl-L

---

### Post by 3pinner on 2009-01-15
> **dcstar said:**
> Ctrl-L

Wait a minute........
That's Waaaaaaaaaaaaaay too simple!
Linux is supposed to be HARD!!!!!!!!

---

