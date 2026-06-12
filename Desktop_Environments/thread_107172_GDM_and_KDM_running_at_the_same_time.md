---
title: "GDM and KDM running at the same time?"
date: 2005-12-22
forum: Desktop Environments
---

### Post by drotter on 2005-12-22
Orginally I installed Kubuntu and so im guessing it uses kdm.  But I eventually installed gnome (apt-get install gnome-destop) which im guessing uses gdm.  When i look at the services it says that kdm and kdm are both running.  So, since I'm using gnome, I turned of kdm and it killed my session.  I went to a console and i had to restart by "startx".

Is it possible that im running gnome through kdm or since i installed kubuntu fist it starts kdm by default and when i log in it starts gdm after?

Is this a problem?  Does it effect preformance?

I would expect that i would be saving resouces by just running one and not the other...
what can I do?

thanks in advance for the help

---

### Post by art on 2005-12-22
kdm and gdm are **login** managers (for KDE and GNOME), so I guess when you installed gnome you still kept your default manager to be kdm. I am not sure why gdm is running, I thought they are mutually exclusive... What happens when you kill gdm?

---

### Post by drotter on 2005-12-22
nothing happens when i kill gdm.  So i'm assuming that its using kdm.  Like i said before when i kill kdm the x windows session stops and it goes to a console.  
But then i dont understand why it loads gdm also.  I think that all it does it control the login screen...If thats true then i dont really care which one it uses.  I just dont get why they are both running...

---

### Post by nalmeth on 2005-12-22
hmm

when you installed gnome-desktop there should have been a screen asking you to pick which one to use. If its really getting to you, or getting in your way, try simply uninstalling the one that you don't think is primary (sounds like kdm may be the primary?)

sudo apt-get remove gdm

I don't think they use much memory, but I can't see why both are running at the same time.

Perhaps others do and will give you something more.

I have had weird experiences with straight debian where kdm and gdm were running at the same time on different servers, but I can't give you much in the way of detail, and this is not the same situation. 

PS:
I like GDM better, but whatever works is best

---

### Post by drotter on 2005-12-22
Thanks for the reply...
I guess its not a real big deal.  To be completely honest, when i installed gnome i wasnt paying that much attention to it so it might have asked me if i prefered kdm or gdm (obviously i must have picked kdm).

Nothing seems to be screwed up and it works.  I never would have noticed if i wasnt looking around to see what services were running.  So whatever...
If its a matter of looks then i dont really care.

thanks anyway

---

