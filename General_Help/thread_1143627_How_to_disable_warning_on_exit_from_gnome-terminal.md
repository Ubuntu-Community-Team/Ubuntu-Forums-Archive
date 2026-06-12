---
title: "How to disable warning on exit from gnome-terminal??"
date: 2009-04-30
forum: General Help
---

### Post by yesint on 2009-04-30
Dear All,
Anybody knows how to get rid of confirmation dialog, which pops up every time when gnome-terminal window is going to close? I'm opening and closing the terminal 100+ times per day, so it is very annoying. This "improvement" only appeared in 9.04 and there is no option to disable warning (at least at GUI level).
Any ideas?

---

### Post by darthmob on 2009-04-30
you are right, it's quite annoying! I just had a quick look in gconf-editor and tada:
open gconf-editor -> go to apps -> gnome-terminal -> global -> untick confirm_window_close

// edit: it does disable the confirmation dialog when closing multiple tabs as well, though.

---

### Post by kpkeerthi on 2009-04-30
I have not noticed this warning you mention about. I will have to check. May be thats because I close the terminal using <Ctrl> + D.

---

### Post by darthmob on 2009-04-30
> **kpkeerthi said:**
> I have not noticed this warning you mention about. I will have to check. May be thats because I close the terminal using <Ctrl> + D.the warning only pops up when you have got still something running. eg. closing the terminal when showing a manpage.

---

### Post by Grenage on 2009-04-30
It might also be looking at something like Yakuake, I know I couldn't live without it these days.

It's basically a quake-style terminal that pops down when you press F12 (or whatever you change it to).  Press it again and it disappears until you need it again.

---

### Post by yesint on 2009-05-01
> **darthmob said:**
> you are right, it's quite annoying! I just had a quick look in gconf-editor and tada:
open gconf-editor -> go to apps -> gnome-terminal -> global -> untick confirm_window_close

// edit: it does disable the confirmation dialog when closing multiple tabs as well, though.

Thanks a lot! That's what I tried to find!

---

### Post by yesint on 2009-05-01
Btw, the "minimalistic" philosophy of gnome sometimes becomes too extreme. The user should be able to disable any warnings at GUI level. I would rather consider this omission as a bug.

---

### Post by mb_webguy on 2009-05-01
> **yesint said:**
> Btw, the "minimalistic" philosophy of gnome sometimes becomes too extreme. The user should be able to disable any warnings at GUI level. I would rather consider this omission as a bug.

Um, unless I missed something, gconf-editor *is* a GUI application...

---

### Post by yesint on 2009-05-02
> **mb_webguy said:**
> Um, unless I missed something, gconf-editor *is* a GUI application...

It is, but many people just don't know that it exists. It is much like running regedit in Window$ - this is not what end user should do.  I just don't understand why not to include such option into the preferences of the terminal itself.

---

### Post by jelle_ on 2009-05-08
thanks, i hated that warning

---

### Post by Speque on 2009-05-12
Thanks, just what I needed.

---

### Post by deepclutch on 2009-05-12
Ubuntu Jaunty just don't shut down if I opened a terminal(and I use "sudo sux -" instead of simple "sudo" to achieve a root terminal) as root  and closed it(without exit-ing).Is there anyway to disable this nagging inorder to shutdown the system fast?

---

### Post by asbesto on 2009-08-05
> **yesint said:**
> Dear All,
Anybody knows how to get rid of confirmation dialog, which pops up every time when gnome-terminal window is going to close? I'm opening and closing the terminal 100+ times per day, so it is very annoying. This "improvement" only appeared in 9.04 and there is no option to disable warning (at least at GUI level).

It's one of the most *STUPID* thing I ever seen on GNU/Linux system; I acknowledge this is the upgoing trend, adding stupid and annoying unuseful "features" (I want to mention also the double click to the "volume" icon, that was SO HANDY - opening the mixer, and now? Now it shut off sound. The most annoying thing in the world. I wonder WHY. :confused: )

Who is the guy that created this? Please, I NEED to know his name. I want to know who is the guy that started up with such an idea. :confused:



Many thanks for the gconf stuff also.

---

### Post by asbesto on 2009-08-05
> **yesint said:**
> Btw, the "minimalistic" philosophy of gnome sometimes becomes too extreme. The user should be able to disable any warnings at GUI level. I would rather consider this omission as a bug.

I think the Gnome philosophy is "IDIOT", not "minimalistic". Minimalism don't require asking STUPID things like "Hey, really you wanna quit yo' terminal?" or "Hey, I decided to wait 60 seconds for shutdown, ha ha ha" or the best, in my opinion: "System policy prevent stopping the system when other users are logged in". Totally INSANE for a unix system. 

I think Gnome developers has to go back in time and LEARN what UNIX means.

:confused:

---

### Post by pp7 on 2011-11-05
Any idea how to do this in 11.10?  dconf-editor which I believe is the same as gconf-editor does not have this option.

---

### Post by oldos2er on 2011-11-05
Closed, please start a new thread for your question.

---

