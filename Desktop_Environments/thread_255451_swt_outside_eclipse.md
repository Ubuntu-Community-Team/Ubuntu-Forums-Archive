---
title: "swt outside eclipse"
date: 2006-09-11
forum: Desktop Environments
---

### Post by staura on 2006-09-11
I use eclipse for java/swt and everthing is working smoothly inside eclipse, including the visual editor. However getting the swt java application to run outside of eclipse is not that easy. I managed to get it running in windows by doing "java -classpath swt.jar javafile", but that doesnt seem to work on ubuntu. Any ideas?

---

### Post by kidders on 2006-09-11
Hi there,

An error message would have been helpful, along with some environment info, like your existing classpath, etc., so we can see whether java is looking in all the right places -- assuming, that is, that your problem is a "class not found" type thing.

If it is, do you know how to check whether java *should* be able to locate swt.jar?

---

### Post by staura on 2006-09-11
Yup I get the: 
```
Exception in thread "main" java.lang.NoClassDefFoundError: org/eclipse/swt/widgets/Composite
```


Since java was able to locate and use swt.jar in windows, and since it's able to run the application just fine inside eclipse then it should be possible to run it 'stand-alone'. I just think it's funny that when so many are developing in eclipse/swt I still can't google up anything. 

I aslo tried using gcj to compile swt, but I didnt get far in that direction. I havent been working with java all that long and I'm not so into classpaths/jars/library path/etc. I'm just hoping there is an explainable way to deploy swt apps?

---

### Post by kidders on 2006-09-11
Hmmm... solving your problem *should* just be a matter of making sure swt.jar is someplace java can find it. slocate swt.jar and make sure wherever it lives is in your library search path... same as if you were using Windows.

Sun's java works more or less the same no matter which OS you run it on. GCJ isn't quite the same thing though.

---

