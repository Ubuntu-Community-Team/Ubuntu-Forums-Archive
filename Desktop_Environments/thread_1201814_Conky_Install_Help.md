---
title: "Conky Install Help"
date: 2009-07-01
forum: Desktop Environments
---

### Post by Wataru8675 on 2009-07-01
So...I'm super new to all this Linux stuff, and I can barely fathom what's going on when I read installation tutorials such as [this]("http://www.junauza.com/2009/06/conky-installset-up-and-auto-start-fix.html") one for Conky.  I THINK I followed it to par (after reading through two or three other similar tutorials to get a feel for the language) and all seemed to go well until I re-logged in to see if it installed correctly.  Conky did not appear on the desktop, so I went to the Terminal and simply typed ```
conky
```.

This however produced something undesireable.

```
kyle@Kyle-laptop:~$ conky
Conky: use_spacer should have an argument of left, right, or none.  'yes' seems to be some form of 'true', so defaulting to right.
Conky: forked to background, pid is 8376
kyle@Kyle-laptop:~$ 
Conky: desktop window (14000a6) is subwindow of root window (122)
Conky: window type - override
Conky: drawing to created window (0x2a00001)
Conky: drawing to double buffer
Conky: attempting to use more CPUs than you have!
obj->data.cpu_index 2 info.cpu_count 1

```I...uh...yeah, I have no idea what's going on or what any of this gibberish means, so after using this forum for 4 days, I decided to register to ask. ._.  I feel bad since I can't advise anyone else, though. ><

---

### Post by oldfred on 2009-07-01
In your home folder is a .conkyrc file. (under view check show hidden files). This was probably a sample or default that has 2 cpu's set up. I think most of the other info is just conky telling what is happening. You can find alternate conky setups on the conky site and other places [http://www.google.com/#hl=en&q=conky+config+files&aq=2&oq=conky+con&aqi=g10&fp=4IixsMzRQY0](http://www.google.com/#hl=en&q=conky+config+files&aq=2&oq=conky+con&aqi=g10&fp=4IixsMzRQY0)

---

