---
title: "remove sidebar/get bottom start menu and taskbar?"
date: 2011-07-04
forum: Desktop Environments
---

### Post by chillydude on 2011-07-04
Hi, I don't like the new interface with 11.04 but don't want to go back to the other one (that was in 10.10) either.  I would like to continue using what's included with the base install but configure it a bit more to my liking.

I would first like a bar on the bottom of the screen, just like windows has.  Admittedly, I've been using windows for a long time now, and that's what I'm used to.  So, how can I move the bar from the top of the screen to the bottom?

Second, how can I have that bar show me the programs I have open?  If I have firefox, office and terminal open, i want those listed in the bar just like windows does it.  When i'm using the interface now, i can't tell what programs i have open - it just doesn't seem too intuitive to me this way.

Finally, how can i get rid of that stupid side bar on the left?  if i want shortcuts on my desktop, i'll put them on my desktop.  otherwise, i want a nice clean UI with a single bar on the bottom just like windows has.  

inb4 "why not just use windows and get off this forum" :p  the windows UI is about the only thing I like about it, and would be using linux full time if at all possible.  

Oh and finally, when the computer boots, before signing in or clicking anything, there is a very loud DONK sound or something...how do i disable that? lol.  thanks :)

---

### Post by Purplerob on 2011-07-04
Before you login select Classic from the menu at the bottom (after you select your name). This will give you a two bar look. Right click on the top panel and remove it.On the bottom panel right click in empty space and click add to panel add the main menu and other things that you want to add. To move or delete stuff from the panel just right click.

---

### Post by oldos2er on 2011-07-04
Perhaps you should give one of the other desktop environments a try, e.g. xfce. Gnome "classic" is going to disappear with 11.10.

---

### Post by chillydude on 2011-07-04
Yes, I know about Classic mode, but don't want to use it because it is going away.  If anything, I'd simply revert back to 10.10 since it was basically perfect for how I like things, but I do like to stay up to date.  :)

I'd also like to stay away from "third party" DWMs since they're horribly unreliable in terms of updates and support and even life span.  That's another point...  I loved the UI in ubuntu 10.10, only to find it completely changed (for the worse imho) in 11.04 :(

Maybe I'm in the minority, but I don't like fancy UIs.  I like minimalistic, spartan interfaces for everything, and so far, windows has everything beat.  I have a plain light blue background, some desktop icons, and a single bar at the bottom from which everything is accessible.  I have shadows disabled, window/menu animations disabled, window "snap" disabled, aero disabled, and even show window while dragging disabled.  Even though ubuntu is much better on memory usage, I still want to disable all the fancy garbage that's included :)

Thanks for the replies!

---

### Post by Krytarik on 2011-07-04
You may want to give AWN a try. You can very much resemble the Windows7 panel with it, and put everything you want into a single panel at the bottom. And it's not hard to 'plain' it down, neither is it resource-hungry, I'm using it on a 10-year-old machine.

See here how to set it up in the default Unity session, or a custom session:
[http://ubuntu4beginners.blogspot.com/2011/05/run-awn-dock-in-natty-narwhal.html](http://ubuntu4beginners.blogspot.com/2011/05/run-awn-dock-in-natty-narwhal.html)

Hope you will like it as much as I do. :)

Greetings.

---

### Post by wildmanne39 on 2011-07-04
> **chillydude said:**
> Yes, I know about Classic mode, but don't want to use it because it is going away.  If anything, I'd simply revert back to 10.10 since it was basically perfect for how I like things, but I do like to stay up to date.  :)

I'd also like to stay away from "third party" DWMs since they're horribly unreliable in terms of updates and support and even life span.  That's another point...  I loved the UI in ubuntu 10.10, only to find it completely changed (for the worse imho) in 11.04 :(

Maybe I'm in the minority, but I don't like fancy UIs.  I like minimalistic, spartan interfaces for everything, and so far, windows has everything beat.  I have a plain light blue background, some desktop icons, and a single bar at the bottom from which everything is accessible.  I have shadows disabled, window/menu animations disabled, window "snap" disabled, aero disabled, and even show window while dragging disabled.  Even though ubuntu is much better on memory usage, I still want to disable all the fancy garbage that's included :)

Thanks for the replies!Hi, there is not a perfect way to do it,but I followed this set of instructions it stays hidden almost all the time it will only open when I hit the super key or move my mouse all the way to the top left screen. ) In the Unity plugin, set Reveal to Auto hide and the Reveal edge to None or Disabled. Screenshot shows that the edges are disabled so that it will not open ,you can tell because all around the little window it is in red, if it was set to open when the mouse was moved to the edge it would be in green. You do have to have ccsm installed to change unity plugin settings.
There is no way to remove the unity launcher hiding it is the best you can do. I use the awn launcher and I put the menu from gnome2 on it so I just click and I have an app menu instead of using dash.Sorry I do not have one that looks more like windows menu. I can see everything that is open by the little triangles at the bottom of the icons in the launcher.

