---
title: "terminal server client window resizing?"
date: 2007-09-29
forum: Desktop Environments
---

### Post by marquee moon on 2007-09-29
Using feisty fawn, when I connect to a terminal using Terminal server client, I cannot re-size the window. Its either minimised or maximised, and the maximised screen is quite small (especially on a laptop)
Is there a way of making the maximised window size the normal full screen size? 

Thanks, 

MM

---

### Post by Wicca on 2007-09-29
Hi,

It's normal behavior that you cannot resize a terminal session window. You can however control the maximized screen size this way:

(I am not using the english version so I have to translate, it might be stated a little differently on your side)
In Terminal Server Client got to tab Screen --> Size of the remote desktop --> select 'Use this size' and pick the highest resolution possible on your screen.

---

### Post by FromFPan2Fire on 2007-11-30
Same issue I've been dealing with on a Gazelle 2000 laptop for several months.  Have not found a solution.  Previous poster's suggestion had, in fact, no effect.  (The other option, for full screen, generates an error message.)

Anyway, here is my post - though I'm mearly restating the problem:

The problem is that when I connect from Ubuntu "Terminal Server Client" (TSC) to a remote machine, The TSC client window cannot be made bigger.  While in other applications, I can drag the sides, top and bottom of the windows to enlarge them, with the TSC window I get the same handles, but when I try to click-and-drag the window to make it larger the window refuses to expand beyond a certain point.  (I can drag the edges to make it smaller.)    On my machine, a quick check seems to show that it is only the TSC window that has this limitation.  [ Options to run TSC "full screen" give an error message. ]

Can anyone suggest a solution using one of these approaches:

(1) Fix it so that the TSC window can be "dragged" and made bigger.

or

(2) Suggest some other client software.  (Note that the other (server) machine is Windows 2000 Pro running VNC Server 4.1.2.  Since it is 2000 Pro options using Terminal Services on the "server" machine are not workable, as 2000 Pro won't run Terminal Services. )

---

