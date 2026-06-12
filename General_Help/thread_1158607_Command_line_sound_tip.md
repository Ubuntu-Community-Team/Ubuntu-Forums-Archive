---
title: "Command line sound tip"
date: 2009-05-13
forum: General Help
---

### Post by PaulWhipp on 2009-05-13
I often run quite time consuming tasks at the command line and its nice to get a sound to let me know when the task is complete because I've often moved off to other windows etc.

Here is how I play a sound at the command line:
```

~ $ aplay -q /usr/share/sounds/question.wav

```

So, for example, if I'm getting a handy list of all of the free sounds available on my system and I want to hear when the job has finished:
```

~ $ find /usr/share/sounds -name "*.wav" -print > sounds; aplay -q /usr/share/sounds/question.wav


```

---

### Post by KhurramM on 2009-05-13
Nice useful tip

Thanks.

But this should gone into Tips and Tutorials Section.

---

### Post by PaulWhipp on 2009-05-13
Good tip :)

Don't know if I can move it now though.

thanks

---

