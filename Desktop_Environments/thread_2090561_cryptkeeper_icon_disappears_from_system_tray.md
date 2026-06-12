---
title: "cryptkeeper icon disappears from system tray"
date: 2012-12-02
forum: Desktop Environments
---

### Post by chiron80 on 2012-12-02
Ever since Ubuntu 11.10, I've had trouble using cryptkeeper with Unity. I have cryptkeeper set to start automatically when I log in, and **the icon initially shows up** in the system tray. However, after a while the icon disappears. The only way I've determined to get it back is to log out and back in again (which is very annoying).

I never notice it is gone until I go to use it, usually when I'm trying to save something to the encrypted folder. Then I need to log out, so I end up saving a temporary copy to an unencrypted folder first, log out, log back in, mount the encrypted folder, and move the file. Very annoying. I have no idea what is causing it to disappear.

This is **not** simply because I need to whitelist 'cryptkeeper'. **I have already done this**, but every time I search to try and find a solution, all I can find are discussions like this:
[http://ubuntuforums.org/showthread.php?t=1791606]("http://ubuntuforums.org/showthread.php?t=1791606")

I've already run this command:

```
gsettings set com.canonical.Unity.Panel systray-whitelist "['all']"
```

I just ran this comand:
```
$ gsettings get com.canonical.Unity.Panel systray-whitelist
['all']
$ ps aux | grep cryptkeeper
ben       2641  0.0  0.4 1074572 16004 ?       Sl   Dec01   0:02 cryptkeeper
ben      14021  0.0  0.0   9404   932 pts/1    S+   18:12   0:00 grep --color=auto cryptkeeper

```

Cryptkeeper is running, and it has been whitelisted, but I do not see it in the system tray.

Any thoughts or suggestions? Because of the predominance of the the issue with whitelisting, I have also been unable to find an existing bug report, so if anybody can point me towards an existing bug report, let me know. Otherwise, I'll file one myself.

Thanks,
- Ben

---

### Post by chiron80 on 2012-12-02
I just found one way to fix it without logging out and loggin back in again.

```
setsid unity
```

I think I've tried this before, and it used to forget the window positions, leaving the windows with their menu bars obscurred by the top panel and preventing you from moving them with the mouse (you had to use alt+F7 to move them back to the correct places). That issue seems to be fixed, so at least this is a temporary work-around. However, the bigger problem remains.

I'll also add that, in addition to the 'cryptkeeper' icon disappearing, I have an icon for 'thinkhdaps' (which indicates when my hard drive has been paused do to vibration/dropping). This icon also disappears, so the problem isn't exclusive to 'cryptkeeper'.

---

### Post by bazmonkey on 2013-07-03
Did anyone figure this one out???  I have the same problem in 13.04.  It's there, and disappears, usually when clicking on the unity dock.

It's hard to find a proper way to word this when searching, and this is the only reference I can find to what I think is the same problem.

---

