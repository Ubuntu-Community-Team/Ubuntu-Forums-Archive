---
title: "I added new user. How do I activate graphics?(compiz ect.)"
date: 2009-09-23
forum: Desktop Environments
---

### Post by Cannon1230 on 2009-09-23
[SIZE=3]my "cay" button will not let me type it...so I use "<" sorry
I added my girlfriend as another user on my Ubuntu 9.04.
My account has wor<ing compiz, rotating cube, and all the cool stuff. My problem is....

When I try to activate the highest level of visual effects in the "Appearance" menu, it will not let me do it. I just cant get her des<top environment to do the same things that mine does. 
All of the same Apps. and programs are on her account.
Why can I not hoo< her des<top up???? Please help!!!!!
Thanx!
Cannon 
[/SIZE]

---

### Post by Giblet5 on 2009-09-24
Does your GF have the same setup because you copied all of your files to her directory?

Did you change the ownership of those files/folders to her account so that she is allowed to write configuration changes?

Assuming her login is "mygf":
```
sudo chown -R mygf:mygf /home/mygf
```

---

