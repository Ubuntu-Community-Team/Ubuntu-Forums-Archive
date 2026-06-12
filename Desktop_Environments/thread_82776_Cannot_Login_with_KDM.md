---
title: "Cannot Login with KDM"
date: 2005-10-27
forum: Desktop Environments
---

### Post by mealz on 2005-10-27
I installed Ubuntu then decided I'd see what KDE was like on this great OS. So I installed kubuntu-desktop and a whole lot of other kde things. Everything is great except that I cannot login from KDM (except for failsafe). When I select any desktop/WM and click login, the screen goes blank and X server restarts I think... back to the login prompt. In my .xsession-errors file I found "No profile for user '<user>' found" Any ideas??? Thanks

---

### Post by tonym on 2005-10-27
Doesn't really solve your problem but you could stay with gdm.  This includes an option to start a KDE session.

---

### Post by mealz on 2005-10-27
I'd really like the integration that KDM provides to kde. In fact I think i'd like to remove most of the gnome stuff.

Ideas anyone?

I've uninstalled and reinstalled KDM no change...

---

### Post by mealz on 2005-10-28
bump:p

---

### Post by moopere on 2005-10-28
There appears to be some problem with KDM and .profile or .bashrc implemented environment variables.

See this thread:

[http://groups.google.com/group/linux.debian.bugs.dist/browse_thread/thread/eff9b271a300701/90666ee3451f130c?lnk=st&q=kdm+no+profile&rnum=6#90666ee3451f130c](http://groups.google.com/group/linux.debian.bugs.dist/browse_thread/thread/eff9b271a300701/90666ee3451f130c?lnk=st&q=kdm+no+profile&rnum=6#90666ee3451f130c)

I'm trying to fix it myself.

Cheers,
Craig

---

### Post by mealz on 2005-10-29
Ah... Good to see the problem has been identified already...
Sounds promising...
Would you mind letting me know how you fixed it when you do?

---

### Post by leo123 on 2005-10-29
In the meantime, how does one login to KDM on Kubntu?

Thanks,

leo123

---

### Post by leo123 on 2005-10-29
Someone out there PLEASE, let me know an alternative way of logging into KDE.

Thank you

---

### Post by beefsprocket on 2005-10-29
This thread might be of help: [http://ubuntuforums.org/showthread.php?t=81431]("http://ubuntuforums.org/showthread.php?t=81431")

Tried changing ownership of your home directory to your user? 

Try: "sudo chown -R beefsprocket:beefsprocket /home/*" substituting your usernmame and group around the colon. No idea if this will work, but it sounds like you might have an ownership problem like that reported in post #3 in the abovementioned thread.

---

### Post by mealz on 2005-10-30
Oh well.. a quick and dirty way to make KDE work from KDM:

backup /etc/kde3/kdm/Xsession

then replace it with Xsession conatining:
```

#! /bin/sh
startkde

```

Yeah, I can only login to KDE now...(no other window manager) but at least I can get in now!

---

### Post by Thorsten on 2005-11-02
[quote=beefsprocket]This thread might be of help: [http://ubuntuforums.org/showthread.php?t=81431]("http://ubuntuforums.org/showthread.php?t=81431")

Tried changing ownership of your home directory to your user? 

Try: "sudo chown -R beefsprocket:beefsprocket /home/*" substituting your usernmame and group around the colon. No idea if this will work, but it sounds like you might have an ownership problem like that reported in post #3 in the abovementioned thread.[/quote] 
Unfortunately, this doesn't correct the problem for me. (I had raised the issue in [http://ubuntuforums.org/showthread.php?t=81431]("http://ubuntuforums.org/showthread.php?t=81431").) I even create a brand new user and used either unchaned ~/.bash* and ~/.profile or none at all. Makes the same difference.

The error message in ~/.xsession-errors is always the same:
"No profile for user 'whatever' found:"
Trying to fix /etc/kde-user-profile or /etc/kderc doesn't do anything, either. The default profile is there (/usr/share/kubuntu-default-settings/kde-profile/default/) (and it's world-readable and world-executable.)

Hardcoding "startkde" in /etc/kde3/kdm/Xession sounds like a good workaround (which I haven't tried) for the short term, but I haven't been able to figure out the underlying problem.

Thorsten

---

### Post by Thorsten on 2005-11-02
[quote=mealz]I cannot login from KDM (except for failsafe). When I select any desktop/WM and click login, the screen goes blank and X server restarts I think... back to the login prompt. In my .xsession-errors file I found "No profile for user '<user>' found" Any ideas??? Thanks[/quote] 
I just figured it out, see [http://ubuntuforums.org/showthread.php?p=439936]("http://ubuntuforums.org/showthread.php?p=439936")
(first  entry, edited) for the solution.

Thanks for pointing me at /etc/kde3/kdm/Xsession, which led me to looking at /etc/X11/Xsession, which finally led me to /etc/X11/Xsession.d/60sabayon_apply.
:KS

Thorsten

---

