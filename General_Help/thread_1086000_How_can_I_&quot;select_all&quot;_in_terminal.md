---
title: "How can I &quot;select all&quot; in terminal"
date: 2009-03-03
forum: General Help
---

### Post by firsttimeuser on 2009-03-03
i use gui a lot, and sometimes I got more than 2000 lines in the terminal and I need copy them over to other text editor, am wondering how can I "select all" content in ubuntu terminal?

---

### Post by cosine352 on 2009-03-03
> history > 'file name to save' 

may be ?

---

### Post by firsttimeuser on 2009-03-03
sorry, that won't work.

> **cosine352 said:**
> may be ?

---

### Post by cosine352 on 2009-03-03
I am not sure what are you trying to do ????????

---

### Post by firsttimeuser on 2009-03-03
say I open up terminal and log into a router, and I do several "show" command and get more than 1000 lines as result. Waht I want here is somehow copy select all the lines, and then paste the result to somewhere else like vi so I can do all kinds of search and edit...

---

### Post by Ryback on 2009-03-03
Try appending 
```
> filetobewrittento.txt
```
to the end of your code.  E.g.
```
ls > listing.txt
```
would send the output of the ls command to a file called listing.txt in the current working directory.  You can then text edit to your heart's content.

---

### Post by tumerictj on 2012-09-07
Just click Edit -->Select All from gnome-terminal.  You may also be interested in the ```
script
``` command (see ```
man script
```).

---

### Post by papibe on 2012-09-07
This is an old thread. It is closed now.

---

