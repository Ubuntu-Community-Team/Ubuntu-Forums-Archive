---
title: "Progress bar not working"
date: 2006-12-05
forum: Desktop Environments
---

### Post by lwr on 2006-12-05
Since installing 6.10 on my Dell 2500, the progress bar (e.g. at the bottom right on Firefox, although it affects all progress bars in Gnome) doesn't show. I think this is a problem with the orange part, although changing the theme doesn't solve the problem. When there is text in the progress bar, this turns white as things progress. If anyone can help me with this problem, it would be highly appreciated. Thanks.

Luke

---

### Post by uber_n00ber on 2007-03-08
*bump*

I've got a similar problem: Although progress bars show up fine at the start of an operation (eg Add/Remove programs), when progress is made, there is no bar being drawn onscreen. The text for the progress is updated (eg, 1 of 39 updates -> 2 of 39 updates -> 3 of 39 updates -> etc).

However, once the bar reaches where the text is (well, where I imagine it would be if there was one!), the text turns white and hard to read.

Does anyone have any idea on this?

I'm too new to ubuntu/linux to diagnose the problem, but my initial thought was that the computer it's running on is too low spec to handle everything (192MB RAM, onboard video).

---

### Post by uber_n00ber on 2007-03-09
I spotted an answer in this thread that solved this problem for me:
[http://ubuntuforums.org/showthread.php?t=328823&highlight=missing+progress+bar](http://ubuntuforums.org/showthread.php?t=328823&highlight=missing+progress+bar)

That thread also credits the bug listed here:
[https://launchpad.net/ubuntu/+source/xorg/+bug/67443](https://launchpad.net/ubuntu/+source/xorg/+bug/67443)

> To fix it:

1 - Edit /etc/X11/xorg.conf, and change display DefaultDepth from 24 to 16.
2 - Log out.
3 - ctrl-alt-backspace to restart X


Being a damn n00b to linux, the case-sensitivity of the file path threw me for a while (x11 versus X11). So, for other n00bs, I'll elaborate a little bit on that fix:

1. Open a new terminal window (Applications > Accessories > Terminal)
2. Type: sudo gedit /etc/X11/xorg.conf
[sudo gives you root access (write privileges), gedit is the editor you use to open the file at that path.]
3. Under Section "Screen", change DefaultDepth from 24 to 16.
4. Save the file.
5. I rebooted instead of restarting X but it did the trick for me.

I hope that helps other people!

---

### Post by vodalus on 2007-05-04
I have this problem as well and noticed that the bug report does not have any replies since April 20th (or so).  Is this a common problem.  In any case I do not want to reduce the color depth to 16 since this will degrade graphics.  But the other suggestion of swithching the theme engine to Clearlooks does work.

I am amazed that such a basic and long standing bug has not been fixed yet.

---

### Post by crazylocha on 2007-05-12
*bump - trip - splat *

Dusts self off , looks to make sure no one saw, ok!

As a fellow nOOb, I do appreciate the job you did with the explanation, right to the point.
Had a look at that bug thread, and didn't like the other more advanced option of messing with the 'gtkrc engines". Didn't seem to fix one problem and cause more??!!??

Tried your method (ctrl-alt-backspace to reboot the X) and tested after logging back in desktop.
Success!! Since this is an older motherboard with built in i810 graphics, I've used the 16bit depth anyway. DSL its almost mandatory to get any desktop icons.

Keep up the useful information with the steps, many experienced users forget those little things for those of us just coming up to speed. Hopefully I can return the favor to you and others such as ourselves.

Definitely loving the overall Ubuntu experience and highly recommend it to others as often as I can.

Thanks again to all!!

---

