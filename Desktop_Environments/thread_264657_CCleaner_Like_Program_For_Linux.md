---
title: "CCleaner Like Program For Linux"
date: 2006-09-25
forum: Desktop Environments
---

### Post by buzlink on 2006-09-25
Is there a program similiar to [CCleaner]("http://www.ccleaner.com/") that will clean up my system of temp and cached files when ran?

Thanks

---

### Post by Monstroxus on 2006-09-25
I love ccleaner on windows, I would like to recommend:

[https://addons.mozilla.org/firefox/1484/](https://addons.mozilla.org/firefox/1484/)

I know its not ccleaner, cause it only cleans internet files etc. But still nice though for if you use Firefox.

---

### Post by buzlink on 2006-11-13
thanks
Any other for general system?

---

### Post by DOD1951 on 2006-11-13
Kleansweep but be warned its not too picky about what to throw out so you really need to have some knowlege so as to know what to do with the suggestions.

---

### Post by Dr. Nick on 2006-11-13
Also the /tmp folder is cleared on boot which helps keep things abit cleaner then in windows

---

### Post by fiskking on 2008-01-30
decided to bump this thread since I was wondering the same thing.  CCleaner is a great tool for windows , so has there been any developments of something similar in Ubuntu/linux?

---

### Post by fiskking on 2008-01-30
ok, just found out that Linux (Ubuntu) doesn´t have a registry, so there is really no need for one like in the case for Windose

---

### Post by flippbonq on 2008-01-30
> **fiskking said:**
> ok, just found out that Linux (Ubuntu) doesn´t have a registry, so there is really no need for one like in the case for Windose

linux/ubuntu might not have a registry... but `[gconf-editor]("http://en.wikipedia.org/wiki/Gconf-editor")` makes it feel like gnome/gtk does. [Baobab]("http://www.marzocca.net/linux/baobab.html") (disk usage analyzer) might help you figure out which parts of your filesystem contain tempfiles or the like that can be cleaned up.

---

### Post by buelligan on 2008-05-17
CCleaner does have an NSA level file shredding option.  Is there anything remotely as easy to use as CCleaner with secure shredding? :-\" (not that I have anything that sensitive on my system...)

---

### Post by drklepto on 2008-06-17
> **buelligan said:**
> CCleaner does have an NSA level file shredding option.  Is there anything remotely as easy to use as CCleaner with secure shredding? :-\" (not that I have anything that sensitive on my system...)

Just for erasing files:

```
sudo apt-get install secure-delete
```

then:

```
you@box:~$  srm filetoshred
```

---

### Post by sam1948 on 2008-06-26
> **drklepto said:**
> Just for erasing files:

```
sudo apt-get install secure-delete
```

then:

```
you@box:~$  srm filetoshred
```


from man page of srm
 ```
srm  is designed to delete data on mediums in a secure manner which can
 not be recovered by thiefs, law enforcement or other threats.  The wipe
 algorythm  is based on the paper "Secure Deletion of Data from Magnetic
 and Solid-State Memory" presented at the 6th Usenix Security  Symposium
 by Peter Gutmann, one of the leading civilian cryptographers.
```

it is not for safe cleaning it is for permanent eraseing
watch out

---

