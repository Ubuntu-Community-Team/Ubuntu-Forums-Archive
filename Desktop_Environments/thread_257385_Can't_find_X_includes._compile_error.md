---
title: "Can't find X includes. compile error"
date: 2006-09-14
forum: Desktop Environments
---

### Post by sludge99 on 2006-09-14
i get this error when trying to compile a program in kdevelop

checking for X... 
configure: error: Can't find X includes. Please check your installation and add the correct paths!

can somebody help me please

---

### Post by daller on 2006-09-14
I expect you to have the package "build-essential" installed.

It may be due to some other packages, try installing these:

```
sudo apt-get install xutils libx11-dev libxext-dev x-dev build-essential
```

---

### Post by sludge99 on 2006-09-14
thanks for the quick reply but it says they are all already the newest version

---

### Post by daller on 2006-09-14
What are you trying to compile?

Maybe I could download it, at struggle with it myself...?

---

### Post by sludge99 on 2006-09-14
just the default "Simple KDE Application" project that comes with it.

---

### Post by daller on 2006-09-15
> **sludge99 said:**
> just the default "Simple KDE Application" project that comes with it.

I don't know that app, what is it? (where)

---

### Post by Dinerty on 2006-09-15
You need to install:

kdebase-dev

---

### Post by sludge99 on 2006-09-15
Well i go from the menu project-->new Project-->c++-->kde-->simple kde application-->type hello in as a application name-->then click next 4 times then finish

kdebase-dev wouldn't install it says

The following packages have unmet dependencies:
  kdebase-dev: Depends: kdelibs4-dev (>= 4:3.5.3) but it is not going to be installed
E: Broken packages

then when i go for kdelibs4-dev it comes with
The following packages have unmet dependencies:
  kdelibs4-dev: Depends: libarts1-dev (>= 1.5.0) but it is not going to be installed
                Depends: libqt3-mt-dev (>= 3:3.3.5) but it is not going to be installed
                Depends: libavahi-qt3-dev (>= 0.4) but it is not going to be installed
E: Broken packages

---

### Post by Dinerty on 2006-09-15
Tried installing kdebase-dev through Synaptic Package Manager?

---

### Post by sludge99 on 2006-09-15
well i tried in adept first dont have Synaptic it just says break when i click install

---

### Post by sludge99 on 2006-09-15
i have had a look through to find where this package problem is coming from and it seems to be these 2 packages libfreetype6-dev and libfontconfig1

when i type sudo apt-get install libfontconfig1-dev
```
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libfontconfig1-dev: Depends: libfontconfig1 (= 2.3.2-1.1ubuntu12) but 2.3.2-7ubuntu1 is to be installed
                      Depends: libfreetype6-dev (>= 2.1.7) but it is not going to be installed
E: Broken packages
```

and when i type sudo apt-get install libfreetype6-dev
```

Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libfreetype6-dev: Depends: libfreetype6 (= 2.1.10-1ubuntu2.2) but 2.2.1-0ubuntu1 is to be installed
E: Broken packages
```

can i just force install these two packages and it will be alright ?

---

### Post by sludge99 on 2006-09-15
well i found some other posts on the forum that have had trouble with libfreetype6-dev the solution is
```
sudo aptitude install libfreetype6-dev
```
and you have to downgrade a few packages then
```
sudo apt-get install kdebase-dev
```

problem solved

thanks daller and Dinerty for your help much appreciated

---

### Post by UpsideDownFace on 2007-01-14
I use Ubuntu 6.06 (  because it has long term support ! ) and I much prefer Gnome to KDE
I have recently installed KDevelop, using Synaptic Package Manager.

When I built the "Hello World" program I got the message:-

  "can't find X includes, please check installations"

So I used Synaptic to search for kdebase-dev and it installed 107 pakages, so maybe KDevelop prefers Kubuntu, because lots of the pakage names started with "K".

The "Hello World" program now runs OK, except that I haven't yet got the Debug facility in KDevelop to work.

Just as explanation, I am doing this to help a friend, who thinks he needs an IDE.
I personally use gedit to write my programs, and debug them with KDbg.

An IDE hides all the things you need for learning C++. They are useful on large complicated projects with lots of programmers collaborating or competing, but under those circumstances there will be experts around to sort out any problems

---

