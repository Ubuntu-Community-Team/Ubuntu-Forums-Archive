---
title: "copy paste files from desktop to nautilus/files ubuntu 21.10"
date: 2021-10-12
forum: Desktop Environments
---

### Post by Claus7 on 2021-10-12
Hello,

I made an upgrade to ubuntu 21.10 and what I noticed is that copy/paste files directly from Desktop to other folders of nautilus do not work under ubuntu gnome shell wayland/xorg. For ubuntu flashback this is a requested feature for more than a year. 

For gnome-shell I searched the forums and I noticed that there is a built-in extension that enables desktop icons and copy paste capabilities. In my upgraded system such an extension does not exist. Also, I came across an extension in gnome-shell extensions that does exactly this, yet installing it did not allow me to copy paste files from desktop. Copy-paste option is there, yet when I try to paste, the word is grayed out. 

My question is: can you copy paste files directly from or to the desktop by right clicking on a file selecting copy and then right clicking and selecting paste wherever you want to paste that file or that feature is entirely gone from ubuntu 21.10?

Regards!

---

### Post by Dennis N on 2021-10-12
Using Ubuntu 21.10, I coundn't duplicate the problem.

1) Saved a test file to the Desktop folder.
2) Opened Files to Desktop folder.
3) Rt-click on saved file, and select copy.
4) Navigate in Files to home folder.
5) Rt-click paste.
6) file copied successfully.
7) pasted to a different destination folder - it still works.
8) paste TO the Desktop also works.

A difference: I'm using Xorg, so that may be it.
Try with Xorg session and see if you still have this issue.

---

### Post by grahammechanical on 2021-10-12
The Gnome developers do not want icons on their Gnome3 shell desktop. The Ubuntu developers have created a Gnome shell extension that allows icon to be put on the Desktop. It is enabled by default.

On the 21.10 desktop there is a folder icon called Home. Drag and drop a file or document on to that folder icon and the file is copied into the user's home folder. Open that Home folder and drag and drop the file onto the folder icon called Desktop and the file will appear in the top left corner of the screen that we call the desktop.

The same can be achieved using the file manager's "copy to" function. Any document in the Home/Desktop folder will appear on the desktop. The file manager of 20.04 lists Desktop with the other folders in its left hand panel. But the file manager for 21.10 does not list Desktop as a folder in that left hand panel. But the Desktop folder still exists.

The windowing system on my 21.10 is Wayland.

Regards

---

### Post by Claus7 on 2021-10-12
Hello,

first of thank you *Dennis N* and *grahammechanical* for your responses.

Now concerning your answers:

> **Dennis N said:**
> ...

1) Saved a test file to the Desktop folder.
2) Opened Files to Desktop folder.
3) Rt-click on saved file, and select copy.
4) Navigate in Files to home folder.
5) Rt-click paste.
6) file copied successfully.
7) pasted to a different destination folder - it still works.


So far so good. Up to now the process is copy/paste-ing while having the nautilus (aka Files) open and navigating in different folders including the desktop folder as well.

> **Dennis N said:**
> 
8) paste TO the Desktop also works.


I think that with this one you can copy paste directly to the Desktop itself and not just to the desktop inside Files. This is not working in my system.

> **Dennis N said:**
> 
A difference: I'm using Xorg, so that may be it.
Try with Xorg session and see if you still have this issue.
Thank you for that, I have tried both wayland and xorg.

> **grahammechanical said:**
> The Gnome developers do not want icons on their Gnome3 shell desktop. The Ubuntu developers have created a Gnome shell extension that allows icon to be put on the Desktop. It is enabled by default.

