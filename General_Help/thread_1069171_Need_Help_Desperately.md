---
title: "Need Help Desperately"
date: 2009-02-13
forum: General Help
---

### Post by pemur1 on 2009-02-13
I was setting permissions under root and everything seemed to go OK. When I logged out as Root and logged in as usual, all that came up was a warning box (I assume, because all it had was a red "stop sign" with a line through it and nothing but little boxes). I couldn't read the warning sign so I have no idea what it says. I couldn't use the mouse, and pressing enter didn't do anything. I couldn't get any farther than that. I tried Recovery mode but the same thing occurred. I also couldn't get on using other kernals. I ended up using the Live CD to get on. I have no idea what happened and I'm rather averse to having to re-install. Any assistance would be greatly appreciated. :(

---

### Post by mcduck on 2009-02-13
What permissions were you setting? There's probably your explanation and also answer to what permissions you need to change back to get things working again..

---

### Post by pemur1 on 2009-02-13
> **mcduck said:**
> What permissions were you setting? There's probably your explanation and also answer to what permissions you need to change back to get things working again..

I was setting the usr/share folders so I wouldn't have to keep logging out as a user and logging in as root if I wanted to change something.

As a follow-up, I am also unable to log in as root as well. All that comes up is the warning box.

---

### Post by mcduck on 2009-02-13
You really shouldn't change any system file/directory permissions, they are what they are for a good reason and changing them will definitely cause problems.

Also you shouldn't even be logging in as root at all. Ubuntu uses "sudo" for root access. [https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

If you can remember which files/directories you changed you can change them back using the Live CD. Otherwise I'd say that reinstalling is the easiest way to get everything back to normal.

---

### Post by pemur1 on 2009-02-13
> **mcduck said:**
> You really shouldn't change any system file/directory permissions, they are what they are for a good reason and changing them will definitely cause problems.

Also you shouldn't even be logging in as root at all. Ubuntu uses "sudo" for root access. [https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

If you can remember which files/directories you changed you can change them back using the Live CD. Otherwise I'd say that reinstalling is the easiest way to get everything back to normal.

I now realize it was a stupid thing to do. ;)

How do I change the permissions back?

---

### Post by mcduck on 2009-02-13
THe same way you changed them now (or with "chown" and "chmod" commands).

There's no way to automatically change back to correct permissions, so you'll just have to reverse what you did to change them in the first place, probably by going through all the files/directories by hand.

If you only changed a couple of things we can probably give you the correct ownerships & permissions for them, but if you made a lot of changes then it might be a lot of work to get them fixed (as different files and directories may need different permissions and ownerships). In that case go for reinstall. Just make a backup of everything in your home directory (including the hidden files) and at least you won't loose any of your personal stuff or program settings.

---

### Post by glotz on 2009-02-13
Bash makes automatically a history file. If you used the root account to make the changes the interesting file will be at /root/.bash_history

---

### Post by Bladeforger on 2009-02-13
And you might be able to log on with the live CD and then make the changes on the hard drive to get your system back to a bootable state.  Depends on the amount of data / installed programs whether it's easier to do that or to do a new install.  Good luck!

---

### Post by pemur1 on 2009-02-13
It looks like I'll have to re-install. I'm doing a backup now of my Home folder. Thanks for the assistance.

---

### Post by jman6495 on 2009-02-13
i've just accidentaly done this with my home folder!
and i sudo'ed it . for some reason it did my entire system...
i spent 4 DAYS restoring it!
but if you can't logon then boot into "recovery mode" and get to a root terminal then chmod your home folder...
if you don't understand i'l give the command

   hope this helps

              jman6495

---

### Post by bodhi.zazen on 2009-02-13
Unless it was a simple chmod / chown IMO it is best to re-install and learn how to sys admin properly.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

[http://www.zzee.com/solutions/linux-permissions.shtml](http://www.zzee.com/solutions/linux-permissions.shtml)

Note: Threads like these remind us **ALL why we need to teach new users about such things** rather then instructing them to log in as root and what not.

---

