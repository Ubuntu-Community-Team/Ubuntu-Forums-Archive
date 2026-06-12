---
title: "useradmin GUI not working - cant add/del users"
date: 2008-12-18
forum: General Help
---

### Post by lenswipe on 2008-12-18
Im finding for some reason that i cant add or delete users from the useradmin GUI under  System >Administration >Users and Groups.


Any user i add there is created with no home directory, and any user i delete in there apears to delete, but then comes back when i re-open the user and groups admin. 

Im afraid re-installation is not an option since i have lots of work on there and im also using it as a webserver so i dont want to have to install apache/php/mysql all over again.

Please help


-L

---

### Post by gsgleason on 2008-12-18
launch users-admin from a shell window and see if any error output comes out.  also, have you tried creating a user manually through the shell?

---

### Post by kanikilu on 2008-12-18
Have you tried [doing things by hand]("http://www.debianadmin.com/users-and-groups-administration-in-linux.html") at the CLI?

If you need a GUI, you could always install something like webmin to try to manage your users and groups (sudo apt-get install webmin).

---

### Post by lenswipe on 2008-12-18
well doing it via the terminal works. I already have webmin and that works. running sudo user-admin doesnt work, as i get the normal user accounts box but i cant click unlock....

I dont need a GUI, but the fact that the GUI doesnt work may or may not be part of something else. Its like if your car exhaust is blowing. You can drive the car with a blowing exhaust, but its something u want to get fixed up.

:)

-L

---

### Post by kanikilu on 2008-12-18
> **lenswipe said:**
> well doing it via the terminal works. I already have webmin and that works. running sudo user-admin doesnt work, as i get the normal user accounts box but i cant click unlock....

Try without sudo there. It should ask you for your password when you click unlock.

> I dont need a GUI, but the fact that the GUI doesnt work may or may not be part of something else. Its like if your car exhaust is blowing. You can drive the car with a blowing exhaust, but its something u want to get fixed up.

Yeah, I hear ya.

---

### Post by lenswipe on 2008-12-18
so...

nyone?

---

### Post by kanikilu on 2008-12-18
Well, for one, you didn't answer gsgleason's question. Start users-admin from the terminal, try to make the changes to your users or groups that you say aren't sticking, and then look for any error output in the console/terminal from which you launched it.

Additionally, there are also several bug reports that sound similar, such as [https://bugs.launchpad.net/gst/+bug/212317](https://bugs.launchpad.net/gst/+bug/212317) and [https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bug/220697](https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bug/220697) -- see if any apply to your situation.

---

### Post by lenswipe on 2008-12-18
> **kanikilu said:**
> Well, for one, you didn't answer gsgleason's question. Start users-admin from the terminal, try to make the changes to your users or groups that you say aren't sticking, and then look for any error output in the console/terminal from which you launched it.


OK, users-admin launches, but i cant click unlock even with using sudo and the error output in terminal says:

```
** (users-admin:6449): CRITICAL **: Unable to lookup session information for process '6449'
```

---

### Post by kanikilu on 2008-12-18
Ok...this may be redundant, but have you tried it *without* sudo? Opening it that way with sudo *will* produce the behavior you're seeing...I can confirm that.

---

### Post by lenswipe on 2008-12-18
> **kanikilu said:**
> Ok...this may be redundant, but have you tried it *without* sudo? Opening it that way with sudo *will* produce the behavior you're seeing...I can confirm that.

ok, ima try it without sudo now...


EDIT: I tried it without sudo, i got no error in terminal, and i was able to click unlock (even if i cant create or delete users)

---

