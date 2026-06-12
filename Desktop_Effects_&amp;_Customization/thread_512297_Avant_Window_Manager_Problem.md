---
title: "Avant Window Manager Problem"
date: 2007-07-29
forum: Desktop Effects &amp; Customization
---

### Post by Supremacy on 2007-07-29
Hi all,

First of all, I have searched for my prob but no luck.

I have Avant Window manager installed. Its running like a charm, except for one thing. I have this white tall line on the right hand side. Here's an image of what I mean:
[[IMG]http://img341.imageshack.us/img341/3779/avantproblemru5.th.png[/IMG]](http://img341.imageshack.us/my.php?image=avantproblemru5.png)


I have reinstalled and even upgraded to the latest SVN version and its still there. My gfx card drivers are up to date (100.14.11)

I have no clue as to what is wrong. Compiz Fusion is running fine too.

Any help is appreciated.

Regards,
Supremacy

---

### Post by PaulFXH on 2007-07-29
I have that line too on one computer but I don't have a solution.
On another where I have not invoked the "angled" dock, it doesn't show up.
Actually you might be better off to post direct to the AWN forum [here]("http://www.planetblur.org/hosted/awnforum/index.php"). If there is a solution, for sure they will help you there.

---

### Post by andrewsomething on 2007-07-29
Have you added any applets?

---

### Post by syko21 on 2007-07-29
all applets other than the Launcher/Taskmanager cause this white line to appear. I think its because the other applets don't function properly. Simply right click your dock, configure applets, and remove all except the Launcher/Taskmanager applet.

---

### Post by andrewsomething on 2007-07-29
> **syko21 said:**
> all applets other than the Launcher/Taskmanager cause this white line to appear. I think its because the other applets don't function properly. Simply right click your dock, configure applets, and remove all except the Launcher/Taskmanager applet.

The applet problem should be gone very soon. It has to do with a change made in the new svn to the applet system which doesn't have backward compatibility. It's a know issue which hopefully will be cleared up.

---

### Post by Supremacy on 2007-07-29
Thanks guys. I'll try remove all those next time I load Ubuntu.

Regards,
Supremacy

---

### Post by hyperair on 2007-07-29
Right click on the dock and go to configure applets. I reckon if you remove all except the task manager applet you won't have that problem. I used to have that problem with the trashcan, but eventually it went away. Then it happened for the workspace switcher, but that went away too. Currently the only one that'll give that problem is the systray applet I reckon.

For the ones that produce the white line bug, the applet itself doesn't appear. Only the white line appears. For those without the white line, the applet works fine.

---

### Post by Supremacy on 2007-07-29
yep, that did the trick. Thanks guys. :KS:D

Regards,
Supremacy

---

### Post by andrewsomething on 2007-07-30
> **andrewsomething said:**
> The applet problem should be gone very soon. It has to do with a change made in the new svn to the applet system which doesn't have backward compatibility. It's a know issue which hopefully will be cleared up.

This issue has been fixed as of svn243. I'm not sure if it hit the repo yet, but if not it will soon. The Gnome-Main-Menu/Affinity applets have also been committed so on more patching for those either.

---

### Post by weezalxc on 2007-12-17
I had the same problem too - but then I removed Clock/Calendar Applet and the white line went away.  Thanks for the help! :)

---

### Post by tuxalot on 2008-02-22
Seems as though the trash applet is causing me the same problem.  All fixed now!  Thanks to you all.

---

