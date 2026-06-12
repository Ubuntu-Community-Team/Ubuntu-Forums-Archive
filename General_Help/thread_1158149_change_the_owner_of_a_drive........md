---
title: "change the owner of a drive......."
date: 2009-05-13
forum: General Help
---

### Post by muctadir on 2009-05-13
in my computer root is the owner of all drives.......

how can i be the owner???

i tried        sudo chown -R yourusername:yourusername  diskname
but not working.........

am i using it wrongly????
pls help.........

---

### Post by mikewhatever on 2009-05-13
A diskname is usually just a label. Try chown'ing the mount point.

---

### Post by muctadir on 2009-05-13
how to do that 
pls explain.........

---

### Post by mikewhatever on 2009-05-13
sudo chown yourusename mount-point

You can find out what's mounted and where with the **df -h** command. You might want to run that command, post the output and specify the drives in question.

---

### Post by stathol on 2009-05-13
Wait...what?

Which directories are you trying to chown? The root user and group *should* be the owner of /, as well as the disk and disk partition devices themselves (ex. /dev/sda1). I would strongly advise that you not attempt to chown / to someone else, especially not recursively. That would likely result in Bad Things(TM).

---

