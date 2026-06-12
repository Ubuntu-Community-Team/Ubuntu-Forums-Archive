---
title: "timezone problem"
date: 2005-07-31
forum: Desktop Environments
---

### Post by dphipps on 2005-07-31
I just installed kubuntu and my local timezone somehow got set to UTC.  This is not my timezone.  How do I change this?

---

### Post by GavinX on 2005-07-31
Damn, how is this done again? I used KDE for a while and should know this.

It's somewhere in Control Panel, just search there and you will see something with configure timezones. Choose where you're and and save. All should be well afterwards.

---

### Post by Xian on 2005-07-31
Open a terminal and enter the command listed below.
It should open the KDE clock management module.

Make adjustments as needed.

```
$ sudo /usr/bin/kcmshell kde-clock.desktop
```

---

### Post by dphipps on 2005-07-31
I have already tried that.  It shows the chanced time in its window but the desktop clock does not change and it goes back to UTC when opened again.

---

### Post by Freddy on 2005-07-31
Use sudo /usr/bin/kcmshell kde-clock.desktop in a console as stated above, put a mark the the box "Set date and time automatically" and choose a ntpserver near you and be sure that you have the correct timezone.

/Freddan

---

### Post by dphipps on 2005-07-31
That doesn't work ether.  My local timezone is still on UTC.

---

### Post by Xian on 2005-07-31
[QUOTE=dphipps]That doesn't work ether.  My local timezone is still on UTC.[/QUOTE]
Make sure you have the universe repos enabled.

Install the timezoneconf package.
Then issue this command in a terminal:

```
$ sudo dpkg-reconfigure timezoneconf
```

---

### Post by dphipps on 2005-07-31
> Make sure you have the universe repos enabled.

Install the timezoneconf package.
Then issue this command in a terminal:

Code:

$ sudo dpkg-reconfigure timezoneconf 

I tried that and the program seemed to work but my timezone still remains unchanged.

---

### Post by Xian on 2005-07-31
The first method should have changed the TZ instantly.
However, you may need to reboot with the timezoneconf edits.

Short of that you may just want to get used to UTC. :)

---

### Post by vdorta on 2005-07-31
I had exactly the same intractable problem but I finally solved it with the timezoneconf suggestion.

Thanks!

---

### Post by sciurus on 2005-12-13
I think the problem is that if /etc/timezone doesn't exist, kde's "adjust date and time" module can't set the timezone.

Run the following command in a terminal: ls -l /etc | grep localtime

It should say something like:
lrwxrwxrwx   1 root   root        30 2005-12-07 21:22 localtime -> /usr/share/zoneinfo/US/Eastern

If it doesn't say anything, look in /usr/share/zoneinfo for your timezone and make /etc/localtime a symlink to it. For EST, the command would be:
sudo ln -s /usr/share/zoneinfo/US/Eastern /etc/localtime

---

