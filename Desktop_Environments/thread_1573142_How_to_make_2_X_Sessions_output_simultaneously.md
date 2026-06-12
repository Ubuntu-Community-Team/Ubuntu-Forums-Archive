---
title: "How to make 2 X Sessions output simultaneously?"
date: 2010-09-12
forum: Desktop Environments
---

### Post by KingNeil on 2010-09-12
I started a new x session on tty8. This is display 1. The first session is tty7 display 0.

I can switch between them easily enough. CTRL ALT F7 goes to tty7. CTRL ALT F8 goes to tty8.

But if I try to run, say, the "import" command for screenshots on tty8, while switched to tty7, all it gives is a black screen.

The reason being, I think, because only one session is actually outputting at any given time. How do I make both of them output, so I can take a screenshot on 1 session, but use the other session to do other stuff?

---

### Post by ronnielsen1 on 2010-09-13
[http://www.tuxfiles.org/linuxhelp/multiple-x.html](http://www.tuxfiles.org/linuxhelp/multiple-x.html)

I've wondered that myself. You can try this

---

### Post by KingNeil on 2010-09-13
No, that isn't what I'm looking for. startx starts a new session, but you can only switch between one and another. You can't receive output from both at the same time. If I run import on session 2 while switched to session 1, all I get is a black screen, because session 2 is not actually outputting at the same time.

---

