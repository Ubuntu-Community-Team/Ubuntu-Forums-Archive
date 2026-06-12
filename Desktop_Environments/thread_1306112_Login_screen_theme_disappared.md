---
title: "Login screen theme disappared"
date: 2009-10-30
forum: Desktop Environments
---

### Post by Simoo on 2009-10-30
Hi,

Love the new login theme, however...

I clicked the accessibility option to change to high contrast, then clicked back, and now the theme is no more, all I have is the traditional grey look.

I tried going to 'login screen' under 'System > Administration' but the option to change theme in there seems to have gone too.

Please help, it would be a shame to have benefited from the new look for only 10 mins!

---

### Post by ludepu on 2009-11-12
when I first installed Karmic my login screen had the black box. now its gone to an ugly grey box and menu bar at the bottom.

[http://resa.linux-hardcore.com/wp-content/uploads/2009/10/KarmicKoala-NewLoginScreen-Part2-SunVirtualBox.png](http://resa.linux-hardcore.com/wp-content/uploads/2009/10/KarmicKoala-NewLoginScreen-Part2-SunVirtualBox.png)

to

[http://www.techairlines.com/wp-content/uploads/2009/10/Ubuntu-Login.png](http://www.techairlines.com/wp-content/uploads/2009/10/Ubuntu-Login.png)

any help would be great. thanks

---

### Post by b-boy on 2009-11-17
Hi

install human-theme

---

### Post by joeycbulk on 2009-11-19
To fix login screen theme after trying out high contrast, **reinstall gdm**.

For new users, here is how.
[LIST=1]
[*]Open System > Administration > **Synaptic Package Manager**
[*]In the Synaptic Package Manager, look for "**gdm**" package
[*]Right click on the gdm package then **Mark for Reinstallation**
[*]**Click Apply** button from the toolbar
[*]Logout to see login screen and check if it worked
[/LIST]

:guitar:

---

### Post by rudy.elgato on 2009-11-19
To restore mine to the original darker color, I ran what's listed in posting #8 in [http://ubuntuforums.org/showthread.php?t=1300171](http://ubuntuforums.org/showthread.php?t=1300171). If this is what you're after, maybe it will work for you as well.

---

### Post by ludepu on 2009-11-23
Thanks. Installing Human Theme worked.

---

### Post by mutex023 on 2009-11-27
One more solution - 

Reinstall the 'human-theme' package.

Run the following commands - 
sudo -u gdm gconftool-2 -t string -s /apps/metacity/general/theme HumanLogin
sudo -u gdm gconftool-2 -t string -s /desktop/gnome/interface/gtk_theme HumanLogin
sudo -u gdm gconftool-2 -t string -s /desktop/gnome/interface/icon_theme HumanLoginIcons

My karmic's gdm screwed up as i was playing around with different gtk themes and icons.This really SHOULD NOT happen !
Why should the login screen get screwed up, if i change the desktop theme ?

---

### Post by ontwowheels on 2010-01-01
> **joeycbulk said:**
> To fix login screen theme after trying out high contrast, **reinstall gdm**.

For new users, here is how.
[LIST=1]
[*]Open System > Administration > **Synaptic Package Manager**
[*]In the Synaptic Package Manager, look for "**gdm**" package
[*]Right click on the gdm package then **Mark for Reinstallation**
[*]**Click Apply** button from the toolbar
[*]Logout to see login screen and check if it worked
[/LIST]

:guitar:

This worked for me, THANKS.  I think my kid was messing with the accessibility settings on the login screen and I lost the black box.

---

### Post by Simoo on 2010-02-03
Thanks for the help guys :)

---

