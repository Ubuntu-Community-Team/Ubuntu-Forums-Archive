---
title: "GNOME panel applets, systray apps and menu in OpenBox?"
date: 2005-12-16
forum: Desktop Environments
---

### Post by chombee on 2005-12-16
I started using OpenBox (by itself, not as a replacement for metacity in GNOME) and want to know how I can get some stuff that is 'just there' in GNOME to appear in OpenBox, such as:

panel applets like the weather applet, volume control, etc.

systray programs like the Ubuntu update-notifier, the network card and wireless monitors, the laptop battery monitor, etc.

I tried finding what looked like the commands to run some of these things from the System Monitor when logged into GNOME, but the commands don't work when run in a GNOME-Terminal.

I am using PyPanel and Docker with OpenBox, these apps can definitely handle GNOME systray apps if I can only figure out how to launch the apps (GAIM and Tomboy, for example, work fine in the PyPanel or Docker systrays) ... I don't know about the possibility of running GNOME panel apps with them, maybe I need something else.

And lastly - the GNOME menu. Lets face it, it's a useful thing to have every now and then. Is there some way to integrate it into the OpenBox menu? Or some other way to access it from within OpenBox? I installed a package called 'menu' which claims to allow integration of the Debian menu into standardised menus, or something like that, and there is already an entry for it in the OpenBox config file even (a comment even says that the entry depends on the package 'menu'), but nothing new appeared in my menu since installing the package (I have restarted OpenBox).

Thanks,
Sean

---

### Post by psychicdragon on 2005-12-16
You need to run gnome-panel if you want to make use of gnome-panel applets. Syetem tray icons and panel applets can sometimes look similar, but they are in fact entirely different things.

---

### Post by Dr. Nick on 2005-12-16
Just curious on why you dont use it as a replacement to metacity. It seems like it would accomplish the same in the end and be easier to do.

---

### Post by chombee on 2005-12-16
I dunno. I'm using openbox because my laptop has a fairly small screen and is not too fast, I want something snappy and efficient. It seems to me that if I just used ob as a replacement to metacity I'd still have a lot of the slowness of GNOME. I have the feeling that gnome-panel is quite resource intensive.

What do people think? Ob seems faster to me if you run it on its own with pypanel and docker... I guess I might have to give up on the gnome-panel applets, unless there is some gnome-panel replacement I can use, but there *must* be a way to launch those systray applications.

---

### Post by Dr. Nick on 2005-12-16
On my old slow laptop I run openbox to replace metacity and its fairly fast, I have a p2 366 with 128 mb of ram. I dont think their is viable alternative to gnome panel right now. I do know that nautilus is a dog on it sometimes so you might look into a replacement for that.

Have you taken a look at xfce? I am not sure what it has in the way of applets like weather , but I am pretty certain it has a good systray function. PLus xfce is lighter than gnome for most

---

