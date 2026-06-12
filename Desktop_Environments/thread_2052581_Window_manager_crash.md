---
title: "Window manager crash"
date: 2012-09-03
forum: Desktop Environments
---

### Post by achuthpnr on 2012-09-03
Hi,
I was working with Xubuntu 12.04 smoothly till today afternoon, when I had a crash. After reboot, Xubutu doesnt work properly. I dont have the window title bars, and Thunderbird gets started from nowhere (it is not in autostart list nor  in any scripts I have) , without title bar ofcourse. 

In the thread below, I found similar problem with the window manager crash
[http://ubuntuforums.org/showthread.php?t=1811712](http://ubuntuforums.org/showthread.php?t=1811712)
and the command 

```
xfwm4 --display=:0.0 --replace
``` fixes the tile bar problem temporarily.  Logging in again gives the same problem. I also lost  all the panel shortcuts - it shows blanc icons and does not function.

There are some errors in the ~/.xsession-errors, find the file attached. 

I dont understand what is the problem here. Is there any way to fix this?

Thanks.

---

### Post by JKyleOKC on 2012-09-03
At your login screen you should have a session chooser, that defaults to "xubuntu session" but which will also show an "xfce session" if you click its little arrow button. Whichever session it offers you as the default, choose the other and see if the problem is still there.

If it goes away, then you have a corrupted session file for the other choice. You can click the setting manager in the applications->system menu and choose the "startup and session manager" applet, and tell it to erase all saved sessions.

On that same applet, you can turn off automatic saving of sessions, which may prevent any similar problem in the future.

Of course, if changing to the other session at login has no effect on the problem, then these steps won't help...

---

### Post by achuthpnr on 2012-09-04
Thanks [JKyleOKC]("http://ubuntuforums.org/member.php?u=374258") for the suggestion. As you pointed out, it seems to be a problem with cache / corrupted sessions file. Deleting the cache brought the title bars back. I had to delete the Xfce config files to make the icons work again followed by reconfiguring everything to my taste. 

I think one should  backup the config files after the system is properly configured, to avoid situations like this.

---

