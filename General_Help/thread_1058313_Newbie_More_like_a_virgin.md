---
title: "Newbie? More like a virgin"
date: 2009-02-02
forum: General Help
---

### Post by puv on 2009-02-02
I install Ubuntu a week ago and its great. The thing is I install it because I want to start learning how to program in C, but I am totally illiterate on this subject and working with the terminal, text editor, compiler, C standard library and commands things like that. I search the Internet for books and I found  "Ubuntu Unleashed 2008 Edition: Covering 8.04 and 8.10 (4th Edition)"  and "HTML, XHTML, and CSS Bible (4th Edition)" and I already have a C programming book called "K.N. King C programming - A MODERN APPROACH (2th Edition)" are these books what I need to learn from the very beginning? Or where should I start?  [-o<

---

### Post by taurus on 2009-02-02
The C programming book should be what you want if you want how to program in C.  However, before you start writing a program and compiling it, you need to install the build-essential package first.

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install build-essential
```
That would install gcc compiler and all the libraries for you.

---

### Post by mb_webguy on 2009-02-02
Those are probably as good a place to start as any.  [This one]("http://www.amazon.com/Beginning-Ubuntu-Linux-Novice-Professional/dp/1590599918/ref=pd_sim_b_1") is supposed to be pretty good for learning how to use Ubuntu.  

If you're new to programming, C isn't necessarily the best place to start.  It's a fairly low-level language, and not very comprehensible if you don't have a good understanding of basic concepts.  If I were you, I'd start with something like PHP.  It's a scripting language that's a bit more readable than C even though it uses similar structures.  Since it's a higher-level language, you can focus on the aspects of programming common to all languages rather than getting bogged down in low-level and often frustrating concepts like garbage collection and pointers.  And since it is a scripted language rather than a compiled language, you won't have to be constantly compiling to see the results of minor changes to the code.  Once you get comfortable with PHP, then you can migrate to C.

---

### Post by Glubbdubdribian on 2009-02-02
I started with Python and that's quite high level and is really good for teaching you the basic concepts. loads of fun books on it too :)

---

### Post by puv on 2009-02-02
> **taurus said:**
> The C programming book should be what you want if you want how to program in C.  However, before you start writing a program and compiling it, you need to install the build-essential package first.

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install build-essential
```
That would install gcc compiler and all the libraries for you.

It work, Thanks! :D

---

### Post by puv on 2009-02-02
> **mb_webguy said:**
> Those are probably as good a place to start as any.  [This one]("http://www.amazon.com/Beginning-Ubuntu-Linux-Novice-Professional/dp/1590599918/ref=pd_sim_b_1") is supposed to be pretty good for learning how to use Ubuntu.  

If you're new to programming, C isn't necessarily the best place to start.  It's a fairly low-level language, and not very comprehensible if you don't have a good understanding of basic concepts.  If I were you, I'd start with something like PHP.  It's a scripting language that's a bit more readable than C even though it uses similar structures.  Since it's a higher-level language, you can focus on the aspects of programming common to all languages rather than getting bogged down in low-level and often frustrating concepts like garbage collection and pointers.  And since it is a scripted language rather than a compiled language, you won't have to be constantly compiling to see the results of minor changes to the code.  Once you get comfortable with PHP, then you can migrate to C.

PHP got, thanks.

---

### Post by adamlau on 2009-02-02
I studied off of *The C Programming Language* by Ritchie & Kernighan while at UCLA. I failed the class the first time around :( .

---

