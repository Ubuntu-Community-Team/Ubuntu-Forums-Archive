---
title: "Beryl And Emerald..."
date: 2007-04-21
forum: Desktop Effects &amp; Customization
---

### Post by des4ij on 2007-04-21
Hey I have a clean Feisty Installation... I installed beryl which told me that it would also intall the core, settings, and manager. However, it did not automatically install emerald with it... Now, I installed it afterwards... I have the themes and everything... Even when I right click the beryl-manager tray icon, I see Emerald theme manager... However, when I click on a theme, my theme doesnt change... Please help... Thank You

---

### Post by francesco_m on 2007-04-21
this is a workaround. choose your theme from emerald theme manager, then right click the beryl-manager tray icon and select Reload Windows Decorator. should work

Francesco

---

### Post by des4ij on 2007-04-21
Hey i got it... i didnt realize but the problem was that emerald wasnt et as the window decorator for beryl... So i just right clicked the tray icon->Select Window Decorator->Emerald...

---

### Post by mgm4352 on 2007-04-22
i've tries both the methods mentioned above, and neither of them is working any other suggestions? 

ps i am rather noob..

---

### Post by des4ij on 2007-04-22
Do you have emerald installed??:

sudo apt-get install emerald emerald-themes


then run beryl
right click the tray icon and Select Window Manager-> Beryl
right click the tray icon and Select Window Decorator->Emerald
right click tray icon and click Emerald Theme Manager->Select a theme
right click tray icon and Reload Window Decorator.

:)

---

### Post by mgm4352 on 2007-04-23
thanks for the advice, i tried to follow it, however, i cannot select beryl as the window manager. it will not change away from metacity.

---

### Post by Tristan9669 on 2007-05-02
When I right click the tray icon and Select Window Decorator I only see GTK Window Decorator. How can I be able to use Emerald instead?

---

### Post by francesco_m on 2007-05-28
> **Tristan9669 said:**
> When I right click the tray icon and Select Window Decorator I only see GTK Window Decorator. How can I be able to use Emerald instead?

do you have emerald package installed?
**sudo apt-get install emerald emerald-themes**

then try reloading beryl-setting-manager and it should be on the list now

---

### Post by Ub1476 on 2007-05-28
What graphic card do you have? The reason you cannot use beryl as your  windows manager is that you probably isn't logged in in XGL.

---

### Post by Tristan9669 on 2007-05-28
> **francesco_m said:**
> do you have emerald package installed?
**sudo apt-get install emerald emerald-themes**

then try reloading beryl-setting-manager and it should be on the list now

I got it to work after I rebooted my computer :)

---

