---
title: "Problems with Eclipse GUI"
date: 2014-12-12
forum: Desktop Environments
---

### Post by tigerjack89 on 2014-12-12
I know the title sounds very general. Problem is that sometimes, without any evident pattern, Eclipse fails to render some stuff. I can't give much more information because the problem is difficult to reproduce, even if it appears often, and also even difficult to screenshot.For example, when I maximize (or minimize) any view, it displays only the GUI elements of the old view and not them of the new one.
A simple typical scenario could be when I have an editor opened, I open a new editor and Eclipse display the text of the old editor instead of that of the new one; basically, it fails to display the updated gui.
This is a brief video explaining this scenario. Actually, when in the video I pause over a page editor, I double click on it (it isn't shown in the video, the screen recorder sucks), but as you can see nothing changes. In the end of the video, I drag the mouse as if I am selecting some text (again, the screen recorder doesn't show muose clicks) and the gui is updated
[http://youtu.be/RFRotBqY9Fc](http://youtu.be/RFRotBqY9Fc)


Here is also a more recent image of a broken gui
[IMG]http://i59.tinypic.com/2ls9xe1.png[/IMG]
As you can see, there are a lot of cursors in various parts:  in package explorer, under "exit"; in "LoginView.java" in many points. Basically, I've only double clicked "LoginView.java" to show it in full screen.


Also, today I identified a specific sequence of events that always broke the GUIs, even if it is only a small part. When I am on a WindowsBuilder>Design view and I select refresh, this is the frame which contains the progress bar. As you can see, some elements were missing.


[img]http://i59.tinypic.com/11iliiw.png[/img]

---

### Post by thorstenr_42 on 2014-12-14
Hey,
Unfortunately I have no solution but also some problems with eclipse and Ubuntu 14.04: 
I am using the newest eclipse ide and 4 virtual desktops. When I try to maximize the window, it sometimes is maximized to another virtual desktop above or below the current desktop or even completely disappears. If the window is disappeared I can just bring it back with alt+right or alt+left.
However the window seems to collapse to a tiny line (see pic)
[IMG]http://i58.tinypic.com/14sl7br.png[/IMG]
I would be very grateful, if someone could tell me what can cause such an behaviour.

---

