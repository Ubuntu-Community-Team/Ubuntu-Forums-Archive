---
title: "any way to switch between gnome and kde?"
date: 2006-09-08
forum: Desktop Environments
---

### Post by whatrucrazy on 2006-09-08
Just read an article describing how in redhat you can switch between gnome and kde as your desktop environment via the terminal:
[I]
Task: To switch from GNOME to KDE, use the command

$ switchdesk kde
Task: To switch from KDE to GNOME, use the command

$ switchdesk gnome [/I]

[from: [http://www.cyberciti.biz/tips/quick-way-to-switch-from-kde-to-gnome-or-viceversa.html]](http://www.cyberciti.biz/tips/quick-way-to-switch-from-kde-to-gnome-or-viceversa.html])

Now i'm assuming this is do-able in redhat and related because the install contains the files for both desktop environments, wheras ubuntu does not. so my question is this: is there any way to achieve the same function in ubuntu?
(i'd like to try kde, but don't have the space for an install of kubuntu right now.) 

thanks

---

### Post by Paul41 on 2006-09-08
This tells you how to do it.

[http://www.psychocats.net/ubuntu/kde.html](http://www.psychocats.net/ubuntu/kde.html)

---

### Post by nrwilk on 2006-09-08
> **Paul41 said:**
> This tells you how to do it.

[http://www.psychocats.net/ubuntu/kde.html](http://www.psychocats.net/ubuntu/kde.html)

That guide tells how to switch between the two DEs the normal way.  You'd have to end the session in one DE before beginning a new session with the other.  What whatrucrazy is asking for is a way to switch between them while running them simultaneously.  I think. :) 

That would be a cool thing to know, whatrucrazy.  I hope you get an answer.

---

### Post by aysiu on 2006-09-09
```
sudo aptitude update
sudo aptitude install xnest
gdmflexiserver --xnest
``` That's how you do it.

---

### Post by whatrucrazy on 2006-09-10
> **aysiu said:**
> ```
sudo aptitude update
sudo aptitude install xnest
gdmflexiserver --xnest
``` That's how you do it.

hmmmm, interesting.
so i've installed all the kde core stuff, installed Xnest and i'm good to go. i can now use Xnest to run kde inside gnome (wow! how cool is that).
i have read the xnest man page, but it seems like xnest is not mainly used for something like this but for servers inside servers kind of stuff (i know that's what i'm doing, but i imagine it was designed for something a bit more serious).

so question/s: 
1/ how do i run a kde window from gnome; what is the command?
2/ where can i fine some other command line options, or exp[lanations? from the man page i wouldn't have been able to see that "gmdflexiserver --xnest" would run a gnome dsiplay inside its own independent xserver.

thanks to aysiu for pointing me in the right direction :^)

---

### Post by aysiu on 2006-09-10
So after you run the GDM login screen in its own window, you just log into a KDE session in that window.

---

### Post by whatrucrazy on 2006-09-10
> **aysiu said:**
> So after you run the GDM login screen in its own window, you just log into a KDE session in that window.

duh! that is so obvious, i can't believe i didn't see it.
thanks again

:^)

---

### Post by theDahv on 2006-09-13
Will any of these methods work for different DE's? For example, say I use GNOME and I want to switch to Fluxbox without having to log out. Is that possible?

---

### Post by aysiu on 2006-09-13
Yes.

---

### Post by DJiNN on 2006-09-16
Wow!! Nice one..... i just gave this a try & it works really well. 

[screenshot]("http://ubuntuforums.org/gallery/showphoto.php?photo=3524&cat=500") 

It's really good for learning about another WM on the same machine. In fact i could think of many good uses...... I shall certainly be trying this one out some more. :)

---

