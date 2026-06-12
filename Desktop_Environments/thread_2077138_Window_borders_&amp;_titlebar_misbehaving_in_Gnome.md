---
title: "Window borders &amp; titlebar misbehaving in Gnome 3.6"
date: 2012-10-27
forum: Desktop Environments
---

### Post by fullerenedream on 2012-10-27
When I try to change my GTK theme to a non-default theme using Gnome Tweak Tool, the window borders and titlebar (metacity stuff basically - is it still called metacity?) don't change to the new theme. I get something weird and ugly instead. Even if I do that business where you type 'alt-f' to get the command line and type 'r' to reload. Even if I power cycle, in fact, it still doesn't change to the proper metacity stuff.

Here is a screenshot. Gnome Tweak Tool is set to Delorean Dark, but the metacity stuff is all messed up.
[http://i.imgur.com/1DOo8.png](http://i.imgur.com/1DOo8.png)

What am I doing wrong? I have a fresh install of Ubuntu 12.10. I installed Gnome Shell and Gnome Tweak Tool. Maybe there is some other little thing I need to install to get this to work right?

Also, here is what may be a stupid question: why does Gnome Tweak Tool have a dropdown menu labelled "Current Theme"? This one appears to select metacity stuff. Why isn't it called "Window Borders" or something like that? Or am I completely confused?

---

### Post by aias on 2012-10-28
hey,
I feel your pain.  So the solution is really simple.  move the theme that you want out of your .themes folder and into /usr/share/themes.  then select it again through gnome tweak tool and it will work fine.  See this posting:
[http://www.fandigital.com/2012/10/use-custom-theme-in-gnome-shell-36.html](http://www.fandigital.com/2012/10/use-custom-theme-in-gnome-shell-36.html)

Thank you fandigital!

---

### Post by fullerenedream on 2012-10-28
Yay awesome! Thank you! It is more of a pain in the butt this way, but it works!

---

### Post by keelzebub on 2012-11-07
I'm just making a note of this in case someone else has this problem:
If the above method didn't quite work for you, make sure all the files under /usr/share/themes are readable and executable by everyone.
```
sudo chmod +rx /usr/share/themes/*
```

---

