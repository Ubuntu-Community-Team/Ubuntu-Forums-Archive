---
title: "Have Conky Run Terminal Commands?"
date: 2009-01-21
forum: General Help
---

### Post by transmition on 2009-01-21
Hello, I was wondering if it is possible to have Conky run terminal commands such as netstat. I have read into embedded terminals on the desktop, however, I wish to have commands launch on bootup, rather then having to type them into an embedded terminal.

So, is this possible?

---

### Post by m_duck on 2009-01-21
Hey, I've not used Conky in a while, but you might want to take a look at the "exec" and "execi" variables [here]("http://conky.sourceforge.net/variables.html").

Exec is to run a command once, and you can use ```
${execi ## ...}
``` to run ... every ## seconds.

Hope this is of some help!

(Also, check out [this conky thread]("http://ubuntuforums.org/showthread.php?t=281865"). A lot of useful info plus a lot of people willing to help.)

---

