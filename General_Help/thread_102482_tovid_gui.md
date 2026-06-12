---
title: "tovid gui"
date: 2005-12-12
forum: General Help
---

### Post by dolny on 2005-12-12
I installed tovid, but I can't find tovidgui.py file, and I cannot launch it. What is the command to run the gui version? Do I need to download more packages? 

'tovidgui' command doesn't work.

If anyone knows any other dvd authoring tool, with a gui, I would be grateful. I know qdvdauthor, but I would like to check more. DVDStyle (or something like that) has dependency problems. 

Thanks!

---

### Post by taurus on 2005-12-12
How did you install it?  If you installed it with either apt-get or synaptic, then it is under the Video section...

---

### Post by RikoW on 2005-12-12
you execute the gui of tovid from the command line in a  terminal by:

```
> which tovidgui.py
/usr/bin/tovidgui.py
> tovidgui.py
```

the first line just tells you, that tovidgui.py is installed in /usr/bin.

Hope that helps,

                 Riko

---

### Post by dolny on 2005-12-12
I installed it through apt-get, and I'm using Ubuntu + KDE, but I decided to post in here, cause there was a higher chance for a reply on more crowded forum section ;)

---

### Post by dolny on 2005-12-12
[QUOTE=RikoW]you execute the gui of tovid from the command line in a  terminal by:

```
> which tovidgui.py
/usr/bin/tovidgui.py
> tovidgui.py
```

the first line just tells you, that tovidgui.py is installed in /usr/bin.

Hope that helps,

                 Riko[/QUOTE]

The problem is that both *which* and *locate* did not find anything... :|

Thanks for your replies anyway.

---

### Post by RikoW on 2005-12-12
Just to make sure: you tried to execute tovidgui**.py** and not just tovidgui, right? Because that's what you wrote in your original post.

---

### Post by dolny on 2005-12-13
Yes tovidgui.py - there's no such file :|

---

### Post by RikoW on 2005-12-13
sorry, I should have checked that earlier ....

In synaptic the gui is a separate package called "tovid-gui". daah! :) 
supposingly, you would install it with this name also via apt-get.

cheers,

             Riko

---

### Post by jtpratt on 2006-03-16
also it depends on whether you installed from source or synaptic.  

for Tovid 0.22 (from the repository) the GUI command is tovid-gui

for Tovid 0.25 the GUI command is tovidgui

my help page for Ubuntu video conversion and Tovid stuff might help some people reading this post:
[http://smorgasbord.net/convert_video_linux]("http://smorgasbord.net/convert_video_linux")

---

