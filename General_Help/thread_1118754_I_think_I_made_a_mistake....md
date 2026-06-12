---
title: "I think I made a mistake..."
date: 2009-04-07
forum: General Help
---

### Post by BardSeed on 2009-04-07
I need help recovering my Desktop. I was following a tutorial from this [site]("http://linuxcommand.org/lts0060.php") and decided to try a few commands. Here's what I did:
```
ciaran@ciaran-desktop:~/Music$ ls > file_list.txt
ciaran@ciaran-desktop:~/Music$ ls
file_list.txt             The_blues_collection    Tool
Jimi_Hendrix-Discography  The_blues_collection_2
ciaran@ciaran-desktop:~/Music$ mv file_list.txt /Desktop
mv: cannot move `file_list.txt' to `/Desktop': Permission denied
ciaran@ciaran-desktop:~/Music$ sudo mv file_list.txt /Desktop
[sudo] password for ciaran: 
```
As you can see, I decided to move my newly made file_list.txt to the desktop. Unfortunately, I've written over Desktop. Can somebody help me?

---

### Post by taurus on 2009-04-07
The problem is /Desktop is not the same as your desktop, ~/Desktop.  Try

```
cp /Desktop ~/Desktop/file_list.txt
ls -la ~/Desktop
```

---

### Post by 3Miro on 2009-04-07
Go to the terminal and type:
```

sudo nautilus

```

NOW BE VERY CAREFUL, you don't want to delete something wring.

You copied your file to /Desktop which is not your desktop folder. Using Nautilus go to / (click on the files system on the left). Delete Desktop (first open it to see what you are deleting).

Whet you initially wanted to do should be done via:
```

$ ls > file_list.txt
$ mv file_list.txt /home/ciaran/Desktop

```

Alternatively:
```

$ mv file_list.txt ~/Desktop

```

~/ is your home folder.

---

### Post by BardSeed on 2009-04-07
```
ciaran@ciaran-desktop:/$ cp /Desktop ~/Desktop/file_list.txt
ciaran@ciaran-desktop:/$ ls -la ~/Desktop
total 100260
drwxr-xr-x  3 ciaran ciaran     4096 2009-04-07 15:36 .
drwxr-xr-x 39 ciaran ciaran     4096 2009-04-07 15:16 ..
-rw-r--r--  1 ciaran ciaran 11849763 2009-04-05 04:36 linux_starter_pack.zip
-rw-r--r--  1 ciaran ciaran  2064348 2009-04-05 04:35 ubuntupocketguide-v1-1.zip

```
Seems like it worked, right?

---

