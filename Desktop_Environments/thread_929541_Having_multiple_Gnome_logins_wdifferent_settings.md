---
title: "Having multiple Gnome logins w/different settings"
date: 2008-09-25
forum: Desktop Environments
---

### Post by Zambini on 2008-09-25
Hi,
I have Ubuntu 8.04 with Gnome 2.22.3

I use it at school and on my desk, so sometimes I need my battery power > looks, and sometimes I want looks > battery power (because its plugged in).

And instead of having to change the settings every time, I was wondering if it was at all possible to have two separate login sessions, one (named something like "Desk Mode" which is gnome, and has everything at maximum pretty), and something that could be called "Portable Mode" (which is gnome, and has effects disabled). This way, I wouldn't have to waste any time (or battery, or potential errors) switching the settings around, and all my files and folders would still be there.

Thanks,
Zambini :)

---

### Post by stuv829 on 2008-09-25
Q: What is the difference between a Methodist and a Baptist? A: A Methodist will at lest say "Hi" to you in a liquor store.[wow gold](http://www.mmoinn.com)[world of warcraft power leveling](http://www.mmoinn.com/mmoinn_pl/)i like here [http://www.mmoinn.com/mmoinn_pl/](http://www.mmoinn.com/mmoinn_pl/)

---

### Post by spin2cool on 2008-09-25
Sure - just create a new user, then use softlinks to link the appropriate directories from one home directory to the other.  For example, firefox settings are stored in .mozilla, so from the new user's home directory, you'd run:

```
ln -s /home/olduser/.mozilla
```

Do the same for any settings that you want to be identical. You may run into some errors because you aren't the owner of some files.  In that case, you'll need to use chmod to set the appropriate permissions.

---

### Post by Zambini on 2008-09-25
> **spin2cool said:**
> Sure - just create a new user, then use softlinks to link the appropriate directories from one home directory to the other.  For example, firefox settings are stored in .mozilla, so from the new user's home directory, you'd run:

```
ln -s /home/olduser/.mozilla
```

Do the same for any settings that you want to be identical. You may run into some errors because you aren't the owner of some files.  In that case, you'll need to use chmod to set the appropriate permissions.


So I would have to do that for every program? 
So for Pidgin, 
```
ln -s /home/olduser/.purple
```
and Skype would just be .Skype, etc etc.

What about system preferences, such as Wifi configuration, Keys, desktop (panels, add-ons, etc)? Where are those, or are they tied in with the Desktop Effects?

Also, how can I access documents between both accounts? Is there a way I can tie them into eachother? or would I just have /home/olduser/ and /home/newuser (if so, how do I see the other one from each account)?


Thank you for your quick help :D

---

