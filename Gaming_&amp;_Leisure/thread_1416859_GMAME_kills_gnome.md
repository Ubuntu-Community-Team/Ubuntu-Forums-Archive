---
title: "GMAME kills gnome"
date: 2010-02-26
forum: Gaming &amp; Leisure
---

### Post by Kirboosy on 2010-02-26
Hey,

I grabbed GMame from the package manger and it installed easily. Heres the problem. I can run the games fine but as soon as I exit the game it kills my Gnome. The game freezes on my screen and I can't do anything with it. I can pull up a terminal by pushing control + alt + F1 but I don't really see how that helps me since its a new login. I tried disabling my desktop effects but that didn't help at all.

Any ideas?

If it helps any I have a ATI Radeon Xpress 1400 Graphics Card

---

### Post by DoktorSeven on 2010-02-26
I've had trouble with MAME freezing on exit myself and wonder if this is the same issue.  I've helped it by setting MAME to use Windowed mode so I can kill it easily if (when) it freezes, but have no idea how to permanently fix the issue.

Regardless, if you're stuck with a fullscreen MAME (or any app) that freezes your desktop, you press CTRL ALT F1, you can log in with your username and kill MAME itself using the **kill** or **killall** commands, with the -9 signal if necessary (forces the program to terminate), e.g. **killall -9 sdlmame** (the frontend just calls MAME itself so you'll have to find the name of the MAME program running to kill, you don't need to kill the frontend itself; use ps (**ps ax**) to find which name to use in **kill**).  Then switch back to X using CTRL ALT F7.

---

### Post by Kirboosy on 2010-02-26
Thanks for the quick reply. First time that has happened to me on this forum. :D

Didn't think about that.....I will probably do that until I can figure out how to really fix it. I'm still googling but to no avail.

---

### Post by lockalidiot on 2010-02-26
I got this same issue with open arena. Thanks for starting the thread and the answers!

---

### Post by Kirboosy on 2010-02-26
I just installed OpenArena and I don't have any issues with it. The only thing that kills my computer is GMAME. You disable compiz before you play right? Cause compiz makes games do really weird things....

---

### Post by DoktorSeven on 2010-03-12
Update to my issue with MAME: seems that using OpenGL mode in MAME + multithreading caused my problems.  Either turning off OpenGL or multithreading in mame.ini makes it work properly, so I guess the Linux build of MAME is having problems with multithreading under OpenGL?  Or is it just me?

---

### Post by hunnydisuza on 2010-03-12
Really great post, and thanks for shearing a nice info, i read your post, i think every users are like that post,

---

### Post by Kirboosy on 2010-03-12
I tried just flipping off multi-threading but it still froze. It didn't lock up on the first exit though. It was like the 5th time. So I went ahead and turned off OpenGL and now it seems to be running perfectly. 

I have noticed however that there is like tons of fuzz in my sound. Its not my ROM because it doesn't do it in a Windows MAME Emulator running the same ROM. Its like the game sounds are made out of fuzz. Any ideas on how to fix this?

---

### Post by AlexanderDGreat on 2010-03-19
> Regardless, if you're stuck with a fullscreen MAME (or any app) that freezes your desktop, you press CTRL ALT F1, you can log in with your username and kill MAME itself using the kill or killall commands, with the -9 signal if necessary (forces the program to terminate), e.g. killall -9 sdlmame (the frontend just calls MAME itself so you'll have to find the name of the MAME program running to kill, you don't need to kill the frontend itself; use ps (ps ax) to find which name to use in kill). Then switch back to X using CTRL ALT F7.

I just type

```
pkill sdlmame
``` and wait for around 5 seconds before ALT F7.

Mame has choppy sound for me, yeah, kills my gnome window too.

---

### Post by AlexanderDGreat on 2010-03-19
I found a workaround for the hanging. Just before exiting switch to a Window Mode. You can configure this by Hitting "TAB" Input In General -> Interface. And there's a shortcut key for making the Game Run In Windowed-Mode, the default is LEFT ALT & RETURN. Now, before exiting the game by pressing ESC, correct? Switch to a window mode then exit gracefully or NOT. Then it won't kill Gnome. This works for me.

And yeah, my sound I just used Sample Rate 11025 so it's pretty decent.

---

