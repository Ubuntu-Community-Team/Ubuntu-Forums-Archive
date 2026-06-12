---
title: "Almost lost my system, .ICEauthority went wrong!"
date: 2005-04-24
forum: Desktop Environments
---

### Post by derrick1985 on 2005-04-24
Hey all, I went to log in to my account on Ubuntu, but ended up with a HUGE problem. I couldn't log in because my .ICEauthority file could't be read. So, luckily I was able to log in through failsafe terminal and copied the file from anothers account, and chmod'ed it to 777 to be able to log in again.

What can cause that to happen, how can I prevent it from happening again, and what's the proper chmod for that file!?

Thanks.

---

### Post by gunnyman on 2005-04-24
I had this happen to me after running K3b in a gnome session.
I was able to fix it by just chown -R my home directory.
Only happened once to me.
the command looks like this 
chown -R myusername:myusername /home/myusername

---

### Post by derrick1985 on 2005-04-24
[QUOTE=gunnyman]I had this happen to me after running K3b in a gnome session.
I was able to fix it by just chown -R my home directory.
Only happened once to me.
the command looks like this 
chown -R myusername:myusername /home/myusername[/QUOTE]

Thanks, i'll give that a try.

Now that I think of it, I tried to use Kopete the other day, that could have done it.

---

