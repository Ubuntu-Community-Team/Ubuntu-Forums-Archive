---
title: "Disabling Hibernate and Suspend for all users, ...then enabling it again."
date: 2009-05-19
forum: Desktop Environments
---

### Post by optimaco on 2009-05-19
I was trying to disable Hibernate and Suspend for all users and followed the suggestions in the following thread:
[http://ubuntuforums.org/showthread.php?t=440225](http://ubuntuforums.org/showthread.php?t=440225)
In short, I ran "gksu gconf-editor" and unchecked the can_hibernate and can_suspend keys and then marked them as mandatory.
After the next login, Hibernate and Suspend were indeed unavailable to all users.

The problem is that this action can apparently not be reversed. If I run "gksu gconf-editor" again, the keys are now displayed as "not writable".
How do I get out of this ?
Any help would be very much appreciated !

---

### Post by Concrete on 2009-05-19
Hmmm... why u didn't made a new group whitout possibility to go in hibernation, then just select user's who can't made that and put them on that group.

Later (how now) if u wont to enabled them to use again possibility to go in hibernation, just unselect them from group!?

---

### Post by optimaco on 2009-05-19
> why u didn't made a new group whitout possibility to go in hibernation, then just select user's who can't made that and put them on that group
Well, yes, your suggestion seems reasonable, and I guess I should have done something like that (although I am not sure how I can apply a gconf-editor setting to a specific group).
However, I am still stuck now with my "not writable" keys... Is a fresh install of the system my only way out?

---

### Post by Concrete on 2009-05-19
I dont see how can be "not writable" when u loged as root!?

Did u try to run gconf-editor via terminal and typeing -su before?

---

### Post by optimaco on 2009-05-19
Believe it or not, after physically shutting down the machine and starting it again, I now have access to those keys again with:
```
sudo -i
gconf-editor
```
They are still displayed as "not writable" but at least I can use the "Unset Key", and they are reset to their initial value.
I don't like rebooting machines (this is a business environment), but I guess that sometimes, the Windows approach (the M$ reboot frenzy) works...

Now, as for your suggestion to set the Hibernate option off for a specific user group: how would you proceed to limit gconf-editor settings to a specific group ?

---

