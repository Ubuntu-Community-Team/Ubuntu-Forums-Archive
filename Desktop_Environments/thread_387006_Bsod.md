---
title: "Bsod"
date: 2007-03-17
forum: Desktop Environments
---

### Post by myusrnm on 2007-03-17
So, this is a blue screen of death. . .
And, I'm running ubuntu. 


So, what happens is. . . 
I start up the computer! 
I get to the login screen, it's the blue one with the flower. 
So, I have two accounts, my normal one running beryl, and another one, without beryl or amorak  or gaim running on startup. 
I can log into my other one, without problems
and, when i log into my normal one, things start loading, I can see the amorak splash screen and gaim appear, then the screen turns blue. 
Completely blue, nothing on the screen, just blue. 
It seems to be the blue from the splash screen. 
And the mouse is there, stuck in that "loading" position. 

So, my suspicion is that beryl is causing problems, and I've done it before and it's been fine. So, I want to know how I could remove beryl from  startup, as it seems to be causing my problems. 

Anyways, I think it's because I recently changed my beryl settings, it may be the fact that I've added features like burn and a skydome during my last login. 

So, any help?

---

### Post by floke on 2007-03-17
Have you tried logging in in failsafe mode?

---

### Post by myusrnm on 2007-03-17
> **Steve.K said:**
> Have you tried logging in in failsafe mode?

no, care to explain? 

and, my computer is still functional, i can use my other account for stuff.

---

### Post by myusrnm on 2007-03-17
> **myusrnm said:**
> So, this is a blue screen of death. . .
And, I'm running ubuntu. 


So, what happens is. . . 
I start up the computer! 
I get to the login screen, it's the blue one with the flower. 
So, I have two accounts, my normal one running beryl, and another one, without beryl or amorak  or gaim running on startup. 
I can log into my other one, without problems
and, when i log into my normal one, things start loading, I can see the amorak splash screen and gaim appear, then the screen turns blue. 
Completely blue, nothing on the screen, just blue. 
It seems to be the blue from the splash screen. 
And the mouse is there, stuck in that "loading" position. 

So, my suspicion is that beryl is causing problems, and I've done it before and it's been fine. So, I want to know how I could remove beryl from  startup, as it seems to be causing my problems. 

Anyways, I think it's because I recently changed my beryl settings, it may be the fact that I've added features like burn and a skydome during my last login. 

So, any help?

after a while the screen will turn black, but if i shake the mouse it goes back to blue

---

### Post by myusrnm on 2007-03-17
man, i need help on this. it annoys me. 

so it's on a laptop, when it goes to the black the touchpad doesn't work
a mouse does though.

---

### Post by myusrnm on 2007-03-18
[FONT="Courier New"][B]b
  u                  h      h   eeeee ll       pppp
    m               h      h   e        ll       p     p
       p             hhhhh   eee    ll        pppp
         i            h      h   e        ll        p
          t           h      h   eeeee lllllllllll p
            y
bump[/B][/FONT]
/ubuntuforums is against crappy ascii art/

---

### Post by floke on 2007-03-18
From your sessions options - choose failsafe gnome and see if that helps.
BTW: Do you have beryl or anything set up to start on login, that might be causing it.

Anyway, try the failsafe Gnome and see what happens.

---

### Post by myusrnm on 2007-03-18
> **Steve.K said:**
> From your sessions options - choose failsafe gnome and see if that helps.
BTW: Do you have beryl or anything set up to start on login, that might be causing it.

Anyway, try the failsafe Gnome and see what happens.

Yeah, I have beryl amorak and gaim set to come on startup. i think it's the beryl. 

How can I do failsafe if I can't use the account ?

---

### Post by myusrnm on 2007-03-18
[http://ubuntuforums.org/showthread.php?t=384189](http://ubuntuforums.org/showthread.php?t=384189)
seems to describe my problem accurately. I think it'll work.

---

### Post by myusrnm on 2007-03-18
yeah, it works. 

Any ideas on what I should do? 
maybe i didn't have emerald loading on startup? 

and to future users of this problem who are inexperienced 
type 
> rm beryl-manager.desktop
or whatever, to remove stuff.

---

### Post by Lord Illidan on 2007-03-18
You can and should also configure beryl-manager to launch a fallback window manager. Have you tried it?

---

