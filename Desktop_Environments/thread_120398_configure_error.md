---
title: "configure: error"
date: 2006-01-21
forum: Desktop Environments
---

### Post by pabs on 2006-01-21
Hello All,

I've run into a little problem on day 2 of my linux life...

I started off trying to install BitTornado.  (I am trying to compile everything from source btw.. I want to use the terminal as much as possible although I'm new to this) After running ./configure I had my first dependency problem.  I needed wxPython installed.  So I downloaded the wxPython source and ran into my next problem of
 
configure: error: no acceptable C compiler found in $PATH

Now I have no idea what $PATH is really, but I was able to gather that for some reason I did not have a C Compiler installed or it wasn't in $Path?  Anyway at the point I caved momentarily and used a apt-get command to install a copy of gcc (which seemed strange to me because it looked like there were quite a few gcc components already installed).  That allowed me to get a bit further in my ./configure for wxPython, but I have a new configure: error...

checking if the C++ compiler requires -ext o... configure: error: cannot figure

This one pretty much stumped me.  I'm not real sure where to go from here.  I tried googling and searching these forums, but I didn't come up with much.  Any help would be much appreciated!

---

### Post by cayamara on 2006-01-21
[QUOTE=pabs]I am trying to compile everything from source btw.. I want to use the terminal as much as possible although I'm new to this[/QUOTE]
With Ubuntu being Debian-based, it comes with a very good binary package manager (apt-get). With that, its easy to add new stuff by just typing ```
apt-get install bittornado
```But if you want to compile it from source and without the help of apt-get; though you could do a ```
apt-get source bittornado
``` you would probably be better off with something like [Gentoo]("http://www.gentoo.org") that lets you compile stuff from source quite easily and you still get to do **everything** from console.

Nevertheless, my suggestion is: Go easy on linux. Use ubuntu with apt-get and try to get a hang of a linux system. Figure out what $PATH means and stuff like that. Otherwise you'll get frustrated pretty soon.

Now for your question: To compile stuff, you need to have the built-essential package: ```
$ sudo apt-get install build-essential
```

---

### Post by pabs on 2006-01-28
thanks for the info on build essential.  That got me a bit further than before but I ran into another road block.  I'm just going to plan on using apt get.  Compiling from source seems like a hassel.  So everything is working ok now.

I turned focus to getting a FTP/SMB server up and running this past week.  Thats all done now just some tweaking is needed.  Woohoo!

---

