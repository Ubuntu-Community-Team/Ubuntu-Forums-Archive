---
title: "Learning Bash"
date: 2009-05-14
forum: General Help
---

### Post by The-ITu on 2009-05-14
hi Ubuntuers!
I know a *tiny* bit about bash and the terminal and i would like to learn more.
could some one please link me to a book or website for Learning bash.
(I only **think** that the language used in the terminal is named bash)

---

### Post by VCoolio on 2009-05-14
[http://ubuntuforums.org/showthread.php?t=1144449](http://ubuntuforums.org/showthread.php?t=1144449)

---

### Post by glotz on 2009-05-14
Good idea. See [http://en.wikipedia.org/wiki/Bash#External_links](http://en.wikipedia.org/wiki/Bash#External_links)

---

### Post by The-ITu on 2009-05-15
thank you all but for some reson when i save a file as .sh it opens up with ext edito
how do i make it open up in the terminal automaticly?

---

### Post by kpkeerthi on 2009-05-15
> **The-ITu said:**
> thank you all but for some reson when i save a file as .sh it opens up with ext edito
how do i make it open up in the terminal automaticly?

Don't change that. You don't want an arbitrary shell script to be run inadvertently by clicking on it. Consider that a security issue.

Run the .sh file from the command prompt:
1. Grant execute permission:
```
chmod +x myscript.sh
```

2. Then run it:
```
./myscript
```

---

