---
title: "How to correctrly isntall python?"
date: 2009-01-29
forum: General Help
---

### Post by mahela007 on 2009-01-29
I installed the package called "python 3.0" using the package manager. How can I check if python was installed? Also I dont think IDLE has been installed. How to I install it?

---

### Post by wilbbe01 on 2009-01-29
> How can I check if python was installed?
you can type the following at the command line and see what version it says, it should be there, although you may want to install the package which is only "python" without the "3"
```
python
```

> Also I dont think IDLE has been installed. How to I install it?
install the idle package from the package manager.

---

### Post by Jastonite on 2009-01-30
You should be able to type ```
python
``` into a console and enter the command-line interpreter.

To install IDLE:
```
sudo apt-get install idle
```

---

### Post by wilbbe01 on 2009-01-30
You shouldn't user idle to edit things either, it is too buggy and a pain to work with.  Find a tutorial on how to set up eclipse using pydev and you'll be a much happier person.  Eclipse should be easy to set up for diferent versions of Python as well (if you needed to write to the python 3 specifications for example).  Eclipse is much more fun to code in than idle, it's like night and day.

---

### Post by abhilashm86 on 2009-01-30
if you have installed python version 3.0, check this,type 

python3 in terminal
then check>> comes and you can work around with python

---

### Post by abhilashm86 on 2009-01-30
its better to use eclipse to work around python, when complex programs are handled in vim/nano/emacs indentation errors are tough to deal with ,use following to install eclipse
[http://www.eclipse.org/](http://www.eclipse.org/)

[http://pydev.sourceforge.net/](http://pydev.sourceforge.net/)

---

### Post by mahela007 on 2009-01-30
Thanks everyone! As usual I being my dumb self forgot to install the IDLE package. Thanks. I'll check out eclipse as well

EDIT: I've made my choice. I like eclipse. Is there anything I have to do besides install eclipse to get it to work with python?

---

### Post by wilbbe01 on 2009-01-30
Yeah, install pydev.  I'm not sure if it can be installed from the package manager in kubuntu or not, but it for sure is available from the eclipse updater thing or whatever it is called in one of the menus at the top.

---

### Post by kindofabuzz on 2009-02-13
Don't listen to any of these idiots saying to use Eclipse instead of Idle. yes they are right if you're an experienced python programmer, but if you're new to it, learn idle. it's very powerful. Eclipse is just overkill for a noob programmer. Idle and Gedit is all I need.

---

### Post by wilbbe01 on 2009-02-13
> Don't listen to any of these idiots saying to use Eclipse instead of Idle. yes they are right if you're an experienced python programmer, but if you're new to it, learn idle. it's very powerful. Eclipse is just overkill for a noob programmer. Idle and Gedit is all I need.

The reason I like eclipse and pydev over idle has nothing to do with my higher level of experience.

As far as simply functioning idle struggles way too often.  Yes, a simple text editor will get your job done without the added features of ecliipse.  However, simple little things like scrolling find struggles in idle.  Eclipse has more advanced features yes, but it also has features convenient to someone who is new at programming which idle does not have.  Also, you can assume the poster to be a new programmer based on context, but they never said that.  I don't care if you are in your first class of programming ever, eclipse if set up correctly will dance circles around idle.

---

### Post by kindofabuzz on 2009-02-15
> **wilbbe01 said:**
> The reason I like eclipse and pydev over idle has nothing to do with my higher level of experience.

As far as simply functioning idle struggles way too often.  Yes, a simple text editor will get your job done without the added features of ecliipse.  However, simple little things like scrolling find struggles in idle.  Eclipse has more advanced features yes, but it also has features convenient to someone who is new at programming which idle does not have.  Also, you can assume the poster to be a new programmer based on context, but they never said that.  I don't care if you are in your first class of programming ever, eclipse if set up correctly will dance circles around idle.

The purpose in idle is to test code snippets, not to write a fully functional script. Can eclipse do that? I don't know, i'm asking.

---

### Post by wilbbe01 on 2009-02-16
> The purpose in idle is to test code snippets, not to write a fully functional script. Can eclipse do that? I don't know, i'm asking.

Sure it can.  If you would like an interactive python console going right in eclipse you can get instructions here.  You can test little code snippets all you want.

[http://www.ibm.com/developerworks/library/os-ecant/](http://www.ibm.com/developerworks/library/os-ecant/)

Or if you would like you can type small code snippets in a file like you can in idle as well.  You can tell an individual little file to run in eclipse by telling it to run as a "python run."

It actually works very nicely.  If you wanted to type 
```
print("Hello world")
```
in eclipse it would do it very happily either as an actual file or in the interactive interpreter.

---

