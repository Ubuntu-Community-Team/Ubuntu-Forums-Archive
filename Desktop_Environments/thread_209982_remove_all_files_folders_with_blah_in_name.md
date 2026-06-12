---
title: "remove all files folders with *blah* in name?"
date: 2006-07-06
forum: Desktop Environments
---

### Post by takayuki on 2006-07-06
Hi,

how can i remove all files and folders with *blah* in the name?

i've tried

```
sudo find / -name *blah.html | rm *blah.html
```

but it ain't workin'.  here's the error:

```
rm: cannot remove `*blah.html': No such file or directory
```

thanks,

takayuki

---

### Post by aysiu on 2006-07-06
Are you trying to learn the terminal commanads to do this, or do you just want it done?

If you want to do it GUI-style, just search for *.blah.html in your favorite search tool and then delete those files and folders.

---

### Post by takayuki on 2006-07-06
hi aysiu,

i was gunning for the terminal solution. 

i can find the files and i can rm them individually, but wanted to combine the two commands somehow.  i'm still googling around for a solution.

thanks

takayuki

---

### Post by takayuki on 2006-07-06
found it!

```
sudo find / -name *blah.html -delete
```

that'll knock out everything with a *blah.html anywhere in the filesystem.  gotta be careful though... ;-)

---

