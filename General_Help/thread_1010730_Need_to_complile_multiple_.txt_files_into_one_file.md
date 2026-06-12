---
title: "Need to complile multiple .txt files into one file"
date: 2008-12-14
forum: General Help
---

### Post by Cideon on 2008-12-14
I need to compile nearly a hundred .txt files into one massive text file without have to open each one individually and do a monotonous copy and paste :confused: Is there a good gui based program to do this? I would prefer not using the terminal simply because there is just to much to type. Please help ](*,)

---

### Post by eBoxNet on 2008-12-14
You can try MELD 
[http://meld.sourceforge.net/](http://meld.sourceforge.net/)

---

### Post by Cideon on 2008-12-14
> **eBoxNet said:**
> You can try MELD 
[http://meld.sourceforge.net/](http://meld.sourceforge.net/)

I installed it but it only allows comparisons of up to three files and its not registering some of the .txt files i have located in the folders. I'm not to worried about copies or identical files, I would gladly settle for a massive, crude compile

---

### Post by eBoxNet on 2008-12-14
check the last post : [http://www.unix.com/shell-programming-scripting/53243-merging-text-files-2.html](http://www.unix.com/shell-programming-scripting/53243-merging-text-files-2.html)

---

### Post by Cideon on 2008-12-14
:( How do i run the command exactly? I'm still relatively new to the terminal and I dont understand where to input the directory

---

### Post by stefangr1 on 2008-12-14
well, you have the text files in one directory, and it is assumed they all have a .txt extension.

You then run:
cat *.txt > /other directory/newfile.txt

You do have to write it to another directory (or don't give the product a .txt estension yet) since otherwise you end up with *twice* the text files.

---

### Post by SPr on 2008-12-14
If they have different names and no extension then open a terminal and type "cat ". Select all the files and drag and drop them into the terminal and add "> bigfile" at the end. Hit enter.

```

/usr/bin/bash
for file in $@
do 
cat $file>>merge.txt
done

```
Save that text as ~/scripts/merge
```

chmod +rx ~/scripts/merge
cd ~/to_directory
./merge *

```
I assume ~/scripts is still in the path. It will merge *all* files into one regardless of the type. And if merge.txt already exists in the present working directory of the terminal it will append the new files to the previous contents.

---

