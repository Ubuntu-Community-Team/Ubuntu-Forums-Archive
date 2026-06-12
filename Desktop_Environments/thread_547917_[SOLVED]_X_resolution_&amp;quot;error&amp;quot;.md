---
title: "[SOLVED] X resolution &amp;quot;error&amp;quot;"
date: 2007-09-10
forum: Desktop Environments
---

### Post by wakeboarder3780 on 2007-09-10
I have an interesting problem that I am unsure how to solve.  I have been tinkering with wine recently and I finally figured out how to get wine to recognize a 1280x1024 resolution in CS:S (it powers down my second monitor which I am unhappy about as in windows I can keep my second one lit displaying gpu temps etc, but thats a diff issue.).

After making this change (adding the resolution: CRT-0: 1280x1024_75 +0+0; to my metamodes section of my xorg.conf file), now as soon as I login (the login page still utilizes both my screens) it drops the left screen and assumes it is using the above metamode.

When I login as a different user it behaves normally leaving both screens up.

I am unsure what I really changed or why X is thinking my default metamode should be CRT-0: 1280x1024_75 +0+0;

My xorg.conf metamode section is as follows:

```
Option         "metamodes" "CRT-0: 1280x1024_75 +0+0, CRT-1: 1280x1024_75 +1280+0; CRT-0: 1280x1024_75 +0+0; CRT-0: 1152x864 +0+0; CRT-0: 1024x768 +0+0; CRT-0: 832x624 +0+0; CRT-0: 800x600 +0+0; CRT-0: 640x480 +0+0"
```

I have a current workaround of using xrandr to choose the proper metamode once logging in but lets get real, this is linux, we have software do things for us!  If anyone could inform me of my error I would love to know.

---

### Post by wakeboarder3780 on 2007-09-11
The more I think about it, the more I think its probably some part of gnome.  Because when X initially loads, it has the proper resolution selected.  It's only after I login and the window manager starts to load that the resolution changes.  Does anyone have any ideas?

---

### Post by wakeboarder3780 on 2007-09-11
I spoke to a friend who knows a lot about ubuntu.  Although I don't know the location of the file to edit, here is a way to fix the problem if anyone else encounters this.

From a terminal, run command:
$ gconf-editor

This should open a GUI representation not too much unlike regedit for windows.  The path of the  value you want to edit is as follows:
desktop/gnome/screen/default/0

At least it was 0 in my case.  By clicking on the directory 0 you can see it's key / value pairs in the  pane adjacent to it.  Change the "resolution" key / value pair and change the value to whatever resolution it should be.

When you are done chose file, quit and you should be able to login as your user and the resolution will be what it is supposed to be.  I have no idea why this value is changed if you add a metamode manually to your xorg.conf file, but if anyone else encounters this problem hopefully you find this page.

Cheers.

---

