---
title: "Shortcut to gnome terminal opens in root directory"
date: 2009-09-08
forum: Desktop Environments
---

### Post by nick_nik on 2009-09-08
Hi All,

I set up a short cut in to gnome terminal in my keyboard shortcuts. When i launch terminal using the keyboard shortcut terminal launches but the working directory is the / slash directory and i'de like it to be my home dir. 

when i launch terminal using gnome-terminal it opens in my home dir which is the same command i used to launch the keyboard shortcut. 


Could somebody explain how to fix it?

Thanks 

Nick

---

### Post by SoftwareExplorer on 2009-09-08
I don't know where you set up keyboard shortcuts, but I think it would do what you want if you change the command to run to ```
gnome-terminal --working-directory=/home/yourUserName
```.

---

### Post by nick_nik on 2009-09-09
Excellent thanks, Did the trick

---

### Post by SoftwareExplorer on 2009-09-09
> **nick_nik said:**
> Excellent thanks, Did the trick

Your Welcome. :) 
You can mark this thread as solved if you go to the thread tools menu.

---

### Post by bzhao on 2011-03-17
Thanks! I have met the same problem and solve it by the post.

---

