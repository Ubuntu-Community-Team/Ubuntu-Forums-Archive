---
title: "KDM theme"
date: 2005-04-10
forum: Desktop Environments
---

### Post by Haiyadragon on 2005-04-10
Is there a way to change the KDM theme? I've tried some options in kcontrol but they have no effect. I mean no offence to anybody but the default kubuntu theme is fugly. Especially the background.

So if someone could help me with this.

---

### Post by André on 2005-04-10
Hi there,

what did you already try?

The normal way to change kdm behaviour would be Control Centrum -> System Administration (the lowest one) -> Log in screen 

The names may vary because i only have a german setup right now.

There you got to change to System Administrator by clicking the lower button and entering your password afterwards. Than you can change everything to your liking.

Hope this helps. Please report back.

Greetings
André

---

### Post by kkathman on 2005-04-10
> Is there a way to change the KDM theme? I've tried some options in kcontrol but they have no effect. I mean no offence to anybody but the default kubuntu theme is fugly. Especially the background. 

First start with the K Control Center. You should see a list of settings on the left. The first is "Appearance & Themes". Click here and you can change Backgrounds to virtually anything you would like.  There are some that come with Kubuntu, but you can go to [www.kde-look.org](www.kde-look.org) and check out both backgrounds and themes. What I did was create a subdirectory called wallpapers in my home folder:  /home/yourname/wallpapers. I downloaded several wallpapers I liked there. Then in the control center under background you have the option to select backgrounds from a location, tile or scale them appropriately.

Also in the Appearance & Themes, you can globally change the color theme by chooseing the color option. The Theme Manager allows you to mix and match various themes together.

If you want more eye candy, look into superkaramba, which allows real time kinds of things like monitors and weather to be displayed on the desktop.

Be aware, that choosing some things chews up memory.

Hope this helps.

---

### Post by Haiyadragon on 2005-04-10
[QUOTE=kkathman]First start with the K Control Center. You should see a list of settings on the left. The first is "Appearance & Themes". Click here and you can change Backgrounds to virtually anything you would like.  There are some that come with Kubuntu, but you can go to [www.kde-look.org](www.kde-look.org) and check out both backgrounds and themes. What I did was create a subdirectory called wallpapers in my home folder:  /home/yourname/wallpapers. I downloaded several wallpapers I liked there. Then in the control center under background you have the option to select backgrounds from a location, tile or scale them appropriately.

Also in the Appearance & Themes, you can globally change the color theme by chooseing the color option. The Theme Manager allows you to mix and match various themes together.

If you want more eye candy, look into superkaramba, which allows real time kinds of things like monitors and weather to be displayed on the desktop.

Be aware, that choosing some things chews up memory.

Hope this helps.[/QUOTE]

No I was talking about KDM, the login manager for KDE. Thanks for the trouble though.

I found the solution a second ago. In /etc/kde3/kdm/kdmrc I commented out the theme=something line. Now it obeyes the Control Center settings. I couldn't find an option to change the KDM theme on the Control Center, but I might have overlooked it.

---

### Post by André on 2005-04-11
Sorry,

i just saw the problem a minute ago. KDM uses themes now too ;-)

Okay, at least i found a workaround on how to install new themes. Maybe this is interesting for you:

[http://www.kde-look.org/content/show.php?content=20653](http://www.kde-look.org/content/show.php?content=20653)

Greetings
André

---

### Post by Haiyadragon on 2005-04-11
> **André]Sorry,

i just saw the problem a minute ago. KDM uses themes now too  said:**
> http://www.kde-look.org/content/show.php?content=20653[/url]

Greetings
André

Thanks. Hopefully they'll add something to the Control Center to select and install new themes.

---

### Post by Kurse on 2005-05-11
It's already in Control Center, and has been for some time.

Control Center > System Administration > Login Manager

---

### Post by SpiritIsReality on 2007-07-30
> **Haiyadragon said:**
> No I was talking about KDM, the login manager for KDE. Thanks for the trouble though.

I found the solution a second ago. In /etc/kde3/kdm/kdmrc I commented out the theme=something line. Now it obeyes the Control Center settings. I couldn't find an option to change the KDM theme on the Control Center, but I might have overlooked it.



thankyou for this.
worked on ubuntu feisty with kubuntu-desktop install,
kdm default.

---

### Post by samwyse on 2007-11-24
I can't get it disabled in Gutsy. Needs some new tricks?

e: Ok, I did something and now I get the default KDE theme.

---

