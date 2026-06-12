---
title: "How do I do this in Ubuntu?"
date: 2005-12-24
forum: Desktop Environments
---

### Post by ardchoille on 2005-12-24
I am learning more and more about this wonderful distro. Now, I'd like to learn about the following. Suppose I see an app that I like and want to install it.

**1) How do I check to see if it is already installed?** On an rpm-based system, the command is

```

rpm -qa | grep appname

```

and that command searches the installed apps database for the text "appname" and returns the name and version of the app if it is installed. Returns nothing if it isn't installed.

How do I do that on Ubuntu 5.10?

**2) If I already have the app installed, how do I find out some information about the app and the package that installed it?** I'd like to be able to see the following info:

[LIST=1]
[*]The name of the app

[*]Any dependencies of the app

[*]The files the package provides

[*]The person who packaged the app

[*]The repo it came from; main, universe, multiverse, etc. (if any)
[/LIST]

Is this possible?

I am coming from Fedora, which is rpm-based, and it used yum and rpm. I have found that apt-get is amazingly fast - which is one of the things that made me fall in love with Ubuntu and drop Fedora (yum is horribly slow).

Ubuntu is the best distro that I have used thus far and I want to learn more about how to do package management on command line.

---

### Post by kaamos on 2005-12-24
[QUOTE=ardchoille]1) How do I check to see if it is already installed?[/quote]
Try this: "dpkg -l | grep name_of_package"
> 
2) If I already have the app installed, how do I find out some information about the app and the package that installed it?
I this "apt-cache show name_of_package" or "apt-cache showpkg name_of_package" do the trick.

I suggest reading the man files for apt-cache and dpkg. Hope this helps and merry christmas. :)

---

### Post by mcsf on 2005-12-24
Hi,

1) I suppose you refer to apps installed through apt, right? In that case, the command would be: ```
apt-cache policy appname
```

2) Again, on an apt-based system:
```
apt-cache show appname
```
```
apt-cache showpkg appname
```

No need for root (or sudo) for any of these commands. ;)
Hope this helps.

Miguel

---

### Post by timfrost on 2005-12-24
Ubuntu uses the debian packing tools.  The program dpkg is a major front-end, and is equivalent to rpm in Fedora.

To see what packages are installed, run
```

dpkg -l

```

The list of files in an installed package is obtained with
```

dpkg -L <packagename>

```

And to get full details about a package
```

dpkg -s <packagename>

```

---

### Post by ardchoille on 2005-12-24
Wow! I knew there was a way to do exactly what I wanted :)
These commands are even better than those available for rpm.

Thank you all for the replies and for contributing to my Ubuntu education :)

You are all appreciated!

---

### Post by dcstar on 2005-12-24
[QUOTE=ardchoille]
.......
Ubuntu is the best distro that I have used thus far and I want to learn more about how to do package management on command line.[/QUOTE]
Or you could simply use Synaptic and see all of this information in an easy to use GUI.

---

### Post by ardchoille on 2005-12-24
[QUOTE=dcstar]Or you could simply use Synaptic and see all of this information in an easy to use GUI.[/QUOTE]
True, but there are lots of times that I use my computer without having X running. In fact, I only run X when I need to surf the web, email or play mp3's, I can do everything else without X. Which reminds me.. some idiot said Ubuntu was "dumbed down", what a load of crap. Ubuntu is no more dumbed down than any other distro.

---

