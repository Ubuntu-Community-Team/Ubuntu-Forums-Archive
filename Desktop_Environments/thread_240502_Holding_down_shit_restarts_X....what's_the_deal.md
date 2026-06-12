---
title: "Holding down shit restarts X....what's the deal?"
date: 2006-08-20
forum: Desktop Environments
---

### Post by offramp13 on 2006-08-20
Whenever i hold down the shift button my Xserver restarts, and its irritating. I dont know if its supposed to be like that but i dont like it. If anyone knows how to help, please do.

---

### Post by Burke on 2006-08-21
I'm sorry I can't help you with your problem, but I have to point out how hilarious it is that you typed ;shit; instead of 'shift'. ;)

---

### Post by Slychilde on 2006-08-21
Would you happen to be running Compiz/XGL by chance?  If so shift+backspace restarts the desktop, annoyed the living crap out of me.  If you are not, I am not sure what is wrong.

---

### Post by offramp13 on 2006-08-21
yeah thats it.... annoying, anyone know how to fix it?

---

### Post by faceoftheearth on 2006-08-21
I don't know a way to fix it a competant way, but I just made the following script and set it to run at login. It changes those keystrokes to mean something else. 

```
#!/bin/bash
xmodmap -e "keycode 22 = BackSpace"

```

---

### Post by offramp13 on 2006-08-26
Thank you very much, if it works, it is compatent enough for me.

---

