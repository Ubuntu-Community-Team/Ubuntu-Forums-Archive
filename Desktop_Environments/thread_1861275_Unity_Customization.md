---
title: "Unity Customization"
date: 2011-10-15
forum: Desktop Environments
---

### Post by HDTimeshifter on 2011-10-15
I just upgraded to 11.10 and installed Unity for the first time (last release my memory failed so never transitioned to Unity).  There's a few things I don't like that I wonder if I can customize to make it more like Gnome or Windows 7:

1.  Can I change the time display to show the date?  This is one thing I liked about Gnome over XP that Win 7 adopted.  If I could hover the mouse over the time and get the date to temporarily pop up, that would work, but really, there is not a scarcity of screen space in the toolbar for it to display all the time.

2.  In the file manager, how do I get it to display details like Gnome and Windows?  I used to use the details display almost exclusively in Gnome and Windows.

3.  Is there a way to set the App toolbar (Launcher/Dashboard or whatever they call it) to stay on the desktop instead of autohiding?  I never liked Windows auto-hide feature of their app toolbar and always had it showing.  Does it have the capability to show mini displays of the app/windows running like in Win7?  That was the best upgrade feature in Win7 IMHO.

---

### Post by howefield on 2011-10-15
> **HDTimeshifter said:**
> Can I change the time display to show the date?

Click on the time and select Time & Date Settings from the bottom of the calendar window, then on the Clock tab and set as appropriate.

> In the file manager, how do I get it to display details like Gnome and Windows? 

Ctrl + 2

> Is there a way to set the App toolbar (Launcher/Dashboard or whatever they call it) to stay on the desktop instead of autohiding?

Install compizconfig-settings-manager and browse about in the Unity plugin. Set it to never hide.

---

### Post by HDTimeshifter on 2011-10-15
Ah, completely missed the Clock tab...

Psst - in the file manager, maybe you guys can add the display by option to the right click menu (where you can select the arrange items order) so it is more intuitive than Ctrl-2...
Also, it always reverts back to icon display when I return to the window.  How do I permanently (or set all windows - like in Windows options) to display details?

Thanks for the quick response.

---

### Post by howefield on 2011-10-15
Open a Nautilus window and navigate through Edit > Preferences menu and from the Views Tab set "View new folders using :" to List View.

---

### Post by HDTimeshifter on 2011-10-15
Ok, so these file windows aren't Nautilus?
Then, I can't seem to find Nautilus in my Dash Home / More Apps or in the Software Center / Installed Apps...

---

### Post by Larkspur on 2011-10-15
> **HDTimeshifter said:**
> I can't seem to find Nautilus in my Dash Home / More Apps or in the Software Center / Installed Apps...

Nautilus is the first icon in the launcher bar, and is listed as "Files" in Installed Apps.

---

### Post by HDTimeshifter on 2011-10-15
Yeah, I've been using Files all along.

So I just figured out the menus have been moved up to where the system menu (toolbar) is.  I thought they had gotten rid of the menus entirely.  Kind of confusing as all other GUIs (Mac, Windows, Gnome) place the app menu within the app window.

---

### Post by HDTimeshifter on 2011-10-16
Is there any way to have the Launcher or Dash home to show a list of most recently used apps?  The Dash home will show a list of most used apps, but I'd like to be able to re-run something I just used that I don't use very often.

---

### Post by ubuntu27 on 2011-10-16
> **HDTimeshifter said:**
> Is there any way to have the Launcher or Dash home to show a list of most recently used apps?  The Dash home will show a list of most used apps, but I'd like to be able to re-run something I just used that I don't use very often.

You can install Zeitgeist-- **Gnome Activity Journal** through Software Center or the Terminal:

```
sudo apt-get install gnome-activity-journal
```


Activity Journal will let you see your activities (which apps and documents did I open on what day?) arranged by time.

---

