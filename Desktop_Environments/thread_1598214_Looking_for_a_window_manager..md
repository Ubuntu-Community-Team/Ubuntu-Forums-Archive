---
title: "Looking for a window manager."
date: 2010-10-16
forum: Desktop Environments
---

### Post by carisch on 2010-10-16
I am creating a Ubuntu based computer that will be displaying various information using various programs. I am starting with Ubuntu server because i would like to use a window manager that has "profiles" configured by a config file that can be edited with a text editor. The profiles Would be triggered by what programs were running at that time. 

Various triggers would run bash scripts that would close out a program so that one could be focused on the entire screen. Later the other programs would be relaunched and the screen would return to its original state. 

The only problem is i am not sure if there is a window manager like this. I have been researching window managers and i think that the WM i am looking for would be a tilling window manager, however not entirely sure. 

 I would also appreciate if the window manger had the option to remove the title bar as this would not be necessary. 


Thanks in Advanced

--Carisch

---

### Post by carisch on 2010-10-16
is there any way to use (and control) x without a window manager?

---

### Post by irv on 2010-10-16
In Gnome you can auto hide the bars so you have a blank screen. If that helps.

---

### Post by carisch on 2010-10-16
> **irv said:**
> In Gnome you can auto hide the bars so you have a blank screen. If that helps.
not really, but thanks.

i am looking for a window manager that can essentially be managed from bash scripts there will be very little mouse (or user for that matter) interaction to this computer.

---

### Post by roggenschrotbrot on 2010-10-16
awesome wm should be able to do at least most of the things you ask for. you can setup different tags with different layouts for each application and its behavior is fully costumizeable, so it should be a good start.

---

### Post by carisch on 2010-10-16
> **roggenschrotbrot said:**
> awesome wm should be able to do at least most of the things you ask for. you can setup different tags with different layouts for each application and its behavior is fully costumizeable, so it should be a good start.

thanks i will look in to it... 


do you know of any wm that can me manipulated by cli commands so i can create batch scripts?

---

### Post by roggenschrotbrot on 2010-10-16
again, awesome can interact with scripts quite well, you should be able to trigger everything awesome is apable of using keyboard shortcuts or scripts.
[http://awesome.naquadah.org/wiki/Signals](http://awesome.naquadah.org/wiki/Signals)

i use a script calling
```
echo "rhythmboxplay.text = \""$(rhythmbox-client --print-playing)"\""| awesome-client
```
to display the currently playing rhythmbox title for example.

edit: you can also just call you keyboard-shortcuts using xte.

---

