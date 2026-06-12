---
title: "Dpkg problem."
date: 2006-08-04
forum: Desktop Environments
---

### Post by eMuNiX on 2006-08-04
Just about to update my install, ran sudo apt-get update and it got halfway though and gives an error ```
dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
``` so I do as it suggests and sudo dpkg --configure -a this throws another error ```
dpkg: parse error, in file `/var/lib/dpkg/updates/0013' near line 11 package `gdm':
 EOF during value of field `Depends' (missing final newline)
```
How do I fix this?  I have tried sudo apt-get -f install just in case there is a dependency but it goes back to the first error, basically I am in a loop and can't install anything.

---

### Post by eMuNiX on 2006-08-04
Don't worry fixed by adding the new line at the end like it said << need more coffee I think

---

### Post by stamen81 on 2006-08-10
Hi, 
Please tell me how to add this final line. I get mad, I have searched a fix solution but nothing. Please HELP:confused:

---

### Post by maniacmusician on 2006-08-10
hey,
you have to add a line at the end of the document with nothing in it. you open the file, go to the bottom, and make sure the last line is blank. if theres something in the last line, go to the end of the line and hit enter, to create a blank line.

---

