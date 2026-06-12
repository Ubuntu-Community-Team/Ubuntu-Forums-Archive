---
title: "Terminal command to continuously repeat a command."
date: 2006-09-22
forum: Desktop Environments
---

### Post by earobinson on 2006-09-22
Im sure I have seen this command before but now I cant find it. what I want is a command that I can do type that will continuously update the terminal will the output of that command until I am done.

For example if I am copying a file from one dir to another in one terminal I would like to be able to do a ls -lh and have it continuously update so I can see the size copied so far.

thanks

---

### Post by thhp on 2006-09-22
This might do what you want:

```

while [ 1 ]; do ls -lh; sleep 1; done

```

When you're tired of seeing the output of 'ls', you can stop the command using CTRL+C.

Btw, for more on Bash scripting there is a good resource here:

[http://www.tldp.net/LDP/abs/html/](http://www.tldp.net/LDP/abs/html/)

---

### Post by earobinson on 2006-09-22
Ya that would work. anyone know of one that wont scroll the output?

---

### Post by mbeierl on 2006-09-22
watch is the command that I use.  It displays a top-like listing of output.

```
watch -- ls -lh
```

---

### Post by Jun0 on 2007-05-15
geart

---

