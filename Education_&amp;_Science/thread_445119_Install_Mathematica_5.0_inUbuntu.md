---
title: "Install Mathematica 5.0 inUbuntu"
date: 2007-05-15
forum: Education &amp; Science
---

### Post by BRUNOALVISIO on 2007-05-15
Hi,

I have installed Mathematica 5.0 in Ubuntu. After iit was complete When I tried tu run it, it appeared a Warning message, Mathematica seems to start but then nothing happens. It appears "Segmentation Fail" in the terminal. 

Could it be that I entered a wrong password when I was installing it???

What should I do???

Thanks

Bruno

---

### Post by parktownprawn on 2007-05-16
I think if you had just entered the wrong password Mathematica would give you the option of re-entering the password.

Once thing you could try is running mathematica without a splash screen. The splash screen is known to cause problems. Try running mathematica with the command

```
mathematica -noSplashScreen

```

---

### Post by BRUNOALVISIO on 2007-05-16
Thanks,, but it did not work. When I run it,, it say segmentation fault. I have read the tens of warning and it says sometihng related to c and xlib library....

Maybe that can help.

Thanks

Bruno

---

### Post by parktownprawn on 2007-05-17
Could you please post the  warnings that come up when you try run mathematica?

Do you have a 64-bit machine?

You might find some useful advice on

[https://help.ubuntu.com/community/Mathematica](https://help.ubuntu.com/community/Mathematica)

or 

[http://support.wolfram.com/mathematica/systems/linux/](http://support.wolfram.com/mathematica/systems/linux/)

---

### Post by Rui Pais on 2007-05-17
hi,
Mathematica under Ubuntu can be tricky, cause some directories are not on the usual paths that linux distro uses, related with locales and XKeysymDB. Usually a complete installation requires to do, by hand, some links to correct these.

Sometimes Mathematica segfaults when, in combination, you have both splashscreen and incorrect XKeysymDB path.

Try to do the instructions on the [2nd. post]("http://ubuntuforums.org/showpost.php?p=496021&postcount=2") of[ this thread]("http://ubuntuforums.org/showthread.php?p=2307928") to see if it works.

good luck.

---

### Post by BRUNOALVISIO on 2007-05-17
Hi,,

Thanks. That worked perfectly.

Bruno

---

### Post by Rui Pais on 2007-05-17
> **BRUNOALVISIO said:**
> Hi,,

Thanks. That worked perfectly.

Bruno

:)

---

### Post by SuperAndy on 2007-05-20
yet another well done!

cheers!

---

### Post by Copter on 2007-05-25
hi!

thanks for help. i tried several things to make it work but finaly this trick solved my problems

[http://support.wolfram.com/mathematica/systems/linux/general/runerror.html]("http://support.wolfram.com/mathematica/systems/linux/general/runerror.html")

copter :]

---