---

### Post by Purplerob on 2011-07-04
If you want something really lightweight try lxde or xfce. (lubuntu, xubuntu)

---

### Post by dFlyer on 2011-07-04
What your asking to do is not yet possible with Unity. You can install ccsm which will allow you to auto hide the side bar, but as far as I know there currently is no way to completely remove it.

You do have the choice of using classic gnome, but your right about it going away for gnome3 in 11.10, which I'm currently waiting for. You also have the choice of downloading and installing Fedora 15 which has gnome3 or continue Unity as that is the future of Ubuntu. The nice thing about Linux is the choice.

---

### Post by chillydude on 2011-07-05
Thanks for all the replies, I really appreciate it.

I just noticed another thing that bugs me...  Where is my "start menu" application list?  Lol...  

You mention gnome3, but also mention that unity is the future of ubuntu.  I guess I don't understand, is gnome3=unity?    Or is gnome3 going to be an option in future ubuntu like "ubuntu classic" is now?

I really just want it to be like it was in 10.10 :|  that was basically perfect for what I like.

Not really interested in trying out different DWMs either, since I really don't want to have to set up menus and crap every time there's an update. 

At this point in the UI evolution, it's actually easier for me to get stuff done on my freebsd box with cli only.  Seriously, I must be missing something with this UI, it just seems a MAJOR step backwards, like the interfaces in linux were a decade ago.  blah

---

### Post by adit on 2011-07-05
> is gnome3=unity? Or is gnome3 going to be an option in future ubuntu like "ubuntu classic" is now?

gnome3 is a desktop environment.  Unity is just an interface to the underlying desktop environment.

1) For example take ubuntu 11.04 *default installation*.  It has gnome 2.32.  On top of it there are two interfaces classic interface and unity interface.  You can select during login whatever interface you want (gnome 2.32 is always loaded whatever interface you select)

2) The future ubuntu releases will use gnome3.  Again you will be provided a lot of choices on which interface to select.

---

### Post by wildmanne39 on 2011-07-05
> **chillydude said:**
> Thanks for all the replies, I really appreciate it.

I just noticed another thing that bugs me...  Where is my "start menu" application list?  Lol...  

You mention gnome3, but also mention that unity is the future of ubuntu.  I guess I don't understand, is gnome3=unity?    Or is gnome3 going to be an option in future ubuntu like "ubuntu classic" is now?

I really just want it to be like it was in 10.10 :|  that was basically perfect for what I like.

Not really interested in trying out different DWMs either, since I really don't want to have to set up menus and crap every time there's an update. 

At this point in the UI evolution, it's actually easier for me to get stuff done on my freebsd box with cli only.  Seriously, I must be missing something with this UI, it just seems a MAJOR step backwards, like the interfaces in linux were a decade ago.  blah
Hi, in my post# 8 I tell you how to make the launcher hide and stay hidden most of the time, and also I have a menu with all apps on my launcher as stated in post# 8, you can install awn launcher then put a menu on it by places an applet called Yet another menu applet, just look at my screen shots and see if you like it, you can download awn from synaptic.

---

### Post by Alwimo on 2011-07-05
> **chillydude said:**
> You mention gnome3, but also mention that unity is the future of ubuntu. I guess I don't understand, is gnome3=unity? 
It helps to separate thinking about Gnome 3 from Gnome-shell. I'm not an expert but my understanding is that Gnome-shell is something that goes over Gnome 3. Just like Unity is a shell that goes over Gnome 2 and 3. Gnome Shell is the new interface but gnome 3 is what it runs on.
 
Ubuntu 11.10 is going to use Unity as a shell over Gnome 3, just like Fedora 15 (for example) is using Gnome-shell as a shell over Gnome 3.
 
 
Also, I recall reading about an indicator that you can install that emulates that Applications/Places/System menu that goes in the top panel of Unity. I saw it on OMG! Ubuntu! but I didn't find it again in my quick search and never used it.

---

### Post by Krytarik on 2011-07-05
> **Alwimo said:**
> 
Also, I recall reading about an indicator that you can install that emulates that Applications/Places/System menu that goes in the top panel of Unity. I saw it on OMG! Ubuntu! but I didn't find it again in my quick search and never used it.
It's this, ClassicMenu Indicator:
[http://ubuntu4beginners.blogspot.com/2011/06/classic-menu-appindicator-for-unity.html](http://ubuntu4beginners.blogspot.com/2011/06/classic-menu-appindicator-for-unity.html)

Greetings.

---

