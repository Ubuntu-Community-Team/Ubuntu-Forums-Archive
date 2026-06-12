---
title: "Python and Opengl"
date: 2006-08-18
forum: Desktop Environments
---

### Post by omargomez on 2006-08-18
Hi Everyone!

I installed the python2.4-opengl package in Dapper to do some opengl work and found something funny that is driving me crazy. What happens is that when I run de demos a message appears:

[COLOR="Red"]freeglut (cube.py): Unable to create direct context rendering for window 'cube'[/COLOR]

What this means is that the program is not using DRI, which doesn't make sense since I have an accelarated hardware and driver. 

Just to check I compiled the C version of the program ( cube.c, one of the classic redbook demos ), and the same message don't appear, which tells me that the problem is not happening from C.

Has anyone experience weird things mixing opengl and python?

Help appreciated.

Omar

---

