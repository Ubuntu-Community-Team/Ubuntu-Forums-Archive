---
title: "Resolution looks odd after running CPU at 100% for 4 hours (Please Read)"
date: 2009-03-09
forum: General Help
---

### Post by Neo_The_User on 2009-03-09
OK, I've been compiling gcc 4.4 for like.... 4 - 6 hours now with my 1 GB RAM and my AMD Athlon XP 2000+ overclocked and for like 10 - 15 seconds everything on the screen looks bigger in firefox and my mouse acts funny like skippy and choppy and my keyboard is locking up from time to time. Is there a way I can limit the CPU usage when running 'make' or no? After when my screen mouse and keyboard act weird, it goes back to normal. My actual resolution isn't changing though.

---

### Post by C-- on 2009-03-09
> **Neo_The_User said:**
> OK, I've been compiling gcc 4.4 for like.... 4 - 6 hours now with my 1 GB RAM and my AMD Athlon XP 2000+ overclocked and for like 10 - 15 seconds everything on the screen looks bigger in firefox and my mouse acts funny like skippy and choppy and my keyboard is locking up from time to time. Is there a way I can limit the CPU usage when running 'make' or no? After when my screen mouse and keyboard act weird, it goes back to normal. My actual resolution isn't changing though.

Try running as a background process by typing:

```
make &
```

If you already typed make without the ampersand, hit ctrl-z to freeze the process, then use the command:

```
bg
```

to force it into the background.

---

### Post by Neo_The_User on 2009-03-09
heh right after it finishes compiling I get your post. sorry. thanks though.

---

