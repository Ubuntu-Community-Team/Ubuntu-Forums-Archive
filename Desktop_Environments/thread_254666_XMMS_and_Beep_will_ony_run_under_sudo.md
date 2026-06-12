---
title: "XMMS and Beep will ony run under sudo"
date: 2006-09-10
forum: Desktop Environments
---

### Post by HoneyGutClusters on 2006-09-10
I really don't understand what happened here. XMMS worked one minute, it crashed, and never worked again!

After many uninstalls and reinstalls, I discovered that XMMS will run when invoked from terminal using sudo. Trying a workaround, I installed Beep Media Player, only to find the same problem plaques that too!

While researching the problem, I found under XMMS's FAQ:

[I]XMMS works OK as root, but not as a user.

You probably have the wrong permissions on the sound device. As root do this: chmod 622 /dev/dsp and chmod 666 /dev/mixer[/I]

I tried this and it didn't help.

Any ideas or suggestions?

---

### Post by taurus on 2006-09-10
What is the permission of xmms?

```
ls -la /usr/bin/xmms
```
I have

```
-rwxr-xr-x 1 root root 998864 Apr 28 10:52 xmms
```

---

### Post by HoneyGutClusters on 2006-09-10
i have 
```

-rwxr-xr-x 1 root root 998864 2006-04-28 10:52 /usr/bin/xmms

```

even so, why wouldn't beep work either?

---

### Post by HAARP on 2006-09-10
Try renaming **/home/*user*/.xmms** to anything else (press ctrl+h to see hidden files/directories)

---

### Post by HoneyGutClusters on 2006-09-10
Well, I rm -rf'ed the .xmms directory thinking I borked the config file and that didn't solve the problem...

---

### Post by HoneyGutClusters on 2006-09-10
UPDATE: I created a second user account and tried running XMMS under it and it started without a hitch. It seems it's just my primary user account that has problems. I restarted and now, magically, XMMS starts under my primary account. Maybe I should've restarted before... 

Thanks for the help anyway!

---

