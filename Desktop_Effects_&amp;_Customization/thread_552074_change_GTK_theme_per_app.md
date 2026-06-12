---
title: "change GTK theme per app?"
date: 2007-09-16
forum: Desktop Effects &amp; Customization
---

### Post by mattigras on 2007-09-16
Is there a way to change GTK class attributes per application?
The theme I'm working on is mostly dark with white text, but when I run Geany, the message window  inherits the white text from my theme, but uses Geany's light-colored background, so i can't see messages unless I click on them (see screenshot).  I'm pretty sure I just need to make another gtkrc file that changes the attributes of that one class to have black text but leave everything else the same.  I just need to know where to put that rc file so that it will load whenever Geany starts. anybody know if this is even possible?

I just started working on my theme tonight, so it's a work in progress but its getting there.  If anybody has any ideas about which class style I need to change, those would be appreciated as well.

I'm running Xubuntu Feisty.

---

### Post by Brucevdk on 2008-05-18
Came across this thread while trying to provide an answer for the thread *[Make Certiain Applications Independant of the System Theme](http://ubuntuforums.org/showthread.php?t=792228)* so I thought I'd just post a reply.

See the following thread (and more precisely [the reply by alvinistic](http://ubuntuforums.org/showpost.php?p=4513676&postcount=6)):
[LIST]
[*][*PLEASE HELP* Override GTK theme - Ubuntu Forums](http://ubuntuforums.org/showthread.php?t=688098)
[/LIST]
So in your case try something like:
```
GTK2_RC_FILES=/usr/share/themes/Human/gtk-2.0/gtkrc geany
```
Or in a launcher:
```
bash -c 'GTK2_RC_FILES=/usr/share/themes/Human/gtk-2.0/gtkrc geany'
```

---

