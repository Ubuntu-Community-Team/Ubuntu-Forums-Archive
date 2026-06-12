---
title: "Scibuntu Script Fails in Kubuntu Edgy"
date: 2007-03-25
forum: Education &amp; Science
---

### Post by lbthrice on 2007-03-25
Hello all,

I am an Ubuntu newbie w/issue using the new scibuntu 4.0 beta script
I am running Kubuntu Edgy.  

Here is what I do:
I run the script in a root terminal with 

```
sh scibuntu
```

then BASH tells me

```
scibuntu: 39: function: not found
scibuntu: 43: Syntax error: "}" unexpected
```

here is the scibuntu script code that BASH is complaining about (starting with line 39 of the script and ending with line 43)

```
function logtouch {
     DATE=`date +%y-%m-%d__%H_%M_%S`
     LOG=$LOG$DATE
     touch $LOG
}
```

Please helpabrutherout if you have a moment...thanks all!

---

### Post by kleeman on 2007-03-25
You are executing it incorrectly. Try
sudo chmod a+x scibuntu040-beta
sudo ./scibuntu040-beta

---

### Post by lbthrice on 2007-03-25
Kleeman, thank you, the script is now currently at work downloading all the **goodies** :KS .

*Note: for anyone who stumbles on the post while trying to install package with scibuntu:

don't forget to aquire zenity 
and all its dependencies with apt 
prior to invokation of the scibuntu script.

---

### Post by in_flu_ence on 2007-03-27
Any website for the scibuntu where i can refer to?

---

### Post by kleeman on 2007-03-27
[http://scibuntu.sourceforge.net/index.html](http://scibuntu.sourceforge.net/index.html)

---

