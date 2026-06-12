---
title: "best way to compile/debug/run C++ programs?"
date: 2009-03-21
forum: Education &amp; Science
---

### Post by irockonguitar on 2009-03-21
Hello

I'm using gedit to write a project in C++, which of course uses a couple of different .cpp and .h files. What's the best way to compile, build, debug, and run the program? 

Thanks in advance.

---

### Post by s|fr on 2009-03-22
The good thing about gnu.linux is that its all about choice. It would help if you think of it in terms of what suits you more instead of thinking along the lines whats best, because there is no such thing as a universal best.
I don't know if its helpful, but I'll tell you what I use.

Editor: vim
Compiler: g++
Debugger: some combination of valgrind and gdb
Project management and the rest: auto-tools

vim lets you launch programs from within so its easier for me to issue build and test commands etc. from one place. I like this setup cause its minimalistic and the core (meaning you get to learn more in the process). However if you are more interested in a complete IDE of doing things you can check out NetBeans, KDevelop and Eclipse. If you'd like another powerful editor you can also check emacs.

Both vim and emacs have a learning curve however I assure you when you do get the hang of these you'd rarely want to use anything else.

hth

---

### Post by irockonguitar on 2009-03-23
I have used emacs before, with g++, at school. What do I need to install and work with those? Any prerequisites, plugins, etc I should be aware of?

Thanks

---

### Post by s|fr on 2009-03-25
I would suggest experimenting a bit take your time and see what packages are available and research a bit on your own to find out the right packages for yourself.

Everything is available via apt-get install you can check for extra packages by doing something like

sudo apt-get install emacs<tab-key>

Pressing the tab key above will give a list of packages starting with emacs. There are tons of other things like syntax highlighting modes for emacs which would be a must.

For make tools you need to install autoconf, automake, m4. for help files or manuals try downloading the doc package (if available for that package) these are usually called "packagename-doc"; automake-doc for example. And you can always check the internet for more details.

most plugins for emacs are referred through their respective websites that you could also check. Google is your friend.

hope that helps.

---

### Post by irockonguitar on 2009-03-30
Ok, so you have to understand, I'm a noob at this. I looked at the installation guide for gcc and may as well have been trying to read a foreign language. Basically, I need to write a lot of C++ programs for school, and the school computers that I used last year ran Linux, and our C++ coding was done with emacs and g++. However, this year, we've supposedly "moved up" so now we're "allowed" to use Windows computers, except that we don't have a choice, and they use Visual Studio for compiling/building/debugging etc. I've gotten fairly comfortable with Visual Studio, but of course I can't use it when I'm trying to work at home, since I don't use Windows at all on my laptop.


That said, what would you recommend for me, keeping in mind that I'm still very much a beginner?

---

### Post by jdunn on 2009-04-01
> **irockonguitar said:**
> I have used emacs before, with g++, at school. What do I need to install and work with those? Any prerequisites, plugins, etc I should be aware of?

Thanks

'build-essential' package from the repositories for the gcc and c++ compiler.  As for an editor, I use gedit but you can get emacs from the repositories.

---

### Post by oldchris on 2009-04-02
Well, I'm a "recycled" noob (started with S360 and TRS80, but haven't done much programming in recent years except on microcontrollers) and I use Eclipse for C++.  

It isn't quite as easy as, say, Borland C++ Builder was (is?) but it does let you get rolling without quite remembering how to use make or gcc or dbg etc.  

I have to say I don't have a grip on GUI programming yet.  Glade and gtk seem to require an inordinate number of steps compared to a visual environment.  Probably terrific for added control when building "serious" code, but for casual use it seems a bit much (although useable). 

I know the CLI mafia will howl, but for things you don't do everyday, a GUI is much easier. 

Chris

---

