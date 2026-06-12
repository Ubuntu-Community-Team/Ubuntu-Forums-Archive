---
title: "After Partial Upgrade, Empathy isn't in Indicator Applet"
date: 2010-04-27
forum: Desktop Environments
---

### Post by sonicroxs on 2010-04-27
Hey,
I accidentally installed a partial upgrade, and Empathy was removed from the indicator applet (next to Evolution Mail under the envelope icon). How can I restore it?

PS: When this happened, I had no idea that partial upgrades could cause problems in our PCs, such as removing packages..

---

### Post by mörgæs on 2010-04-28
If it is not urgent, you could simply wait a few days and see if a  complete update fixes the problem.

---

### Post by sonicroxs on 2010-04-28
Well, yeah... I didn't remember that Lucid Lynx is released tomorrow.. Thanks for the advice.

---

### Post by lapor on 2010-05-02
I did upgrade of Empathy to 2.30.0.1 and after that, Empathy disapearse from Indicator Applet.

Anybody knows how to fix that?


Thanks

---

### Post by paperpill on 2010-05-04
Got the same problem, upgraded Empathy to its newest version and is not supported by the Indicator Applet. 
Is there a way to downgrade the program or wait till indicator applet is updated?

---

### Post by mörgæs on 2010-05-04
In general downgrading is not a good idea. One never knows which problems are re-introduced into the system by doing so.

There is attention on the bug as can be seen here:
[https://bugs.launchpad.net/ubuntu/+source/empathy/+bug/533109](https://bugs.launchpad.net/ubuntu/+source/empathy/+bug/533109)

If you have additional information you could add your findings in the bug report, pushing it a little closer to a solution.

---

### Post by drunkncrew on 2010-05-22
I have done the exact same thing and the exact same thing happened to me. I found out how to create a "link" to empathy back in the indicator applet by creating a ".desktop" file in the indicator applet folder. However, it doesn't restore the functionality back to the indicator applet, were the new messages show up in there and everything. Maybe one of our great ubuntu geeks will come up with a solution quick!:P

---

