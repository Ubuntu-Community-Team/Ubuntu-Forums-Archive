---
title: "Running 2 X sessions"
date: 2008-07-13
forum: Desktop Environments
---

### Post by LebLinux on 2008-07-13
Hello, any ideas about running 2 X sessions at the same time for example:

I have WM E17 running as default on tty7.

Question is:

Can I run also Gnome on tty8 ???

Both should be up, one on tty7 and the other on tty8..

Thanks.

---

### Post by p_quarles on 2008-07-13
It's pretty easy, but I should note a couple things about the way I do this:
1) I use different accounts for each X session
2) I use startx to run both sessions, rather than a login manager. 

Anyway, just log into an unused terminal (like I said, I've only tested this with a new user), make sure that .xinitrc is configured, and run:
```
startx -- :1
```
to run X on display 1 (0 is the default).

---

### Post by LebLinux on 2008-07-13
Thanks, but what do you mean .xinitrc should be configured? and by running startx -- :1   <=== the "--" should be replaced with "gnome" for example if I already have e17 running on display :0 ?

---

### Post by p_quarles on 2008-07-13
> **LebLinux said:**
> Thanks, but what do you mean .xinitrc should be configured? and by running startx -- :1   <=== the "--" should be replaced with "gnome" for example if I already have e17 running on display :0 ?
~/.xinitrc in the current user's directory should indicate the program that X should execute, e.g. for Gnome:
```
gnome-session
```
And no (as the foregoing indicates), the "-- :1" is literal.

---

### Post by boblemur on 2008-07-13
hey im trying to do the same with one being a X11 forwarded over ssh...

im just not sure how i should go about doing this...

iv gone to tty8 and iv tried what you said above but i cant read the output it just says that its waiting to shutdown...

any help would be much apreciated

---

### Post by p_quarles on 2008-07-13
> **boblemur said:**
> hey im trying to do the same with one being a X11 forwarded over ssh...

im just not sure how i should go about doing this...

iv gone to tty8 and iv tried what you said above but i cant read the output it just says that its waiting to shutdown...

any help would be much apreciated
Try going to tty2. By default tty8 doesn't even exist. It will be created, though, if you run a second X session from a terminal that does exist.

---

### Post by boblemur on 2008-07-13
sorry i read it wrong... it was 6...


but im logged in and i can ssh -X to the other computer on my lan..


what should i do from here?

---

### Post by p_quarles on 2008-07-13
> **boblemur said:**
> sorry i read it wrong... it was 6...


but im logged in and i can ssh -X to the other computer on my lan..


what should i do from here?
If you've tried what I said and that doesn't work, then I don't know. I'm not in a position to test that kind of setup right now, so I could only offer wild guesses.

---

### Post by boblemur on 2008-07-13
hmmm ok, cause it says something about d?? is not enabled on moniter 1

should i be using display 1??

and a wild guess is more than i have :p so please guess away

---

### Post by LebLinux on 2008-07-13
> **p_quarles said:**
> ~/.xinitrc in the current user's directory should indicate the program that X should execute, e.g. for Gnome:
```
gnome-session
```
And no (as the foregoing indicates), the "-- :1" is literal.

Thanks, but I dont have .xinitrc in my home dirs...

---

### Post by p_quarles on 2008-07-13
> **LebLinux said:**
> Thanks, but I dont have .xinitrc in my home dirs...
Create it then. It only needs a single line, and that can be the one I already mentioned.

---

### Post by LebLinux on 2008-07-13
should I make it execute?  or just touch it and add "gnome-session" line to it?

Also If I added in user "y" everytime I run startx -- :1 from user "y" should uses "y"'s .xinitrc "gnome-session" line?

If I want to add other then gnome to .xinitrc . ex adding e17. I should change gnome-session in .xinitrc to "enlightenment-session" ?

Thanks.

---

### Post by LebLinux on 2008-07-13
never mind, I figured it :) .xinitrc leave permissions as usual. Also every window manager has its running "command line"

Gnome = gnome-session
enlightenment = enlightenment _or_ enlightenment_start.

Many Thanks.

---

