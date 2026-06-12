---
title: "Want to upgrade nmap..debian repos?"
date: 2005-11-09
forum: Desktop Environments
---

### Post by NewWithoutClue on 2005-11-09
Well i have version 3.81, then current version is 3.93. ( nmap, remember ).
Now..i want to upgrade it..but when i downloaded the .deb from debian.com and tried to install using just that .deb...it's spit out errors ( missing, you have, you don't have...blah blah ) i want to add the debians repo just for nmap...can i? so you see any problems with this? i want unstable BTW.

Thanks,
( and as the name suggests, i am new and clueless )
Paul.

---

### Post by Pablo_Escobar on 2005-11-09
My 2 cents - it can mess up Your system pretty badly.
Only option is to try to compile it by hand (which can be a very long and tedious process depending how many and which versions of dependencies You need).

---

### Post by NewWithoutClue on 2005-11-09
So...I would probably be better off waiting till someone updates it in the ubuntu repos...I guess I hate waiting..and the fact that I love this tool doesn't help.

Paul.

---

### Post by NewWithoutClue on 2005-11-09
FYI i am still awaiting thoughts/tutorials/guides/HOWTOS/manuals/flames.

---

### Post by heimo on 2005-11-09
You could install it from source.
These instructions are only partially tested in current form...

 ```

sudo apt-get remove nmap
sudo apt-get update
sudo apt-get install checkinstall
sudo apt-get build-dep nmap
wget [http://freshmeat.net/redir/nmap/7202/url_bz2/nmap-3.93.tar.bz2]("http://freshmeat.net/redir/nmap/7202/url_bz2/nmap-3.93.tar.bz2")
tar xjvf nmap-3.93.tar.bz2
cd nmap-3.93
./configure

---------------------
  (  )   /\   _                 (
    \ |  (  \ ( \.(               )                      _____
  \  \ \  `  `   ) \             (  ___                 / _   \
 (_`    \+   . x  ( .\            \/   \____-----------/ (o)   \_
- .-               \+  ;          (  O                           \____
                          )        \_____________  `              \  /
(__                +- .( -'.- <. - _  VVVVVVV VV V\                 \/
(_____            ._._: <_ - <- _  (--  _AAAAAAA__A_/                |
  .    /./.+-  . .- /  +--  - .     \______________//_              \_______
  (__ ' /x  / x _/ (                                  \___'          \     /
 , x / ( '  . / .  /                                      |           \   /
    /  /  _/ /    +                                      /              \/
   '  (__/                                             /                  \
             NMAP IS A POWERFUL TOOL -- USE CAREFULLY AND REPONSIBLY
Configuration complete.  Type make (or gmake on some *BSD machines) to compile.
---------------------

make
sudo checkinstall -D make install
ls -l *deb
sudo dpkg -i nmap-3.93_3.93-1_i386.deb
nmap --version

``` 

Remember to update the package when later version is available.

---

### Post by NewWithoutClue on 2005-11-09
[QUOTE=heimo]You could install it from source.
These instructions are only partially tested in current form...

 ```

sudo apt-get remove nmap
sudo apt-get update
sudo apt-get install checkinstall
sudo apt-get build-dep nmap
wget [http://freshmeat.net/redir/nmap/7202/url_bz2/nmap-3.93.tar.bz2]("http://freshmeat.net/redir/nmap/7202/url_bz2/nmap-3.93.tar.bz2")
tar xjvf nmap-3.93.tar.bz2
cd nmap-3.93
./configure

---------------------
  (  )   /\   _                 (
    \ |  (  \ ( \.(               )                      _____
  \  \ \  `  `   ) \             (  ___                 / _   \
 (_`    \+   . x  ( .\            \/   \____-----------/ (o)   \_
- .-               \+  ;          (  O                           \____
                          )        \_____________  `              \  /
(__                +- .( -'.- <. - _  VVVVVVV VV V\                 \/
(_____            ._._: <_ - <- _  (--  _AAAAAAA__A_/                |
  .    /./.+-  . .- /  +--  - .     \______________//_              \_______
  (__ ' /x  / x _/ (                                  \___'          \     /
 , x / ( '  . / .  /                                      |           \   /
    /  /  _/ /    +                                      /              \/
   '  (__/                                             /                  \
             NMAP IS A POWERFUL TOOL -- USE CAREFULLY AND REPONSIBLY
Configuration complete.  Type make (or gmake on some *BSD machines) to compile.
---------------------

make
sudo checkinstall -D make install
ls -l *deb
sudo dpkg -i nmap-3.93_3.93-1_i386.deb
nmap --version

``` 

Remember to update the package when later version is available.[/QUOTE]

Thanks, will do!

Paul.

---

### Post by NewWithoutClue on 2005-11-09
Worked flawlessly.
Although i had to cp nmap to /usr/bin ...it was looking for it there..but it was in roots home dir..maybe something to do with the fact i'm doing this through ssh and a root login...anyway...it worked..thanks alot...i'm going to look into the some of the commands and stuff you used.

Paul.

---

