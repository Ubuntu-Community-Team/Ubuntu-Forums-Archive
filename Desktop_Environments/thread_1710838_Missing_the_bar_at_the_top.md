---
title: "Missing the bar at the top"
date: 2011-03-20
forum: Desktop Environments
---

### Post by jony121 on 2011-03-20
I made the mistake of installing e16 window manager from the synaptic. I logged out and logged into e16 for a session. I logged out and logged back into gnome but it seemed gnome and e16 were both running at the same time. I couldn't figure out what had gone wrong so I killed X and ran 
"sudo apt-get remove e16" when I logged back in all the windows had no bar at the top.

Screenshot:
[http://img715.imageshack.us/i/screenshotqj.png/](http://img715.imageshack.us/i/screenshotqj.png/)

It says ylmf os but it's just ubuntu 10.4 with a theme installed by default. I tried restarting the computer but it makes no difference.

---

### Post by jony121 on 2011-03-20
Some good new. I was able to create a new user. The new user does not have the problem. Which means it's the gnome settings for my user. I am going to try and find which files I have to delete to get things back to normal.

---

### Post by jony121 on 2011-03-20
It's ok now. YAY. Solved it. Deleted ~/.gconf & ~/.gconfd & ~/.gnome & ~/.gnome2
Hope this helps someone in the future. Also I still don't know what to call that bar.

---

### Post by GTRees on 2011-08-29
HAHA Thankyou so much!
I had the exact same problem, but it's fixed now.
:D
Thanks again

---

