---
title: "[SOLVED] Learning C++ and I am Lost"
date: 2008-12-20
forum: General Help
---

### Post by thenocturnalhoodie on 2008-12-20
Hello everyone!
So I just got my computer running Ubuntu 8.04 LTS, and I've spent the past few days learning how to get around the terminal and everything. I've got a pretty solid grip on it. (I migrated from OSX, using the X11 terminal, so I've got some of the commands down). Anywho, one of my major reasons for moving to Ubuntu was for the developing and programming environments. I tried learning C++ on windows, and couldn't get any compilers for it. I tried using xcode on OSX, but I couldn't install it because I'm under 18 years of age, and can't join the ADC. 

So anyways. I need help getting my code to compile. I have written the source code in the anjuta text editor thing. I've got a simple "hello world" program right now. I saved it. I can get to the .cpp file, and then I am lost. I just installed the g++ program, but I don't know how to get my hello world file to run at all. 

I searched and searched for solutions. I found on thing that almost made sense, 
```
g++ code.cpp -o code
```

So I run that. Then a new file shows up in my home directory. It shows up as green text in the terminal. Now what do I do with it? I tried;
```
cat code
```
and all I got was gibberish to me. (I know cat shows everything about the file, so that would explain it)

But yea... where do I go from here?

---

### Post by Ayuthia on 2008-12-20
Try doing:
```
./code
```
When you use the -o option, the filename after the -o is the executable name.  To execute in the current directory, you just need to put ./ in front of the filename as shown in the code box above.  It just says to look for the file in the current directory.

The reason why you see gibberish when you did the cat, it is because the code has been compiled to an executable which is written in a code that the system will translate.

---

### Post by thenocturnalhoodie on 2008-12-20
Thank you! It worked!

Now to go on to the actual learning part of C++, hah.

---

### Post by ibuclaw on 2008-12-20
I tend to recommend this to new users of C or C++.

There is a really cool pseudo interpreter (doesn't actually do any interpreting, just packages, compiles and runs the code for you) called C ('large C').

It can be found here:
[http://www.archivum.info/fm.announce/2006-05/msg01184.html](http://www.archivum.info/fm.announce/2006-05/msg01184.html)

And usage for C++ applications is:
```
C -p **sourcecode.cpp**
```
First run will be slow as it is being compiled.
But since it caches all compiled sourcecode to /tmp, all runs of the file afterwards are at native speed.


Also, I hope you are getting your tutorials from here :)
[http://www.cprogramming.com/tutorial.html#c++tutorial](http://www.cprogramming.com/tutorial.html#c++tutorial)
Is above helped alot when I first started out with C/C++

Regards
Iain

---

### Post by monkeyking on 2008-12-21
> **tinivole said:**
> I tend to recommend this to new users of C or C++.

There is a really cool pseudo interpreter (doesn't actually do any interpreting, just packages, compiles and runs the code for you) called C ('large C').


Thats a strange tool.

I would go the otherway,
and recommend that the user,
stops using anjuta, and just use gedit.

Such that nothing is hidden, and the person will actually learn what happens with the text code they write.

---

### Post by jpmelos on 2008-12-21
Indeed, I'd recommend you to stop using Anjuta. If you are willing to use a tool like that, use NetBeans instead. Way better. You can find it in your Synaptic Package Manager. gEdit will get you tired fast, as to compile and test your application, you'll have to go to the terminal and type those lines, and eventually type Makefiles.

---

### Post by thenocturnalhoodie on 2008-12-25
Thank you everyone else who replied. I just checked back on this thread. Moved away from anjuta, using gedit now. and I"m using the tutorial that tinivole recommended, hand in hand with the book i bought. They complement each other well, actually.

---

