---
title: "Help: blender 3D dual screen setup"
date: 2008-01-26
forum: Desktop Environments
---

### Post by L14UX_1NS1D3 on 2008-01-26
Hello everyone!

I have sort of a an wierd setup with my computer. I have an nvidia 6200 GPU with a VGA and DVI port. Currently I have a large 17" CRT hooked up via VGA. This screen is running at 1600x1200. Just yesterday I was given an old flatpanel LCD screen with a max res of  1024x768. This other screen I plugged into the DVI.

I fired up the gnome "screens and graphics" from the control panel. I didn't have much luck with that. instead I went with setting up the monitor by invoking "nvidia-setting". because I am running the two screens different resolutions. I was getting some weird effects when I tried setting it up as an extended desktop. But after mucking about with the settings I was finally able to get the extra monitor working as separate screen. It's pretty cool, now it like I have two different computers. the extra screen has its own configurations such as the desktop bars and such. except when I change the wallpaper on either desktop they both change and when I run compiz on the 17" , the smaller screen does not run compiz. when I start up compiz from the smaller screen, both screen switch to the excelerated window manager. I also can't drag window between the two monitors . 
Now what I would to know is how I could possibly run blender on both screens. the large screen being the main window for modeling, posing etc. with this dual screen setup. have this extra screen just for regular computer tasks has added flexibility in workflow and productivity that I didn't expect. This is yet another reason why I love Linux and just enforces my devotion to ... Ubuuunnntuuuu!!

so if anyone has some good Ideas in how I might get this to work it I would be more than greatful and if anyone has any connections with a website or forum for blender. Maybe the question could be posted there as well

Thanks to all!

---

### Post by thedaemon on 2008-01-26
[www.blenderartists.org](www.blenderartists.org) is the best forum I know for blender. That being said, glad to see other blender users here. Have you tried scaling blenders window? I know the windowed mode menu button isn't properly configured by default. If you don't know how to fix it. Goto System/Preferences/Main Menu/ then goto graphics and right click on blender window mode and bring up the properties menu. "blender -p 50 50 1280 1024" this is what I have by default minus the quotes. This starts a blender window at 50 pixels down and 50 pixels across from the upper left of the screen 1280x1024 size. Maybe you can do this then stretch the window on the other monitor? I only have one 24" monitor so I just use one monitor. Also, compiz may hinder OGL performance with 3d applications. Hope I've helped.

---

