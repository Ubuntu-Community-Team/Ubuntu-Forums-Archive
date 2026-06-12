---
title: "programing windows programs in linux"
date: 2009-04-16
forum: General Help
---

### Post by ayastona on 2009-04-16
hey.. programing question here..

i want to build a simple database program that will run on my windows machine. i am familiar with visual basic and visual c++ and a few other languages but up until a few weeks ago i was a windows user..

is it just possible for me to write the program in, say, c++ and use a specific compiler to make it an .exe?

thanks.

---

### Post by codeseer on 2009-04-16
> **ayastona said:**
> hey.. programing question here..

i want to build a simple database program that will run on my windows machine. i am familiar with visual basic and visual c++ and a few other languages but up until a few weeks ago i was a windows user..

is it just possible for me to write the program in, say, c++ and use a specific compiler to make it an .exe?

thanks.

Generally the non-crossing parts of source code come when you start adding an interface. I believe GTK is your answer for cross-platform interfaces with C++.

Edit:

Here you go: [http://www.gtk.org/]("http://www.gtk.org/")
It says it supports C, C++, Python, C# and more.

I'm not sure you can compile an .exe on the Linux side; you probably can somehow. But, you could use a windows machine and the basic command line compiler.

---

### Post by James_Lochhead on 2009-04-16
QT is also cross platform. KDE uses QT rather GTK. I am not sure that was his question though.

---

### Post by James_Lochhead on 2009-04-16
g++ (the GNU C++ compiler) can run on both Windoze and Linux (as well as other platforms). As long as your code has no platform specific components you should simply be able to compile it on your Windoze machine and it will work.

---

### Post by James_Lochhead on 2009-04-16
I think the title of this post if misleading. I think it is meant to be "Programming Windows programs in Linux" (i.e. capital W in windows).

---

### Post by codeseer on 2009-04-16
Yeah, I forgot about QT. I haven't hardly touched C/C++ since C# came out.

*Places a barrier of defence between himself and the angry mob of C# haters*

Edit:

*Reinforces that barrier*
*Seals the cracks in the barrier*
*Throws a rabid sheep over the barrier*

---

### Post by 3Miro on 2009-04-16
I use Virtual Box to create windows .dll files.

Some people have made Visual Studio work under wine.

QT has a cross platform thing, but I am not sure is something needs to be installed first.

---

### Post by ayastona on 2009-04-16
okay so a couple things are going on with this thread here...

first of all, yeah the title sucks... it should be "How do i make a program for Microsoft Windows on my linux machine"

and the post it should read something more like this:

"i want to write a program with a GUI that runs on Windows Vista/XP. How do i do this?"

next: i downloaded gtk (im using gnome; ubuntu 8.10) and i also ran another apt-get command that people on this site suggested ubuntu users also run... i dont remember the commands because i just copied and pasted them (but i saw them on alot of websites and it was the same two commands suggested on all the sites)... 

I CANT FIGURE OUT HOW TO OPEN GTK! its not the applications menu and when i go to terminal and type gtk, nothing is found...

i wanna write this program its a very simple one too! (if you wanna know what it is supposed to do, just personal message me)

and the last thing i wanna ask is about this c# business.. i stopped learning about programing when i entered college and i didnt bother even reading up about c#... enlighten me please?

---

### Post by James_Lochhead on 2009-04-16
GTK is pre-installed on Ubuntu as Ubuntu uses it for all its applications. If you want a designer try: 

```
sudo apt-get install glade-3
```

C# is just a programming language by Microsoft. Personally, I would just stick with C++...

---

### Post by Tibuda on 2009-04-16
You can also use [wxWidgets]("http://www.wxwidgets.org/"). See [this tutorial on cross-compiling]("http://wiki.wxwidgets.org/Cross-Compiling_Under_Linux").

> **ayastona said:**
> I CANT FIGURE OUT HOW TO OPEN GTK! its not the applications menu and when i go to terminal and type gtk, nothing is found...GTK+ is only a library, it should not be in your menu. You can use any text editor to write your application. Then, you compile it with a command (g++ for C++) or a Makefile. In Gedit, you can press Ctrl+F8 to run your Makefile if you install the "external tools" plugin.

> and the last thing i wanna ask is about this c# business.. i stopped learning about programing when i entered college and i didnt bother even reading up about c#... enlighten me please?
That's a long story. I can't say much, but you can see more here: [http://mono-project.com/Start](http://mono-project.com/Start)

---

### Post by codeseer on 2009-04-16
The way I understand GTK is it's just libraries. So, with C/C++ you'll be including the gtk header files.

C# is basically a mix between C++ and Java syntax, more Java probably. It does automatic garbage collection and is designed for rapid application development; from my experience, if you really know what you're doing and have a nice IDE and debugging environment, you can write a large application in 1/3rd the time it would take in C/C++. It is an ISO standard language with [ECMA specification]("http://www.ecma-international.org/publications/standards/Ecma-334.htm"). It was really created by Microsoft for use as the main language for the .NET Framework. However, .NET is essentially being ported from Windows to Linux in a project called [Mono]("http://mono-project.com"). Mono or .NET, whichever is used, is essentially the same as the basic libraries/header files you use in C++.

The whole idea behind C# is modernizing languages, having to not deal with garbage collection manually and being able to rapidly develop applications.

---

### Post by stoneage on 2009-04-16
Is Gambas any use to you? It is a lot like Visual Studio.

[http://gambas.sourceforge.net/](http://gambas.sourceforge.net/)

It is also available from the ubuntu repository.

---

### Post by directhex on 2009-04-17
Install "mingw32" and compile with "i586-mingw32msvc-g++" instead of "g++". This'll make Windows apps instead of Linux apps from C++ source.

---

### Post by Arup on 2009-04-17
For database nothing is better than couchdb which is included in the repos, its the easiest cross platform db to impelement.[http://couchdb.apache.org/](http://couchdb.apache.org/)

---

### Post by cb951303 on 2009-04-17
I recommend C# with MonoDevelop 2.0 as gui builder.

---

### Post by lisati on 2009-04-17
Suggestion: start with the stuff that doesn't depend on the OS, and add the GUI stuff later.

---

