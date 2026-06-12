---
title: "How to copy filenames"
date: 2009-05-04
forum: General Help
---

### Post by LOVIN on 2009-05-04
I know how to copy file content but how can I copy a list of the file _names_ of files in a folder to the clip board?

---

### Post by unutbu on 2009-05-04
Open a terminal (Applications>Accessories>Terminal), and type
```

cd /path/to/dir       # Change /path/to/dir to the path you want
ls
ls -1                 # Use the "minus one" flag if you want one filename per line.

```
The filenames will be printed to the terminal.
You can use the mouse to select the text. That copies it to the clipboard.

---

### Post by DeMus on 2009-05-04
> **unutbu said:**
> Open a terminal (Applications>Accessories>Terminal), and type
```

cd /path/to/dir       # Change /path/to/dir to the path you want
ls
ls -1                 # Use the "minus one" flag if you want one filename per line.

```
The filenames will be printed to the terminal.
You can use the mouse to select the text. That copies it to the clipboard.

Or use
```
ls -l > text.txt
```
It will create a text file with the folder listing.

---

### Post by LOVIN on 2009-05-10
Thank you so much.
It solved my problem.

---

### Post by springwater on 2012-07-09
I am new to Ubuntu and wanted to know this myself. I only have a problem with the ls -l script also adding the properties I believe of the file in front of them like this "rzrzrzrza" ect. Is there anything I can add to the ls -l < text.txt script to only copy the filenames as so?
File1
File2
File3

---

### Post by steeldriver on 2012-07-09
> **springwater said:**
> I am new to Ubuntu and wanted to know this myself. I only have a problem with the ls -l script also adding the properties I believe of the file in front of them like this "rzrzrzrza" ect. Is there anything I can add to the ls -l < text.txt script to only copy the filenames as so?
File1
File2
File3


Hi I think you are confusing 2 different options

```
ls -l
```('minus ell') produces the 'long' form of the listing including file permissions etc.

```
ls -1
```('minus one') produces just the filenames, one per line

so you want the 'minus one' form

```
ls -1 > text.txt
```

---

### Post by springwater on 2012-07-09
> **steeldriver said:**
> Hi I think you are confusing 2 different options

```
ls -l
```('minus ell') produces the 'long' form of the listing including file permissions etc.

```
ls -1
```('minus one') produces just the filenames, one per line

so you want the 'minus one' form

```
ls -1 > text.txt
```

Thank you for your help and the quick response.

---

### Post by wildmanne39 on 2012-07-09
Hi, this is an old thread so it has been closed please start a new thread of your own with a descriptive title. 
Thanks

---

