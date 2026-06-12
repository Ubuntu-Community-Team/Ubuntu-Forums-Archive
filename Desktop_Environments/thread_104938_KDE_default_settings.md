---
title: "KDE default settings"
date: 2005-12-17
forum: Desktop Environments
---

### Post by Neo Ex on 2005-12-17
Hi to all.
Sorry for my bad English, but I'm Italian.
I have Kubuntu but I don't like the default settings of Kubuntu (the Lipstick style and a lot of other things), and I want to know how I can get back to the default KDE settings, or, better, how can I see the first startup wizard of KDE, where you can choose the details and the style, for example.
I have tried to remove the .kde directory in my home, but when I logout, it will reappear.
If I remove the kubuntu-default-settings, I obtain the KDE as it is released, but it doesn't show me the startup wizard, even if I remove again the .kde directory.
How can I get all of the default KDE settings/show the first startup wizard (it is better if I haven't to remove the kubuntu-default-settings)?
Thank you (and sorry for the stupid question :) )

---

### Post by nrwilk on 2005-12-17
go to your konsole, and type the following:
```

sudo kcontrol

```
then enter your password.

This brings up the preference and control center for KDE.  The first catagory in the list on the upper-left is "Appearance and Themes."  Expand that catagory, and all the stuff that you want to change will be in the section within it.  Window decorations, Backgrounds, Colors, Fonts, Icons, Splash Screens, Styles, etc...

BTW, I wouldn't have known that English wasn't your first language if you hadn't told us.  There are many people who speak English as a first language and cannot do near as well as you do.

---

### Post by GoldBuggie on 2005-12-17
just start it with kcontrol not with sudo since i'm guessing you want to change the appearance for your user not for the apps which you start using sudo.

---

### Post by Neo Ex on 2005-12-17
I know about KControl, and I know that there is a button for replacing the get back to the default settings, but there are a lot of things that in Kubuntu settings are different than the KDE default settings, and I don't want to change all of them by hand.
And then, there are, for example, the bad Kubuntu logo in Konqueror instead the KDE logo (I want this one) and the background image in Konqueror I want to remove.
And I don't know how to change the icon dimension in the K men&#249; (I want the icons smaller, not like default in Kubuntu)...
So I prefer to have a 'clean' KDE without changes, because it is nearly perfect for me :)

P.S. Thanks :D (for your last sentence).

---

### Post by nrwilk on 2005-12-17
Well, then I'm not sure what you can do.  I'm pretty sure that Kubuntu does not have the initial setup utility that you'd use to setup KDE when you first install it on another distro.  One of my favorite parts of installation is going through KControl and setting all my settings, hehe. :p 

GoldBuggie:  If you don't start it with sudo, you'll not be able to set some things, like timezones and printer settings.  <sudo kcontrol> still gets you controls over your user settings, and not root settings.  If you were to initiate KControl with su, you would then be setting root's settings.  Believe me, I've had the learning try-and-try-again experience.

---

### Post by Neo Ex on 2005-12-17
I think I've found what I was seeking for: Kpersonalizer!
Tomorrow I'm going to install it and I'll see if it is appear when I'll log in or if I have to delete the .kde directory or uninstall the kubuntu-default-settings package.

EDIT: I have installed Kpersonalizer, I uninstalled kubuntu-default-settings and now the wizard starts and finally I have a 'default' KDE! :D
However thank you for your answers ;)

---

### Post by nrwilk on 2005-12-17
Sweet!  That's good to know.

Thanks for your digging, Neo Ex!

---

