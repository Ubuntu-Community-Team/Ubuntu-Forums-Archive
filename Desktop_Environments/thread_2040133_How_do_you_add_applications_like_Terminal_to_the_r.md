---
title: "How do you add applications like Terminal to the right click menu?"
date: 2012-08-10
forum: Desktop Environments
---

### Post by nezeray on 2012-08-10
I'm new to Unity and miss having Terminal available when I right click on the desktop.  Is there an easy way to add applications to that menu?  

Thanks!

James / Nezeray

:popcorn:

---

### Post by irv on 2012-08-10
If you are running Ubuntu with Unity and you are referring to the launch area from the Dash, then just run terminal and while it is running right click on the icon in the launch and lock it to the launch. Then when you close the terminal the icon will remain in the launch.

---

### Post by nezeray on 2012-08-10
I've done that.  What I mean is when you're actually in the center of a workspace, and right click.  You get "Create New Folder", Create New Document"... "Change Desktop Backgroud".   I want to be able to open a terminal from there.

I don't want to have to keep going back over to the Launcher to run it.  If there's a shortcut key combo that may work too.

James / Nezeray

---

### Post by vasilbelarus on 2012-08-10
If you lock any applycations on Dash(left panel) then you can open them by shortcut key Win+1...9.
Press and held Win and you will see much more shortcuts

---

### Post by vasilbelarus on 2012-08-10
Ctrl+Alt+T for terminal is also awailable by default.

---

### Post by Kalanac on 2012-08-10
With dash you can also hit the superkey (the one typically labelled with the windows logo) and type the name of the application.  When it's the first or only option hit enter and it'll run.

---

### Post by irv on 2012-08-10
> **vasilbelarus said:**
> Ctrl+Alt+T for terminal is also awailable by default.

Agree: this is the best way to do it. This is what I use.

---

### Post by nezeray on 2012-08-10
Thanks!  Those suggestions help!

James / Nezeray

---

### Post by Kalanac on 2012-08-10
Don't forget to mark solved :)

---

### Post by bcschmerker on 2012-08-11
> **vasilbelarus said:**
> Ctrl+Alt+T for terminal is also awailable by default.
Just what I need for my eMachines®/Acer® EL1210-09 with Shuttle® PC6300002 PSU and Asus® EN210/DI/512MD2(LP) upgrades.  I recently installed 12.04-LTS and have to install additional Packages specific to nVIDIA® hardware in order to bring the planar GeForce® 9200 online as a secondary display adapter; the Live/Install DVD recognized the GeForce® 210 and not the 9200. :-k Thanks for the tip on a needful hotkey.

---

### Post by irv on 2012-08-11
> **bcschmerker said:**
> Just what I need for my eMachines®/Acer® EL1210-09 with Shuttle® PC6300002 PSU and Asus® EN210/DI/512MD2(LP) upgrades.  I recently installed 12.04-LTS and have to install additional Packages specific to nVIDIA® hardware in order to bring the planar GeForce® 9200 online as a secondary display adapter; the Live/Install DVD recognized the GeForce® 210 and not the 9200. :-k Thanks for the tip on a needful hotkey.

Another quick tip: if you just press and hold down the super key it will bring up a list of many other hot keys.

---

### Post by hakermania on 2012-08-11
Another quick tip: you can use this guide so as to create/append/edit launchers to/from the unity sidebar: [https://help.ubuntu.com/community/UnityLaunchersAndDesktopFiles](https://help.ubuntu.com/community/UnityLaunchersAndDesktopFiles)

---

### Post by Kleenux on 2012-08-12
Finally using Unity (on a new fresh 12.04).

Opened an application, right click on icon in Dash, and no "Lock to launcher" in the menu.

Is there any other *simple* way to add an application to the launcher?

---

### Post by deadflowr on 2012-08-12
> **Kleenux said:**
> Finally using Unity (on a new fresh 12.04).

Opened an application, right click on icon in Dash, and no "Lock to launcher" in the menu.

Is there any other *simple* way to add an application to the launcher?

Drag 'em from the dash screen. You can also rearrange the icons in the launcher, to suit your needs.(All except the dash, workspace switcher, trash ,and any removable media icons.
I don't think I opened and then locked any of my launcher items, I've just always dragged 'em over, once added they're automatically locked in.
And know that if you don't want an app in the launcher anymore, just drag into the trash.

---

### Post by Kleenux on 2012-08-13
> **deadflowr said:**
> Drag 'em from the dash screen. You can also rearrange the icons in the launcher, to suit your needs.(All except the dash, workspace switcher, trash ,and any removable media icons.
I don't think I opened and then locked any of my launcher items, I've just always dragged 'em over, once added they're automatically locked in.
And know that if you don't want an app in the launcher anymore, just drag into the trash.

Well, tried that. The application is a bash script, and it doesn't appear in Dash Search. So the "Drag" thing doesn't work (believe me, tried all possible combinations).

Tried also to add a .desktop to ~/.local/share/applications, with all the required options => didn't work for some reasons (yes, logged out, rebooted....).

Finally got it to work, after installing "Main menu" (alacarte), adding the app to the Gnome "menu", allowing Dash Search to see it. Then dragged to the Dash bar.

Wow. Seriously, do you think all this gymnastics to simply add an icon to the launcher will help Ubuntuers to forget about Gnome Classic? (which has other flaws, I admit)

The right-click is very sober: not even Properties to change icon or path or options etc... 

I like the waddling icon and all but come on...

---

