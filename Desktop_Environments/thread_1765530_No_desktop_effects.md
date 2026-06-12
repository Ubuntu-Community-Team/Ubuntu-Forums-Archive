---
title: "No desktop effects"
date: 2011-05-23
forum: Desktop Environments
---

### Post by deshmukh on 2011-05-23
I have Kubuntu 11.04 running KDE 4.6.2.

I am trying to use GNOME (NOT UNITY) as an alternative to KDE. I installed the 'GNOME 1:2.30+7ubuntu3' (The GNOME Desktop Environment, with extra components) package from the repositories.

Installation went well and now in KDM, I do get multiple options including Ubuntu, Ubuntu Classic, etc

When I log in to Ubuntu Classic, I do not get desktop effects - I am especially interested in Scale Plugin.

I have installed Compiz and CCSM. I have changed values of keys containing words 'windowmanager' and 'window_manager' in gconf-editor to compiz but no result.

Thanks for your help in advance.

---

### Post by 3Miro on 2011-05-23
What do you get if in Ubuntu Classic you try:

```
compiz --replace
```

---

### Post by deshmukh on 2011-05-23
> **3Miro said:**
> What do you get if in Ubuntu Classic you try:

```
compiz --replace
```

Thanks for a quick reply.

It works! I have only tried the Scale plugin. But if it works, I am sure, others will.

Now, how do I ensure that compiz --replace is executed everytime I log into Ubuntu Classic?

Also, is there any other more elegant way of achieving the same thing - say, through gconf-edit?

---

### Post by 3Miro on 2011-05-23
In System -> Prefs -> Startup Applications, you can add "compiz --replace". This isn't very elegant, but it should work.

In "gconf-editor" you can also try to edit Desktop -> Gnome -> Session -> Required Components and put the window manager as "compiz" (without --replace).

You can also manually start "compiz --replace" with Alt+F2 so you don't have to keep a terminal window open.

---

### Post by deshmukh on 2011-05-23
> **3Miro said:**
> In System -> Prefs -> Startup Applications, you can add "compiz --replace". This isn't very elegant, but it should work.

Did that. Works perfectly. Thanks.

> **3Miro said:**
> In "gconf-editor" you can also try to edit Desktop -> Gnome -> Session -> Required Components and put the window manager as "compiz" (without --replace).

Tried this. Does not work. So, reverted the entry back to gnome-wm.

> **3Miro said:**
> You can also manually start "compiz --replace" with Alt+F2 so you don't have to keep a terminal window open.

Yes - that is how I had done that earlier.

Marking this thread as solved.

---

