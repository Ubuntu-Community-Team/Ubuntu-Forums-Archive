---
title: "nautilus file type/contents issue"
date: 2007-09-06
forum: Desktop Environments
---

### Post by dsailer on 2007-09-06
I recently started using ubuntu, installed 7.04 a month or so ago. in nautilus when I dbl-click on a file wlth a ppt extension, I get a dialog that says:

cannot open foobar.ppt. The file name "foobar.ppt" indicates that this file is of type "Powerpoint presentation". The contents of the file indicate the the file is of type "mail disposition report". If you open this file, the file might present a security risk........

The dialog has only a cancel button. I can open the file with rt-mouse, "open with", and it opens ok. I can open a different ppt file fine without getting this dialog, so apparently the dialog is telling the truth. It thinks there is something up with the contents of the file. To me, this is very microsoft-like, and frankly I'd like to turn this "feature" off.  Is there a way?

---

### Post by Beggar on 2007-09-07
<Scratch that misread what was happening here>


The problem is that unlike windows, nautilus goes as far as checking the contents of a file to see what type of file it is. In this case based on the filename ppt it is expecting a powerpoint presentation, but after analyzing the contents of the file it sees that it is not a powerpoint file (the program it would normally use to open the file), and thus makes you choose to open that file manually. Have you tried changing the default "Open With" program?

Either way you would need to use the right click - open because otherwise it would try to open this  mail disposition report using OO, which would fail.

---

