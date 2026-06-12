---
title: "Thinkfinger on XPS M1330"
date: 2008-08-29
forum: Dell Ubuntu Support (CLOSED)
---

### Post by undoIT on 2008-08-29
I installed thinkfinger on my XPS M1330 with Ubuntu 8.04.1 64-bit. For the most part it is working great. However, after suspend there is no prompt to swipe finger and the finger print reader does not work. If I just press enter and wait for the prompt to tell me I put in the wrong password, the swipe finger prompt shows up and then I can use it.

Is anybody else having this problem or know of a fix?

---

### Post by superm1 on 2008-08-29
> **undoIT said:**
> I installed thinkfinger on my XPS M1330 with Ubuntu 8.04.1 64-bit. For the most part it is working great. However, after suspend there is no prompt to swipe finger and the finger print reader does not work. If I just press enter and wait for the prompt to tell me I put in the wrong password, the swipe finger prompt shows up and then I can use it.

Is anybody else having this problem or know of a fix?
It's a race condition caused by how quickly the USB device is found post resume.  Just hit esc if it's not there immediately and try again.

---

### Post by undoIT on 2008-08-29
Pressing Esc takes even longer to reload the prompt than pressing Enter. I think I need to buy Thinkfinger a new pair of running shoes ;)

---

