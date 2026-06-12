---
title: "[SOLVED] Problem with firefox"
date: 2008-12-09
forum: Desktop Environments
---

### Post by lidengdeng on 2008-12-09
Hi, recently my firefox collapsed frequently and I don't know whether it has something down with compiz effects, which I enabled just days ago. After the firefox collapsed, I tried to open a new firefox window, but it turns up a "Close Firefox" which presents "Firefox is already running, but is not respoding. To open a new window, you mush fire close the existing Firefox process, or restart your system."

And here is my case:
1). I could not find any firefox icon in the bottom. And I could not find Firefox process  in top -c command either. So how could I completely close the opened firefox window?

2). I have some program running, so I don't want to restart my pc.

Any help? Thanks in advance.

---

### Post by barisurum on 2008-12-09
Open the system monitor and check to see if there's a firefox process running. Try to end it or kill it.

---

### Post by davidbilla on 2008-12-09
Or if you like command line, type

```
$ ps ax|grep firefox
```

and then use 
```
$ kill <firefox-process-id>
```

---

### Post by lidengdeng on 2008-12-09
> **barisurum said:**
> Open the system monitor and check to see if there's a firefox process running. Try to end it or kill it.

Thanks, but how to open the System Monitor. I am a newbie to Ubuntu.:confused:

---

### Post by barisurum on 2008-12-09
Its in system\administration

---

