---
title: "How to merge a number of pdf files into a single file?"
date: 2009-05-19
forum: General Help
---

### Post by dipaish on 2009-05-19
How to merge a number of pdf files into a single file?

 

Lets say that you have 4 different pdf files named file1.pdf,file2.pdf,file3.pdf and file4.pdf.

 

With the following steps you can create a single file name merged_file.pdf by merging different pdf files.

 

Step 1: Install pdftk

 

deep@deep-laptop:~$ sudo apt-get install pdftk

 

Step 2: Type the following code in the command mode. file1.pdf ,file2.pdf ....are the names of file that we are going to merge . You can merge as many number of files as you want merged_file.pdf is the new megerd pdf file.

 

deep@deep-laptop:~$ pdftk file1.pdf file2.pdf file3.pdf file4.pdf cat output merged_file.pdf

---

### Post by Egi_Power on 2009-05-19
> **dipaish said:**
> How to merge a number of pdf files into a single file?
You could also try using **JoinPDF**.

Egi_Power

---

