---
title: "crontab/rcX.d problem"
date: 2009-02-11
forum: General Help
---

### Post by zpon on 2009-02-11
Hello

I am trying to get a script working, it should run once on boot up and once each hour, I have added it with update-rc.d script default, but it does not seem to run. I have also added it to crontab with 0 * * * * /etc/init.d/script start

The script can be seen here [http://pastebin.com/f25538005](http://pastebin.com/f25538005)

---

### Post by zpon on 2009-02-11
Apparently the crontab problem was because the time wasn't set right (so the script was first executed 10 minutes later). But the boot-time execution is still needed.

---

### Post by NTolerance on 2009-02-11
> **zpon said:**
> Apparently the crontab problem was because the time wasn't set right (so the script was first executed 10 minutes later). But the boot-time execution is still needed.

To run scripts at boot time you can use Debian's init system rather than crontab.  To add a script to the Debian init system run this command:
```
sudo update-rc.d /etc/init.d/script defaults
```

---

### Post by dcstar on 2009-02-12
> **zpon said:**
> Hello

I am trying to get a script working, it should run once on boot up and once each hour, I have added it with update-rc.d script default, but it does not seem to run. I have also added it to crontab with 0 * * * * /etc/init.d/script start

The script can be seen here [http://pastebin.com/f25538005](http://pastebin.com/f25538005)

And which run level have you put the script in?

---

### Post by zpon on 2009-02-12
> **NTolerance said:**
> To run scripts at boot time you can use Debian's init system rather than crontab.  To add a script to the Debian init system run this command:
```
sudo update-rc.d /etc/init.d/script defaults
```

Yeah I do that already for the boot time execution, I think the problem is that the computer doesn't have a network connection at the time it is run.

[QUOTE=dcstar]
And which run level have you put the script in?
[/QUOTE]
default adds the script to 1, 2, 3, 4 and 5 if I remember correctly

---

### Post by NTolerance on 2009-02-12
> **zpon said:**
> Yeah I do that already for the boot time execution, I think the problem is that the computer doesn't have a network connection at the time it is run.


default adds the script to 1, 2, 3, 4 and 5 if I remember correctly

Sorry, I should read more carefully.  This might be messy, but have you tried some sleep commands in that script to possibly wait for the network connection?

---

### Post by zpon on 2009-02-12
> **NTolerance said:**
> Sorry, I should read more carefully.  This might be messy, but have you tried some sleep commands in that script to possibly wait for the network connection?

I have thought about it, but didn't hope it would be necessary. I have earlier modified a livecd to use the script (and set up a SSH server on boot), I needed it for a computer with a busted screen, and it worked fine.
I guess I just have to "poke" around some more.

---

