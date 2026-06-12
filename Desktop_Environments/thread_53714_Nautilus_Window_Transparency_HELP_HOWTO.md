---
title: "Nautilus Window Transparency HELP HOWTO?"
date: 2005-08-01
forum: Desktop Environments
---

### Post by snivitz0 on 2005-08-01
Eye candy question. I have been browsing a variety of different Ubuntu Hoary screens and have noticed a few where Nautilus file browsing windows backgrounds are transparent. I was wondering how this was done! Thanks in advance, snivitzo.

---

### Post by jasmuz on 2005-08-01
You could read here about how to tweak your Xorg to display transparencies:

[http://www.ubuntuforums.org/showthread.php?t=20769](http://www.ubuntuforums.org/showthread.php?t=20769)

---

### Post by snivitz0 on 2005-08-02
In a simple definition how would you define Xorg? Still trying to figure this out, but fairly new to the environment concepts in Linux. Would the proper configuration of Xorg integrate transparency anywhere within Linux? Thanks in advance  :) !

---

### Post by Reb on 2005-08-02
Xorg is a server to which applications send data.  Xorg draws this data onto your screen.  The transparency it provides with the Composite extension can be applied to any application by using the transset command.  Beware though, the software is still somewhat bugged.
I hope that helped and I hope I didn't get something wrong.

---

### Post by snivitz0 on 2005-08-02
Thanks Reb, I will look into that method when I get out of the office. I am curious of a simpler way to do this, I would imagine there to be a easy way of doing it. Any other feedback or input would be outstanding, thanks in advance again!

---

### Post by snivitz0 on 2005-08-02
I did the Xorg tweak, unfortunately I can not seem to get it to work at all for my video card (ATI 9800 Pro Atlantis). Back to the drawing board and open for ideas  :???: .

---

### Post by ruff on 2005-08-03
I have a notebook with an ATI radeon Mobility 9100 and have succesfully enabled transparency for my terminal window within gnome. 

> Open a terminal window
> Select current profile in the edit menu
> Select the effects tab
> Click the transparent background button

Presto ... transparent terminal window

---

### Post by Perfect Storm on 2005-08-03
[QUOTE=jasmuz]You could read here about how to tweak your Xorg to display transparencies:

[http://www.ubuntuforums.org/showthread.php?t=20769](http://www.ubuntuforums.org/showthread.php?t=20769)[/QUOTE]

In my humble opinion it's not worth it at the moment. 
1) It eats alot of resources.
2) It's bugged like heck.

---

### Post by snivitz0 on 2005-08-03
ruff: I have the terminal transparent, I just would just like Nautilus file manager transparent at this point.

A.I.: From what I was reading and gathered from a few people I heard the same thing, but I tried it anyway on a decent system, to no avail though. I could not even get into gnome under a few of the settings, it may have something to do with the card being newer or maybe 256MB, I am not sure.

If I remember correctly, I believe a few of the screens I saw of Nautilus transparent it was just the window background; it was not the entire window. This leads me to believe it was not done with Xorg configurations. I will keep at it, and if I find out anything new I will post.

---

