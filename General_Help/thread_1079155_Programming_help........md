---
title: "Programming help......."
date: 2009-02-24
forum: General Help
---

### Post by longlivethebestos on 2009-02-24
Hi, I want to learn a programming language so that I can contribute back to linux. I am havng trouble deciding between C or C++.

Here are the things I'm looking at:

Which is most usefull/most powerfull, so that you can create bigger things

I know that for linux if I wanted to create a program for gnome i have to learn c but for kde i have to learn c++, is this true? because virtual box is done in c++ and thats available in gnome..

Somethings telling me to learn C++, so I just wanted clarification but I'm sure I'll be fine with C++


Thanks for your time

---

### Post by mb_webguy on 2009-02-24
C is a lower-level language than C++, which means that C++ does some things for you and has some features that C doesn't.  For example, in C, you tend to access memory locations directly fairly often.  This makes C++ easier to write, but C somewhat better for things like writing operating systems and device drivers.

Because C is a lower-level language, you have to have a more thorough understanding of programming concepts.  It's sort of like the difference between using a calculator and using an old slide rule.  To use a calculator to multiply, you just have to know what multiplication *is*.  To use a slide rule, you have to know how multiplication *works*.  So if you have no programming experience whatsoever, it's probably better to start with a higher-level language so you can learn the basics like conditionals and flow control instead of worrying about things like memory pointers and garbage collection.

Personally, if you have no programming experience whatsoever, I wouldn't advise starting with either C *or* C++.  (And I teach computer science, btw, if that has any influence on your decision at all.)  It's better to learn to program than to learn a programming language.  Once you learn the fundamentals of programming, picking up a new language is just a matter of learning the differences in syntax.  I'd suggest starting with something like PHP or Python.  They're higher-level languages so it's easier to jump right in.  They're also scripting languages, so you can see the results of changes to your code instantly, without having to waste a lot of time compiling.  

Python is a more general-use scripting language and is becoming quite popular, but has a rather odd syntax that's a bit different from languages in the C family (including C++, C#, Java, etc.).  Python is used for quite a few desktop apps, including several of the applets you might use on the Gnome panel.  Because it's a general-purpose language, writing normal desktop applications or terminal programs is fairly straightforward.

PHP is very popular, but focused primarily on web applications.  It can do anything Python can do, however, though using it for things other than web scripting is slightly less straightforward than with Python.  That said, I've written a couple of simple desktop applications in PHP (using a combination of [PHP-GTK]("http://gtk.php.net/") and the [PHP command line interface]("http://www.php-cli.com/")).  PHP also has a syntax more similar to C than Python, which may make it easier to move to C or C++ later.

---

### Post by heindsight on 2009-02-24
> **mb_webguy said:**
> It's better to learn to program than to learn a programming language. Once you learn the fundamentals of programming, picking up a new language is just a matter of learning the differences in syntax.++


I might just add that your choice of desktop environment shouldn't affect your choice of programming language at all. KDE apps generally use the QT toolkit while GNOME apps use GTK. Both of those have bindings for a wide array of languages (including C, C++, Python, Java, Perl and C#). However, I'd recommend that you stay away from GUI programming at first.

---

### Post by jespdj on 2009-02-24
Note that there's a [Programming Talk](http://ubuntuforums.org/forumdisplay.php?f=39) forum here in which questions about programming belong.

---

### Post by simeon87 on 2009-02-24
Yes, languages like C and C++ force you to deal with issues that aren't essential to solving the actual problem but they are needed to get things running on a computer (like allocating or freeing memory) but the actual problem solving is thinking about which steps should be taken and in which order to compute the right values.

---

### Post by longlivethebestos on 2009-02-24
Thats cleared up alot, one thing though - Is python not slow? Some people say it is, like in linux mint the start menu is writen in python and for the most part is good but there can be times where it's a bit delayed.

I didn't know there was a programming forum :eek:


Thanks again

---

### Post by heindsight on 2009-02-24
> **longlivethebestos said:**
> Thats cleared up alot, one thing though - Is python not slow? Some people say it is, like in linux mint the start menu is writen in python and for the most part is good but there can be times where it's a bit delayed.

I didn't know there was a programming forum :eek:


Thanks again

Python is an interpreted language, so a program written in Python won't as quick as an equivalent program in say C or C++, but chances are you (as a human) won't even notice the difference.

---

### Post by ibuclaw on 2009-02-24
I started programming on C/C++ ... so I have no reason not to say that you should try basic C++ first to learn the simple compulsory bits that define imperative programming.
A pretty good site to teach you is here: [http://www.cprogramming.com/tutorial.html#c++tutorial](http://www.cprogramming.com/tutorial.html#c++tutorial)

But I do agree with others that where you may shine more is in the 4th Generation, or scripting languages. such as Perl, Ruby or Bash Shell scripting.

Bash shell knowledge is one of the most useful things to have, as what you are wanting to achieve is almost likely already been written, and just waiting for you to figure out what programs, arguments, and order of the piped text ;)

Regards
Iain

---

