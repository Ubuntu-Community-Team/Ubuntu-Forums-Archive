---
title: "Can't change Controls in Gnome themes"
date: 2006-02-11
forum: Desktop Environments
---

### Post by gmleuty on 2006-02-11
Something odd is happening with my themes under Gnome. "Window Border" and "Icons" change properly, but "Controls" does not. The only choices that work are "Human" and "Clearlooks".

I have tried running
sudo dpkg-reconfigure gnome-themes
and
sudo dpkg-reconfigure gconf2
but this has not helped.

I'd be grateful for any hints or suggestions.

Mike

---

### Post by Jiawen on 2006-11-15
I can't imagine that you're still looking for the solution, but I had a similar (the same?) [problem]("http://ubuntuforums.org/showthread.php?p=1760971#post1760971") and solved it... Install gtk2-engines-pixbuf and everything should work fine.

---

### Post by AnRkey on 2007-10-16
Same problem as above. I have gtk2-engines-pixbuf installed already.

Attached to this post is a screeny of my problem (Window border and controls should be blubuntu)

I have tried remove compiz* and gnome-themes as well as purging these packages. I have also tried all the steps in the posts above.

Any help would be cool.

---

