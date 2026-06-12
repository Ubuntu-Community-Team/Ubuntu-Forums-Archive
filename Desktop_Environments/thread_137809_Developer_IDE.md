---
title: "Developer IDE?"
date: 2006-02-28
forum: Desktop Environments
---

### Post by Thund3rstruck on 2006-02-28
I'm a .NET programmer. I've been testing out Ubuntu at home and I love it. Is there a developer IDE and SDK similar to Visual Studio that I can use to start programming for Linux? What languages are most often used in Linux and will my efforts translate to propritary UNIX platforms if I decide to persue the UNIX path  professionally sometime in the future? (though at present I am happy with C# and VB)

Thanks,
T3

---

### Post by andrewsawyer on 2006-02-28
Give Anjuta a try.  It can be downloaded from Synaptic or apt-get.

I don't know much about which programming languages are most often used in Linux, as I only took an intro to programming at Uni.  Have a play with that one though and tell us what you think.

---

### Post by jimjawn on 2006-02-28
Well you're in luck my friend.  Currently, there is the mono project which lets you write C# code for linux.  Its kind of like java is (sort of) but if you're using linux at all, then you probably know some of the applications that are written using mono.

Check out the [mono project]("http://www.mono-project.com/Main_Page") for more info.  They do a great job on getting you started learning about it.

Additionally, there are literally dozens of other languages and off-shoots that you can use in linux.  C (I believe) is used for kernel development.  You see a lot of C++, Python, Perl, Java around, those seem to be the big ones, and there are tons of smaller ones as well.  In fact, as a programmer, I find that the support in linux is much better and certainly the community is.

In terms of IDE's, there's a bunch out there, but most stuff is written with text and command line.  I used to be afraid of it, but the more I use linux, the more I like the command line.

Check out [monodevelop]("http://www.monodevelop.com/Main_Page") and the [eclipse project]("http://www.eclipse.org/").  Both are great IDE's and the most like Visual Studio.

Hope that helps you out a bit.  Personally, I like the more hands on approach.  I've learned a lot more faster by using a text editor and compiler programs, although its kind of tricky to understand at first.

---

### Post by Grey on 2006-02-28
Whatever your language of choice is, it should work in Linux.  I would strongly advise not using VB or .NET though.  I BELIEVE that they do have interpreters available however.  So you are free to use C#.  As for VB... I would strongly recommend using something else, simply because the language is so horrid.  ;)

As I mentioned, you CAN use any language you would like.  However, most of Linux is coded in C.  (As opposed to Windows' C++).  As a result, low level code will work best if coded in C or C++.  But there's a great deal of scripted languages available for simple stuff, such as the much beloved Python.

I kind of switch between Anjuta and Eclipse for IDEs... depending on what I'm developing.

---

### Post by Thund3rstruck on 2006-02-28
Great, I will spend some time playing with these and deciding which language to pick up in my spare time. Unfortunatly, since it is a hobby, I will not have the opportunity that I have on the windows side developing enterprise applications but it should get me on the road to contributing back to the community. 

I know a lot of you guys prefer coding at the command line but the idea of having to code every single button, OpenFileDialog, progressbar, and all the other controls just seems way too tedious to me, so I'll be sticking with the developer IDEs

Thanks,
T3

---

### Post by RAOF on 2006-02-28
[QUOTE=Grey]...
As I mentioned, you CAN use any language you would like.  However, most of Linux is coded in C.  (As opposed to Windows' C++).  As a result, low level code will work best if coded in C or C++.  But there's a great deal of scripted languages available for simple stuff, such as the much beloved Python.
...[/QUOTE]
Gnome (and GTK) is mostly written in C (although they use the crazy GObject system to get object-oriented stuff in there).  KDE (and Qt) is C++.  But they both have bindings for the language of your choice.

Mono also is an implementation of the .NET framework, so if you know that, you can code mono apps.  You just need to be aware the there is a small amount of the .NET stuff which is not fully implemented in mono yet.

---

