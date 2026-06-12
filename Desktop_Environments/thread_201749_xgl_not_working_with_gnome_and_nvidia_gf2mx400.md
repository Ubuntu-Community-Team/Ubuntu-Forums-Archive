---
title: "xgl not working with gnome and nvidia gf2mx400"
date: 2006-06-22
forum: Desktop Environments
---

### Post by mc_bizon on 2006-06-22
I installed Xgl and compiz following <a href="https://help.ubuntu.com/community/CompositeManager/Xgl">this howto</a>.
With Xgl i chose "Method A: Xgl session" - I can choose xgl session from the login screen. I added gnome-window-decorator and compiz --replace gconf to startup programs in gnome.

But when I log in to xgl session I can see no difference. 

When I try to start compiz from terminal it gives me this output:
```
oliver@ubuntu:~$ gnome-window-decorator
gnome-window-decorator: Another window decorator is already running
oliver@ubuntu:~$ compiz --replace gconf decoration wobbly fade minimize cube rotate zoom scale move resize place switcher water
compiz.real: No composite extension
oliver@ubuntu:~$

```

[here is my xorg.conf]("http://www.sgymlc.sk/~pha/xorg.conf")

what should i do to make it work?

---

### Post by bitwise on 2006-06-27
I am having the same issue. Anyone?

Also, can someone explain how to tell what session you are in after logging in? ie, Xgl or Gnome...

Thanks

---

### Post by poper on 2006-06-28
same here

---

### Post by bitwise on 2006-06-28
Ok, I got it working. I scrapped the help.ubuntu.com guide and went with this one:

[http://www.ubuntuforums.org/showthread.php?t=131267](http://www.ubuntuforums.org/showthread.php?t=131267)

You can still use the ubuntu.com one for setting up packages, but as far as getting Xgl running properly, the /etc/gdm/gdm.conf-custom method seems to have better results. You shouldn't need the Composite option in /etc/X11/xorg.conf either.

Also, go with this method for configuring compiz after you get it installed:

[http://www.ubuntuforums.org/showpost.php?p=760273&postcount=507](http://www.ubuntuforums.org/showpost.php?p=760273&postcount=507)

With one exception:

Instead of adding **compiz gconf** to the Session Startup Programs, add: **compiz --replace gconf**

If neccessary, I can write up the steps, of the two tutorials combined. It does seem to work, and its quite snappy with the Geforce2 MX 400. However, I did experience a lockup when I left the machine on overnight. I believe its from the screensaver, and I am trying to track that issue down now.

Good luck

---

### Post by poper on 2006-06-28
Thanks a lot bitwise. It finally works. It's great :)

---

### Post by bitwise on 2006-06-28
ah cool good to hear -- can you post back if you experience screensaver/opengl lockups? hopefully someone can chime in on how to address those issues.

---

### Post by poper on 2006-06-28
No lockups until now, but after loging in, the window where the "processes" (I don't know the proper word, see the screenshot) load, doesn't disappear as usual. It stays *frozen* in the middle of the screen for a while. After spinning the cube several times, It disappears.

[[IMG]http://img121.imageshack.us/img121/1949/pantallazo26tj.th.png[/IMG]](http://img121.imageshack.us/my.php?image=pantallazo26tj.png)

---

### Post by bitwise on 2006-06-28
noticing some more screensaver weirdness -- the screensaver that comes on isnt the same screensaver that i set my gnome-screensaver preference to.

also when the incorrect screensaver does come on, i notice its heavily choppy. and i am getting decent framerates in glxgears. one thing im not sure about, glxgears -printfps no longer works, but running glxgears on its own does now print out fps to the console. is that something that happened when i switched to xgl/compiz?

---

### Post by bitwise on 2006-06-29
[QUOTE=poper]No lockups until now, but after loging in, the window where the "processes" (I don't know the proper word, see the screenshot) load, doesn't disappear as usual. It stays *frozen* in the middle of the screen for a while. After spinning the cube several times, It disappears.

[[IMG]http://img121.imageshack.us/img121/1949/pantallazo26tj.th.png[/IMG]](http://img121.imageshack.us/my.php?image=pantallazo26tj.png)[/QUOTE]
[http://www.ubuntuforums.org/archive/index.php/t-186976.html](http://www.ubuntuforums.org/archive/index.php/t-186976.html)

---

