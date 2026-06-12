---
title: "How does one build from source?"
date: 2009-01-08
forum: General Help
---

### Post by KingAlanI on 2009-01-08
The application-install process is one of the big differences I notice between Ubuntu and Windows.

The package manager makes it easy to install stuff *that is listed in the package manager*...

However, would I have to build from source to install something that isn't listed in the package manager? The application's developers may or may not make a package available...

Source often comes in the form of .tar.gz files, does it not?
That's a form of archive/compression from what I understand. It presumably would be straightforward to unarchive/uncompress, but what would I do with the resultant files?

I don;t need to build my own apps, I am interested in building other peoples' apps.

---

### Post by lykwydchykyn on 2009-01-08
Depends what's in the files; sometimes it's sourcecode you have to compile, sometimes it's a precompiled binary that you just run.  Usually there's a file called README or INSTALL that tells you what to do.

Don't forget you can always search for a third party repo, or maybe find it on getdeb.com or similar sites (if there are any similar sites...).

Here's the community docs on compiling, though:
[https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware)

---

### Post by logos34 on 2009-01-08
this should get you started:

[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)
[http://www.tuxfiles.org/linuxhelp/softinstall.html](http://www.tuxfiles.org/linuxhelp/softinstall.html)

good luck and enjoy

---

### Post by agim on 2009-01-08
It is best to read the README file.

Remember though, compiling 3rd party programs from source is a great way to install something bad onto your computer. There are over 20,000 programs in Synaptic. That will cover most things.

I really can't stress enough how careful you have to be installing 3rd party programs. Ubuntu is safe, but can only be as safe as the user operating it.

---

### Post by sonu 1807 on 2009-01-08
Installing from synaptic is always better and try to avoid other installations 
But if you still want to do it then you can do this depending on the package you downloaded

.rpm (requires sudo aptitude install alien)

sudo alien -i *.rpm

.tar.gz (requires sudo aptitude install checkinstall)

tar xzvf ABC.tar.gz
cd ABC
./configure
make
sudo checkinstall

.package, .sh, .bin (Just download and execute)

chmod +x ABC
./ABC

.exe (requires sudo aptitude install wine)

wine ABC.exe

If you are installing theme for ubuntu then on desktop rightclick and select change desktop background and click the theme tab and then simply drag and drop the tar file to it

---

### Post by KingAlanI on 2009-01-08
I intend to use this sparingly, but it's a good thing to know *how* to do.

Linux tinkering planned as one of my weekend projects...

Not going to do WINE, I don't think - I can boot my Windows box if I feel like using Windows apps. :)

---

### Post by oldos2er on 2009-01-08
First thing to do is to install the package build-essential.

---

### Post by KingAlanI on 2009-01-23
would the terminal command for that be "sudo apt-get build-essential" ?

Also, I may want to practice building from source with a trusted mainstream app, as this will let me test the process without the security risk.

In relation to the above, does anyone have suggestions for such an app that is relatively straightforward to build from source? 
@agim: (Yes, I recognize that downloading and executing random stuff is a risky idea regardless of OS)

---

### Post by oldos2er on 2009-01-24
> **KingAlanI said:**
> would the terminal command for that be "sudo apt-get build-essential" ?

Also, I may want to practice building from source with a trusted mainstream app, as this will let me test the process without the security risk.

In relation to the above, does anyone have suggestions for such an app that is relatively straightforward to build from source? 
@agim: (Yes, I recognize that downloading and executing random stuff is a risky idea regardless of OS)

```
sudo apt-get update && sudo apt-get install build-essential
```

 is what you're looking for.

 If you stay with a well-known source like sourceforge.net or freshmeat.net you should be ok. Start a new thread if you get stuck.

---

