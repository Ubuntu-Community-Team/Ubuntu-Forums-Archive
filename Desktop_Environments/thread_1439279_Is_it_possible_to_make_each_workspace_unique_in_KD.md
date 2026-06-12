---
title: "Is it possible to make each workspace unique in KDE?"
date: 2010-03-26
forum: Desktop Environments
---

### Post by hortstu on 2010-03-26
I mean can I set up different Icons on the desktop of each workspace in KDE?  Seems that a mirror image of each workspace is a waste.  What do I need four identical workspaces for?  I want 4,5, or 6 different ones for different types of tasks.  No I don't care so much about wall paper.

Apparently this is impossible in Gnome.

---

### Post by lykwydchykyn on 2010-03-26
Yes.

If you turn on "Different activity for each desktop" under "settings->desktop=>multiple desktops"

each desktop becomes independent, with its own wallpaper, widgets, etc.

---

### Post by hortstu on 2010-03-26
> **lykwydchykyn said:**
> Yes.

If you turn on "Different activity for each desktop" under "settings->desktop=>multiple desktops"

each desktop becomes independent, with its own wallpaper, widgets, etc.

Thanks... sorry for the newbish question but is their an easy way to switch to KDE or do I have to install kubuntu as a seperate OS and then reset up everything?

---

### Post by Enigmapond on 2010-03-26
KDE is not an OS, but a desktop environment. When you install KDE, you will have the option at the Login screen which session you want. Gnome or KDE.

---

### Post by TheSqueak on 2010-03-26
> **hortstu said:**
> Thanks... sorry for the newbish question but is their an easy way to switch to KDE or do I have to install kubuntu as a seperate OS and then reset up everything?

```
sudo apt-get install kubuntu-desktop
```

Then you should have KDE available as a session option on login

---

### Post by hortstu on 2010-03-26
Great thanks for the help.

---

### Post by hortstu on 2010-03-26
> **lykwydchykyn said:**
> Yes.

If you turn on "Different activity for each desktop" under "settings->desktop=>multiple desktops"

each desktop becomes independent, with its own wallpaper, widgets, etc.


OK so I logged in with a kde session.  Everything looks exactly the same.  Where am I supposed to find this

settings->desktop=>multiple desktops

under compiz or system?  I'm not finding these options anywhere

---

### Post by 3Miro on 2010-03-26
> **hortstu said:**
> OK so I logged in with a kde session.  Everything looks exactly the same.  Where am I supposed to find this

settings->desktop=>multiple desktops

under compiz or system?  I'm not finding these options anywhere

On KDE 4.3 you need to click on the Cashew on the upper right corner and select zoom out. Then you can select some of the settings and use different activities per desktop. Here is more information:

[http://userbase.kde.org/Plasma/FAQ/HowTo](http://userbase.kde.org/Plasma/FAQ/HowTo)

On KDE 4.3, this still doesn't work very well. There are some annoying bugs. On KDE 4.4, this has been fixed and activities can be controlled form the System Settings Menu.

---

### Post by lykwydchykyn on 2010-03-26
> **hortstu said:**
> OK so I logged in with a kde session.  Everything looks exactly the same.  Where am I supposed to find this

settings->desktop=>multiple desktops

under compiz or system?  I'm not finding these options anywhere

You're probably going to have better luck using kwin under kde, not compiz.

For configuration, try the "system settings" tool, located in the menu.

---

### Post by hortstu on 2010-03-26
There's no cashew in my upper left corner.

Should I uninstall compiz and install kwin?

> **3Miro said:**
> On KDE 4.3 you need to click on the Cashew on the upper right corner and select zoom out. Then you can select some of the settings and use different activities per desktop. Here is more information:

[http://userbase.kde.org/Plasma/FAQ/HowTo](http://userbase.kde.org/Plasma/FAQ/HowTo)

On KDE 4.3, this still doesn't work very well. There are some annoying bugs. On KDE 4.4, this has been fixed and activities can be controlled form the System Settings Menu.

---

### Post by lykwydchykyn on 2010-03-26
> **hortstu said:**
> There's no cashew in my upper left corner.

Should I uninstall compiz and install kwin?

You don't need to uninstall compiz, and kwin should be installed if you installed kubuntu-desktop.

Check in system settings:
Personal=>Default Applications

Select "window manager" and make sure it's set to default.

BTW what version of KDE did you install?

---

### Post by hortstu on 2010-03-26
I appreciate all this help but none of the stuff anyone is describing seems right to me.  This looks exactly like gnome did.

I chose kde in options.  It said kubuntu instead of ubuntu when it loaded.

Across the top of my screen I have the same stuff I did before this...

applications, places, system, some quickstart icons, bluetooth, power mgmt, compiz internet signal, audio controls, time and date, logoff options.

How do I figure out which version of KDE I installed... by the way in case it's important i'm using hardy for at least another month.



> **lykwydchykyn said:**
> You don't need to uninstall compiz, and kwin should be installed if you installed kubuntu-desktop.

Check in system settings:
Personal=>Default Applications

Select "window manager" and make sure it's set to default.

BTW what version of KDE did you install?

---

### Post by lykwydchykyn on 2010-03-26
> **hortstu said:**
> 
How do I figure out which version of KDE I installed... by the way in case it's important i'm using hardy for at least another month.

Well, that would make a difference... because what everyone is describing to you is KDE 4.3 or higher, and what you're getting on hardy by default is KDE 3.5.

AFAIK there is no way to accomplish what you want on KDE 3.  I think KDE 4.0 might be available for Hardy, but it won't do what you want to do.

I assume you want to stick with LTS releases, so unless anyone knows of another DE that will do what you're asking, you'll have to wait until Lucid.

---

### Post by Enigmapond on 2010-03-26
On the bottom of the login screen, there is I think a tab for session or settings and THIS is what you use to change the session desktop, It will also give you the option of making KDE the default session. Right now you are just logging straight in to the gnome session without changing it AT THE LOGIN SCREEN to KDE...I hope this helps...

---

### Post by hortstu on 2010-03-27
Yes thanks that helped enigma.

I managed to get into KDE now but it seems the only reason to be here is to get used to it so that I can set this up the way I want when the next LTS is released.  

It baffles me that this feature isn't standard in all DEs... otherwise what is the point of separate work spaces?

Thanks for all the help.  I'm sure I'll be back on this issue before May.

> **Enigmapond said:**
> On the bottom of the login screen, there is I think a tab for session or settings and THIS is what you use to change the session desktop, It will also give you the option of making KDE the default session. Right now you are just logging straight in to the gnome session without changing it AT THE LOGIN SCREEN to KDE...I hope this helps...

---

### Post by lykwydchykyn on 2010-03-27
> **hortstu said:**
> Yes thanks that helped enigma.

I managed to get into KDE now but it seems the only reason to be here is to get used to it so that I can set this up the way I want when the next LTS is released.  

It baffles me that this feature isn't standard in all DEs... otherwise what is the point of separate work spaces?


Traditionally, the point has been more to be able to work with a lot of windows without constantly minimizing them.  It's nice particularly when you have multi-window apps like GIMP, or if your working on a project involving multiple applications and get suddenly interrupted with some other task.

---

### Post by hortstu on 2010-09-30
So has this ever been developed by gnome?  I'd prefer to stick with the DE I know but will reluctantly make the switch if someone can show me how to make it happen.

---

