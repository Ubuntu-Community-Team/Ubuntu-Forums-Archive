---
title: "Question about hiding files with the &quot;dot&quot; method"
date: 2009-02-17
forum: General Help
---

### Post by cheway on 2009-02-17
Hello all.

Quick question - does placing a dot in front of a filename actually CHANGE the file name?

I.e. if I put a dot in front of "lost+found" so that it becomes ".lost+found", will "lost+found" cease to exist? Would any process that looks for "lost+found" (to place files into) be able to find it?

Sorry if that's a silly question.

---

### Post by heindsight on 2009-02-17
yes, it does change the filename. foo is not the same as .foo and any application that is looking for foo will not look at .foo (unless it's specifically programmed to look for either foo or .foo)

---

### Post by drs305 on 2009-02-17
Yes it changes the file name. Here is a technique to hide files and folders you don't want to see in nautilus. In the same directory as "lost+found", create a text file called ".hidden". Open this file and on the first line type: lost+found

You can add any file or folder name, one per line, you wish to hide. Save the file. If you then tell nautilus to hide *hidden* files, the *.hidden* file and all the files/folders listed within it will be hidden. You can hide/unhide in nautilus with CTRL-H. The files will not be hidden from command line operations.

The lost+found folder is created during an fsck check to store file fragments. If you delete the folder, it will be recreated the next time fsck is run.

---

### Post by cheway on 2009-02-17
Thanks for the replies guys.

So going by what you just said...

> 
The lost+found folder is created during an fsck check to store file fragments. If you delete the folder, it will be recreated the next time fsck is run.

...am I right in saying that if I changed "lost+found" to ".lost+found", a new "lost+found" folder would be created anyway when fsuk is run? So I would have both "lost+found" and ".lost+found"?

Thanks for the .hidden tip, I like that!

---

### Post by matthew.ball on 2009-02-17
> **drs305 said:**
> Here is a technique to hide files and folders you don't want to see in nautilus. In the same directory as "lost+found", create a text file called ".hidden". Open this file and on the first line type: lost+found

You can add any file or folder name, one per line, you wish to hide. Save the file. If you then tell nautilus to hide *hidden* files, the *.hidden* file and all the files/folders listed within it will be hidden. You can hide/unhide in nautilus with CTRL-H. The files will not be hidden from command line operations.
That's awesome, thanks heaps and I wasn't even looking for help with this.

---

### Post by drs305 on 2009-02-17
> **cheway said:**
> ...am I right in saying that if I changed "lost+found" to ".lost+found", a new "lost+found" folder would be created anyway when fsuk is run? So I would have both "lost+found" and ".lost+found"?

Yes, that is exactly what will happen. As for the tip, you are welcome. ;-)

---

