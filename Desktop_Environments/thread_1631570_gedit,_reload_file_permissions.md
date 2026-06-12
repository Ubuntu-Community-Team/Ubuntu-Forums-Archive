---
title: "gedit, reload file permissions?"
date: 2010-11-26
forum: Desktop Environments
---

### Post by mesh2005 on 2010-11-26
Is there anyway to force gedit to be aware of changes made to file permissions? The thing is, sometimes I open a readonly file and I just go back to the terminal and set write permissions on that file, but I have to close and open the file again so that gedit saves it. Is there anyway we can make gedit aware of changes to file permissions?

---

### Post by asmoore82 on 2010-11-26
I just tested this on 10.04 and gedit does immediately notice file permission changes automagically.

---

### Post by oldfred on 2010-11-27
I just right click, open with other applications, Click on use custom command and it opens a terminal line. If I enter gksudo gedit it will also remember that as a custom command, so I do not have to type it again.

---

