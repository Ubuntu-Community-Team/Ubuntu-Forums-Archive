---
title: "tovid and todiscgui problems please help"
date: 2009-11-17
forum: Desktop Environments
---

### Post by Mia1990 on 2009-11-17
Hi,

I found tovid and todiscgui i really love how todiscgui does menus but it will not work it doesn't give me any errors it just sets there.I also have tovidgui installed it tries to make a movie but after 3 hours it still hasn't converted it.I'm using ubuntu 9.10 tovid 0.31 and todisc 0.31 and trying to convert a avi to dvd.I would love to get todiscgui working.I've read a lot of post about todiscgui on the forum but can't find a solution to this any help with this would be greatly appreciated

---

### Post by serfcx on 2009-11-17
I used todiscgui for a while up to Ubuntu 8.10 but the update to 9.04 and by inference 9.10 broke it. Something to do with python I think. I can still use tovid through the terminal to create mpg from avi.
The svn repo has not been updated for a long while and the tovid google group is stagnant so I think the project has died.:(
Sorry nothing positive. Have you tried DeVeDe ? Its not bad.
Or you could use the command line for tovid to create mpg and then something like dvdauthor to create your menu.

---

### Post by Mia1990 on 2009-11-20
I tried to use devede but i would like to do full menus and can't seem to find a way to do it if it can.I had read on the internet were tovid or todisc didn't work with avi files could someone tell me if that is true.I am using avidemux to convert avi to mpeg and bombono dvd for authoring.

---

### Post by serfcx on 2009-11-20
> **Mia1990 said:**
> I tried to use devede but i would like to do full menus and can't seem to find a way to do it if it can.I had read on the internet were tovid or todisc didn't work with avi files could someone tell me if that is true.I am using avidemux to convert avi to mpeg and bombono dvd for authoring.

Tovid works fine with avi files - have a look at the man pages;)

An example

In terminal

tovid -pal -dvd -in my_file.avi -out output.mpg

This would convert the file my_file.avi into a pal dvd named output.mpg
If your region uses ntsc tv format then replace -pal with -ntsc

You can then use makexml to define the chapters or use another program of your choice - I have not heard of bombono

---

### Post by Mia1990 on 2009-11-21
Ok i've been learning devede a little more and it will do everything i wanted to do i still like how todiscgui makes menu's but i don't guess it's working right now so devede will work.

---

### Post by JBAlaska on 2009-11-21
DeVeDe Tip: If you have a multicore CPU, Check "Use optimizations for multicore CPU's" under advanced options.

It shortened my transcode time from 55min to about 16min for a 1.4GB avi with my AMD 9950BE.

---

### Post by Mia1990 on 2009-12-07
Hi,

I've just got todiscgui to work in Karmic 
 
I needed to add a line of code to 
/usr/lib/python2.6/lib-tk/tkMessageBox.py 
(i.e. in a terminal window 
gksudo gedit /usr/lib/python2.6/lib-tk/tkMessageBox.py 

 
 
(make sure that you indent the lines properly, the formatting here is messed up) 
 
def _show(title=None, message=None, _icon=None, _type=None, **options): 
if _icon and "icon" not in options: options["icon"] = _icon 
if _type and "type" not in options: options["type"] = _type 
if title: options["title"] = title 
if message: options["message"] = message 
res = Message(**options).show() 
# In some Tcl installations, Tcl converts yes/no into a boolean 
if isinstance(res, bool): 
if res: return YES 
return NO 
**res = str(res)** 
return res 
 
Don't forget to restart your computer after you add the line in bold 
Just in case anyone else has this problem this is how to fix it

---

