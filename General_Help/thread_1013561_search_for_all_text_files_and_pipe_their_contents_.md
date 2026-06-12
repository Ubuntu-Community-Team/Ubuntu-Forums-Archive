---
title: "search for all text files and pipe their contents into one file?"
date: 2008-12-17
forum: General Help
---

### Post by wildgraphite on 2008-12-17
Hi.
I was just trying to take all of my writing and put it into one file to manipulate with dadadodo.  I can't seem to figure out how to with the terminal.
Thanks!
-Alden

---

### Post by lensman3 on 2008-12-17
cat *.txt >output.txt

will concatenate (oxymoron word) all txt files into "output.txt"


ls -1 *.txt >output.sh

will dump all the names of the txt files into a file called output.sh with one file per line.  The dash is a dash-one.

find . -name "*.txt" >output.txt
will dump one file ending in txt to output.txt and will go down the directory tree.

---

### Post by Poyntz on 2008-12-17
also if you happen to leave a file out don't type
cat <left out file> > output.txt because it will rewrite the file and you'll loose everything already there
type:
```
cat <left out file> **>>** output.txt
``` - this will add the text to the file and leave all the information in that file intact

---

### Post by dcstar on 2008-12-17
> **lensman3 said:**
> cat *.txt >output.txt

will concatenate (oxymoron word) all txt files into "output.txt"
........

"Text files" do not necessarily have a .txt extension, this is not DOS/Windows.

There may be a way of identifying any text file by its magic number, but I'm not aware of it.

---

### Post by Poyntz on 2008-12-17
> **dcstar said:**
> "Text files" do not necessarily have a .txt extension, this is not DOS/Windows.

1. oh... are you suggesting .txt standard for naming text files is only applicable to DOS/Windows because I can assure you it is quite widely accepted across platforms.
2. you can grant text files any extension you like on any platform, however, on certain platforms it's a lot easier to read files if they have the .txt extension
3. both out posts only use the .txt extension as an example. try the code we have both supplied and output the text into files with other extensions and you'll find it works in much the same way

---

