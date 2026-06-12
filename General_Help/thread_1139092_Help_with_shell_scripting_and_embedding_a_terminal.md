---
title: "Help with shell scripting and embedding a terminal window..."
date: 2009-04-26
forum: General Help
---

### Post by Rahul Buttar on 2009-04-26
In the past I've tried to embed a terminal into my desktop for convenience and to make a habit of using the terminal more.  I'd usually mess up my gnome settings and have to reinstall ubuntu from scratch.  In fact last night I messed everything up again trying to do this and had to reinstall 9.04.  But today I finally figured it out!  I learned a little bit about shell scripting too and set up a script to open an embedded terminal every time I start my computer.  I've attached a picture of my desktop.

The script that opens the terminal reads:

#!/bin/sh
sleep 5s
gnome-terminal --window-with-profile=trans777

It's awesome that I finally got it to work but now I've run into another (slight) problem.  It only opens this embedded terminal on the first desktop and I'm running compiz fusion with 4 desktops.  How do I open a terminal window in all 4 using a startup script?

Also, one other thing.  Does anyone know how to make the desktop icons automatically align to the right in gnome?

---

### Post by Rahul Buttar on 2009-04-26
bump.  Anyone know?

---

### Post by Rahul Buttar on 2009-04-26
One last bump...

---

### Post by VCoolio on 2009-04-26
if you use compiz you can make it sticky in the window rules plugin. In the "Sticky" entry field you should add something like
```
(class=gnome-terminal)
```
but that would make all gnome-terminals you open alongside the one on your desktop sticky. Google adding by window name or id to fix that if you want. Oh, and forum etiquette states that you shouldn't bump within 24 hours.

---

### Post by utnubuuser on 2009-04-26
Hey Rahul Buttar

How do you implement this script?  Do I add this to a file or something to get the embedded terminal?

---

### Post by mb_webguy on 2009-04-26
Ok... What you need to do is create a profile in the terminal that uses a transparent background (which you seem to have done) *and* has an unusual title.

Now you can use that title to set what rules you want in the Compiz plugin Window Rules, and to remove window decoration for the terminal in the Window Decoration plugin.

---

### Post by Rahul Buttar on 2009-04-27
Wow, I feel stupid.

All I did was add "title=trans" to the sticky feild under window rules and it copied my console to every desktop.

I was messing around with devilspie for a little while before that and I was actually trying to get 4 seperate embedded terminals running simultaneously on different desktops.  The solution that I have now simply copies the output of this 1 terminal window 4 times.  It would be really cool to have 4 seperate terminals but that is a task for another day.

Now that I've actually gone through the steps of making a desktop terminal I think I might write up a guide for it because the websites that I visited when researching this subject all had incomplete information which is what I think causes people to do this wrong and mess up gnome.

> **VCoolio said:**
> if you use compiz you can make it sticky in the window rules plugin. In the "Sticky" entry field you should add something like
```
(class=gnome-terminal)
```but that would make all gnome-terminals you open alongside the one on your desktop sticky. Google adding by window name or id to fix that if you want. Oh, and forum etiquette states that you shouldn't bump within 24 hours.

Thank you!  (BTW the (class=gnome-terminal) didn't work for some reason, maybe it was the parenthesis?)

I'm really sorry for breaking forum etiquette.  I won't do it again in the future.

---

