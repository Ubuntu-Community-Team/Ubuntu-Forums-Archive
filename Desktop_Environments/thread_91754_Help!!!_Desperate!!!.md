---
title: "Help!!! Desperate!!!"
date: 2005-11-17
forum: Desktop Environments
---

### Post by seismicmike on 2005-11-17
I tried to install something from an rpm...

```

$ sudo alien <filename>.rpm

```

then

```

$ sudo dpkg -i <filename>.deb

```

but it didn't work...

HERE'S THE BAD PART:

I went to apt-get something else:

```

root@ubuntu:~# apt-get install <program>
Reading package lists... Done
Building dependency tree... Done
E: The package <filename from above> needs to be reinstalled, but I can't find an archive for it.

```

HOW DO I FIX THIS!!!!!!!!!!!!! I NEED TO FAST!!!! I HAVE A LIST OF LIKE 20 THINGS I NEED TO APT-GET!!!!

---

### Post by kingler on 2005-11-17
it sounds strange.

try to use
```
apt-get update
```
before 
```
apt-get install <program>
```

---

### Post by seismicmike on 2005-11-17
LOL... as simple as that may seem, it didn't work...

Thanks for trying to help though :)

---

### Post by aysiu on 2005-11-17
Make sure your sources.list is good, too. See the first link in my sig.

---

### Post by seismicmike on 2005-11-18
yeah... didn't work... sorry

also, I tried a locate and found all the places where the file shows up and deleted all them...

then i went back and tried to do it again

still didn't work...

tried to locate again, and it found all the files i had just deleted :evil:

---

### Post by seismicmike on 2005-11-18
i tried this:

```

root@ubuntu:~# dpkg -r <filename>

```

with this result:

```

dpkg: error processing <filename> (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 <filename>

```

How do I bloody reinstall????????????????!!!!!!!!!!!!!!!!!!!!????????????????!!!!!!!!!!!!!

---

### Post by ltmon on 2005-11-18
Have you tried:

> sudo dpkg -r <packagname>

It seems the aborted install has left some remenants in your dpkg database.

Also, have a look in /var/lib/dpkg/status and see if the package is mentioned in there and what it's status is.

L.

---

### Post by seismicmike on 2005-11-18
ltmon, you are my new hero!!!

you also get the prize of the yellow bunny :)

---

### Post by ltmon on 2005-11-18
[QUOTE=seismicmike]ltmon, you are my new hero!!!

you also get the prize of the yellow bunny :)[/QUOTE]

What worked in the end?

L.

---

### Post by seismicmike on 2005-11-18
well, i had already done the dpkg -r thing and it hadn't worked, so it was deleting it from /var/lib/dpkg/status :)

---

