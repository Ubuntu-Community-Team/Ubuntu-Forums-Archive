---
title: "System stats blended in with desktop"
date: 2006-04-16
forum: Desktop Environments
---

### Post by talos452 on 2006-04-16
Hey folks...   Im a lil new to ubuntu... and i love it... but a friend of mine uses DSL Linux... and he has this "system stats" thing on his desktop... is there any such interface for ubuntu? If so...  how to get it running?
](*,)

---

### Post by teasum on 2006-04-16
There is--it's called conky (based on Torsmo, which is what you're seeing in DSL): [http://conky.sourceforge.net/](http://conky.sourceforge.net/)

The problem is that Conky (and Torsmo) have trouble dealing with the Nautilus desktop in Ubuntu, so you have to do a little tweaking to get it to work.  

Check out this thread:

[http://ubuntuforums.org/showthread.php?t=61297&highlight=Conky](http://ubuntuforums.org/showthread.php?t=61297&highlight=Conky)

Good luck!

---

### Post by art on 2006-04-17
I would suggest gkrellm over conky, since no matter how much you tweak conky, even if does not flicker, it does not let you see your files on the desktop, which I think is weird at best. 
You could use gkrellm with a transparent theme I attach.

---

### Post by teasum on 2006-04-17
I second art's reply.  I was just responding to your original post, though, which was asking about a system monitoring tool integrated into your desktop.  In fact, I use Gkrellm, especially since it works well (via a plugin) with my dell inspiron laptop.  I think if conky didn't have difficulty running with nautilus, however, I'd spend time configuring and using that instead of gkrellm, because I like the neat desktop integration.  I'll give the invisible theme a shot, however.  Art: is there a way to get gkrellm to stick to the desktop in some way similar (at least in appearance) to conky/torsmo?

---

### Post by art on 2006-04-17
Absolutely. I attach a screenshot of my desktop. Right click on gkrellm, choose Configuration. Then in General->Options choose "Remember Screen Location...", then in General->Properties choose "Do not include on a taskbar" and "Do not include on a pager". Tweak further to your liking...

---

### Post by talos452 on 2006-04-17
how do i use this program...   im getting all kinds of errors

---

### Post by Ramses de Norre on 2006-04-17
Type gkrellm in terminal.
What errors do you get?
(to actually run it do gkrellm & so you can close the terminal without the program being stopped.)

---

### Post by talos452 on 2006-04-18
[QUOTE=art]I would suggest gkrellm over conky, since no matter how much you tweak conky, even if does not flicker, it does not let you see your files on the desktop, which I think is weird at best. 
You could use gkrellm with a transparent theme I attach.[/QUOTE]


I saved the file with your post....   i cant figure out how to run it ](*,) :confused: :-k

---

### Post by Bender the Robot on 2006-04-18
I believe it goes in the "Themes" folder, inside the .gkrellm2 folder which is in your home folder.

---

### Post by art on 2006-04-18
As Bender sais, move it to .gkrellm2/themes (don't forget the dot in front of gkrellm2), and then right click on gkrellm window and from configurations choose the theme invisible.

---

