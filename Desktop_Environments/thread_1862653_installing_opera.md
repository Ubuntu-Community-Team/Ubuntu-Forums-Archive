---
title: "installing opera"
date: 2011-10-17
forum: Desktop Environments
---

### Post by boblizar on 2011-10-17
if you have not noticed, this is my ubuntu master thesis....
[http://ubuntuforums.org/showthread.php?t=1836890](http://ubuntuforums.org/showthread.php?t=1836890)
check it out and share it with your friends =)

operas deb package is broken for me, so i am installing from tar.bz

[http://www.opera.com/download/get.pl?id=34047&location=380&nothanks=yes&sub=marine](http://www.opera.com/download/get.pl?id=34047&location=380&nothanks=yes&sub=marine)

is where i nabbed my bz from

upon receipt of the tarball i

alt + f2

gnome-terminal

run

then drop this to my terminal

```

cd $HOME/Downloads
tar -xf opera-11.51-1087.x86_64.linux.tar.bz
cd $HOME/Downloads/opera-11.51-1087.x86_64.linux
sudo ./install

```

in the shell it will load a install script that asks a few questions.....

i answer the questions with

/usr

for my prefix

and everything else is enter enter enter then i clean my mess up by droppings this block of code

```

rm $HOME/Downloads/opera-11.51-1087.x86_64.linux.tar.bz
rm -rf $HOME/Downloads/opera-11.51-1087.x86_64.linux

```

and to load opera up its

alt + f2

opera

run

---

