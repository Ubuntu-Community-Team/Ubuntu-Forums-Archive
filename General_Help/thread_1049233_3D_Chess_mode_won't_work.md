---
title: "3D Chess mode won't work"
date: 2009-01-24
forum: General Help
---

### Post by Shadow12313 on 2009-01-24
Hi, I am using Ubuntu 8.10 and I can't get Chess in 3D view to work, when I try I get the following error message:

You are unable to play in 3D mode due to the following problems:
No Python OpenGL support
No Python GTKGLExt support

Any ideas?

---

### Post by llamabr on 2009-01-24
Have you tried installing those packages?

sudo aptitude install python-opengl python-gtkglext1

---

### Post by Shadow12313 on 2009-01-24
I just tried it and now it works!  Thank-you!

---

### Post by karlmp on 2009-01-24
don't forget to mark your thread as solved

---

### Post by Shadow12313 on 2009-01-24
How do I do that?

---

### Post by starcannon on 2009-01-24
Look under Thread Tools *points up and to the right* red text.

Grats btw :)

---

### Post by Dr Small on 2009-01-24
> **karlmp said:**
> don't forget to mark your thread as solved

> **starcannon said:**
> Look under Thread Tools *points up and to the right* red text.

Grats btw :)


For your information, you can no longer mark threads as [SOLVED]. [Read more here...]("http://ubuntuforums.org/showpost.php?p=6548974&postcount=1")

---

### Post by starcannon on 2009-01-25
> **Dr Small said:**
> For your information, you can no longer mark threads as [SOLVED]. [Read more here...]("http://ubuntuforums.org/showpost.php?p=6548974&postcount=1")

Ack thanks Dr Small, I remember this happened last year as well; I look forward to it being resolved. In the meantime I suppose one could modify the title of the original post; while tedious, considering the price of support here, it seems fair enough ;)

---

### Post by Shadow12313 on 2009-01-25
> **Dr Small said:**
> For your information, you can no longer mark threads as [SOLVED]. [Read more here...]("http://ubuntuforums.org/showpost.php?p=6548974&postcount=1")

I hope it's fixed soon :(

---

### Post by OBpaddleoutSD on 2009-09-09
> **llamabr said:**
> Have you tried installing those packages?

sudo aptitude install python-opengl python-gtkglext1


I have the same problem, ran above command and still nothing, any pointers?

oh and now chess crashes and won't open... i suck... HELP!

---

### Post by hawthornso23 on 2009-09-10
> **OBpaddleoutSD said:**
> I have the same problem, ran above command and still nothing, any pointers?

oh and now chess crashes and won't open... i suck... HELP!

This is most likely a video driver issue. That is where I'd start looking anyway. Have you got 3-D drivers installed and working properly for your video card. Can you use compiz desktop effects? This most likely isn't anything specific to chess. That is just the program which tries to use 3-D effects and thus provokes the crash. The video and multimedia help forum may be a better place to look for help on this issue. The exact resolution will probably depend on what video card you have. 

Hope that gives you a place to start in trying to resolve your crashing problem. I can't help with the sucking problem. 

:lolflag:

---

### Post by OBpaddleoutSD on 2009-09-10
Compiz desktop effects all work, i got desktop cube to work real nice along with wobbly windows etc.
 
Have tried installing drivers for intel graphics card. Maybe i did it wrong...
 
thanks

---

