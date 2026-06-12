---
title: "google earth refuses to work on ubuntu"
date: 2009-02-13
forum: General Help
---

### Post by lenswipe on 2009-02-13
I just installed google earth and whenever i try to run it, it just crashes straight away and closes....

Any ideas?

---

### Post by unixeducation on 2009-02-13
What version of Ubuntu are you running, and what output do you see when you launch Google Earth from a terminal?

---

### Post by Slim Odds on 2009-02-13
> **lenswipe said:**
> I just installed google earth and whenever i try to run it, it just crashes straight away and closes....

Any ideas?

For the love of all things holy.... check the forums first. This has been discussed dozens of times.

It's the libcrypt that they ship that conflicts with the one in Ubuntu. Go to their directory and delete it (many people suggest renaming it, but you don't need it. So just delete it).

---

### Post by NetworkGuy on 2009-02-13
Try the older 4.3 version.   Version 5 does not work on my 8.10 but 4.3 works like a charm.

---

### Post by unixeducation on 2009-02-13
Here you go (in the google earth install directory):

```
mv libcrypto.so.0.9.8 libcrypto.so.0.9.8.bak
```

It'll run now.

---

### Post by NetworkGuy on 2009-02-13
> **unixeducation said:**
> Here you go (in the google earth install directory):

```
mv libcrypto.so.0.9.8 libcrypto.so.0.9.8.bak
```

It'll run now.

Is that for 5.0?   Sweet!!

---

### Post by bellylint on 2009-02-13
Google Earth 5.0 does work on Ubuntu 8.10
Here's what worked for me on Intrepid...

- Download GoogleEarthLinux.bin to desktop.
- Open terminal and enter the following commands:

$ cd Desktop
$ sudo su
# chmod +x GoogleEarthLinux.bin
# ./GoogleEarthLinux.bin

- The program installed under opt/google-earth
- In that folder rename libcrypto.so.0.9.8 as sudo to anything else...then enjoy.

---

### Post by Slim Odds on 2009-02-13
> **unixeducation said:**
> Here you go (in the google earth install directory):

```
mv libcrypto.so.0.9.8 libcrypto.so.0.9.8.bak
```It'll run now.

Better yet:
```
rm libcrypto.so.0.9.8
```

it's not needed, get rid of it!

---

### Post by unixeducation on 2009-02-13
> **Slim Odds said:**
> Better yet:
```
rm libcrypto.so.0.9.8
```

it's not needed, get rid of it!

As a programmer, I've developed a habit over the years of rarely deleting files, only renaming them for testing purposes. It's a good habit to get into; advice on forums isn't always good, and installs get hosed when files get deleted that shouldn't. If you just rename things, you can always go back.

---

### Post by NetworkGuy on 2009-02-13
IT works.   Thanks for the tip   (Now where is that thank you button again??)

---

