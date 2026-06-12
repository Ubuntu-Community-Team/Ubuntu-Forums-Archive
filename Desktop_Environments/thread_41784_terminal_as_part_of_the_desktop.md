---
title: "terminal as part of the desktop?"
date: 2005-06-14
forum: Desktop Environments
---

### Post by angryfix on 2005-06-14
Is there a program that literally makes the terminal a part of the desktop? I've already experimented with opening a full-sized terminal window and setting it to full transparency, but I'd rather just have a terminal that's "always there." Any ideas?

---

### Post by Takis on 2005-06-14
This *might* help.
[http://ubuntuforums.org/showthread.php?t=36811](http://ubuntuforums.org/showthread.php?t=36811)

---

### Post by angryfix on 2005-06-14
Thanks, it's so close to working. The only problem is the transparency, given by option --trans isn't working on startup. When Ubuntu starts up, the terminal is there, but there's a  background to it. The odd thing is when I exectute Eterm in the terminal after startup with --trans, the transparency works perfectly. So do I need to modify something, or create a file that exectutes the code after startup to make sure the transparency works.

---

### Post by Takis on 2005-06-15
There are a number of places you can put a call to start Eterm upon logon, but since (I'm guessing) you're using GNOME I have no idea where to put it. It'll have to be somewhere after the X server has started.

---

