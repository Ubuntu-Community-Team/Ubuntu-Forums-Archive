---
title: "blackbox style"
date: 2006-06-29
forum: Desktop Environments
---

### Post by Family_Guy on 2006-06-29
I've got a script for a blackbox style, problem is it wont let me save it to usr/share/blackbox/styles/ 

Here's the error.

Could not save the file "/home/familyguy/usr/share/blackbox/styles/Enough"

Pretty vague.

---

### Post by oldmanstan on 2006-06-29
what program are you using to save? in order to save in that directory you need root permissions so you need to run the command or program using sudo, for instance:
```
sudo gedit
```
would launch the text editor as the root user

---

### Post by Family_Guy on 2006-06-29
I tried that and it still wouldn't let me save, I got past that with a tip from another thread, still, even though I pointed to the file (which is now in the usr/share/blackbox/styles/) folder, it's not loading up when I log in with blackbox.

---

### Post by oldmanstan on 2006-06-29
so the file IS there? or it isn't there? need more information:

what program are you using to "save" it? are you actually trying to SAVE the file from and editor or are you just trying to MOVE the file into that directory?

if you just need to MOVE the file then do this in a terminal:
```
sudo cp /original/file/path/style.whatever /usr/share/blackbox/styles/style.whatever
```

otherwise you have to provide more info as mentioned above

---

### Post by nevle on 2006-07-01
Have you tried saving in ~/.blackbox/styles then pointing to that location in ~/.blackboxrc? Bit of a cop out but might work.:rolleyes:

---

