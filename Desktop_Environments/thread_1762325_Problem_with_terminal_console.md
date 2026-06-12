---
title: "Problem with terminal console"
date: 2011-05-19
forum: Desktop Environments
---

### Post by ilyatau on 2011-05-19
Hello,
In my ubuntu in terminal if I press letter "f" or "b" nothing happened, it not output it. And one strange thing, if I copy word with letters "f" or "b" and paste to console they disappeared from word. example: copy word "Hello far boo" it paste "Hello  ar  oo"
Any ideas?
Thank you.

---

### Post by Copper Bezel on 2011-05-19
Very strange.

I wonder if your .bashrc or terminal profile could be wonky - I don't know what else could cause the problem. To test the later, try another terminal emulator, like xterm. If it works, we'll fix your terminal settings so you can continue using Gnome Terminal. If it doesn't, try creating a new user account and seeing if the problem persists there. If it doesn't, we'll reset your user account's .bashrc. 

If the problem does persist both in xterm and in Gnome Terminal in a separate user account, I really wouldn't know what the next step would be, as a problem in the system bash profile would doubtless have caused you other problems by now.

---

### Post by ilyatau on 2011-05-19
Ok,
It's happened in xterm, but with new user it's all right. 
How reset my user account's .bashrc?

EDIT: Ok I found how to reset this in [http://ubuntuforums.org/showthread.php?t=1185571]("http://ubuntuforums.org/showthread.php?t=1185571")

Thank you

---

### Post by Copper Bezel on 2011-05-19
Excellent - I'm glad that worked out!

Please mark the thread as solved in Thread Tools at the upper right. = )

---

