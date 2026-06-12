---
title: "Compiz adds hover-tooltips to main panel"
date: 2015-12-01
forum: Desktop Environments
---

### Post by Megadoomer on 2015-12-01
Hello everyone,

I installed Compiz with additional plugins and Metacity as the compositing- and window manager on my XFCE desktop. Now, every time I hover my mouse pointer over an element that displays a tooltip, this tooltip "frame" will be added to my main panel with its own icon and tab as if it was an autonomous window.

Example: I open the Amarok music player and its wolf icon is displayed in my panel, I hover over a song name, the song info will be displayed as a tooltip next to my mouse pointer and a second, greyed-out wolf icon is displayed next to the main Amarok icon. As soon as the mouse pointer leaves the tooltip area, the icon disappears from the panel as well.

While not being a harmful issue, this behaviour is quite annoying and can sometimes be irritating when not expecting a new window to pop up in the main panel suddenly.

This also only seems to happen when the grey- or beige-coloured tooltips are displayed. If the tooltips are displayed in a white font on black background, there is no icon added to the panel, but not all other applications show this issue, such as VLC for example.

I am not sure where to begin looking for a solution, so I would be very glad if you could give me a hint or know Compiz and XFCE very well and know a solution for this.


Kind regards!

---

### Post by deadflowr on 2015-12-01
Understanding that compiz and metacity do not run at the same time:
[http://askubuntu.com/questions/24977/why-does-ubuntu-use-two-window-managers-compiz-and-metacity](http://askubuntu.com/questions/24977/why-does-ubuntu-use-two-window-managers-compiz-and-metacity)
to get that out of the way...

What plugins have you enabled in compiz?

---

### Post by Megadoomer on 2015-12-02
> **deadflowr said:**
> Understanding that compiz and metacity do not run at the same time:

Oh okay, I have used [this guide]("http://www.webupd8.org/2012/11/how-to-set-up-compiz-in-xubuntu-1210-or.html") do install and set up Compiz, I wasn't aware of how the programs interact exactly.

> **deadflowr said:**
> What plugins have you enabled in compiz?

Those would be:

General - Composite, Gnome Compatibility, OpenGL
Desktop - Cube, Expo, Rotate Cube, Viewport Switcher
Effects -  3D Windows, Animations, Fade Windows, Window Decoration (gtk-window-decorator with Metacity set to Greybird theme)
Image Loading - PNG
Utility - Compiz Library Toolbox, Mouse position polling, Regular Expressions
Window Management - Application Switcher, Place Windows, Move Window, Resize Window, Grid

Those should have the basic settings, all I changed were some window animations when minimizing/maximizing and set vertical workspaces and a skybox for the cube. I am not really sure where to look for a suspicious setting, but most of it should be on default.

If this could be a problem with Metacity or the window decoration, I could also try to change that. Originally, I wanted to keep the XFCE window decorator, but I was not sure if it would work, that's why I followed the method from the guide above.

---

