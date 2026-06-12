---
title: "strange, blue output from grep/cat"
date: 2006-07-12
forum: Desktop Environments
---

### Post by jegerjensen on 2006-07-12
Hi

I have recently experienced som weird behaviour on the command line of my breezy laptop. I do not think it is a problem but I am puzzled, perhaps someone can explain what is going on?

I started gnome-terminal and did
```

$ grep hal /var/log/base-config.log.1

```
I expected a list of lines containing the pattern 'hal', but instead the terminal went blue and it looked like I was installing something, with progress line and all.  

At first I went paranoid and thought my laptop was hacked or something, but after a little testing I realized that I got the same output from cat and from xterm.  Besides, I did not run as root, so everything should be ok.

I tried googling this, but couldn't find anything.  It is certainly a strange way to store a log... Does anyone know what's happening?   Does it work on your installation?  Any ideas how to grep such a strange file?

:-k

---

