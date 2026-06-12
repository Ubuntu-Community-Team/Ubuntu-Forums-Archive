---
title: "I don't have terminal?"
date: 2005-10-13
forum: Desktop Environments
---

### Post by garciadc on 2005-10-13
Hello,
     I installed 5.10 on my amd64 laptop, and  I can't find terminal.  Is anyone having similar problem?

---

### Post by invalid on 2005-10-13
Assuming you are using gnome, it should be in Applications -> Accesories -> Terminal

Cheers,
Cb

---

### Post by taurus on 2005-10-13
Or 

sudo apt-get install aterm
-or-
sudo apt-get install rxvt

for a nice terminal...

---

### Post by invalid on 2005-10-13
[QUOTE=taurus]Or 

sudo apt-get install aterm
-or-
sudo apt-get install rxvt

for a nice terminal...[/QUOTE]

You sort of need a terminal to use apt-get ..

But you could choose to install through synaptic instead

Cheers,
Cb

---

### Post by darkmatter on 2005-10-13
The terminal is under Application -> Accessories. If you need it on right click
```
sudo apt-get install nautilus-open-terminal
```

---

### Post by dbott67 on 2005-10-13
[QUOTE=darkmatter]The terminal is under Application -> Accessories. If you need it on right click
```
sudo apt-get install nautilus-open-terminal
```[/QUOTE]

If you've been using Warty and/or Hoary and want the terminal back in the context menu (i.e. right-click), then follow darkmatter's instructions.

-Dave

---

### Post by Wolki on 2005-10-13
[QUOTE=invalid]You sort of need a terminal to use apt-get ..[/QUOTE]

There's also the virtual consoles on <ctrl>+<alt>+<F1-6>. Useful to know if you need quick access to a terminal (a task locks & breaks X, and you want to kill it, for example). Use <ctrl>+<alt>+<F7> to go back to your X session.

---

### Post by kvidell on 2005-10-13
And yet again;
If you're using Gnome, you can hit Alt+F2 to pop up a little run dialog, type in the name of your favourite terminal emulator (I like xterm) and hit "Run"

It's a handy little trick.
I also have the mini-commander on my bottom gnome-panel. It's very useful.
- Kev

---

### Post by Leigh on 2005-10-14
I would like to get "Terminal" in my context menu (right-click menu) so I tried darkmatter's instructions, however, I got an error saying "Couldn't find package nautilus-open-terminal."  Any ideas what I've done or am missing?

---

### Post by dbott67 on 2005-10-14
[quote=Leigh]I would like to get "Terminal" in my context menu (right-click menu) so I tried darkmatter's instructions, however, I got an error saying "Couldn't find package nautilus-open-terminal." Any ideas what I've done or am missing?[/quote] 
Have you enabled all of the extra repositories?

Read my post in [this thread]("http://www.ubuntuforums.org/showthread.php?t=73527") --- it explains how to add extra repositories from the command line & graphically.

-Dave

---

### Post by Leigh on 2005-10-14
Thanks for your help, Dave.  I added the extra repositories and there are no errors, but there is still no "terminal" option when I right click my desktop. Maybe I misunderstood what was said in this thread, but I was wanting to right-click my desktop and see terminal in the context-menu. Is this what all of the bove allows me to do or am I barking up the wrong tree?

---

### Post by dbott67 on 2005-10-14
No... this is what it does (you're barking up the right tree) :).  You may have to type the following to get it to work:

```
killall gnome-panel
``` 
(or maybe a logout/login/re-boot.  I seem to recall that it didn't show up right away for me).

-Dave

---

### Post by Leigh on 2005-10-14
Once again thanks for you help.

The command didn't work, but a re-login gave me what I wanted.

Thanks again.

---

