---
title: "Whisker menu button very slow to appear after login"
date: 2014-05-05
forum: Desktop Environments
---

### Post by The Cog on 2014-05-05
I have a strange issue with whisper menu (Xubuntu 14.04, 64bit). I like to set a custom icon for it (a penguin) instead of the default rat. As soon as I do this, I find that the menu button take a long time to appear on the panel after I log in - several minutes. If I add a second whisper menu to the panel, this one appears immediately until I change the icon.
Has anyone else seen this? Found a solution, even?

---

### Post by brainwash on 2014-05-05
I suggest that you add your findings to the upstream report.

[https://github.com/gottcode/xfce4-whiskermenu-plugin/issues/86](https://github.com/gottcode/xfce4-whiskermenu-plugin/issues/86)

---

### Post by The Cog on 2014-05-05
Thanks for the link brainwash, but that's not quite the same thing. My issue is that the menu button does not appear on the panel, not that the menu is slow to draw after I click the button. 
Here is my panel when I first log in. The menu button on the right has the default image and always appears instantly:
[ATTACH=CONFIG]252876[/ATTACH]
A couple of minutes later, the one on the left with a custom icon appears:
[ATTACH=CONFIG]252877[/ATTACH]
I've tried both gif and png images.

I'll wait for a while before logging a bug, and see if anyone here already knows about it.

---

### Post by Elfy on 2014-05-05
I've just tried with a couple of stock icons - no issue with those, is this icon you're using a real custom one - eg something you've knocked up or got elsewhere? If so link it here and I'll try with that.

---

### Post by The Cog on 2014-05-05
These are they. I copied them from the web somewhere a long time ago.

[https://drive.google.com/file/d/0B0gAvr5jz1N9NWd2VEZHMGVIWGc/edit?usp=sharing](https://drive.google.com/file/d/0B0gAvr5jz1N9NWd2VEZHMGVIWGc/edit?usp=sharing)
[https://drive.google.com/file/d/0B0gAvr5jz1N9ZjJEZzdtYzkxalE/edit?usp=sharing](https://drive.google.com/file/d/0B0gAvr5jz1N9ZjJEZzdtYzkxalE/edit?usp=sharing)

It occurs to me, maybe it's to do with the size. I hadn't realised they were that big until I went to post them, although they always worked OK with the previous Xubuntu menu/panel. 
I just tried shrinking one to 64px and logged out/in a couple of times and that seems not to be a problem. Will reboot a few times to double-check.

Edit:
Having rebooted a couple of times, it seems that the problem was indeed the size of the images (249x249) that caused the delay. Shrinking it to 64px seems to have fixed it.
I'll mark the thread as solved. Sorry to waste your time Elfy - I was convinced the images were quite small anyway.

---

### Post by Elfy on 2014-05-05
worked fine for me with the first one

---

### Post by The Cog on 2014-05-05
That's odd. Always troublesome for me. Oh well. One of life's little mysteries to file away.

---

