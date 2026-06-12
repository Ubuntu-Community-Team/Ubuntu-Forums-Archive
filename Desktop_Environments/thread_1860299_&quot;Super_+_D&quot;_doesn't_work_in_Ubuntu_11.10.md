---
title: "&quot;Super + D&quot; doesn't work in Ubuntu 11.10 anymore"
date: 2011-10-14
forum: Desktop Environments
---

### Post by mgt2000 on 2011-10-14
Hi everybody,
I installed Ubuntu 11.10 yesterday but I have a small problem! one of the shortcuts (Super + D) which minimize all windows doesn't work any more. what is the problem?
of course I already use another shortcut (Ctrl + Alt + D) but still I prefer the previous one and based on documentation it should work in this new version of Ubuntu too.

Thanks

---

### Post by mc4man on 2011-10-14
If you wish to change ctrl+alt+d to super+d then you can do so in system settings > keyboard > shortcuts > navigation

(the 'show desktop' in 11.10 unity currently is a bit bugged, though nothing to due with the binding used

---

### Post by Cobalto on 2011-10-16
I tried that, but it only brings up the Launcher and types 'd' into the Dash. Also, for some reason, it registers my Super key as Mod4. Could that be the problem? Additionally, CTRL+ALT+d usually needs to be pressed twice. Anybody else seeing that?

---

### Post by vasa1 on 2011-10-16
It (super+D) works for me if I press both keys together without a lag.

---

### Post by Cobalto on 2011-10-16
Mine doesn't, at least not consistently. It does work about every second time, but every attempt -successful or otherwise- brings up the Launcher and Dash.

I wonder why the inconsistency and the difference from yours...I'm on a Dell Studio XPS, if that matters.

---

### Post by tommo1982 on 2011-10-16
Pressing Super + D will try to run something placed on the Launcher. If you hold Super for some time you will see numbers and letters on the icons there. You'll see that by pressing Super + 1 Nautilus will run, Super + 2 browser if you left the default setting. I think Super + D is set to something that no longer exists at the Launcher, that's why it returns an error (in my case at least). Now to find what it is bound to.

Btw, when I try to change CTRL + ALT + D to Super + D, it shows like Mod4 + D as well.

---

### Post by mc4man on 2011-10-16
super+d works fine here to 'show desktop'
You would want to press & hold super, then press d - a tap on super opens dash so if trying to do super & d at same time may open it instead
In any event 'show desktop' has issues, at least for many, bug on is not yet fixed.
This has been seen here on numerous fresh installs, I don't do upgrades 
bug on - can affect both the keyboard & alt-tab switcher
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/864870](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/864870)

---

### Post by Hakunka-Matata on 2011-10-16
> **tommo1982 said:**
> Pressing Super + D will try to run something placed on the Launcher. If you hold Super for some time you will see numbers and letters on the icons there. You'll see that by pressing Super + 1 Nautilus will run, Super + 2 browser if you left the default setting. I think Super + D is set to something that no longer exists at the Launcher, that's why it returns an error (in my case at least). Now to find what it is bound to.

Btw, when I try to change CTRL + ALT + D to Super + D, it shows like Mod4 + D as well.

Mod4+D equates to SuperKey + D

---

### Post by tommo1982 on 2011-10-16
Everything works now. I'm not really sure if it's a bug or a configuration problem. I was playing with compiz settings and had to re-enable Unity plugin. After that Super + D works fine. Either it was that or something else I did fixed the problem.

---

### Post by Cobalto on 2011-10-16
It works for me now too! WEIRD. I just rebooted and noticed it just now. Maybe it needed a full restart rather than a logout/login.

---

### Post by mdacova on 2011-10-24
> **Cobalto said:**
> It works for me now too! WEIRD. I just rebooted and noticed it just now. Maybe it needed a full restart rather than a logout/login.

also had to reboot to fix, nice one guys

---

### Post by xedi on 2012-01-30
It doesn't work for me on my computer either after I upgraded from 11.04 to 11.10. How do you reenable the plugin? If I understand correctly that fixed the problem (rebooting alone doesn't.

---

