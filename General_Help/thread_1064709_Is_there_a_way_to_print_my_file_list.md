---
title: "Is there a way to print my file list?"
date: 2009-02-09
forum: General Help
---

### Post by Survivalism on 2009-02-09
I need to know if there is a way to print my file list.

I have all of my music and movies on hard drives, and would like to be able to print a list of all available files.  I don't care if I need to download a new file browser, I just need to know which one.

---

### Post by geirha on 2009-02-09
In the terminal you can do something like this:
```
find $HOME/Video $HOME/Music > $HOME/mediafilelist.txt
```
It will recursively find all files and folders under Video and Music in your home folder and store the list in mediafilelist.txt in your homedir. The text file should be easy to print. Also, the find command is very feature rich, so the list can be further filtered if you feel that is necessary.

---

### Post by ajgreeny on 2009-02-09
It should be```
 ls -lhR /home/username/Music
```You can vary the options if you want.  In my example the** l** gives you all info on each file, the **h** gives sizes in Kb or Mb, and the **R** does the job recursively.  You will find the file music.txt in your home folder.

---

### Post by howefield on 2009-02-09
> **ajgreeny said:**
> It should be```
 ls -lhR /home/username/Music
```

Hmmm... didn't work for me, other than list the documemts in the terminal but no txt file ?

---

### Post by ajgreeny on 2009-02-09
Sorry, I forgot the end part of the command.  Stupid me!! ```
ls -lhR /home/username/Music > music.txt
```

---

### Post by Survivalism on 2009-02-09
Thank you very much.  This works very well for me.  Much easier than trying to remember what I have when people ask.  

Also helps when I go to buy new movies or CDs.  I see them on sale and think "Man, that's awesome.  I should buy it."  Then I get home and realize I already have it.  I give away a lot of good stuff to my friends and family.

I need to start learning these commands...

---

