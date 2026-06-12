---
title: "Removing whitespaces in folder names"
date: 2009-06-11
forum: General Help
---

### Post by zainka on 2009-06-11
Hi

I have a bunch of projects, actually a huge pile of projects moved from a windows environment to Linux. All are gcc projects but I have problems making them since most of the paths includes whitespaces.

I therefor wondered if there are any tools I could use to rename all folders given and replace white spaces with _  . I am using krusader with krename but I could not find any options for what I am trying to do.

Any sugestions??

Breg
Vidar

---

### Post by kaibob on 2009-06-11
Post deleted by kaibob.

---

### Post by Cowchip7 on 2009-06-11
I took one Unix class and now refuse to use spaces when naming file. :D People at work think I'm crazy!

---

### Post by _Purple_ on 2009-06-11
You can use rename. See
```
man rename
```

---

### Post by ActiveFrost on 2009-06-11
Operations with files containing spaces in their names :
```
cp "your file name" $HOME/somewhere/
```
Add your file name into quotation marks and you'll be able to do whatever you want with it.

Regarding mass-rename, this thread should help you ( the same question ) : [http://ubuntuforums.org/showthread.php?t=832948](http://ubuntuforums.org/showthread.php?t=832948)

---

### Post by Metallion on 2009-06-11
Open a terminal and type this command in the directory where those files/folders are:
```
rename -v 'y\" "\_\' *
```

---

### Post by zainka on 2009-06-11
Hi
 and Thnx

> rename -v 's/[ \t\r\n\f]/_/g' *


-Did the trix... 
It replaced all whitespaces in a second according to the output 
> 
.
.
.
Z016 AM receiver renamed as Z016_AM_receiver
Z017 Keyboard switcher renamed as Z017_Keyboard_switcher
.
.



One could also used
> rename -v 's/ /_/g' *


By replacing -v with -n one would get a preview instead, but no changes would be done.

---

