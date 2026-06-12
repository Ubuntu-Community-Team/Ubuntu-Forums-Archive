---
title: "Panel location keeps reverting"
date: 2009-10-18
forum: Desktop Environments
---

### Post by ssouthparkk on 2009-10-18
I have set up a 2-panel system on the bottom of my screen to maximize functionality and space. (For what I do on a regular basis, anyway.)

So, the problem I have is that on one panel, I have ONLY an open windows list.  I want that as the top panel, but, after I log out and then back in, it is on the bottom again.  Here is a screencap:

[IMG]http://i35.tinypic.com/28jgl84.png[/IMG]

So, I want the panel that is on the bottom in that pic to stay on the top.  Does anyone know if this is possible?  

EDIT:

Ok, this is strange...  On my OTHER computer I have Ubuntu on, I do not have this problem.  It stays where I put it...  Hmmmm
[IMG]http://i34.tinypic.com/vqmvz9.png[/IMG]


Thanks in advance, and I am loving Ubuntu.  I have reformatted my PC and now have XP on a 6gb partition.  Instead of Ubuntu being the less used and secondary one, that is now XP.  I need XP for some things I do, so I kept it on that small partition.  (I think everyone should still have it on their PCs for some things....  I am not fanboy of any OS, but I do hate MAC fanboys.  lol)

---

### Post by coldReactive on 2009-10-18
I had this happen on Xubuntu once.

try **sudo apt-get purge gnome-panel**. After that completes, immediately (from the same terminal) **sudo apt-get install gnome-panel**.

See if that helps next time it happens. You'll have to reconfigure the panel after you do a "purge" as it wipes all configurations.

---

### Post by ssouthparkk on 2009-10-19
That didn't work.  :(

I mean, it did it in Terminal, no signs of the command not working.  But that panel is still there with the same configuration.  No changes at all.

I guess I can get used to it.  Just weird in that position.

---

### Post by shazzer on 2009-10-19
Im having a problem dont know if this is the right place to fix it... Every time I minimize a package, it simply disappears. For example I have shiretoko running, or thunderbird, want to go back to it but cant find it minmized anywhere? Its driving me nuts, sure its a simple thing but I need to be able to re-maximize my stuff thats minimized but dont know how. Have gnome running and its written version 2.26.1.Dont know if its relative for gnome or specific to the package that I have to change a setting but it does it for everything whatever I start and minimize just disappears..??

Any ideas please much appreciated. Im using a netbook EEPC

---

### Post by mcduck on 2009-10-19
> **coldReactive said:**
> I had this happen on Xubuntu once.

try **sudo apt-get purge gnome-panel**. After that completes, immediately (from the same terminal) **sudo apt-get install gnome-panel**.

See if that helps next time it happens. You'll have to reconfigure the panel after you do a "purge" as it wipes all configurations.

--purge will not touch any user's configuration files, only system-wide settings. Every user's own configurations belong to that user, so only the user can remove them, never any administration tool.

Anyway, for the OP: ave you tried locking the panel (through gconf-editor)? Configure everything the way you like it, then hit Alt-F2 and run "gconf-editor". Browse to apps/panel/global and enable the "locked_down"-key.

---

### Post by Marflus on 2009-10-19
> **shazzer said:**
> Im having a problem dont know if this is the right place to fix it... Every time I minimize a package, it simply disappears. For example I have shiretoko running, or thunderbird, want to go back to it but cant find it minmized anywhere? Its driving me nuts, sure its a simple thing but I need to be able to re-maximize my stuff thats minimized but dont know how. Have gnome running and its written version 2.26.1.Dont know if its relative for gnome or specific to the package that I have to change a setting but it does it for everything whatever I start and minimize just disappears..??

Any ideas please much appreciated. Im using a netbook EEPC

No, this isn't the place - you should start your own thread, really. I assume you've tried Alt+Tab?

---

### Post by alienclone on 2009-10-19
> **shazzer said:**
> Im having a problem dont know if this is the right place to fix it... Every time I minimize a package, it simply disappears. For example I have shiretoko running, or thunderbird, want to go back to it but cant find it minmized anywhere? Its driving me nuts, sure its a simple thing but I need to be able to re-maximize my stuff thats minimized but dont know how. Have gnome running and its written version 2.26.1.Dont know if its relative for gnome or specific to the package that I have to change a setting but it does it for everything whatever I start and minimize just disappears..??

Any ideas please much appreciated. Im using a netbook EEPC

as another has already said, you should start your own thread for this problem, but maybe you dont know how since you are new to the forum so i will try to help anyway.

it sounds like you deleted one of the two default gnome panels that come with a fresh install, if that is what you did then you either need to create a new panel and right click on it and chose "add to panel" then chose "window list" or just add it to your one existing panel if you prefer only one panel.

---

### Post by ssouthparkk on 2009-10-19
> **mcduck said:**
> --purge will not touch any user's configuration files, only system-wide settings. Every user's own configurations belong to that user, so only the user can remove them, never any administration tool.

Anyway, for the OP: ave you tried locking the panel (through gconf-editor)? Configure everything the way you like it, then hit Alt-F2 and run "gconf-editor". Browse to apps/panel/global and enable the "locked_down"-key.
Thanks for the advice, but I thought of that.

I figured as much, that it would work, but I am constantly adding and removing to the panel, so I think it would be wiser to just leave it as it is.

The reason I wanted to have it on the bottom in the first place is because I normally, to get to the menu, just move my mouse all the way down and click.  (I am just use to it from XP, hard to break the habit.  Now I have to look and be careful. lol)

---

### Post by shazzer on 2009-10-20
Thank you so much alien clone.. thats solved it.. simple thing that drives you nuts. Thank you also for answering here, I will post my new problem via the new thread system... Thanks again.

---

### Post by mcduck on 2009-10-20
> **ssouthparkk said:**
> Thanks for the advice, but I thought of that.

I figured as much, that it would work, but I am constantly adding and removing to the panel, so I think it would be wiser to just leave it as it is.

The reason I wanted to have it on the bottom in the first place is because I normally, to get to the menu, just move my mouse all the way down and click.  (I am just use to it from XP, hard to break the habit.  Now I have to look and be careful. lol)

Another option would be configuring the panel's position by x & y coordinates, through gconf. That setting only works on non-expanded panels, but since you can also set the panel's width & height you could use a  non-expanded panel and just set it's size to use the full screen width.

---

