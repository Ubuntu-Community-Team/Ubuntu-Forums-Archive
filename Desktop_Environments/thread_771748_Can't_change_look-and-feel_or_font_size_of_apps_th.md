---
title: "Can't change look-and-feel or font size of apps that run as root (sudo)"
date: 2008-04-27
forum: Desktop Environments
---

### Post by oobuntoo on 2008-04-27
There is no way to change settings for programs that run as sudo. I've tried sudo kcontrol, sudo systemsettings, and sudo any kcontrol module, then make changes to fonts, colors, or style but nothing works.

---

### Post by unoodles on 2008-04-27
The themes must be located in /usr/share/themes for them to show up on apps running as root. open nautilus as root and copy all the theme folders from ~/.themes to /usr/share/themes

---

### Post by p_quarles on 2008-04-28
> **unoodles said:**
> The themes must be located in /usr/share/themes for them to show up on apps running as root. open nautilus as root and copy all the theme folders from ~/.themes to /usr/share/themes
Umm, no. That won't fix the problem, and if it does anything, it  likely won't be good. 

> **oobuntoo said:**
> There is no way to change settings for programs that run as sudo. I've tried sudo kcontrol, sudo systemsettings, and sudo any kcontrol module, then make changes to fonts, colors, or style but nothing works.
"sudo" isn't set up to correctly run all graphical applications. Using "kdesu" (the graphical sudo wrapper) in this case is recommended, and should resolve the issue. 

If you need to tweak things manually, you will find the root configuration files in the /root directory. This is, for all intents and purposes, the root user's home directory, and you will find all the normal userspace configuration files there, including a .bashrc, .gconf/ and/or .kde/

Hope that helps.

---

### Post by oobuntoo on 2008-04-29
I've tried kdesu; it makes no difference. Before Gutsy, settings for root/sudo and regular user were separated. In Gutsy, settings for regular user are also used by root/sudo to get consistency in look and feel. In Hardy, I just don't know what the hell developers did. Where are root/sudo config files responsible for font and theme setting? I look under root home directory and sub directories and there aren't any files there associated with font and theme settings.

---

### Post by realn on 2010-06-06
Hi, I have the same problem. I want to have the same look&feel for the applications running as root. 
All I could do was to change the icon theme by copying the icon folder in /root/.kde3/share/.icons
However, I cannot change neither the fonts, nor the icons for GTK applications running as root. I am especially interested in changing the fonts, I like so much Tahome fonts.
 I tried to change them by making the chenges in "kdesudo systemsettings", the changes are not taken into account.
 Is there any KDE3 guru that can help us, please?

---

### Post by wieman01 on 2010-06-06
realn, I would open a new thread, this one is old and probably won't be paid much attention to.

---

### Post by RahulBatra on 2010-06-12
@realn: This is how I was able to solve this problem for myself:

1. Open Konsole / Terminal.

2. If you have not yet set the "root" user's password, you can do so by:
```
sudo passwd root
```
If you already have the root user's password set, please ignore this step.

3. Issue the command:
```
sudo kate /etc/kde4/kdm/kdmrc
```

4. Change the line
from:
```
AllowRootLogin=false
```
to:
```
AllowRootLogin=true
```

5. Log out and log in as root (use the password you had set in step 2).

6. Open "System Settings" and make changes to the font settings etc.

7. Log out and log in as your normal user account.

8. You might want to restore the changes made to /etc/kde4/kdm/kdmrc file in step 4.


I know this workaround is probably pretty lengthy with security flaws, but this should work until someone comes up with a better solution.

---

### Post by Raffles10 on 2010-06-13
```
kdesudo systemsettings
```

You should start all graphical apps as root using kdesudo.

---

