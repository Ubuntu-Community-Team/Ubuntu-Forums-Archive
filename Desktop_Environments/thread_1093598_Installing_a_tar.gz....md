---
title: "Installing a tar.gz..."
date: 2009-03-11
forum: Desktop Environments
---

### Post by Leo Dragonheart on 2009-03-11
I just downloaded Matrix full pack.tar.gz. Can someone tell me the proper way to install it please? I also downloaded an Icon tar.gz. How do I install that?

---

### Post by taurus on 2009-03-11
With some games (I assume Matrix full pack.tar.gz is a game), you just unpack it and change to the new directory and run it from there.

But if you can provide the exact link where you've downloaded it, I can have a quick look and tell you how to get it working/running.

---

### Post by Leo Dragonheart on 2009-03-11
I downloaded it from below on the second page:

```
http://www.gnome-look.org/content/search.php?xsortmode=new&search=1&type=0&name=Matrix&user=&text=&sort=0&scorefilter=0&license=99&page=1
```

and the Icons were on page one called Matrixxx...

I downloaded both files to leo/home/Downloads/ on my computer.

---

### Post by C-- on 2009-03-11
```

cd [name of directory holding tar file goes here]
tar -xvf [tar file name goes here]
cd [name of extracted directory goes here]
./configure
make
sudo make install

```

---

### Post by Leo Dragonheart on 2009-03-11
> **C-- said:**
> ```

cd [name of directory holding tar file goes here]
tar -xvf [tar file name goes here]
cd [name of extracted directory goes here]
./configure
make
sudo make install

```

Will this install it to the extracted folder or to a different place?

I must be doing something wrong it tells me the package is not accessible.

---

### Post by taurus on 2009-03-11
There is nothing to build or config.  Looks like you get wallpapers, themes (gtk, icon, GMD), and icons from **Matrix full pack.tar.gz**.

---

### Post by Leo Dragonheart on 2009-03-11
This is the error reading I get:

root@Illuzionz:/home/leo/Downloads# tar -xvf /Matrix-full_pack.tar.gz
tar: /Matrix-full_pack.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now

---

### Post by Leo Dragonheart on 2009-03-11
So how do I use them then?

---

### Post by taurus on 2009-03-11
First, no need to log in as root if you just want to unpack it.  Your download is in ~/Desktop/Matrix full pack.tar.gz, not **[COLOR="Red"]/[/COLOR]**Matrix full pack.tar.gz because the front / will it to look in the top directory--/.

```
tar xvzf ~/Desktop/"Matrix full pack.tar.gz"
```

p.s.  Did you change the name from "Matrix full pack.tar.gz" to "Matrix-full_pack.tar.gz"?

---

### Post by Leo Dragonheart on 2009-03-11
yes I changed the the name in terminal not to the download. I just did not know how to type it in terminal so was guessing...;-)

---

### Post by Leo Dragonheart on 2009-03-11
> **taurus said:**
> First, no need to log in as root if you just want to unpack it.  Your download is in ~/Desktop/Matrix full pack.tar.gz, not **[COLOR="Red"]/[/COLOR]**Matrix full pack.tar.gz because the front / will it to look in the top directory--/.

```
tar xvzf ~/Desktop/"Matrix full pack.tar.gz"
```

p.s.  Did you change the name from "Matrix full pack.tar.gz" to "Matrix-full_pack.tar.gz"?

That did something so I am guessing they are installed now? Thanx very much!

---

### Post by Leo Dragonheart on 2009-03-11
No that just unpacked them I still can not use them. How do I make it so I can use them now?

---

