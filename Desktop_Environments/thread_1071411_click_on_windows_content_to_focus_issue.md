---
title: "click on windows content to focus issue"
date: 2009-02-16
forum: Desktop Environments
---

### Post by pire1024 on 2009-02-16
Hi,
I'm having a strange issue. 
Sometimes I can't focus on a windows by clicking on its content. But it stills work when I click on the bar. It works with ALT+TAB.
And it works all the time with firefox. 
When I reboot, it works fine for a while, until it stops working.. 

I have found another old unsolved thread mentioning it. But none of the solutions work.
[http://ubuntuforums.org/archive/index.php/t-367468.html](http://ubuntuforums.org/archive/index.php/t-367468.html)

Does anybody have a clue?
Best regards
--Pire

---

### Post by blastus on 2009-02-17
I just recently installed 8.10 and now have this issue. I never had this issue with 8.04. I can only bring a window to focus by clicking on the title bar.

Have you tried just logging out and logging back in again? Don't reboot just log out and log in again. I just did that and it seems to work now...I can focus a window by clicking anywhere inside that window.

---

### Post by pire1024 on 2009-02-18
Yes, logging out and in works for me too. But I lose the feature after some time. I couldn't figure out what causes it. 
It might be firefox.

If anyone figure it out, please let us know!
Best regards
--pire

---

### Post by mohr tutchy on 2009-02-26
I suspect it is a problem with maximized windows related to compiz.
Two days ago I unchecked the "Snapoff maximized windows" box in Move Window plugin and the "Ignore hints when maximized" in General Options and the problem doesn't occurs. I don't know if this is the way to solve just because I didn't found a way to reproduce this bug.
I also opened a bug report in launchpad
[[COLOR="Blue"]https://bugs.launchpad.net/ubuntu/+source/meta-gnome2/+bug/330894[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/meta-gnome2/+bug/330894")
hoping that someone could give us other details.

One love

Sorry for bad english :s

---

### Post by virx on 2009-03-12
I must also say that it is hard find real cause of the problem, since it is hard make the focus issue reappear.

pire1024, interesting theory, but what if I do not use desktop effects and have deleted ~/.compiz directory - the problem still occurred.

---

### Post by cybergalvez on 2009-03-14
I just waned to add a "me too" to this thread.  Basically its happening every day now as soon at eh computer boots I cant get the focus to work.  If I click on a title bar the window is raised, but it does not get the focus.  Restarting compiz does not work.  I have to log off and back on and then it works for a while.

---

### Post by cybergalvez on 2009-03-15
> **mohr tutchy said:**
> I suspect it is a problem with maximized windows related to compiz.
Two days ago I unchecked the "Snapoff maximized windows" box in Move Window plugin and the "Ignore hints when maximized" in General Options and the problem doesn't occurs. I don't know if this is the way to solve just because I didn't found a way to reproduce this bug.
I also opened a bug report in launchpad
[[COLOR="Blue"]https://bugs.launchpad.net/ubuntu/+source/meta-gnome2/+bug/330894[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/meta-gnome2/+bug/330894")
hoping that someone could give us other details.

One love

Sorry for bad english :s

Tried this solution and it didn't work for me, I'm still having the same issue

---

### Post by pire1024 on 2009-03-23
Hey, by the way, which version of ubuntu do you guys work with? I'm using the server version (mainly because I have 8GB of ram on a 32bits machine).

Here are more info on my config.
Ubuntu 8.10. Linux 2.6.27-11-server
Gnome 2.24.1
7,8GB
2 processors: Intel Core2Duo CPU E6750 @ 2.66Ghx


Just a random shot in the air..
It's a bit mysterious that there isn't more people with this issue.

Did somebody notice the loss of focus capacity without having firefox or evolution on?


Cheers
--pire

---

### Post by ingrid_ozikem on 2009-05-05
me too!

sometimes, with a fresh login, it works for a while.. and then the problem appears. often it appears with a fresh login as well. I'm using 8.10.

The problem -- If I have several windows in a deskspace, clicking on an inactive window does NOT change the focus.. merely raises it. Very annoying since then I need to use Alt+Tab to get the focus to the right window..  

On the other hand, if I change workspaces, a maximized window in a new workspace automatically takes the focus..

I do use Firefox and Compiz.. can't do without Compiz but could try not using Firefox for a while.

---

