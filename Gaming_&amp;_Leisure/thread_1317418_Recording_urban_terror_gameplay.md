---
title: "Recording urban terror gameplay?"
date: 2009-11-06
forum: Gaming &amp; Leisure
---

### Post by what, what? on 2009-11-06
I recorded some gameplay, and i went to [this website]("http://en.kioskea.net/faq/sujet-4220-make-a-video-of-your-urban-terror-gameplay") and it said i needed to run some shell script in " ~/.q3a/q3ut4/demos" to correct the file names. First off, I have no idea what the whole shell script thing is, and it said to run this : 

#!/bin/bash
rename 'y/a-z/A-Z/' *
rename 's/.DM_68/.dm_68/' * 

Can anybody explain how I am to do this?

---

### Post by what, what? on 2009-11-06
..

---

### Post by 569874123 on 2009-11-07
If u want to watch ur demos, change the name of the demos to capital only or numbers then add the .dm_16
examples:
1.dm_16
2.dm_16
FRAGS.dm_16

---

### Post by what, what? on 2009-11-10
> **569874123 said:**
> If u want to watch ur demos, change the name of the demos to capital only or numbers then add the .dm_16
examples:
1.dm_16
2.dm_16
FRAGS.dm_16

but theyre allready in capital leters..

---

### Post by Technophobia on 2009-11-10
what, what?,

Had a file ugndemo1.dm_68 renamed to UGNDEMO1.dm_68 and I was able to play it. Some odd limitation that required the file names to be capitalised. By the way if you didn't know you play demos from the Urban Terror main menu.

Also if your interested every second Sunday of the month UGN ( Ubuntu Game Night [[http://gwos.org/ugn/doku.php]](http://gwos.org/ugn/doku.php]) ) plays Urban Terror.

---

### Post by what, what? on 2009-11-11
Ok, but how do i rename it?

---

### Post by 569874123 on 2009-11-11
go to the folder with the demos, select one and press f2

---

### Post by what, what? on 2009-11-11
Do you mean the folder on my computer or on the demos thing on the main menu of the game?

---

### Post by what, what? on 2009-11-11
How can i access the folder containing the demos?

---

### Post by what, what? on 2009-11-11
Im surebody knows the answer to how i get to the folder with the demos

---

### Post by Technophobia on 2009-11-11
open up a file browser

type this into the location bar by clicking the pencil at the far left:
[B][SIZE="2"]
~/.q3a/q3ut4/demos[/SIZE][/B]

capitalise only the filename and not the extension. 

A little be of an explanation of the command above. The ~/ at the beginning automatically gets replaced with your home directory after you hit enter. Directories with a '.' at the beginning are hidden, but you may still enter them if you know the name. If you enter your home directory and hit Ctrl + h  all hidden files and directories will be visible until you close the window. The ".q3a/q3ut4" directory is created once you run Urban Terror for the first time.

good luck

---

### Post by what, what? on 2009-11-11
> **Technophobia said:**
> open up a file browser

type this into the location bar by clicking the pencil at the far left:
[B][SIZE=2]
~/.q3a/q3ut4/demos[/SIZE][/B]

capitalise only the filename and not the extension. 

A little be of an explanation of the command above. The ~/ at the beginning automatically gets replaced with your home directory after you hit enter. Directories with a '.' at the beginning are hidden, but you may still enter them if you know the name. If you enter your home directory and hit Ctrl + h  all hidden files and directories will be visible until you close the window. The ".q3a/q3ut4" directory is created once you run Urban Terror for the first time.

good luck

I did what you said and it worked, Thanks!! :)

---

