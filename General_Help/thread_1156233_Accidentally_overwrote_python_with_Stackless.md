---
title: "Accidentally overwrote python with Stackless"
date: 2009-05-11
forum: General Help
---

### Post by outofthemadness on 2009-05-11
Over the weekend I installed stackless python to test out some code I'd written on my other machine. Unfortunately, I was careless during the install and forgot to change the prefix (for the location of the install) and I overwrote the default Python install. I tried to uninstall stackless, but I might have had a mistaken understanding of what I was doing. I recompiled stackless, but I changed its options so it would compile a normal python install. Now, my problem is, my sys.path changed from whatever the default for Ubuntu is to the default for a linux Python install. As a result of this, anything that depends ona library that is not in my (very abbreviated) sys.path, it will not function. 

I tried 

```
sudo apt-get install --reinstall python
```

but that had no effect  (or none that I could see)

So I guess what I'm asking is, could someone give me an idea of how 

a) I can successfully get the version of python that's in the repos
(this is the preferred option)

b) I can change my sys.path to permanently match the sys.path of the default python install

c) any other option I've failed to consider that will solve my problem


my sys.path looks like this:

```


['', '/usr/local/lib/python26.zip', '/usr/local/lib/python2.6',
 '/usr/local/lib/python2.6/plat-linux2', '/usr/local/lib/python2.6/lib-tk',
 '/usr/local/lib/python2.6/lib-old',
 '/usr/local/lib/python2.6/lib-dynload', 
'/usr/local/lib/python2.6/site-packages']


```
Any thoughts?

---

### Post by unutbu on 2009-05-11
See [http://ubuntuforums.org/showpost.php?p=6902170&postcount=16](http://ubuntuforums.org/showpost.php?p=6902170&postcount=16)
If you read the entire thread, that post seems to have led to a happy ending:
[http://ubuntuforums.org/showthread.php?t=785928&page=3](http://ubuntuforums.org/showthread.php?t=785928&page=3)

You might want to try it without the 
```


sudo apt-get dist-upgrade
```

first, though, in case you aren't using Jaunty and don't want to upgrade to Jaunty...

---

### Post by outofthemadness on 2009-05-11
I probably should have mentioned that according to the Synaptic, python is already installed and at its latest version.


are you saying that I should first remove python(and all things that depend on it) and then reinstall it and everything else?That seems a bit like the nuclear option, so I'd like to explore some other avenues before I go that far. Do you know any other way?

---

### Post by outofthemadness on 2009-05-22
Alright. I've solved my problem. I didn't do what that thread detailed, and if I had, I probably would have run into more problems. While I thought I had overwritten the default Python install,this is what actually happened:

When I installed stackless, it put executables named 'python' and 'python2.6' in /usr/local/bin. Since this is earlier on my PATH than /usr/bin(where the original python and python2.6 were), when something called python it was getting stackless and its abbreviated sys.path.This also explains why Synaptic didn't see anything wrong with the installed python, because there wasn't. To remedy this, I just renamed the files stackless put in /usr/local/bin, and I was done.

---

