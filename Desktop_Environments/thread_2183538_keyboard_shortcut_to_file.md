---
title: "keyboard shortcut to file"
date: 2013-10-25
forum: Desktop Environments
---

### Post by cmcanulty on 2013-10-25
I have a keyboard shortcut to a file I use a lot that works in gnome classic but I can't get it to work in xfce. It is ctrl+alt+p and it opens a simple text file. Is there a way to do this in xfce or to get all my keyboard shortcuts to carry over from gnome classic? I am trying out xfce but there are several things that are hard to do in it like this. I tried going to settings-keyboard and typing the path to the file then OK then typed in the key combo but it doesn't work

---

### Post by Bucky Ball on 2013-10-25
Yep, I just got it working without a problem using Application shortcuts. For the command you need to provide whatever command will open the app from a terminal (soffice -writer for instance) then the path to the file you want to open. Like so:

Command: 'soffice -writer /home/user/Documents/MyLeftHand.odt'

Will open the file 'MyLeftHand' in Libre Office Writer. And that's it.

Let us know what code and app you're trying to use if you can't get it happening and we'll see what we can deduce. ;)

---

### Post by cmcanulty on 2013-10-25
Still it won't work here is what I put 'gedit /home/cmcanulty/Documents/file.txt'
(I have another name I used instead of file)

---

### Post by Bucky Ball on 2013-10-25
I don't have Gedit installed so can't help you with that one. I would suggest you use something like:

```
gksudo gedit /home/cmcanulty/Documents/file.txt
```

... though and see if that makes any difference.

---

### Post by cmcanulty on 2013-10-26
OK I got it to work by taking out the quote like this I didn't need gksudo as it is in my home folder. Thanks

gedit /home/cmcanulty/Documents/file.txt

---

### Post by Bucky Ball on 2013-10-26
Excellent. I like it when I see 'solved'. Good luck cm and see you next time. ;)

---

### Post by cmcanulty on 2014-01-23
it doesn't work anymore is there a simple way to shortcut to a file from keyboard?
here is what I have that doesn't work gedit /home/cmcanulty/Documents/MyFile.txt

---

