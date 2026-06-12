---
title: "Ubuntu 11.04 - Unity is a Disaster - Help"
date: 2011-05-17
forum: Desktop Environments
---

### Post by barlaventoexpert on 2011-05-17
The hours of productivity I am loosing trying to work with Unity is ridiculous. (And I have a business to run!)

I am very close to formatting the machine and building my own distro based on debian!

Can anyone help me this problem?

When I open a terminal window or when the download window in Firefox opens, they both lock to the top left hand corner of the screen! 

I have tried to click the X on the top left hand window bar to no avail.

I have wandered around the Compiz window manager but cannot see how to rectify this problem.

Any ideas?

Canonical, Get your act together! Ubuntu 11.04 is close to becoming the Windows ME of the Ubuntu world! 

Happy 100% Ubuntu user since 2004
UnHappy 100% Ubuntu user 2011!

---

### Post by teachop on 2011-05-17
> **barlaventoexpert said:**
> The hours of productivity I am loosing trying to work with Unity is ridiculous. (And I have a business to run!)

I am very close to formatting the machine and building my own distro based on debian!

Can anyone help me this problem?

When I open a terminal window or when the download window in Firefox opens, they both lock to the top left hand corner of the screen! 

I have tried to click the X on the top left hand window bar to no avail.

I have wandered around the Compiz window manager but cannot see how to rectify this problem.

Any ideas?

Canonical, Get your act together! Ubuntu 11.04 is close to becoming the Windows ME of the Ubuntu world! 

Happy 100% Ubuntu user since 2004
UnHappy 100% Ubuntu user 2011!
If you don't like Unity, at the login screen, click your name, then go to the bottom and find the session menu, and select "Ubuntu Classic", and finish logging in.  You can switch back and forth at will.

I don't understand the problem you have, try to click the window restore button in the menu if they are full screen.

---

### Post by wildmanne39 on 2011-05-17
> **barlaventoexpert said:**
> The hours of productivity I am loosing trying to work with Unity is ridiculous. (And I have a business to run!)

I am very close to formatting the machine and building my own distro based on debian!

Can anyone help me this problem?

When I open a terminal window or when the download window in Firefox opens, they both lock to the top left hand corner of the screen! 

I have tried to click the X on the top left hand window bar to no avail.

I have wandered around the Compiz window manager but cannot see how to rectify this problem.

Any ideas?

Canonical, Get your act together! Ubuntu 11.04 is close to becoming the Windows ME of the Ubuntu world! 

Happy 100% Ubuntu user since 2004
UnHappy 100% Ubuntu user 2011!

Hi, it sounds like you deactivate unity plug in when messing with compiz. If so  just open a terminal by hitting alt+f2 or ctrl +alt+t and type unity --reset  and let it run for about three minutes, do not worry about the errors it will list, then hit ctrl+alt+del to restart the computer and everything should be fine.

---

### Post by donniesito on 2011-05-17
> When I open a terminal window or when the download window in Firefox opens, they both lock to the top left hand corner of the screen

I had that same exact thing happen, even when running in "Classic Ubuntu" mode. I fixed it by going into CompizConfig Settings Manager, under "Window Management" make sure there's a check by "Move Window".

Worked for me, hope this helps :)

Also, since I run "Classic Ubuntu" instead of "Unity,"  I have the Unity Plugin disabled in CompizConfig Settings Manager.

---

