---
title: "Open Program Without Making Listing In Taskbar"
date: 2011-02-19
forum: Desktop Environments
---

### Post by Shadow21 on 2011-02-19
Is there a way to make it so a certain program won't be listed in the taskbar when the program is opened?

---

### Post by Copper Bezel on 2011-02-20
If you're using Compiz, yes. Open ccsm if you have it (install it if you don't.) There's a plugin called "Window Rules" in the Window Management section of the main ccsm screen. Check the box next to the icon, then click it to configure the plugin.

The first item in the list of possible rules is "skip taskbar." We want to make a rule that identifies this application by name (not titlebar title) and exempts it from the taskbar list. Click the + sign next to the "Skip Taskbar" field, change the dropdown menu to "Application Name," click "Grab," and click on the window of the program you want to exempt.

The dialog box won't always create the rule automatically - Grab displays the name, but then often doesn't actually input it into the field. If this happens, just manually input the name into the Skip Taskbar field, as "name=whatever" (without quotation marks.)

Notice that this will also make the application unavailable to your Alt+Tab application switcher.

---

### Post by Shadow21 on 2011-02-20
> **Copper Bezel said:**
> If you're using Compiz, yes. Open ccsm if you have it (install it if you don't.) There's a plugin called "Window Rules" in the Window Management section of the main ccsm screen. Check the box next to the icon, then click it to configure the plugin.

The first item in the list of possible rules is "skip taskbar." We want to make a rule that identifies this application by name (not titlebar title) and exempts it from the taskbar list. Click the + sign next to the "Skip Taskbar" field, change the dropdown menu to "Application Name," click "Grab," and click on the window of the program you want to exempt.

The dialog box won't always create the rule automatically - Grab displays the name, but then often doesn't actually input it into the field. If this happens, just manually input the name into the Skip Taskbar field, as "name=whatever" (without quotation marks.)

Notice that this will also make the application unavailable to your Alt+Tab application switcher.

Thanks for the help :D

I was running a Windows program under Mono and it wasn't wanting to work correctly (it was suppose to minimize to the notification area) but now it works.

---

