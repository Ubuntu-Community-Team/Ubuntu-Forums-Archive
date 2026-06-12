---
title: "VNC server for ubuntu"
date: 2009-03-13
forum: General Help
---

### Post by sdwinder on 2009-03-13
Hi, I am trying to make ubuntu desktop accessible via vnc viewers which will be run from windows machines, the windows machines are using realvnc variants (anything from tightvnc to ultravnc), i managed to get the connection going (In ubuntu i just used the built in remote desktop feature, i think its vino) but when the screenloaded, the mouse was non responsive, and the screen was not refreshing. I made sure of this because i was looking at the ubuntu machine at the time, the only thing that seemed to work was the click functions of the mouse, the mouse was stuck in the top left corner so when i clicked the menu opened, but it never refreshed the window on the windows machine to show that the window opened.
Now ive heard that when using vnc in ubuntu, it starts a new x window session, I am wondering if there is a way to get the functionality of a regular windows machine running a vnc server, as in being able to control the same x window session, and if there is anyway to fix the non refresh


On a side now, i tried installing tightvnc server in ubuntu, it installed successfully, but it never installed any menu items or anything, so i have no idea how to launch it.

---

### Post by HermanAB on 2009-03-13
VNC is primarily a Windows thing and is almost always the *wrong* solution for Linux.

You would do much better by installing ssh-server on Linux and Xming with PuTTY on Windows. You can run any X program over SSH and can go click happy by running the Gnome taskbar:
$ ssh -X -C -c blowfish user@server gnome-panel

Cheers,

Herman

---

### Post by sdwinder on 2009-03-13
unfortunately the program has to be a VNC program for the person connecting to the linux machine, its important to the point where if it wont work, i will need to scrap linux and just install windows.

---

