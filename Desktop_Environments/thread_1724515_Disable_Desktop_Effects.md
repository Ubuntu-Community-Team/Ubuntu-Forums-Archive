---
title: "Disable Desktop Effects ?"
date: 2011-04-08
forum: Desktop Environments
---

### Post by younishd on 2011-04-08
:|
Hey,
I have a problem with disabling the Desktop Effects.
I know that they are in System>Preferences>Appearance>Visual Effects>None , but when I select "None" it doesn't stay disabled after rebooting the machine.
When I uninstall Compiz, the "Title bar" of the Windows disappear. (Metacity is installed)
Dunno wut I'm doing wrong. I have another PC, where I did the same thing, it's working when I just do "None" (it stays after reboot) …
*confused*
btw, when I do
```
sudo metacity --replace
```
It gives me the same thing.
Has anyone an idea ? \:
I want to disable them 'cause I have a problem with those effects. Compiz makes some problems with applications like Skype …
I'm trying to set the Visual Effect Settings to "None" and **KEEP** them saved.
Thanks.
OS: Ubuntu Linux 10.10 Maverick Meerkat (64bit)
Graphic Card: ATi Radeon HD 5700 Series (1024Mb)
(Other information needed ?)
___
[INDENT][INDENT][/INDENT][/INDENT]YouniS

---

### Post by 3Miro on 2011-04-08
metacity --replace is without sudo!

Changing the settings from appearance should fix the problem. Maybe the session is not saved properly, try logout login (after setting effects to None).

Do you have any other programs running that can start compiz, a custom script maybe or Fusion-icon?

---

### Post by younishd on 2011-04-08
Thanks for the fast answer.
> metacity --replace is without sudo!
Ah yea it's without sudo.

> Do you have any other programs running that can start compiz, a custom script maybe or Fusion-icon?
No I don't have any other application that could run it and there's no Fusion icon either.

> Maybe the session is not saved properly, try logout login (after setting effects to None).
Tried to Logout after doing the setting, then Logged in.
Same thing. I selected "None" then I logged out / in then Checked it, and it was set "Normal".
:confused:
YouniS

---

### Post by 3Miro on 2011-04-08
Go to System -> Prefs -> Startup Applications. Then see if there are any compiz related things. If not, then go to the next tab (Options) and select "Remember Currently Running Applications" (do that with effects set to None). Then try logout/login.

---

### Post by younishd on 2011-04-08
> Go to System -> Prefs -> Startup Applications. Then see if there are any compiz related things.
Nothing there.

> If not, then go to the next tab (Options) and select "Remember Currently Running Applications" (do that with effects set to None). Then try logout/login.
Worked fine ^^ ! :D

I'll set the thread as SOLVED.

Thanks for Help.
YouniS :)

---