I think that flashback does not use gnome3 shell desktop, yet just gnome3. Still this change affects flashback as well. For ubuntu gnome (either wayland or xorg) the built in extensions displayed are the following:
[LIST]
[*]Applications Menu
[*]Arc Menu (not working)
[*]Auto Move Windows
[*]Draw on You(r) Screen
[*]Launch new instance
[*]Move Clock (not working)
[*]Native Window Placement
[*]OpenWeather
[*]Places Status Indicator
[*]Removable Drive Menu
[*]Screenshot Window Sizer
[*]Ubuntu AppIndicators
[*]Ubuntu Dock
[*]User Themes
[*]Window List
[*]windowNavigator
[*]Workspace Indicator
[/LIST]

The extension I installed extra for Desktop icons was: Desktop Icons: Neo.
[EDIT2]: Checking synaptic package manager I was able to find a package about desktop extension which I installed and the name appearing to extensions is Desktop Icons NG (DING). Still no copy paste from/to Desktop.

> **grahammechanical said:**
> 
On the 21.10 desktop there is a folder icon called Home. Drag and drop a file or document on to that folder icon and the file is copied into the user's home folder. Open that Home folder and drag and drop the file onto the folder icon called Desktop and the file will appear in the top left corner of the screen that we call the desktop.

I have not such a folder icon. Disabling the Desktop Icons: Neo extension, no folder or icon appears on the Desktop.

> **grahammechanical said:**
> 
The same can be achieved using the file manager's "copy to" function. Any document in the Home/Desktop folder will appear on the desktop. The file manager of 20.04 lists Desktop with the other folders in its left hand panel. But the file manager for 21.10 does not list Desktop as a folder in that left hand panel. But the Desktop folder still exists.

The windowing system on my 21.10 is Wayland.

Regards

The first time I did not have the Desktop folder in the left hand panel as well. Yet, tampering with dconf it showed up again. 
[EDIT]: In ubuntu wayland, Desktop is not present. In ubuntu xorg it is.

As a result copy paste (both) from Desktop (and Desktop folder inside Files) is working in ubuntu 21.10 which, by default has a home folder icon on Desktop. 

Thank you for your input,
Regards!

---

### Post by vanadium on 2021-10-13
Make sure you have the extension "gnome-shell-extension-desktop-icons-ng"  (Desktop Icons New generation) installed and enabled. This is the one that is used by default since Ubuntu 21.04.

---

### Post by Claus7 on 2021-10-13
Hello,

> **vanadium said:**
> Make sure you have the extension "gnome-shell-extension-desktop-icons-ng"  (Desktop Icons New generation) installed and enabled. This is the one that is used by default since Ubuntu 21.04.

thank you for the input. For some reason, copy paste still is not working. I checked also file and folder permissions in case they had something to do with it, but they are fine. At least I know that this feature is not deprecated and there is something wrong which I have to fix.

Regards!

---

### Post by Dennis N on 2021-10-13
> My question is: can you copy paste files directly from or to the desktop by right clicking on a file selecting copy and then right clicking and selecting paste wherever you want to paste that file or that feature is entirely gone from ubuntu 21.10?

In my post #2, I was working with file manager windows. Now I see that is not what you meant here. I tried this again, using the file manager window only to do the paste of the file. It is exactly as you say - the copy is allowed, but the paste is not - that option is greyed out.

We do know that the default gnome behavior is not to have icons visible over the background. The extension allows the display, but apparently it's not entirely functional for the copy/paste without using the Files windows. It is possible to open files from the icons - that is probably the way it was envisioned for use.

Tested with Ubuntu 21.10.

---

### Post by Claus7 on 2021-10-13
Hello,

> **Dennis N said:**
> In my post #2, I was working with file manager windows. Now I see that is not what you meant here. I tried this again, using the file manager window only to do the paste of the file. It is exactly as you say - the copy is allowed, but the paste is not - that option is greyed out.

We do know that the default gnome behavior is not to have icons visible over the background. The extension allows the display, but apparently it's not entirely functional for the copy/paste without using the Files windows. It is possible to open files from the icons - that is probably the way it was envisioned for use.

Tested with Ubuntu 21.10.

thank you very much for your clarification. I will mark this thread as solved.

Regards!

---

