---
title: "synaptic works now, yay! So how do I install without internet?"
date: 2005-09-30
forum: Desktop Environments
---

### Post by urbandryad on 2005-09-30
In root that is. ^^ Assuming get it to work with sudo,  how do I install applications without the internet? Whats a compiler, how do I get Synaptic to read packages I download myself, if it can, and can I install packages without terminal, or how do I do it if so? Terminal newbie, so include all codes. ^^ O-o I'm still so new to all this.

Forgive me if I've already asked the above before, I can't find it in my 'search for your threads' function.

---

### Post by mlomker on 2005-09-30
[This is]("http://forums.livingwithstyle.com/archive/index.php/t-186392-how-to-compile-programs-from-source--p-1.html") a pretty good explanation of compiling things from source.

---

### Post by aysiu on 2005-09-30
If you download the .debs from through another computer, you can install them this way (assumes your .deb is on the desktop) ```
cd Desktop
sudo dpkg -i packagename.deb
``` Unfortunately, the *dpkg* command, unlike the *apt-get* command (which is really what Synaptic is--just graphically), doesn't resolve dependencies.

---

### Post by mlomker on 2005-09-30
Here's the [how-to]("http://www.ubuntuforums.org/showpost.php?p=98665&postcount=5") for creating a repository of your own (on your hard disk or your own web server if you have one).

---

### Post by Wolki on 2005-09-30
[QUOTE=urbandryad]In root that is. ^^ Assuming get it to work with sudo,  how do I install applications without the internet? Whats a compiler, how do I get Synaptic to read packages I download myself, if it can, and can I install packages without terminal, or how do I do it if so?[/QUOTE]

Installing a lot of coomon programs from a cd:

[http://www.mrbass.org/linux/ubuntu/](http://www.mrbass.org/linux/ubuntu/)

installing .debs without terminal:

[http://ubuntuforums.org/showthread.php?t=33584](http://ubuntuforums.org/showthread.php?t=33584)

---

### Post by regebro on 2005-10-01
[QUOTE=urbandryad]In root that is. [/QUOTE]Aha! So THAT's why that bloody dialog box refused to open!

I assume there is a file that has the wrong permission settings for it to be runnable with sudo, or? Because it works if you do a clean install...

---

### Post by urbandryad on 2005-10-01
[QUOTE=Wolki]Installing a lot of coomon programs from a cd:
[http://www.mrbass.org/linux/ubuntu/](http://www.mrbass.org/linux/ubuntu/)
installing .debs without terminal:
[http://ubuntuforums.org/showthread.php?t=33584](http://ubuntuforums.org/showthread.php?t=33584)[/QUOTE]

Eh, debian apps run on ubuntu right? So if I find an app thats a tar, can I use a debian version if thats available, as long as its Hoary compatible? ^^

---

### Post by Wolki on 2005-10-03
[QUOTE=urbandryad]Eh, debian apps run on ubuntu right? So if I find an app thats a tar, can I use a debian version if thats available, as long as its Hoary compatible? ^^[/QUOTE]

Well, usually you don't wnat to install things as a .tar, because you have to compile them (not hard, but people avoid it when possible).

If you can find a .deb for that application, you might be able to install that. Several .debs are not compatible with Hoary as they're made for a newer version of debian, they should work on Breezy in two weeks.

It's best to get .debs from packages.ubuntu.com, as they're the official ubuntu versions. Be prepared that you might have to install other software before you can install some packages, those are called dependencies. When you install them, it'll tell you what it needs.

If you tell us more specific what you want to install, the help you get can be more specific :)

---

