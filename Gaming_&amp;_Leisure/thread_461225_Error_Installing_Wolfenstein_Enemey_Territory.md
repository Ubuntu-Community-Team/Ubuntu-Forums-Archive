---
title: "Error: Installing Wolfenstein Enemey Territory"
date: 2007-06-01
forum: Gaming &amp; Leisure
---

### Post by Fearless Twit on 2007-06-01
Hi all,
I'm a complete newbie to Ubuntu, so forgive me if I have got it all wrong...

I was wondering if any of you could help me out here.
I'm trying to install Wolfenstein ET, but every time I try and install it with the command: 

sudo sh et-linux-2.55.x86.run

it comes up with the following:

sh: Can't open et-linux-2.55.x86.run

So then I try:

sudo apt-get install et-linux-2.60.x86.run

It comes up with:

Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package et-linux-2.60.x86.run

But I have downloaded it from two sites for Linux, but they are both in shell script script format.

Anyone out there know where I have gone wrong?

-FT

---

### Post by B0rsuk on 2007-06-01
You didn't try executing the file.

```
./et-linux-2.55.x86.run
```

By the way, it's clearly not a .deb file, so why should apt-get have anything to do with it ? Besides, this is not how you install .deb files you downloaded manually. Instead, you would do:

```
dpkg install filename.deb
```

---

### Post by Fearless Twit on 2007-06-01
I tried that and this is what it says:

```
Verifying archive integrity... All good.
Uncompressing Enemy Territory 2.55...........................................................................................................................................................................................................................................................................................................
/home/derby-boyz/.setup12937: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
The setup program seems to have failed on x86/glibc-2.1

```

---

### Post by Fearless Twit on 2007-06-01
> **B0rsuk said:**
> 
By the way, it's clearly not a .deb file, so why should apt-get have anything to do with it ? Besides, this is not how you install .deb files you downloaded manually. Instead, you would do:

```
dpkg install filename.deb
```

As I said before I am a newbie...

---

### Post by B0rsuk on 2007-06-01
Are you sure you have gtk installed ? Try:

```
dpkg -l | grep libgtk
```

(alternatively, try running Synaptic or Adept and check there)

It should print the list of matching packages on your system. In my case (Kubuntu Edgy) it looks like this:

ii  libgtk1.2                              1.2.10-18                                  The GIMP Toolkit set of widgets for X
ii  libgtk1.2-common                       1.2.10-18                                  Common files for the GTK+ library
ii  libgtk2-perl                           1.102-1ubuntu1                             Perl interface to the 2.x series of the Gimp
ii  libgtk2.0-0                            2.8.20-0ubuntu1.1                          The GTK+ graphical user interface library
ii  libgtk2.0-bin                          2.8.20-0ubuntu1.1                          The programs for the GTK+ graphical user int
ii  libgtk2.0-common                       2.8.20-0ubuntu1.1                          Common files for the GTK+ graphical user int
ii  libgtkhtml2-0                          2.11.0-1                                   HTML rendering/editing library - runtime fil

Finally, I've found this:

[https://help.ubuntu.com/community/EnemyTerritory](https://help.ubuntu.com/community/EnemyTerritory)

---

### Post by Fearless Twit on 2007-06-01
I'm usinf Ubuntu 7.04

When I did this:
```
dpkg -l | grep libgtk
```

this came up:
```
ii  libgtk-java                            2.10.1-0ubuntu2                        GTK+ bindings for Java
ii  libgtk-jni                             2.10.1-0ubuntu2                        GTK+ bindings for Java
ii  libgtk2-perl                           1.140-1build1                          Perl interface to the 2.x series of the Gimp Toolkit lib
ii  libgtk2.0-0                            2.10.11-0ubuntu3                       The GTK+ graphical user interface library
ii  libgtk2.0-bin                          2.10.11-0ubuntu3                       The programs for the GTK+ graphical user interface libra
ii  libgtk2.0-cil                          2.10.0-0ubuntu4                        CLI binding for the GTK+ toolkit 2.10
ii  libgtk2.0-common                       2.10.11-0ubuntu3                       Common files for the GTK+ graphical user interface libra
ii  libgtkhtml2-0                          2.11.0+svn20061107-0ubuntu1            HTML rendering/editing library - runtime files. (for GNO
ii  libgtkhtml3.14-19                      3.14.1-0ubuntu2                        HTML rendering/editing library - runtime files
ii  libgtkhtml3.8-15                       3.13.5-1                               HTML rendering/editing library - runtime files
ii  libgtksourceview-common                1.8.5-0ubuntu1                         common files for the GTK+ syntax highlighting widget
ii  libgtksourceview1.0-0                  1.8.5-0ubuntu1                         shared libraries for the GTK+ syntax highlighting widget
ii  libgtkspell0                           2.0.10-3                               a spell-checking addon for GTK's TextView widget

```

---

### Post by B0rsuk on 2007-06-01
Try installing libgtk1.2 this way:

```
sudo apt-get install libgtk1.2
```

and then execute the *.run* file.

---

### Post by Fearless Twit on 2007-06-01
Ok, thank you.

---

### Post by Fearless Twit on 2007-06-01
Thanks a lot B0rsuk, it is now installing!

---

### Post by B0rsuk on 2007-06-01
> **Fearless Twit said:**
> Thanks a lot B0rsuk, it is now installing!

No problem. Show windows  fanboys who's the boss. 
And if you start getting kicked (punkbuster), you need to update punkbuster manually.

---

### Post by Fearless Twit on 2007-06-01
Lol.

I'm now trying to install ActionCube, which is simular to ET but its not set in any time period.;)

---

