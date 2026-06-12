---
title: "MUD Codebase [Python3]?"
date: 2010-10-20
forum: Gaming &amp; Leisure
---

### Post by Carpentr on 2010-10-20
As stated in the topic, I am wondering if there are any MUD Codebases written in Python 3? I am learning to code in Python 3.1 and have yet to find a MUD Codebase written with Python 3. I could only find ones written in Python 2.x. Anyone know if there are any out there?

If I could find one I was hoping to use it to motivate me to learn more Python programming, because I think making a MUD would be interesting.

---

### Post by OgreProgrammer on 2010-10-20
Python 3 doesnt change python very much. If you have a python 2 app, you can convert it. There is even a tool packaged with your python 3 to assist in this.

[http://docs.python.org/library/2to3.html](http://docs.python.org/library/2to3.html)

---

### Post by Carpentr on 2010-10-20
> **OgreProgrammer said:**
> Python 3 doesnt change python very much. If you have a python 2 app, you can convert it. There is even a tool packaged with your python 3 to assist in this.

[http://docs.python.org/library/2to3.html](http://docs.python.org/library/2to3.html)

Wow! I did not know this. Thanks a lot this should be really helpful. Now I guess I gotta start looking at Python Code bases and try and find a decent one.

---

### Post by OgreProgrammer on 2010-10-20
Hey point me back at some python muds. I have always wanted to read the code for one.

---

### Post by Carpentr on 2010-10-20
grailmud:
[http://pypi.python.org/pypi/grailmud/0.1a3#downloads]("http://pypi.python.org/pypi/grailmud/0.1a3#downloads")

I'm going to start with this one for now. I downloaded the source a couple hours ago. I'm going to go through the code soon, and hopefully convert it to 3.1. 

The only thing that worries me is that it uses Twisted as a dependency, and I'm not sure if converting the 2.x code to 3.x will cause issues.

NakedMud is also a fairly well known MUD Codebase. It's coded in C and scripted using Python. Don't think I'll use this, I'm looking for a pure Python Codebase.
[http://www.nakedmud.org/]("http://www.nakedmud.org/")

---

### Post by maligal on 2010-10-20
How did the conversion go? I've found upgrading from python 2.6 to 3.x to be fairly smooth (at least in the small apps I've tried).

Here is another open source mud: [http://www.ggsoft.org/ggmud/](http://www.ggsoft.org/ggmud/) looks fairly promising

---

### Post by Carpentr on 2010-10-21
Haven't attempted the conversion yet. I actually got side-tracked and played **[Ivalice MUD]("http://www.ivalicemud.com/index.php/Main_Page")** all night. 

I'm trying to decide if I should make a decently featured single-player text game before attempting to build a MUD from a code base. I figure porting the code base to 3.1 would a couple hours (lots of .py files) if everything went relatively smoothly. Not really sure though, I have never done it before.

---

### Post by OgreProgrammer on 2010-10-21
Thanks for the links Carpentr (and maligal).

---

### Post by Carpentr on 2010-10-21
> **OgreProgrammer said:**
> Thanks for the links Carpentr (and maligal).

Not a problem. Thanks for the help.

---

### Post by OgreProgrammer on 2010-10-21
> **Carpentr said:**
> Not a problem. Thanks for the help.

De rien.

---

### Post by jvc26 on 2010-10-28
Evennia is a very tidy looking python-based MUD codebase. You might want to get involved esp as its an OSS project! [http://code.google.com/p/evennia/](http://code.google.com/p/evennia/) 

J

---

