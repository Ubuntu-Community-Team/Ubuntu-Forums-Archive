---
title: "Issues with login: Xsession"
date: 2005-08-05
forum: Desktop Environments
---

### Post by Ndlovu on 2005-08-05
I've had a problem for a while now with logging into Hoary. Just after login a window that says Xsession: pops up with the only option being to click the OK button. This makes it go away and the system loads without a hitch from there. Pretty simple workaround, which is probably why I haven't tried to fix it yet!

I've looked through the forums, and a couple of other users have been having the same issue, specifically the following threads:

[http://www.ubuntuforums.org/showthread.php?postid=287752#post287752](http://www.ubuntuforums.org/showthread.php?postid=287752#post287752)
[http://www.ubuntuforums.org/showthread.php?postid=258849#post258849](http://www.ubuntuforums.org/showthread.php?postid=258849#post258849)

It seems that there's something wanting the package xrdb installed, which is supported by the output from my .Xsession-errors file ([FONT=Courier New]# less ~/.Xsession-errors[/FONT]):

[INDENT]
[FONT=Courier New]/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/X11/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "rudi"
/etc/gdm/Xsession: Beginning session setup...
Xsession: warning: xrdb command not found; X resources not merged.
SESSION_MANAGER=local/ndlovu:/tmp/.ICE-unix/7958
Gnome-Message: gnome_execute_async_with_env_fds: returning -1
Gnome-Message: gnome_execute_async_with_env_fds: returning -1
Gnome-Message: gnome_execute_async_with_env_fds: returning -1
seahorse nautilus module initialized
mork error: No space left on device
*** loading the extensions datasource
*** loading the extensions datasource
Warning: more than one line!
Warning: more than one line![/FONT][/INDENT]

The problem is that I can't find xrdb with synaptic or with apt-get install. I've done an apt-get update and apt-get dist-upgrade so should have an up to date list (I've got a Hoary install, but most others seem to have had this problem with Breezy). Any ideas?

Thanks,
Rudi

---

