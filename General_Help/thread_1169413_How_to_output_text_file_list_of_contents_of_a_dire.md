---
title: "How to output text file list of contents of a directory?"
date: 2009-05-25
forum: General Help
---

### Post by Pipps on 2009-05-25
I have a directory which contains 30 files.

How may I create a simple text file which contains all over the file names of the files in this directory?

Thank you.

---

### Post by m_duck on 2009-05-25
A simple way would be to **cd** to the directory and then run **ls > file.txt**. So for example if the directory in question in ~/Documents:```
cd ~/Documents
ls > file.txt
```

---

### Post by Pipps on 2009-05-25
Sir, that works perfectly! Thank you! :)

---

### Post by Iusedtowearatie on 2009-05-25
alt 1)
Show all the files in a normal window, select View - List, mark the files using the mouse, ctrl-c.
Open a text editor (gEdit, Writer, whatever) and paste (e.g. using ctrl-v)

alt 2)
Open a terminal window. Move to the directory in question using the cd command. Then enter "ls > filename.txt" and the list will be found in the file namned filename.txt.

---

### Post by cmost on 2009-05-25
Another simple way to print the contents of a directory is to use Firefox / Iceweasel / Swiftfox.  This works in Windows or Mac too (it's stupid that Windows Explorer can't print a directory listing without third party software.)

Simply type the location in the Address bar of the folder whose contents you wish to list.  Example:  /home  and hit Enter.

Firefox now displays the contents of the directory in a very neat fashion.

Either file->print it directly, or print to file or if CUPS-pdf is installed, to a PDF file for safe-keeping.

Viola! :D

---

### Post by Pipps on 2009-05-25
So many options!

Thank you so much much! :)

---

### Post by captainron042 on 2011-05-30
Any way to include subfolders?

For instance, I want to return a list of all filenames in "pictures", including folders: "may", "feb", "march", ect

---

### Post by AlphaLexman on 2011-05-30
> **captainron042 said:**
> Any way to include subfolders?
Use the '**tree**' command.
```
tree ~/Pictures > files_and_subfolders.txt
```

---

