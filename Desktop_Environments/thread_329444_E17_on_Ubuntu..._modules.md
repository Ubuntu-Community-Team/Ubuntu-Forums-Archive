---
title: "E17 on Ubuntu... modules"
date: 2007-01-01
forum: Desktop Environments
---

### Post by linnerd40 on 2007-01-01
I have recently installed Enlightenment 17 on my Ubuntu system. All packages were installed from CVS. I used the following guide:

[http://www0.get-e.org/E17_User_Guide/English/_pages/2.1.html](http://www0.get-e.org/E17_User_Guide/English/_pages/2.1.html)

Here is my problem. Enlightenment loads fine... BUT, I can't load any modules or shelves. I think. What are shelves anyway? Are they places for modules to sit? When I try to load a module, I got to the configuration for modules, and enable the one I want... but nothing shows up. Now, if I have add a shelf to my desktop... and then try to load a module. I get an error. A "very bad error." Apparently, Enlightenment segfaulted. It suggests to recompile EVERYTHING... with a debugger extension. I am hoping for a quicker fix.... I really want to run Enlightenment 17... it just looks awesome. Any ideas on how I can over come this? I am very new to enlightenment.. but when I saw it run on my pentoo LiveCD, i just couldn't resist trying to load it onto Ubuntu. 

Thanks in advance!

---

### Post by linnerd40 on 2007-01-01
Anybody? Should I just uninstall everything... and try it again?

---

### Post by ting on 2007-01-05
Wy didn't you use the repos on get-e?

[http://www4.get-e.org/Main/News/_articles/365.html](http://www4.get-e.org/Main/News/_articles/365.html)

Iwe been using the repos for quite some time.

You just add the repositories in you /etc/apt sources.list

add the key

aptitude update

aptitude install e17


Oh. and you should probably uninstall the cvs version.
The repos are usualy only about a week old so I doubt you will miss any features.

---

### Post by linnerd40 on 2007-01-05
Yeah, that would have been a good idea :D . I found a script online that compiles and installed e27 from cvs. So it was really easy. Now I have E17! Yay!

---

