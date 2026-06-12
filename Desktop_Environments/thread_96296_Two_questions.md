---
title: "Two questions"
date: 2005-11-28
forum: Desktop Environments
---

### Post by Alvin on 2005-11-28
One is more urgent than the other, so I'll mention that one first.

I have recently updated to ubuntu 5.10, and have apt-get'd gcc (apt-get install gcc). Unlike the previous version, this one doesn't compile, so I can't get anything more up-to-date.

The second problem is, I can't seem to get my resolution up to 1280x1024, even though my monitor can support it.

Thanks,
Alvin.

---

### Post by aysiu on 2005-11-28
[QUOTE=Alvin]
I have recently updated to ubuntu 5.10, and have apt-get'd gcc (apt-get install gcc). Unlike the previous version, this one doesn't compile, so I can't get anything more up-to-date.[/quote] "Doesn't compile" doesn't help. Post the output (copy and paste it into a message) of the command ```
sudo apt-get install gcc
``` Any reason you're installing gcc isntead of build-essential?

> 
The second problem is, I can't seem to get my resolution up to 1280x1024, even though my monitor can support it. The solution's somewhere in [here](http://ubuntuforums.org/showpost.php?p=129379&postcount=21)

---

### Post by Alvin on 2005-11-28
[QUOTE=aysiu]"Doesn't compile" doesn't help. Post the output (copy and paste it into a message) of the command ```
sudo apt-get install gcc
``` Any reason you're installing gcc isntead of build-essential?



 The solution's somewhere in [here](http://ubuntuforums.org/showpost.php?p=129379&postcount=21)[/QUOTE]

Sorry, wrong way to put it. It's installed fine, however when it comes to compiling something, it says something like "C compiler cannot compile" and aborts. Thanks for the link.

---

### Post by aysiu on 2005-11-28
[QUOTE=Alvin]Sorry, wrong way to put it. It's installed fine, however when it comes to compiling something, it says something like "C compiler cannot compile" and aborts. Thanks for the link.[/QUOTE] Hm. Are you trying to install applications from source, or are you programming and trying to compile your own programs to test them?

---

### Post by Alvin on 2005-11-28
I'm trying to install applications from source, but gcc doesn't work with my source either.

---

### Post by artinla on 2005-11-28
Aysiu is right, you should try uninstalling and reinstalling "build-essential".

Make sure you don't have any 3rd party repositories enabled when you do it.

Art

---

### Post by aysiu on 2005-11-28
[QUOTE=Alvin]I'm trying to install applications from source, but gcc doesn't work with my source either.[/QUOTE] If you're trying to install applications from source, then this is what you want: ```
sudo apt-get install build-essential
```

---

### Post by linkunderscore on 2005-11-28
Also, Im just curious as to what you are trying to compile?

---

