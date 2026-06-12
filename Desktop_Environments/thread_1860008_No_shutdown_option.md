---
title: "No shutdown option"
date: 2011-10-14
forum: Desktop Environments
---

### Post by heiowge on 2011-10-14
Since upgrading to 11.10, my shutdown and restart buttons have disappeared.

I had them active in 11.04, but they're gone now.  The option to show them appears to be active, but does nothing.

On a similar note, the auto-login doesn't work anymore.

Any ideas?

---

### Post by 176-671 on 2011-10-15
I have the same problem. I have the option Leave in my start menu, which opens a new menu with the following choices:
Session:
Log out
Lock
Switch user

System:
Sleep
Hibernate

But no Shutdown or restart.

In Add widgets there is only a Logout/lock - couple of buttons, but with no option to shut down or restart.
The only way to shutdown is to first logout and then at the login screen choose shutdown, which is too much hazzle. Any way to get back the shutdown option on KDE? A bugfix?

---

### Post by chrestomanci on 2011-10-16
I also have this problem.

See bugs [872098](https://bugs.launchpad.net/bugs/872098) and [853294](https://bugs.launchpad.net/bugs/853294) in launchpad.

It appears to be related to KDM. Unless you are using KDM (not GDM) for your login screen, then KDE does not support a shut-down option.

---

### Post by chrestomanci on 2011-10-16
> **chrestomanci said:**
> It appears to be related to KDM. Unless you are using KDM (not GDM) for your login screen, then KDE does not support a shut-down option.

Update: I have fixed this on my system:

```
sudo dpkg-reconfigure kdm
```

Chose kdm from the list, then logged out, rebooted, and now I have the shutdown option on the Leave menu.

---

### Post by Linux Lurker on 2011-10-16
> Update: I have fixed this on my system:

```
sudo dpkg-reconfigure kdm
```

Chose kdm from the list, then logged out, rebooted, and now I have the shutdown option on the Leave menu.

I entered this in the terminal, but got no indication that it did anything, except taking a couple of moments to return to the command prompt.  Still hopeful, I rebooted.  Excellent! This solved my issue (shutdown/reboot button(s) did nothing).  Now shutdown/reboot is performed as expected.

I had another issue that I hoped would be resolved by this as well.  For things such as the Muon Package Manager, I was not given the opportunity to enter my password to proceed with operations.  The only way I could get Muon to work, was to start it from the terminal with 
```
sudo muon
```
That is now unnecessary, as I'm once again being given the permission dialog boxes.

Thanks for the solution.
Now I only have to fix 99 more things on 11.10 upgrade. :shock:

---

### Post by heiowge on 2011-10-17
Thanks.  I'm glad someone worked on this.  I have switched my main desktop to mint 11, but my netbook still uses 11.04, so I'll use this when I upgrade that, but I won't be doing that until the auto login bug is fixed.

---

### Post by elnur on 2011-10-22
Go to System Settings &#8594; Startup and Shutdown &#8594; Session Management and check the &#8220;Offer shutdown options&#8221; checkbox.

[IMG]http://img38.imageshack.us/img38/781/shutdownoptions.png[/IMG]

---

