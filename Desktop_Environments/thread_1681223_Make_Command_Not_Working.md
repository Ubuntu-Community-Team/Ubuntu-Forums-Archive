---
title: "Make Command Not Working"
date: 2011-02-03
forum: Desktop Environments
---

### Post by Melvin Frohike on 2011-02-03
Hey, I'm trying to composit some extra Compiz plugins, I used this tutorial >>>http://tombuntu.com/index.php/2008/07/31/install-three-experimental-compiz-plugins/<<<

And when I try to make the file I get this:

```
user@ComputerName:~$ cd ~/compizplugins/freewins
user@ComputerName:~/compizplugins/freewins$ make
make: *** No targets specified and no makefile found.  Stop.
```

There is a CMakeList.txt, I've tried this in every different plugin I'm trying to compile and it doesn't work on any of them, I searched for a solution and have found none.

What am I doing wrog here? 

Thanks in advance.

---

### Post by anglican on 2011-02-04
> **Melvin Frohike said:**
> Hey, I'm trying to composit some extra Compiz plugins, I used this tutorial >>>http://tombuntu.com/index.php/2008/07/31/install-three-experimental-compiz-plugins/<<<

And when I try to make the file I get this:

```
user@ComputerName:~$ cd ~/compizplugins/freewins
user@ComputerName:~/compizplugins/freewins$ make
make: *** No targets specified and no makefile found.  Stop.
```

There is a CMakeList.txt, I've tried this in every different plugin I'm trying to compile and it doesn't work on any of them, I searched for a solution and have found none.

What am I doing wrog here? 

Thanks in advance.Try:
```
sudo apt-get install cmake
```then in your ~/compizplugins/freewins directory try:
```
cmake .
```

H

---

