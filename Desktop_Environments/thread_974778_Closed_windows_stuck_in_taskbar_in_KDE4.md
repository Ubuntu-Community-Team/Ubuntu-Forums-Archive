---
title: "Closed windows stuck in taskbar in KDE4"
date: 2008-11-07
forum: Desktop Environments
---

### Post by GameKyuubi on 2008-11-07
Hi everyone. I'm pretty new to Kubanto and need help figuring out a problem here. Sometimes when I close a window, the window will close but the icon on the taskbar stays there. The window is totally gone, it isn't on any of the desktops, hiding behind something, or minimized, but the taskbar still has an entry for the window that was open. I can click it but nothing happens. Right click -> close doesn't work either. The only way to get rid of them is to log out and then log in again. Anybody know what's going on?

I'm running:
Kubuntu 8.10
KDE 4.1.3
CompizFusion
NVIDIA 177.80 drivers

---

### Post by grotto on 2008-11-08
I have the same problem. Switching to another workspace clears it. As long as the task bar settings are set to only show tasks from the current desktop. I suppose it is an issue with that particular plasmoid.

---

### Post by tombh on 2009-01-19
I seemed to have solved this problem by going to the General Options in CompizConfig Settings Manager, then to the Desktop Size tab and making sure the Horizontal Virtual Size was set to 4 (for cube type goodness) and the Number of Desktops was set to 0. By default that latter value was set to 4 and that's what seemed to cause window tabs to get unclosably stuck on the taskbar.

Hope that helps. 

BTW this was in Debian Lenny, KDE 4.1.3 and Shame's September 2008 GIT Compiz packages.

tom :)

---

### Post by Ymer on 2009-11-24
So I have the same problem. Is this problem only specific to a few people or it's wide spread? And is there any solution of course?

---

### Post by Silver Knight on 2010-01-17
I also have experienced this oddity (but only in the past few days) and thus far has happened with two different applications getting stuck this way on two different days.  First was Konqueror a few days ago (in web browser mode), and then today was VYM (a QT4 based mindmapping application).  Like the original poster, the only way I can find to clear these stuck items from the task bar is to log out of KDE entirely.

I hereby retract the last half of the last sentence in the above paragraph.  On page three of the thread **"**[**Getting a Windows 7-like taskbar in Ubuntu**]("http://ubuntuforums.org/showthread.php?p=7464108#post7464108")**"**  the user [carlee]("http://ubuntuforums.org/member.php?u=717412") suggests Stasks as a solution to that question.  Oddly enough, it's also a solution to **this** issue as well.  Simply replace the original taskbar with Stasks and configure it to look like you want and strangely this issue magically vanishes.  :)

---

### Post by Farmer of Bricks on 2010-01-17
> **grotto said:**
> Switching to another workspace clears it.
It sounds like this is more of a graphics-card-not-redrawing-the-taskbar-fast-enough problem than it is a taskbar-not-working-right one. Don't worry, and be happy in the knowledge that your graphics card is too slow to render all your eyecandy *and* and your taskbar.

---

