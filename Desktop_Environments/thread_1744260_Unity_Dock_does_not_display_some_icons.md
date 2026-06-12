---
title: "Unity Dock does not display some icons"
date: 2011-04-30
forum: Desktop Environments
---

### Post by Simoo on 2011-04-30
Hi,

Sometimes when adding an application link to the Unity dock it does not display an icon in the dock, just a blank space.

An example would be the image manipulation app 'Pinta'. Installing this from the Ubuntu Software Centre, finding it in the apps menu and dragging it to the Unity dock results in a blank space being put in the dock.

I am happy to report a bug but can anyone explain why this happens?

Temporary work around for anyone with this problem:

1. Create a launcher for the app on the desktop
2. Move the launcher to ~/.local/share/applications
3. Drag it to the dock from there

---

### Post by gonto on 2011-05-07
> **Simoo said:**
> Hi,

Sometimes when adding an application link to the Unity dock it does not display an icon in the dock, just a blank space.

An example would be the image manipulation app 'Pinta'. Installing this from the Ubuntu Software Centre, finding it in the apps menu and dragging it to the Unity dock results in a blank space being put in the dock.

I am happy to report a bug but can anyone explain why this happens?

Temporary work around for anyone with this problem:

1. Create a launcher for the app on the desktop
2. Move the launcher to ~/.local/share/applications
3. Drag it to the dock from there

I'm having that same problem.

I have a launcher in my desktop with the right icon (I checked in the file via vim that it's ok) I D&D to Unity DockBar and the icon dissapears

---

