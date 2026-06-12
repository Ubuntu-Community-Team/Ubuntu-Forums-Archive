---
title: "Xfce Power Manager"
date: 2012-08-02
forum: Desktop Environments
---

### Post by themuCkk on 2012-08-02
Hey,

I am using an Ubuntu installation with Xfce as desktop environment on my Thinkpad E520. After installing updates (including a reboot) my power manager stopped working and I also get crash reports about the network manager on every start. I tried reinstalling (sudo apt-get remove, then install) xfce4-power-manager, but it didn't help. Here are some screenshots:

[https://dl.dropbox.com/u/12769915/power1.png](https://dl.dropbox.com/u/12769915/power1.png)
[https://dl.dropbox.com/u/12769915/power2.png](https://dl.dropbox.com/u/12769915/power2.png)
(The text says "Can't establish connection to the power manager for Xfce")

Any ideas how to fix this problem?

muCkk

---

### Post by Toz on 2012-08-02
Hello themuCkk and welcome to the forums.

Is xfce4-power-manager running? You can check by typing in the following in a terminal window:
```
ps -ef | grep xfce4-power
```

There also might be some useful information in the ~/.xsession-errors log file.

---

### Post by themuCkk on 2012-08-02
Hello,

xfce4-power is running. The only related message in the log was this:
> (xfce4-power-manager-settings:3227): xfce4-power-manager-settings-CRITICAL **: Unable to get configuration information from xfce power manager: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

Thanks for your fast reply :).

---

### Post by Toz on 2012-08-02
Try clearing out your sessions cache. Logout form Xfce, Ctrl+Alt+F1 to go to first tty, login to tty (text-based), clear the cache with:
```
rm -rf ~/.cache/sessions
```
...then go back to the GUI (Ctrl+Alt+F7) and log back in.

---

### Post by themuCkk on 2012-08-03
That solved it, thanks!

---

### Post by Mavashi on 2012-11-02
> **Toz said:**
> Try clearing out your sessions cache. Logout form Xfce, Ctrl+Alt+F1 to go to first tty, login to tty (text-based), clear the cache with:
```
rm -rf ~/.cache/sessions
```
...then go back to the GUI (Ctrl+Alt+F7) and log back in.

That helped me also. Thanks, Toz!

---

### Post by vbeggi on 2013-08-22
> **Mavashi said:**
> That helped me also. Thanks, Toz!

If the problem consists in thunar, right after login, waiting  long time before opening home and doing it after error message (unspecified resource/directory not available), it seems solved by a small change in : /etc/nsswitch.conf.

The original line:         [hosts:          files dns]
when changed to:       [hosts:          files wins dns]

seems to solve the problem without further interventions.
Even the "Network" link in thunar works out of the box.

---

### Post by kNKGbYy on 2013-10-18
> **Toz said:**
> Try clearing out your sessions cache. Logout form Xfce, Ctrl+Alt+F1 to go to first tty, login to tty (text-based), clear the cache with:
```
rm -rf ~/.cache/sessions
```
...then go back to the GUI (Ctrl+Alt+F7) and log back in.

Thanks Toz! Helped me out as well! Cheers mate!

---

### Post by fkkroundabout on 2014-05-29
> **Toz said:**
> Try clearing out your sessions cache. Logout form Xfce, Ctrl+Alt+F1 to go to first tty, login to tty (text-based), clear the cache with:
```
rm -rf ~/.cache/sessions
```
...then go back to the GUI (Ctrl+Alt+F7) and log back in.

worked for me

---

### Post by Toz on 2014-05-29
This fix, although still valid, was necessary for earlier versions of Xfce. The later versions of Xfce (4.10+) including the version in 14.04 has added the ability to clear the sessions cache without the need to go to a text console. Look for it in Settings Manager >> Session and Startup >> Session tab >> "Clear saved sessions". It is much easier now to clear the saved sessions cache.

Closing this thread.

---

