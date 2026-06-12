---
title: "[x]Ubuntu Locks up"
date: 2009-03-18
forum: General Help
---

### Post by .:Justus:. on 2009-03-18
At random times [X]ubuntu will lock-up completely.
Nothing works, not the mouse, not the keyboard, absolutely no response from the system and i can only manually turn it off with the power button.
I have never had a more annoying problem^^
Currently using xubuntu +xfce on an acer aspire one.

If anyone else is experiencing the same problem please post here,
I would greatly appreciate it.
thanks!

---

### Post by wpshooter on 2009-03-18
Could be that you just have a bad installation.

1) Do you know for a fact that you have at least the minimum hardware/system requirements for running Xubuntu ?

2) Do you have any other O/Ss on the computer or is it just Xubuntu ?

3) Do you know for a fact that you do not have any hardware issues, i.e. have you ran any hardware diagnostic software to test your components ?

4) Did you test the integrity of your Xubuntu CD by running the verification function that is found on the initial Xubuntu boot screen menu ?

5) If you did your installation from the live (desktop) CD version of Xubuntu have you tried doing the installation from the ALTERNATE (texted based) CD version of Xubuntu ?

Good luck.

---

### Post by fieroboom on 2009-03-18
In order to properly identify and fix the issue, you first need to start troubleshooting, and the best place to start is with log files. The next time it crashes, run these commands and copy/paste the output here.

```
tail -n 50 /var/log/syslog

tail -n 50 /var/log/syslog.0

tail -n 50 /var/log/dmesg

grep EE /var/log/Xorg.0.log

grep EE /var/log/Xorg.1.log
```
I'm not sure if 50 lines will give you enough clues, but we don't wanna make the post too long.
Always remember, knowing where to look is half the solution...
:D
-Paul

---

### Post by .:Justus:. on 2009-03-18
> **wpshooter said:**
> Could be that you just have a bad installation.

1) Do you know for a fact that you have at least the minimum hardware/system requirements for running Xubuntu ?

2) Do you have any other O/Ss on the computer or is it just Xubuntu ?

3) Do you know for a fact that you do not have any hardware issues, i.e. have you ran any hardware diagnostic software to test your components ?

4) Did you test the integrity of your Xubuntu CD by running the verification function that is found on the initial Xubuntu boot screen menu ?

5) If you did your installation from the live (desktop) CD version of Xubuntu have you tried doing the installation from the ALTERNATE (texted based) CD version of Xubuntu ?

Good luck.

Phew^^

1: All requirements are met yes.

2: used to have winxp a while ago, never experienced crashes on it.

3: If you can recommend me a hardware diognostic program ill give that a go, but since everything else runs perfectly fine i think everythings ok.

4: I installed via usb with unetbootin,if that changes anything.

5: nope, but ill only do that as a last resort since i have a lot of stuff on here.

thanks^^

---

