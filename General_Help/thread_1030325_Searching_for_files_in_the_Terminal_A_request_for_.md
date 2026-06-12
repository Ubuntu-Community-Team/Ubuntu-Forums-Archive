---
title: "Searching for files in the Terminal? A request for basic command-line advice!"
date: 2009-01-04
forum: General Help
---

### Post by Pipps on 2009-01-04
Hello

I would like to know how to use the terminal to search and find files on my local drive. There are a few different ways that I would like to do this, and I am hoping someone can help me with the right commands to use.

I would like to know how to do the following within the terminal:

1. Search for a file anywhere on my local drive called 'readme.txt'?
2. Search for a file within my /home directory called 'readme.txt'?
3. Search for a file anywhere on my local drive, but exclude the entire /media directory from the search? (For instance, where I have a large external USB drive attached at the time of searching, and don't want to wait half an hour for a result.)
4. Search for the specific text, 'guidance' within a file called /home/username/readme.txt?

Your assistance would be much appreciated. Thank you.

---

### Post by zcecc22 on 2009-01-04
Personally I usually do a:

sudo find / -name "fileToFind" that should solve 1. and 2. (ie just change to find /home -name "fileToFind") 

for 3. I suggest looking in the man page, 

for 4. No clue, maybe a combination of cat and grep?

---

### Post by Keith_Beef on 2009-01-04
> **Pipps said:**
> 
4. Search for the specific text, 'guidance' within a file called /home/username/readme.txt?


grep [text to find] [path to file]

This will find each and every line containing the string [text to find].

e.g.
```
$ grep "&#954;&#945;&#964;&#963;&#945;&#961;&#972;&#955;&#945;" ./&#949;&#954;&#956;&#949;&#954;\ &#954;&#945;&#964;&#945;&#912;&#966;&#953;.txt 
-&#914;&#940;&#950;&#949;&#964;&#949; &#963;&#949; &#956;&#943;&#945; &#954;&#945;&#964;&#963;&#945;&#961;&#972;&#955;&#945; &#964;&#951; &#950;&#940;&#967;&#945;&#961;&#951; &#954;&#945;&#953; &#964;&#945; &#945;&#965;&#947;&#940;
-&#932;&#959;&#960;&#959;&#952;&#949;&#964;&#949;&#943;&#964;&#949; &#963;&#964;&#951; &#966;&#969;&#964;&#953;&#940; &#964;&#951;&#957; &#954;&#945;&#964;&#963;&#945;&#961;&#972;&#955;&#945; &#954;&#945;&#953; &#945;&#957;&#945;&#954;&#945;&#964;&#949;&#973;&#949;&#964;&#949; &#956;&#941;&#967;&#961;&#953; &#957;&#945; &#960;&#940;&#961;&#949;&#953; &#946;&#961;&#940;&#963;&#951;
-&#917;&#957; &#964;&#969; &#956;&#949;&#964;&#945;&#958;&#973; &#946;&#961;&#940;&#950;&#949;&#964;&#949; &#963;&#949; &#956;&#943;&#945; &#940;&#955;&#955;&#951; &#954;&#945;&#964;&#963;&#945;&#961;&#972;&#955;&#945; &#964;&#959; &#957;&#949;&#961;&#972; &#954;&#945;&#953; &#964;&#951; &#950;&#940;&#967;&#945;&#961;&#951; &#956;&#949; &#964;&#945; &#956;&#965;&#961;&#969;&#948;&#953;&#954;&#940; &#957;&#945; &#966;&#964;&#953;&#940;&#958;&#949;&#964;&#949; &#964;&#959; &#963;&#953;&#961;&#972;&#960;&#953;
```

Add the -n switch to show the line number of occurences.

```
$ grep "&#954;&#945;&#964;&#963;&#945;&#961;&#972;&#955;&#945;" -n ./&#949;&#954;&#956;&#949;&#954;\ &#954;&#945;&#964;&#945;&#912;&#966;&#953;.txt 
17:-&#914;&#940;&#950;&#949;&#964;&#949; &#963;&#949; &#956;&#943;&#945; &#954;&#945;&#964;&#963;&#945;&#961;&#972;&#955;&#945; &#964;&#951; &#950;&#940;&#967;&#945;&#961;&#951; &#954;&#945;&#953; &#964;&#945; &#945;&#965;&#947;&#940;
21:-&#932;&#959;&#960;&#959;&#952;&#949;&#964;&#949;&#943;&#964;&#949; &#963;&#964;&#951; &#966;&#969;&#964;&#953;&#940; &#964;&#951;&#957; &#954;&#945;&#964;&#963;&#945;&#961;&#972;&#955;&#945; &#954;&#945;&#953; &#945;&#957;&#945;&#954;&#945;&#964;&#949;&#973;&#949;&#964;&#949; &#956;&#941;&#967;&#961;&#953; &#957;&#945; &#960;&#940;&#961;&#949;&#953; &#946;&#961;&#940;&#963;&#951;
33:-&#917;&#957; &#964;&#969; &#956;&#949;&#964;&#945;&#958;&#973; &#946;&#961;&#940;&#950;&#949;&#964;&#949; &#963;&#949; &#956;&#943;&#945; &#940;&#955;&#955;&#951; &#954;&#945;&#964;&#963;&#945;&#961;&#972;&#955;&#945; &#964;&#959; &#957;&#949;&#961;&#972; &#954;&#945;&#953; &#964;&#951; &#950;&#940;&#967;&#945;&#961;&#951; &#956;&#949; &#964;&#945; &#956;&#965;&#961;&#969;&#948;&#953;&#954;&#940; &#957;&#945; &#966;&#964;&#953;&#940;&#958;&#949;&#964;&#949; &#964;&#959; &#963;&#953;&#961;&#972;&#960;&#953;
```

This shows that the string "&#954;&#945;&#964;&#963;&#945;&#961;&#972;&#955;&#945;" occurs in lines 17, 21 and 33 of the file.

The grep command is extremely powerful, and you should at least try reading the man page for it, and probably the sections on grep in O'Reilly's Unix Power Tools.

---

### Post by kaibob on 2009-01-04
> **Pipps said:**
> ...3. Search for a file anywhere on my local drive, but exclude the entire /media directory from the search? (For instance, where I have a large external USB drive attached at the time of searching, and don't want to wait half an hour for a result.)...

Some time back, I tried to find something such as this but couldn't come up with anything. I finally started using the -xdev option, which is described in the man file as "don’t descend directories on other filesystems." For me, this keeps all find searches out of Windows and external usb drives. If you come up with something better, please let me know.

---

### Post by Keith_Beef on 2009-01-04
> **kaibob said:**
> Some time back, I tried to find something such as this but couldn't come up with anything. I finally started using the -xdev option, which is described in the man file as "don&#8217;t descend directories on other filesystems." For me, this keeps all find searches out of Windows and external usb drives. If you come up with something better, please let me know.

I mentioned above that grep is extremely powerful... but find is even more powerful and confusing than grep.

There is a -prune switch to ingore a directory and its subdirectories.

From the man page for find:

```
 To ignore a whole directory tree, use -prune rather than checking every file in the tree.
For example, to skip  the  directory  &#8216;src/emacs&#8217;  and  all files and directories under it,
and print the names of the other files found, do something like this:
           find . -path ./src/emacs -prune -o -print
```

Once again: read the man page and the O'Reilly book.

---

### Post by fragos on 2009-01-05
If you want to find a file anywhere try "locate file.txt" on the command line. Whenever you boot or run "sudo updatedb" locate's data base is updated. Search is instantanious and would respond with full path to every url which contained the search argument. "locate .jpg" will give you all .jpg files on your system.

---

