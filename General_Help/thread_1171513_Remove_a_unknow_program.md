---
title: "Remove a unknow program"
date: 2009-05-27
forum: General Help
---

### Post by DouglasCaixeta on 2009-05-27
Hi,

I have a program installed in my computer, and it brings a quote everytime I open the terminal. I don't know the name of this program, but I want to remove it. I already search on the internet, but I can't figure it out the name of this.

Here is an example of a quote:

```
 ___________________________________
( After all, all he did was string  )
( together a lot of old, well-known )
( quotations.                       )
(                                   )
( -- H. L. Mencken, on Shakespeare  )
 -----------------------------------
  o
   o   \_\_    _/_/
    o      \__/
           (oo)\_______
           (__)\       )\/\
               ||----w |
               ||     ||
```

Everytime I open the terminal, brings a new one.
Anyone know the name of this program?

---

### Post by ActiveFrost on 2009-05-27
Nice "quote" :D
Anyway, here's the answer : [http://ubuntuforums.org/showthread.php?p=7260218](http://ubuntuforums.org/showthread.php?p=7260218)

This one should remove it :
```
sudo apt-get remove fortune
```

---

### Post by Wayne_V on 2009-05-27
Sounds like fortune.   Check .profile and/or .bashrc and/or /etc/profile.

You can remove fortune ("dpkg --list | grep fortune" to see what's installed) but if you don't remove it from your startup script as well you'll start getting an error instead of a fortune.

---

### Post by baseface on 2009-05-27
fortune through "cowsay"

---

### Post by DouglasCaixeta on 2009-05-27
Thanks, problem solved!

---

