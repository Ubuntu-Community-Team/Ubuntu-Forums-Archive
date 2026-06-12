---
title: "PyDev for Python 2.7 and 3.2"
date: 2011-11-30
forum: Desktop Environments
---

### Post by lucacerone on 2011-11-30
Dear all,
I'm a Python newbie and would like to make some experience programming
both in Python 2.x and 3.x.
I could easily set up PyDev (Eclipse plugin) to use Python 2.7,
but I'd like to know if it is possible to create some profile
that runs my code using the Python 3.2 interpreter
to test if my code is portable in both the versions,
and eventually correct the parts that are not.

I've found a lot of guides referring to Python 2.x but very few tutorial
for Python 3 development in Ubuntu using Eclipse.

Thanks a lot in advance for your help,
Cheers, -Luca

---

### Post by dniMretsaM on 2011-11-30
PyDev can easily be set up to use 3.x. Simply point it to the 3.x interpreter during setup.

---

### Post by lucacerone on 2011-12-01
Hi dniMretsaM, thanks for your answer but may I ask you some more details?
I'm new both to eclipse and python, so I'm not sure what exactly I should be doing.

As far as I have understood in Eclipse I go to Windows->Preferences->PyDev
there I have to set the Python interpreter (I can see the one for 2.7).
I click on New..
In the interpreter name I set Python3.2,
and in the filesystem path /usr/bin/python3.2
(but after I do so, the path becomes /usr/bin/python3.2mu is that ok
or should I do again this step?)

Eclipse retrieves the systems libraries. I confirm the choice.

So I think this way Python3.2 interpreter is configured properly.

Now there are a few things I can't understand though.
Say I have a test.py file (a simple "Hello world" program that should run
flawlessly both using Python2 and 3).

I created this "module" before configuring Python3,
so in the Project view I can see that Python2.7 is going to be used
(you know if you expand the project name, you see the src folder and 
something saying Python2.7 with all the libraries etc etc).

How can I test my code using the Python3 interpreter?
Can I "switch" from one interpreter to an other during the development
so that I can test my code using both Python2.7 and Python3 while writing my code?

Also, I received from a friend at University some Python libraries he wrote. I unzipped them into my ~/friendpythonlib.
Ho can I use them in my code? Is it possible to add them only to a project
but not to the whole systems'libraries???

Thanks in advance for your help,
any hint is greatly appreciated.

Cheers, -Luca

---

### Post by dniMretsaM on 2011-12-01
If you write your code with something thing like [FONT=Courier New]#!/usr/bin/python2.7[/FONT] as the first line, you can only run it using Python 2.7. But if you don't use that, you can run it with any version you want by using this in terminal:
```
python2.7 /path/to/script
``````
python3.2 /path/to/script
```As for testing with different version of Python from within Eclipse, I'm not exactly sure (I haven't used it in a while, I use Emacs now). You probably just need to change the perspective (from 2.7 to 3.2 and vice versa) and run it in each.

> **lucacerone said:**
> Also, I received from a friend at University some Python libraries he wrote. I unzipped them into my ~/friendpythonlib.
Ho can I use them in my code? Is it possible to add them only to a project
but not to the whole systems'libraries???

To use a Python module in a singular project without adding them to the entire system, simply place the desired .py file in the same file as your program source code and call it the same as any system-wide module ([FONT=Courier New]import nameofmodule[/FONT], etc.).

---

