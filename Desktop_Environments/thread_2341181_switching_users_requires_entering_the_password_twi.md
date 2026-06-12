---
title: "switching users requires entering the password twice"
date: 2016-10-25
forum: Desktop Environments
---

### Post by tuuk on 2016-10-25
I have recently upgraded to Ubuntu 16.10. Before the upgrade, my 16.04 was a bit unstable. It seems quite stable after the upgrade. 

One issue I am having is that when I switch from one user to another in Unity, I need to enter my password twice. Here is how it goes. When I choose a different user to switch to from the list on the upper right corner, first I am given the purple login screen and I enter the password for the other user (say, who is already logged in). Then, after a short wait, I get the password prompt that you get when you lock the screen (with the chosen wallpaper in the background). Only when I enter the password for a second time there, I am logged in. And, I have my settings such that the screen is not locked even after a long period of inactivity.

Is anyone else experiencing this problem? Does anyone have a solution?

Thanks.
tuuk

---

### Post by TheFu on 2016-10-26
Don't know if this is helpful, but ... 

I don't switch desktops just to access other user accounts.  I'll open a new terminal and **su - {USERID}** then do what I need there.  That is the old-school Unix way.  For remote systems, using **ssh** can accomplish the same thing.

Might not work how you need it. I dunno.

---

### Post by tuuk on 2016-10-26
Thanks, TheFu. Other user account is for my wife, so actual desktop switching is needed for the graphical applications as we share the machine.

---

### Post by TheFu on 2016-10-27
> **tuuk said:**
> Thanks, TheFu. Other user account is for my wife, so actual desktop switching is needed for the graphical applications as we share the machine.

Suspected it was something like that - does logging out and back in under the other account not work? A little inconvenient since the other account's desktop is lost. There are methods to avoid that, but it would be running a remote desktop on the same machine. Probably not really a better answer, but the desktop wouldn't be lost.

---

### Post by tuuk on 2016-10-27
The point is that, when we both use the machine simultaneously, we want to be able to switch back and forth without losing the current state of our desktops. It is just a nuisance to have to enter the password twice for these switches and I expect that this is not intentional, but a bug or a matter of a setting somewhere.

---

### Post by TheFu on 2016-10-27
> **tuuk said:**
> The point is that, when we both use the machine simultaneously, we want to be able to switch back and forth without losing the current state of our desktops. It is just a nuisance to have to enter the password twice for these switches and I expect that this is not intentional, but a bug or a matter of a setting somewhere.

Yep.  Getting things just how you like them is nice.  I wrote a script to do that, but it is very specific to my machine(s) and needs.  

Have you opened a bug report?  [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs) sounds like a bug to me.
BTW, folks here aren't employees of Canonical.

As a last effort, does changing the DE make a difference?  Try Mate instead of Unity or KDE or ... Are both userids using the same DE?

---

### Post by tuuk on 2016-10-27
I didn't try different DEs; we both use Unity. I'd rather not install a new DE for testing, especially since we probably will not switch to it just for this reason.

Thanks for the idea of reporting a bug. I might try that.

---

