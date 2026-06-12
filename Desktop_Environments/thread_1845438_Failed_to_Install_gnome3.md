---
title: "Failed to Install gnome3"
date: 2011-09-17
forum: Desktop Environments
---

### Post by sptutusukanta on 2011-09-17
I'm using UBUNTU 11.04.

I've added the gnome ppa to the repository.
```
ppa:gnome3-team/gnome3
```

Using terminal I ran the command
```
sudo apt-get install gnome-shell
```
It gives an error:
```
The following packages have unmet dependencies:
 gnome-shell : Depends: mesa-utils but it is not installable
E: Broken packages

```

Then I tried to install mesa-utils:
```
 sudo apt-get install mesa-utils
```
Then I got another error:

```
Package mesa-utils is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'mesa-utils' has no installation candidate

```


How can I install GNOME3 now..?????:-(:-(:sad:

---

### Post by raja.genupula on 2011-09-17
> **sptutusukanta said:**
> I'm using UBUNTU 11.04.

I've added the gnome ppa to the repository.
```
ppa:gnome3-team/gnome3
```

Using terminal I ran the command
```
sudo apt-get install gnome-shell
```
It gives an error:
```
The following packages have unmet dependencies:
 gnome-shell : Depends: mesa-utils but it is not installable
E: Broken packages

```

Then I tried to install mesa-utils:
```
 sudo apt-get install mesa-utils
```
Then I got another error:

```
Package mesa-utils is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'mesa-utils' has no installation candidate

```


How can I install GNOME3 now..?????:-(:-(:sad:

hey try to install it by this 

```
sudo aptitude install mesa-utils
```

or
download form here and install 
[http://packages.ubuntu.com/natty/mesa-utils](http://packages.ubuntu.com/natty/mesa-utils)

all the best

---

### Post by sptutusukanta on 2011-09-17
Thank you **raja.genupula** for your suggestion!

It is solved now.
I just check on the resources which were by default checked off and update using [FONT="Courier New"]apt-get update[/FONT].
Then use [FONT="Courier New"]apt-get install gnome-shell[/FONT] and installed perfectly!! :-)

---

### Post by raja.genupula on 2011-09-17
Hey 
    I am glad that you have solved you issue. . But one thing, i am  viewing some threads about Gnome 3 .Its not better to use Gnome 3 for office work .But in these days maximum problems are getting solved .if it is your office system better to be Gnome 2 upto some time.

all the best my friend

---

