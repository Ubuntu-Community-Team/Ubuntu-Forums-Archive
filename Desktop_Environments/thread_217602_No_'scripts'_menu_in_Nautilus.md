---
title: "No 'scripts' menu in Nautilus"
date: 2006-07-17
forum: Desktop Environments
---

### Post by razorsmile on 2006-07-17
Hiya

simple problem I expect, as I'm new to U., but I cannot seem to get a 'scripts' option up inside Nautilus.  I've just re-installed Dapper clanly after playing around with it for a little and am configuring the OS and want to get the scripts available.  Previously I used automatix but this time I wanted to do things individually ... so I get the scripts package from [http://g-scripts.sourceforge.net/index.php](http://g-scripts.sourceforge.net/index.php) and then I mkdir nautilus-scripts, in ~/.gnome, after which I make sure everything is set to execute and direct my nautilus file browser to the right folder.  Then nothing...

Have tried rebooting the desktop, then the whole system but still nadder.  No 'scripts' option at all, no matter where I right click...

Can anyone help here?

](*,)

[it was the wrong directory - the website said ./gnome but it should be ./gnome2 that the nautilus-scripts folder goes in]

---

### Post by christhemonkey on 2006-07-17
```
sudo apt-get install nautilus-script-manager 
```

I find that it is always much easier to install things from the repositories.

---

### Post by razorsmile on 2006-07-17
OK, all fixed - when I posted this the 'similiar threads' brought Up something that I hadn't found in the previous hours searching and it transpires that it's not ~/.gnome but ./gnome2 that the nautilus-scripts folder goes into...a small error on the page I got the scripts from it would seem ;-)

ttfn

---

### Post by razorsmile on 2006-07-17
yeah that would make sense - is there some good place I would be able to find a list of the sort of things since I didn't find anything in the add/remove tool ... but if I had known about nautilus-script-manager I would have tried that...

---

### Post by orb9220 on 2006-07-17
I am sure thier is a good reason but why no scripts when using sudo nautilus?

---

### Post by christhemonkey on 2006-07-17
As the scripts are installed into your ~/.gnome2 whereas root has its own home partition in /root.
I guess you could copy that folder there, but it might not be worth the effort!
(and may be potentially dangerous and all that whooha)

---

