---
title: "autologin with lightdm"
date: 2017-06-22
forum: Desktop Environments
---

### Post by francois.e on 2017-06-22
autologin with lightdm. I have tried following procedure without success:
[https://www.htpcbeginner.com/enable-lubuntu-auto-login/](https://www.htpcbeginner.com/enable-lubuntu-auto-login/)
and 
[https://wiki.debian.org/fr/LightDM](https://wiki.debian.org/fr/LightDM)
and 
[https://wiki.archlinux.org/index.php/LightDM#Enabling_autologin](https://wiki.archlinux.org/index.php/LightDM#Enabling_autologin)

Not working.  :(

Finally, the solution comes from here:
[https://askubuntu.com/questions/779358/autologin-with-lightdm-on-xenial-16-04](https://askubuntu.com/questions/779358/autologin-with-lightdm-on-xenial-16-04)

Testing it right now!

---

### Post by Frogs Hair on 2017-06-22
You've just posted regarding adding another DE (XFCE) and if you have you won't be able use it if auto login is enabled

---

### Post by deadflowr on 2017-06-22
> **Frogs Hair said:**
> You've just posted regarding adding another DE (XFCE) and if you have you won't be able use it if auto login is enabled

You can, just set the timeout in the /etc/lightdm/lightdm.conf.d/11-some-autologin-config.conf entry to anything other than zero (0).
Time would really depend on how long it take for the system to load the login screen. If that makes sense.

(I mean how long it takes for the login screen to show up and whether the amount of time you set is long enough to actually access the switcher utility.
Just the time to load the screen may eat up some of those precious seconds)

---

### Post by ajgreeny on 2017-06-22
> **Frogs Hair said:**
> You've just posted regarding adding another DE (XFCE) and if you have you won't be able use it if auto login is enabled
Yes you will.

You either do what deadflowr says or if you don't want to do that, simply logout from whatever DE you get at autologin. You will then get the normal login screen as you would otherwise do when logging in with autologin disabled.

Autologin works only from a cold boot as far as I'm aware.

---

### Post by Frogs Hair on 2017-06-22
> [COLOR=#000000][INDENT]Autologin works only from a cold boot as far as I'm aware.[/INDENT]
[/COLOR]


I'd forgotten that . Auto login does add a step to using another DE which is fine if intended. Thanks ajgreeney !

---

### Post by francois.e on 2017-06-22
Thanks for these fast and numerous interventions.

3 is not enough trying presently on file /etc/lightdm/lightdm.conf.d/12-autologin.conf :

[Seat:*]
autologin-user=fl
autologin-user-timeout=10

---

