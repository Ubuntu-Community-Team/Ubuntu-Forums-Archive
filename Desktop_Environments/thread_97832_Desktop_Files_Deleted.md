---
title: "Desktop Files Deleted"
date: 2005-12-01
forum: Desktop Environments
---

### Post by jdway on 2005-12-01
I am not sure what happened exactly so all I can tell you is what I was doing before the error occured. I was toying with the multimedia systems selector in order to play cd's and installing goobox when something strange happened. After I installed goobox i went to click on a music file on my desktop and the file disappeared. I then proceeded to click on a text file and then a folder and they both were deleted as well (just by clicking on them one time). I performed a search on my home folder and the file system but I could not find the files. I then rebooted the system and on the boot screen instead of giving me the option to choose either ubuntu, ubuntu recovery, or windows there are two ubuntu listings as well as two copies of ubuntu recovery mode.  Is there any way to get the files back or am I screwed? More importantly, what did I mess up so I will not do it again.

---

### Post by jdway on 2005-12-01
I also just realized that everything in my home folder has been deleted. Approximately 20G of music, video, and text files have just been deleted in a matter of seconds. Someone please tell me there is hope.

---

### Post by anil_robo on 2005-12-01
Did you check your recycle bin? It lies at lower right corner of screen.

---

### Post by jdway on 2005-12-01
Yes, I checked the recycle bin but there was they files that were recently lost were not there. Only the ones which I intentionally deleted were present.

---

### Post by cwaldbieser on 2005-12-01
[QUOTE=jdway]Yes, I checked the recycle bin but there was they files that were recently lost were not there. Only the ones which I intentionally deleted were present.[/QUOTE]
If you open a terminal and type
```

$ ls Desktop

```
are the files listed?  Maybe they were just hidden or moved somewhere else?  Not sure what you did.

---

### Post by jdway on 2005-12-01
No the files are not listed. I thought that they may be deleted but I dont see how it could delete so much information so quickly.

---

### Post by cwaldbieser on 2005-12-01
[QUOTE=jdway]No the files are not listed. I thought that they may be deleted but I dont see how it could delete so much information so quickly.[/QUOTE]
Well, unlinking a file (what the "rm" command does) is actually pretty quick.  The filesystem does not actually clear out all the data-- it just marks that node as clear to write stuff over.  It doesn't depend on the amount of data.

Is anything in /lost+found?  Sometimes messed up data gets put there after being reclaimed by an fsck...

I am really puzzled.  I am not sure what could have caused the problem you describe.

---

### Post by jdway on 2005-12-02
Nope, there was nothing in the lost and found folder.

---

### Post by jdway on 2005-12-02
I figured out what the problem was. I downloaded baobab and looked to see if there was anything unusual and I found the files. Somehow they managed to end up in the firefox 1.5 folder that I had installed on a test run earlier that day and then uninstalled. I dont know how they got there but everything is back to normal now.

---

