---
title: "Making new OS, need to create applications, how?"
date: 2009-06-16
forum: General Help
---

### Post by Poyzin on 2009-06-16
What would I code linux applications in? And what I REALLY want done is an application that browses the entire computer. Like the folders in Ubuntu. But I want to remake it, edit it so I can do things easier with it.

Any info would be great. Thanks.

-Brett

---

### Post by LowSky on 2009-06-16
what exactly are you trying to do?

Ubuntu has many options for traking down files and folders, even using the CLI, heres a tutorial,
[http://content.hccfl.edu/pollock/Unix/FindCmd.htm](http://content.hccfl.edu/pollock/Unix/FindCmd.htm)

Linux programs can be created in many coding languageslanguages

---

### Post by Poyzin on 2009-06-16
> **LowSky said:**
> what exactly are you trying to do?

Ubuntu has many options for traking down files and folders, even using the CLI, heres a tutorial,
[http://content.hccfl.edu/pollock/Unix/FindCmd.htm](http://content.hccfl.edu/pollock/Unix/FindCmd.htm)

Linux programs can be created in many coding languageslanguages


I want to create a transparent and animated window of the contents of the folder you clicked on appear. But it would take awhile to modify ubuntu's. So, I just want to get rid of ubuntu's, and make my own.

---

### Post by billgoldberg on 2009-06-16
> **Poyzin said:**
> What would I code linux applications in? 
-Brett

Mono.

Easy and fast.

Python is easy too, but slow.

---

### Post by Cheesemill on 2009-06-16
What programming experience do you have?

What you're talking about is a **major** piece of programming.
The beauty of open source software is that you can take the source code of a program and alter it to your own needs. It would be a much easier task to take a look at the nautilus source and adjust it as needed rather than re-inventing the wheel.

---

### Post by LinuxGuy1234 on 2009-06-16
> **Poyzin said:**
> I want to create a transparent and animated window of the contents of the folder you clicked on appear. But it would take awhile to modify ubuntu's. So, I just want to get rid of ubuntu's, and make my own.

For all of this, use compiz-fusion with a Python file manager (or you can use Qt's file viewer demo (Qt3 only?))

---

### Post by 3rdalbum on 2009-06-16
Well, you're probably looking at something like C++ or maybe Python. For animation, you might want to use the Clutter toolkit.

It could take you years to reach the level of programming proficiency where you can write a file manager on your own. The best place to start for Python is the tutorial on python.org - this takes you through the basics, you won't be programming GUIs with this tutorial.

There might be a file manager out there that does approximately what you want, but you haven't defined to us exactly what you want it to do. I'm not sure what you mean by "browsing the whole computer" - what part of the computer can't Nautilus browse? As for animations, that sounds like a fairly weak justification for writing a new file manager.

I believe the Enlightenment E17 project has a file manager. I don't know what state it's in, but Enlightenment has always been about being flashy. But yeah, if you could explain exactly what your file manager would do that Nautilus can't do, then we can help you better.

---

### Post by 3rdalbum on 2009-06-16
> **billgoldberg said:**
> Mono.

Easy and fast.

Python is easy too, but slow.

Slow to develop, or slow to execute?

Python is far from being slow to develop in.

As for execution speed, that depends on the implementation, not on the language. CPython might be slower than Mono, but what if you're using Psyco? And does it matter for a file manager? And will it matter considering that much of the program is going to be precompiled C libraries anyway?

---

### Post by juancarlospaco on 2009-06-16
> **billgoldberg said:**
> Mono.
Easy and fast.
Python is easy too, but slow.

Python.

Easy and fast.

Python is easy, and more fast than Mono, using with Psyco+Python.

---

### Post by Poyzin on 2009-06-16
thanks! I will defiantly use these.

-brett

---

### Post by decoherence on 2009-06-29
"I will defiantly use these."

That's the spirit! :lolflag:

---

