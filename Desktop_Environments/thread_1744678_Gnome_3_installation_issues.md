---
title: "Gnome 3 installation issues"
date: 2011-04-30
forum: Desktop Environments
---

### Post by Stewart54 on 2011-04-30
Good Morning,

Running Ubuntu 11.04 and installed Gnome3 upgrade.  Messed things up big time.  Ubuntu will load, but will shut down when I try to access almost anything but terminal.  How can I remove Gnome 3 or try to get back to Unity desktop or whatever.

Thanks in advance for your help

Stew

---

### Post by bmbaker on 2011-04-30
> **Stewart54 said:**
> Good Morning,

Running Ubuntu 11.04 and installed Gnome3 upgrade.  Messed things up big time.  Ubuntu will load, but will shut down when I try to access almost anything but terminal.  How can I remove Gnome 3 or try to get back to Unity desktop or whatever.

Thanks in advance for your help

Stew
if you installed gnome3 from the ppa:
then do alt-ctl-f2
enter login stuff and password
then do
```
sudo apt-get install ppa-purge
sudo ppa-purge ppa:gnome3-team/gnome3
sudo apt-get update
sudo aptitude safe-upgrade
```

---

### Post by WinRiddance on 2011-04-30
Your post isn't clear enough. You installed 11.04 with Unity, I got that.
But before you "upgraded" to Gnome 3, did you first try to login by selecting the Classic Gnome Desktop when the login screen was visible? Gnome 3 is obviously not going to run with the Unity desktop so you'd have to login to the Classic Gnome session first.

When you get the login screen, _before you log in_ look at the bottom of your screen. There should be an option there where you can switch the preferred type of desktop, one of these being Classic Gnome. Have you tried that?

Also, have you installed any proprietary graphic drivers before you upgraded the Gnome 3 desktop? ATI drivers in particular are known to cause problems/conflicts with Ubuntu.

---

### Post by Stewart54 on 2011-04-30
Stewart back to you,

Installed 11.04 and all was good, did not like Unity desktop so I switched to the Classic Gnome 2, and again all was good.  Thought That I would try gnome3 and all went to hell.  Try to log into Classic Gnome and get a system error and than it boots up again.  Gnome shell will get me to desktop, when I try to open an application, screen splits in half and is at a 45 degree angle, can no longer click or type or anything.  Firefox will not connect, etc etc etc.

How badly am I screwed on this mess.  Even tried to reinstall 10.10 from disk and nothing.

Appreciate any thoughts that you may have

Thanks

Stew

---

### Post by itmanvn on 2011-05-01
after install gnome 3 i cant login, error show below
>  I get the error "Could not update ICEauthority file /home/<user>/.ICEauthority" 

tried boot into recovery mode and chown,chmod entire my home directory but still no luck, pls help

---

### Post by Charlski on 2011-05-02
For now, Gnome 3 install on Ubuntu 11.04 is broken. You can't install it until they find a fix.

---

### Post by techgs on 2011-05-02
No its not correct.  

I am using Gnome 3 on natty and stunned with its performance.

Excellent work.

For .ICEauthority error you need to take following steps.

  a.  When the login screen appears, do not login.  Instead press CTL+ALT F1 to log into terminal.

  b.  You need to install lxde as window manager.

command :  sudo apt-get install lxde

reboot.

c.  Next login select lxde as your window manager and log into system.

d.  Switch off autologin from gnome3 setting - usermanager.

reboot.

e.   Now you will can use gnome3 as window manager and you are in.


I must confess that gnome 3 is awesome!!!!

---

### Post by itmanvn on 2011-05-03
for ICEauthority problem, install gnome-session will fix it:popcorn:

---

### Post by tails29 on 2011-05-03
This might be a stupid question, as i've only been using Ubuntu for a couple of months but if i install Gnome 3, will the option still be there at login to load unity 2D (3D doesn't work on my PC) if i wanted to?

---

