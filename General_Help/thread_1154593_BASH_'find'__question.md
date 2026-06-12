---
title: "BASH 'find'  question"
date: 2009-05-09
forum: General Help
---

### Post by max_power on 2009-05-09
```
ls |tail -1 |find -type f -name *.mpg

```

Im trying to search for the newest mpg file in a folder

my result is preceded with a "./"

ex: ```
$ ls |tail -1 |find -type f -name *.mpg
$ ./myvideo.mpg

```

What switch is used to remove the './' in the results?


thanks

---

### Post by 73ckn797 on 2009-05-09
Why not just use Places/Computer and go to the directory then by clicking on the header "Date Modified" above the date listings, it will toggle the order of the latest or earlier created files?

That is if you know the directory where it is located. Otherwise I am probably missing the point which could be the case.

---

### Post by max_power on 2009-05-09
> **73ckn797 said:**
> Why not just use Places/Computer and go to the directory then by clicking on the header "Date Modified" above the date listings, it will toggle the order of the latest or earlier created files?

That is if you know the directory where it is located. Otherwise I am probably missing the point which could be the case.

thanks for you reply but im using this command in a script, so therefor using the GUI would not be appropriate.

---

### Post by 73ckn797 on 2009-05-09
> **max_power said:**
> thanks for you reply but im using this command in a script, so therefor using the GUI would not be appropriate.

You are welcome. Just thought there is also the gui method to try. I do not use cli if there is a gui method.

---

### Post by kaibob on 2009-05-10
> **max_power said:**
> Im trying to search for the newest mpg file in a folder. my result is preceded with a "./"...
I don't believe you need to use the find command. For example, the following appears to do what you want and the output consists of the file name only.

```
ls -t *.mpg | head -n 1
```

---

### Post by max_power on 2009-05-10
That worked. thanks!

---

### Post by max_power on 2009-05-10
sorry, i forgot to mark this as solved

---

