---
title: "Qcad printing problem"
date: 2005-11-10
forum: Desktop Environments
---

### Post by Pete051 on 2005-11-10
I've just found out that Qcad apparently can't see the printer, The setup printer shows nothing at all odd as it works with every thing else. Ideas anyone?
Pete

---

### Post by Joe_lurker on 2005-11-10
I had the same problem but I could not find any information how QCad sees printers.  Since it is a QT application it probably needs something from KDE that isn't running/present.  Here is a work around:

Open a terminal window to the folder your home folder.
Print the drawing to file and send it to your home folder.  Name the file printer.ps.
In the terminal enter thcommand 'lpr -P <printer> printer.ps'  Where <printer> is the name of the printer you want to output to.  Once you have entered the command in the terminal you can reissue that command by pressing the up arrow then press enter.

Not pretty but it works.

-Joe

---

### Post by sawjew on 2005-11-22
Check out this, it solves the problem.

[http://www.linuxquestions.org/questions/showthread.php?s=&threadid=363383&highlight=no+printer+qcad]("http://www.linuxquestions.org/questions/showthread.php?s=&threadid=363383&highlight=no+printer+qcad")

I had the same problem and now its fine.

---

### Post by dreadnought on 2005-12-04
Worked for me too.
Thanks sawjew for the link.

---

