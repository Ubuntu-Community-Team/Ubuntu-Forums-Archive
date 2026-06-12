---
title: "xubuntu 20.04 two odd problems"
date: 2020-10-04
forum: Desktop Environments
---

### Post by lou6 on 2020-10-04
Xubuntu 18.04 used to show the logout options screen when the power button was pressed - 20.04 just powers off immediately.

Xubuntu 18.04 booted up to the login screen when powered on - 20.04 boots to my desktop.

Nothing fatal here but I'd like to change back to the previous actions.

---

### Post by CelticWarrior on 2020-10-04
I don't use Xubuntu so I won't comment about the first issue.
The second, however, must be related to autologin that you enabled, it isn't enabled by default (and shouldn't be used).

---

### Post by lou6 on 2020-10-04
My wife and I are the only users and neither of us had to enter a password to login to 18.04.  I thought that was the result of selecting "no password required".  When the system started up, the LightDM signon screen came up.

Perhaps "problems" is the wrong word - "minor annoyances" is better.

---

### Post by lou6 on 2020-10-04
My question should have been, "how do I get lightdm to run at startup?".

---

### Post by deadflowr on 2020-10-04
There is autologin, which logs into the desktop directly.

And there is no password login, which starts at the login screen, 
and when you select a user if the user belongs to the nopasswdlogin group, 
it will not ask for a password and can be logged in by clicking the enter key only.

The former is set in a conf file in /etc/lightdm, possibly lightdm-gtk-greeter.conf or something like that.
(It might also be in /etc/lightdm/lightdm.conf.)
It usually consists of two lines, one for the autologin user and one for a timeout which is for how long it shows at the login screen.
You can delete the lines or comment (add a # to the beginning of the entry) them out.

The latter only requires the user to be in the nopasswdlogin group.

---

### Post by lou6 on 2020-10-04
My wife and I are in the nopasswdlogin group.  I added Lighdm to the Applications Autostart  in Sessions and Startup but it isn't running after a shutdown/restart.  I'm missing something. I commented out the timeout=0 line in etc/lightdm/lightdm.conf but it's not working.

Whoops - should have made the timeout longer?  Made it 60 (hopefully seconds).

Works now.  What time setting would you recommend?

Thank you for the help.

---

### Post by lou6 on 2020-10-04
I think I've done something wrong - changed the timeout to 180 and now the system logs itself back in after 3 minutes.  I don't understand how this should be set...

Never mind - I've finally got it working.

Thanks again.  I've mark this as solved.

---

### Post by ajgreeny on 2020-10-04
For the instant shutdown problem you are seeing open up power-manager-settings and change the "drop-down" setting to **Ask** as in my screenshot.

---

