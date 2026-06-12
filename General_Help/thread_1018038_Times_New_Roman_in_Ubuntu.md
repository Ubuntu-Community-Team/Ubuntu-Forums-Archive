---
title: "Times New Roman in Ubuntu?"
date: 2008-12-21
forum: General Help
---

### Post by WeEatVista on 2008-12-21
Having switched from vista to ubuntu and then ubuntu back to vista, i have finally realized that vista is trying to get me to use ubuntu:P
Since the world is globalized as M$, I am in need to have a font that is almost an exact clone of Times New Roman in Windows. My professors won't accept it any other way. I followed this thread:[http://ubuntuforums.org/showthread.php?t=589588]("http://ubuntuforums.org/showthread.php?t=589588") 

But in the terminal I get this error:
```
ubuntu@ubuntu:~$ sudo apt-get install msttcorefonts
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package msttcorefonts is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package msttcorefonts has no installation candidate
```

What is causing this error? And are there any workarounds? I just need a Times New Roman font for Ubuntu. Any help?

Thanks,

We Eat Vista

---

### Post by R.Bucky on 2008-12-21
you would need to make the correct repositories available. 
[https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu")
System > Administration > Software-Sources - Third Party...

---

### Post by kostkon on 2008-12-21
> **WeEatVista said:**
> Having switched from vista to ubuntu and then ubuntu back to vista, i have finally realized that vista is trying to get me to use ubuntu:P
Since the world is globalized as M$, I am in need to have a font that is almost an exact clone of Times New Roman in Windows. My professors won't accept it any other way. I followed this thread:[http://ubuntuforums.org/showthread.php?t=589588]("http://ubuntuforums.org/showthread.php?t=589588") 

But in the terminal I get this error:
```
ubuntu@ubuntu:~$ sudo apt-get install msttcorefonts
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package msttcorefonts is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package msttcorefonts has no installation candidate
```

What is causing this error? And are there any workarounds? I just need a Times New Roman font for Ubuntu. Any help?

Thanks,

We Eat Vista
Check if you have all the repositories enabled. Go to *System &#8594; Administration &#8594; Software Sources* and in the fist tab (*Ubuntu Software*) check if the *main*, *restricted*, *universe*, and *multiverse* are enabled.

The [*msttcorefonts*]("http://packages.ubuntu.com/intrepid/msttcorefonts") is offered by the *multiverse* repository as you can see.

---

### Post by fragos on 2008-12-21
It's my understanding that Vista has replaced Times New Roman with Cambria. In fact Vista has changed many of the fonts Microsoft has used in the past.

---

