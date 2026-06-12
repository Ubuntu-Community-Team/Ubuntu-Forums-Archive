---
title: "Setting KDE Logout Options"
date: 2009-05-17
forum: Desktop Environments
---

### Post by skewray on 2009-05-17
Where are KDE logout options set?  I have two computers.  On one, when I logout of KDE the computer just shuts down.  On the other, when I logout I am returned to the login manager, and then I have to shut the machine down.  Hunting through the various settings managers hasn't turned anything up for me yet.  Thanks!

Brian

---

### Post by benerivo on 2009-05-17
The logout options are set in System Settings > Session Manager. But i think it also depends on how you log out. The three ways i can see, all offer different options...

1. Right (context) click on the desktop area.
2. From the main menu.
3. From the logout plasmoid.

---

### Post by skewray on 2009-05-17
> **benerivo said:**
> The logout options are set in System Settings > Session Manager. But i think it also depends on how you log out. The three ways i can see, all offer different options...

1. Right (context) click on the desktop area.
2. From the main menu.
3. From the logout plasmoid.

The same thing happens with all three ways to log out.  I already used the Session Manager to set the options to shutdown and don't ask, but it does anyway.

Brian

---

### Post by surfed on 2009-06-07
Any solution? My kde shuts down if i log out and if i say shut down....somethings borked

---

### Post by skewray on 2009-06-13
No solution yet.  I may file a bug report if nothing turns up.

---

### Post by Zorael on 2009-06-13
Perhaps there's a setting you could manually change in /etc/kde4/kdm/kdmrc?

---

### Post by skewray on 2009-07-04
I looked through /etc/kde4/kdm/kdmrc and changed various settings that seemed appropriate, but nothing had any effect.  The problem must be elsewhere.

---

### Post by kingjere on 2009-07-18
I'm experiencing this too. I just noticed this today. The problem is, I seldom just logout and therefore have no idea how long this has been going on.

---

### Post by kingjere on 2009-07-18
to try to diagnose this I created a new user. That new user could logout correctly. The only difference in the settings is that "confirm logout" was checked. I changed mine and it worked.

In summary Kickoff --> System Settings --> Advanced --> Session Manager

check Confirm logout
check offer shutdown options
Select End current session
Select Restore previous session
Click apply

logout

Can you folks confirm?

---

### Post by skewray on 2009-07-27
You've nailed it.  That fixes the problem admirably.  Thanks!

Brian

---

