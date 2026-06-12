---
title: "R statistical language and X11"
date: 2005-12-26
forum: General Help
---

### Post by lmlahti on 2005-12-26
Hello world, I tried to plot a picture in R but did not succeed. There is something wrong with X11 thing but I could not find instructions how to fix this, Below is the error message, does anyone know what to do to make plots functioning? 

> plot(c(1,2,3))
Error in X11() : could not find any X11 fonts
Check that the Font Path is correct.

---

### Post by woro2006 on 2006-10-31
> **lmlahti said:**
> Hello world, I tried to plot a picture in R but did not succeed. There is something wrong with X11 thing but I could not find instructions how to fix this, Below is the error message, does anyone know what to do to make plots functioning? 

> plot(c(1,2,3))
Error in X11() : could not find any X11 fonts
Check that the Font Path is correct.

It's very super annoying. The simple reason X11 cannot start is because R does not support UTF.8, which is the default choice for English. 

So you have to configure your language to en_US instead (not US_UTF8). Just read this article on how to generate your choice of locale.

[https://help.ubuntu.com/community/LocaleConf](https://help.ubuntu.com/community/LocaleConf)

---

### Post by sagarm on 2006-11-30
You don't have to reconfigure your locale; you can just start R like this: 

```
user@machine:~$ **LANG=en_US R**
```

No need to make system wide changes.

---

### Post by lmlahti on 2007-11-18
Thanks, these answers solved the problem.

LML

---

