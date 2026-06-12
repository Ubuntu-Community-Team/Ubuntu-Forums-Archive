---
title: "Python programming creating functions"
date: 2013-10-04
forum: Education &amp; Science
---

### Post by courtney2 on 2013-10-04
Hey guys! I wasn't sure where to post this, so I apologize if I put it in the wrong spot. If I did, please let me know where you prefer me to post stuff like this!

My problem is this: I'm trying to do an assignment for my beginners programming class, and I'm having troubles outputting a word when I return the value. Here's what I have.

def greeting(firstname, lastname, yearborn):
    age = (2013 - yearborn)
    return ((firstname),(lastname), str(age))

What I'm trying to do, is spit out a message saying "Hello firstname lastname. You are x years old."
The thing is, when I type in "greeting(firstname, lastname, 1994)" I get a message saying it doesn't recognize "firstname". This works if I use a number in place of firstname and lastname. I've tried doing str() with them but no luck there either

---

### Post by sanderj on 2013-10-05
Why all the ()'s around the variables?

Anyway: it works for me. So post the exact code (including tabs) and the output if you need more help.

---

### Post by drmrgd on 2013-10-05
We can see your sub code and how you're calling it, but we don't have any idea on how the variables are getting loaded up before you pass them to the sub.  Definitely need the rest of your code before we can offer any advice on where you might be going wrong.

---

### Post by courtney2 on 2013-10-08
> **sanderj said:**
> Why all the ()'s around the variables?

Anyway: it works for me. So post the exact code (including tabs) and the output if you need more help.

I often just prefer using the parenthesis for my ease, but also keep in mind I'm new to programming :) 

when I run the module, I type in greeting(name, lastname, 1994) and I get the error

Traceback (most recent call last):
  File "<pyshell#1>", line 1, in <module>
    greeting(name, lastname, 1994)
NameError: name 'name' is not defined

---

### Post by courtney2 on 2013-10-08
> **drmrgd said:**
> We can see your sub code and how you're calling it, but we don't have any idea on how the variables are getting loaded up before you pass them to the sub.  Definitely need the rest of your code before we can offer any advice on where you might be going wrong.

That is ultimately all that I'm trying to code. I'm having troubles getting the program to return user input where I input a word for the variable "firstname" and "lastname". If I use a word, I get an error, if i type in an integer, then when it runs through return, it will return the integers I used and age. However, like I said I can't get it to function when I use a word. For example, here is what I get when I enter this:

>>> greeting(1, 3, 1994)
(1, 3, 19)
>>> 

my last reply shows what error message I get when I use a word

---

### Post by sanderj on 2013-10-08
... so define name ...

EDIT:

or run

greeting ('courtney','smith',1994)

---

### Post by courtney2 on 2013-10-09
> **sanderj said:**
> ... so define name ...

EDIT:

or run

greeting ('courtney','smith',1994)

Oh I see...I feel dumb haha. I don't know why I didn't think to use single quotes. That answered my question. Thank you for your help everyone!

---

