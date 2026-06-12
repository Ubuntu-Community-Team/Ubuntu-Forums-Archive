---
title: "Highlight code in Gedit"
date: 2006-01-05
forum: Desktop Environments
---

### Post by Zariski on 2006-01-05
Hello!

If I open a java (or html, php, ... ) file in Gedit, the code is automatically colored. But if I create a newfile, say by typing "gedit Test.java", the code I write is not highligted, not even if I save the file and reopen it. How can that be? Why are my java files different from other java files?

Thanks!

---

### Post by bjourne on 2006-01-05
That's a bug in gedit (or gtksourceview). When you type "gedit Test.java", gedit creates a new textbuffer named "Test.java" without any syntax highlighting. When you save it, gedit remembers that the file was last edited without syntax highlighting and therefore doesn't load Java syntax highlighting as it should. View->Syntax highlighting->Source codes->Java should fix it. :)

---

