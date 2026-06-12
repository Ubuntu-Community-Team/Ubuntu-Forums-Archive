---
title: "How to Fix Emerald in Ubuntu 11.04"
date: 2011-05-20
forum: Desktop Environments
---

### Post by shantiq on 2011-05-20
Some people might find they have problems with the repository emerald in Natty
I myself could not see the buttons; they were just not there so i found [ this]("http://abz89.wordpress.com/2011/05/02/how-to-fix-emerald-in-ubuntu-11-04/#comment-294") written by Abz





1. Remove emerald completely

```
 sudo apt-get purge emerald
```

2. Install some deps packages

 ```
sudo apt-get install git autoconf libtool libwnck1.0-cil-dev libwnck-dev intltool libdecoration0-dev libemeraldengine0
```

3. Fetch emerald via GIT

 ```
git clone git://anongit.compiz.org/fusion/decorators/emerald
```

4. Compile and install it!

 ```
cd emerald
```

```
 git checkout -b compiz++ origin/compiz++

```
```
 ./autogen.sh

```
 ```
./configure [COLOR="Red"]-[/COLOR]prefix=/usr/local
```

 ```
make
```

```
 sudo make install

```

then either in terminal or alt F2

```
emerald --replace

```



[COLOR="DarkRed"]**PS**:   also make sure to  mark the option &#8216;move window&#8217; in compiz setting[/COLOR]

---

