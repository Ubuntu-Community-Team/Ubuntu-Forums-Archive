---
title: "&quot;decoupling&quot; my two monitors? 1 virtual desktop &lt;-&gt; 1 screen"
date: 2010-01-06
forum: Desktop Environments
---

### Post by laramichaels1978 on 2010-01-06
Hi everyone,

I am a VERY happy user of ubuntu; thank you to all those involved! : )

I am using Ubuntu 9.10. Earlier this week I got myself an external screen. Configuration was a breeze using Preferences->Display and I now have two screens showing different parts of a large virtual desktop (the virtual desktop has the combined width of both screens).

My question (which I will try hard to make clear; sorry if I fail!) is:

As I mentioned, currently my two (physical) screens are always showing the left and right parts of a single very wide virtual desktop. I can then switch (Alt+{1,2,3,4}) to different virtual desktops. When I switch to a different virtual desktop, the contents of *both* screens are always changed (which makes sense, since the virtual screen spans both physical screens).

Is there a way for me to go back to having an array of normal/"single-screen sized" virtual desktops and just picking

- "show virtual desktop 1 on my left-hand-side screen and show virtual desktop 3 on my right-hand-side screen" 

only, a few minutes later, when I need to continue one of those virtual desktops in sight but need to bring something else into view, say

- "now show virtual desktop 4 on my left-hand-side screen, leaving the right-hand-side screen as it is [showing desktop 3, as per the previous example]"

Did this make any sense? : ) Is there any hope of getting things to work this way?

Basically, I would like to be able to control what goes onto each screen *individually*, rather than assigning a single virtual desktop to *BOTH* screens at the same time. Currently, my screens act just like if they were a giant one. I would like to retain control over them individually, and be able to  load a specific virtual desktop onto a specific screen -- while leaving the other physical screen as it is.

Thank you for any help; this must be one of the weirdest questions ever asked! : )

-lara

---

### Post by Vand3lay on 2010-11-15
I've been searching for the exact same thing for some time now and this post is all I could find. I actually started looking at compiz since I originally wanted each monitor to have it's own side of the desktop cube instead of sharing the same side of a bigger desktop cube. I then realized it probably has nothing to do with compiz and has to do with gnome and still couldn't find anything. I even tried looking to see if kde had this ability and was unsuccessful. I'd rather stick with gnome but if someone knows how to do this or at least point me in the right direction where to look I may be able to make a patch for this. If it does require someone to make this, don't expect a solution from me for at least a year since I only started and don't know much yet.

---

### Post by Vand3lay on 2010-11-19
I just found this;

[http://forum.kde.org/brainstorm.php#idea39358_page1](http://forum.kde.org/brainstorm.php#idea39358_page1)

I don't have much time to look at this now but this appears to be the solution

[http://xmonad.org/](http://xmonad.org/)

Hopefully when Ubuntu makes the switch to wayland, it will already have this feature built in.

[http://www.omgubuntu.co.uk/2010/11/unity-to-embrace-wayland-display-server/](http://www.omgubuntu.co.uk/2010/11/unity-to-embrace-wayland-display-server/)

---

