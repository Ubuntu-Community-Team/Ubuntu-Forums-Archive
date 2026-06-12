---
title: "swapping keyboard keys?"
date: 2007-02-21
forum: Desktop Environments
---

### Post by BigCdaAnswer3 on 2007-02-21
I just recently bought a new laptop that has the fn(function) key where the left control should be. this is pissing me off to no end and i'm wondering if there's anyone here that knows how to use xev or xmodmap to switch the functionality of these two keys? xev doesn't return an event when the fn button is pressed....

---

### Post by RedSquirrel on 2007-02-22
If xev didn't show anything, I'm pretty sure you're out of luck in using that key in linux. xmodmap won't help if xev didn't show anything when you pressed the key.

---

