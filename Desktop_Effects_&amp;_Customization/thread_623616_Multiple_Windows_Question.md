---
title: "Multiple Windows Question"
date: 2007-11-26
forum: Desktop Effects &amp; Customization
---

### Post by sstomek on 2007-11-26
hey everybody,

I just installed Ubuntu gutsy and have been playing around with Compiz. Now I wanted to use the cube but I only have 2 windows to switch around with. How can I create the 4 windows needed to have the cube?

Also this question is a little off topic but I just (kinda) finished applying the Mac Leopard theme and I wanted to switch the background picture that comes up after the Usplash and also after the Login Window.  Reason being is that Usplash and Login Window are from the Leopard theme but the background image before that is still from the Ubuntu theme.

Thanks for looking,

Tomek

---

### Post by subs on 2007-11-26
System - Preferences - Advanced Desktop Effect Settings - General Options - Desktop Size

Then set Number of Desktops and Vertical Virtual Size to 1 and Horizontal Virtual Size to 4

---

### Post by subs on 2007-11-26
> **subs said:**
> System - Preferences - Advanced Desktop Effect Settings - General Options - Desktop Size

Then set Number of Desktops and Vertical Virtual Size to 1 and Horizontal Virtual Size to 4

that is... if u want a cube.... if u want more faces to ur 3d desktop put a higher number..... from my experience it gets a little hard to manage with anything more than 10

---

### Post by erginemr on 2007-11-26
Hello and Welcome to Ubuntu Forums.

As fas as I know, to be able to have the "Advanced Desktop Effect Settings" item in your menu, you should first install the package "compizconfig-settings-manager", that is, if you do not have it already.

You can also adjust the number of virtual desktops via right-clicking the virtual desktops applet on the bottom-right corner of your desktop and selecting options / preferences from the pop-up menu.

As regards your second question, you can right-click your desktop and select backgrounds tab. From there, you can select the one you like or add more backgrounds to the existing list by clicking on the "Add..." button.

P.S. For the cube to work, you should also enable it by using the "Advanced Desktop Effect Settings" config dialog. There should be check marks for "Enable Cube", "Rotate Cube" or something.

---

### Post by sstomek on 2007-11-26
was able to get the 4 windows, thanks for that.

However, for the background question, I am trying to get the Mac4Lin appearance and I have pretty much everything working including the desktop background. However, my question is pertaining to the background that pops up in between the usplash (the screen that has the loading bar) and the login window and also in between the login window and the splash screen right before the desktop loads.

The reason I wanted to change this is because the brown ubuntu background in between those screens takes away from the Mac feel.

Thanks for the help,

Tomek

---

### Post by Forlong on 2007-11-26
Regarding the brown screen: [http://ubuntuforums.org/showthread.php?p=3672448#post3672448](http://ubuntuforums.org/showthread.php?p=3672448#post3672448)

---

### Post by sstomek on 2007-11-26
> **Forlong said:**
> Regarding the brown screen: [http://ubuntuforums.org/showthread.php?p=3672448#post3672448](http://ubuntuforums.org/showthread.php?p=3672448#post3672448)


hey that worked great. That worked for the screen after the login window and before the desktop loads, but the screen after the usplash and before the login window is still brown. any ideas where the config file for that screen is?

Sorry for being picky,

Tomek

---

### Post by oobuntoo on 2007-11-28
Try this:

System-->Administration-->Login window

Click on "Local" tab

Change the "Background color" to any color you want.

Log out to see if it works.

---

