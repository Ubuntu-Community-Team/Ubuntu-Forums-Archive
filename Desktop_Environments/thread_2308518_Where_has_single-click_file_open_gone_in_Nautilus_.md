---
title: "Where has single-click file open gone in Nautilus 3.14.2?"
date: 2016-01-03
forum: Desktop Environments
---

### Post by john-w-bales on 2016-01-03
I switched to Linux in 1999 and have been using single-click to open files ever since. Just switched from Ubuntu 15.10 to Ubuntu Gnome 15.10 only to discover that one can no longer switch from the default double-click to single-click file open using File > Preferences.  There also is nothing in the tweak tool which enables one to select single-click. All I have found in a two hour search of the forums and the web are instructions referring to earlier versions of Nautilus.

Does anyone know of a solution to this conundrum?

---

### Post by deadflowr on 2016-01-03
I thought the preferences option was built into the title bar for gnome/nautilus, but perhaps I'm thinking of something else.

Maybe try gsettings or dconf.
What does
```
gsettings get org.gnome.nautilus.preferences  click-policy
```
give you?

If anything, then what about
```
gsettings range org.gnome.nautilus.preferences  click-policy
```
does it still list single and double as options?
If so, then try using set to change it to single
```
gsettings set org.gnome.nautilus.preferences  click-policy single
```
does that do anything?

---

### Post by Tadaen_Sylvermane on 2016-01-04
On the top bar right click the title next to Activities when you have Nautilus open, think it's Files now. The preferences are there. They claim Gnome is intuitive, doesn't seem that way to me :/

---

### Post by deadflowr on 2016-01-04
> **Tadaen_Sylvermane said:**
> On the top bar right click the title next to Activities when you have Nautilus open, think it's Files now. The preferences are there. They claim Gnome is intuitive, doesn't seem that way to me :/

Good point.
Though you would only need to left click the Files entry.
It's has a setting in tweak tool in the "top bar" section.
It needs to have the show application menu turned to on.

---

### Post by buzzingrobot on 2016-01-04
> **deadflowr said:**
> Good point.
Though you would only need to left click the Files entry.
It's has a setting in tweak tool in the "top bar" section.
It needs to have the show application menu turned to on.

Hmm.  I just toggled that off, restarted the shell, and menus were where they belong, up in the top panel. The OP's setting is in Files->Preferences->Behavior.

(Intuitive -- A nine-letter word meaning "I already know how to do that!") ;)

---

### Post by deadflowr on 2016-01-04
> **buzzingrobot said:**
> Hmm.  I just toggled that off, restarted the shell, and menus were where they belong, up in the top panel. The OP's setting is in Files->Preferences->Behavior.

(Intuitive -- A nine-letter word meaning "I already know how to do that!") ;)

The op seems to be having an opposite reaction.
Or something.
Status is unknown since the initial post...

---

### Post by john-w-bales on 2016-01-05
There are no menus in the top-bar of a Nautilus window identified by names. No File menu, no Activities menu. There are icons representing: Search, View by list, View as icons, View options and Location options. On the Location options drop down menu is a Preferences but single-click is not an option. There is nothing in the top bar of Nautilus or any of the drop down menus pertaining to single or double click to open files. I am including a picture it that is allowed. I shortened the window but there are no named menus even when the window is maximized.
[IMG]http://jwbales.us/NautilusWindow.png[/IMG]

---

### Post by john-w-bales on 2016-01-05
Thank you Deadflowr, This did the trick:  gsettings set org.gnome.nautilus.preferences click-policy single 
I'm not sure why they did not give a non-command line method to switch to single-click. I've been using the unix/linux command line for decades but have gotten spoiled by the GUI environment.

---

### Post by qamelian on 2016-01-05
The Activities menu is at the very left of the Gnome panel in Gnome-shell, not in the title bar of the application, which is what you show in your screenshot. When Nautilus is open, the File menu appears immediately to the right of Activities menu. In the File menu, is the Preferences item, which includes the setting you are looking for, in the Behaviour tab. This is the way application menus work now in native Gnome 3 applications. So, there really is a GUI method and no need to resort to the command line.

---

### Post by buzzingrobot on 2016-01-06
> **john-w-bales said:**
> There are no menus in the top-bar of a Nautilus window identified by names...

In Gnome Shell, 3.14 and otherwise, application menus are global, meaning they are displayed in Gnome's panel, not in the individual application.  E.g, launch Files and the word "Files" appears on the left of the panel. Click it and the drop-down menu that is displayed contains an entry for "Preferences", which contains the option to choose single-click. 

If you are not seeing those global menu entries in the panel, something may be wrong with your Gnome install.

Menus in Unity are also global, but, depending on release version, may be configured to display within the application.

---

