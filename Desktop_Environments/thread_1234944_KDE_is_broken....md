---
title: "KDE is broken..."
date: 2009-08-08
forum: Desktop Environments
---

### Post by the8thstar on 2009-08-08
I tried to upgrade KDE to 4.3 using some additional (unofficial) sources as mentioned in these forums.

The upgrade broke KDE. Now I can still log in but I get a weird fatal error and the system hangs. I tried reinstalling it but nothing changed...

Any suggestions?

---

### Post by brexsis on 2009-08-08
i had KDE 4.2, but when i upgraded it to version 4.3 it broke my graphical environment too.
i added ```
deb http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu jaunty main
``` 
to sources list like it said in kubuntu homepage. but i cannot even get back to work KDE 4.2 when i remove this new adress from sources.list.
after login screen i got some 2 errors:
1 is about something not compsited
2 is something about plasma
and then my screen is just black with mouse cursor on it.

1) how i can get working kde 4.3 or 4.2?
2) how can i disable auto-login from console?

---

### Post by Zorael on 2009-08-08
Boot into recovery mode and see if it didn't upgrade all the packages.
```
aptitude update
aptitude full-upgrade
```

As for auto-login, you'd have to modify **/etc/kde4/kdm/kdmrc**. Find the part that looks like the following.
```
# Core config for 1st local display
[X-:0-Core]
# The VT the X-server should run on; auto-assign if zero, don't assign if -1.
# Better leave it zero and use ServerVTs.
# Default is 0
#ServerVT=7
[B]# Enable automatic login. USE WITH EXTREME CARE!
# Default is false
#AutoLoginEnable=[COLOR="Lime"]true[/COLOR][/B]
# If true, auto-login after logout. If false, auto-login is performed only
# when a display session starts up.
# Default is false
#AutoLoginAgain=true
# The delay in seconds before automatic login kicks in.
# Default is 0
#AutoLoginDelay=10
# The user to log in automatically. NEVER specify root!
# Default is ""
#AutoLoginUser=fred
# The password for the user to log in automatically. This is NOT required
# unless the user is logged into a NIS or Kerberos domain. If you use this
# option, you should "chmod 600 kdmrc" for obvious reasons.
# Default is ""
#AutoLoginPass=secret!
# Immediately lock the automatically started session. This works only with
# KDE sessions.
# Default is false
#AutoLoginLocked=true
# See above
ClientLogFile=.xsession-errors
```
Disable it by commenting out that line by placing a hashmark (**#**) in front of it (as it defaults to disabled if not explicitly enabled), or just have it say **[COLOR="Red"]false[/COLOR]** instead of **[COLOR="lime"]true[/COLOR]**.

---

### Post by the8thstar on 2009-08-10
> **Zorael said:**
> Boot into recovery mode and see if it didn't upgrade all the packages.
```
aptitude update
aptitude full-upgrade
```

As for auto-login, you'd have to modify **/etc/kde4/kdm/kdmrc**. Find the part that looks like the following.
```
# Core config for 1st local display
[X-:0-Core]
# The VT the X-server should run on; auto-assign if zero, don't assign if -1.
# Better leave it zero and use ServerVTs.
# Default is 0
#ServerVT=7
[B]# Enable automatic login. USE WITH EXTREME CARE!
# Default is false
#AutoLoginEnable=[COLOR="Lime"]true[/COLOR][/B]
# If true, auto-login after logout. If false, auto-login is performed only
# when a display session starts up.
# Default is false
#AutoLoginAgain=true
# The delay in seconds before automatic login kicks in.
# Default is 0
#AutoLoginDelay=10
# The user to log in automatically. NEVER specify root!
# Default is ""
#AutoLoginUser=fred
# The password for the user to log in automatically. This is NOT required
# unless the user is logged into a NIS or Kerberos domain. If you use this
# option, you should "chmod 600 kdmrc" for obvious reasons.
# Default is ""
#AutoLoginPass=secret!
# Immediately lock the automatically started session. This works only with
# KDE sessions.
# Default is false
#AutoLoginLocked=true
# See above
ClientLogFile=.xsession-errors
```
Disable it by commenting out that line by placing a hashmark (**#**) in front of it (as it defaults to disabled if not explicitly enabled), or just have it say **[COLOR="Red"]false[/COLOR]** instead of **[COLOR="lime"]true[/COLOR]**.

Thanks a lot for your help **Zorael**! The full upgrade did the trick. I didn't follow your suggestion about auto login since I still navigate between Gnome and KDE (see sig).

---

