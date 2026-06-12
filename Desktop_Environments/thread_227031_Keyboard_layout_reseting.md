---
title: "Keyboard layout reseting"
date: 2006-08-01
forum: Desktop Environments
---

### Post by nathandh on 2006-08-01
Hello,

I'm having quite an anoying problem with kubuntu. For some bizare reason it resets my keyboard layout every time I reboot and even at random when I'm working on it.

I made a little script that sets it back to what it should (be- layout)be on my desktop tho so I just have to click it everytime it reseted to the standard us- layout. But still its quite silly and it would be nice if this could be solved.

Nathan

---

### Post by it.henrik on 2006-08-01
I am having the same strange behaviour in gnome .... 

did this start to occure after you tried glx+compiz?

---

### Post by nathandh on 2006-08-01
> **it.henrik said:**
> I am having the same strange behaviour in gnome .... 

did this start to occure after you tried glx+compiz?
Yep now you mentioned it, right after I started experimenting with compiz.

---

### Post by it.henrik on 2006-08-01
hmm we are onto something here ...

I have started 3 other threads about this and never ever got any replies. Lets hope for better luck this time.

Do you have any clues about what can be causing this?

---

### Post by Soyle Mycelf on 2006-08-01
I get this as well and I would really like this fixed.  Just throwing my repsonse in so developers are aware of how many are experiencing this problem.  Otherwise, I love xgl+compiz and even with this issue I am not giving it up.

---

### Post by bachisanerd on 2006-09-13
I am also having this problem, and while the Linux world is often this way (fix one bell, loose a whistle), I'd be interested in knowing if there is a modification to the xorg.conf file that will make the keyboard layout stay put.  I'm really liking this GLX stuff though.

---

### Post by sethmahoney on 2006-09-13
You all should bring this up on [www.compiz.net](www.compiz.net) - maybe they know something more.

---

### Post by Martin-Prise on 2006-09-15
I have this exact same issue, and have sorta found a way around it.

go to System -> Preferences -> Sessions -> Startup Programs, and add the command "setxkbmap [KEYMAP]", where my keymap (danish) was simply "dk".

Not using xgl/compiz btw, had the issue since installing ubuntu

---

### Post by argash on 2006-09-15
Out of curiosity how can i tell specifically which keymap is loaded. For example my keyboard is listed as Generic US 104 key and my layout is listed as US-English but I can't figure out which specific xmodmap that translates to.

---

### Post by Ciego on 2006-09-15
Same here .... I think this thread may be related too [http://www.ubuntuforums.org/showthread.php?t=224394](http://www.ubuntuforums.org/showthread.php?t=224394)

---

### Post by argash on 2006-09-16
> **argash said:**
> Out of curiosity how can i tell specifically which keymap is loaded. For example my keyboard is listed as Generic US 104 key and my layout is listed as US-English but I can't figure out which specific xmodmap that translates to.
anyone? anyone?

---

### Post by olnir on 2006-10-04
Having the same problems.
Does compiz/beryl take control of the keyboard (keymode) when it is loaded?
Keep having to reload keymap at startup to get my keyboard to work.

---

### Post by Ciego on 2006-10-04
Argash, 

Try using Keytouch ... it solved my problems.  
[http://keytouch.sourceforge.net/](http://keytouch.sourceforge.net/)

Orb recommended it in this thread
[http://ubuntuforums.org/showthread.php?t=224394](http://ubuntuforums.org/showthread.php?t=224394)

---

### Post by durand on 2008-03-16
> **Martin-Prise said:**
> I have this exact same issue, and have sorta found a way around it.

go to System -> Preferences -> Sessions -> Startup Programs, and add the command "setxkbmap [KEYMAP]", where my keymap (danish) was simply "dk".

Not using xgl/compiz btw, had the issue since installing ubuntu

Thanks a lot!

---

