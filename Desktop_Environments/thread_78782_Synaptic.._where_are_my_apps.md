---
title: "Synaptic.. where are my apps?"
date: 2005-10-18
forum: Desktop Environments
---

### Post by BRODEL on 2005-10-18
So, I was browsing around synaptic and the web looking for some cool apps to put on my new ubuntu laptop. I install a few (thunderbird, firestarter, xmms, vlc.. etc) anyway, the only one I can find is thunderbird. It's under applications -> internet

How do I know where synaptic puts my applications or shortcuts to them? :confused:

Edit: Just found vlc too.. Applications -> sound and video

---

### Post by Dr. Nick on 2005-10-18
You really dont and sometimes you just have to look, though if you right click and hit properties/installed files on the program in synsptic you can see where everything went. look for /usr/bin/"Usually-program-name" if you want the command to launch it from a terminal or make your own shortcut if it didnt make one or you cant find it anywhere. 

If you want to re-arrange the menus use "smeg" i'll tell you where that shourtcut is :)
Applications-System Tools- Applications menu editor

---

### Post by aysiu on 2005-10-18
Sometimes you have to refresh the Gnome panel to get the shortcuts to appear ```
killall gnome-panel
```

---

### Post by BRODEL on 2005-10-18
[QUOTE=Dr. Nick]You really dont and sometimes you just have to look, though if you right click and hit properties/installed files on the program in synsptic you can see where everything went. look for /usr/bin/"Usually-program-name" if you want the command to launch it from a terminal or make your own shortcut if it didnt make one or you cant find it anywhere. 

If you want to re-arrange the menus use "smeg" i'll tell you where that shourtcut is :)
Applications-System Tools- Applications menu editor[/QUOTE]
Dude, you rock!

Firestarter was in /user/sbin is that normal? I don't know the differences of these places I'm used to em all being in C:\Program Files :(

Anywho, I think that will help me with most of my issues when it comes to that. Thanks. 

[QUOTE=aysiu]Sometimes you have to refresh the Gnome panel to get the shortcuts to appear [/QUOTE]

Thanks for the tip :)

---

### Post by Dr. Nick on 2005-10-18
My firestarter is in sbin aswell, I guess its normal , I dont really know the difference either between bin/sbin, havent really needed to. Unlike windows if you use the command line you ususally dont have to be in the directory the program is installed in to launch it, unless its in your home directory. Most apps these days have gotten good about making shortcuts, It wasnt always like that though.

---

### Post by BRODEL on 2005-10-18
Well the shortcut I made for firestarter is usless anyway since you have to sudo to run it anyway. I'll just run it from the command line. No biggie. Thanks again.

---

### Post by Dr. Nick on 2005-10-19
[QUOTE=BRODEL]Well the shortcut I made for firestarter is usless anyway since you have to sudo to run it anyway. I'll just run it from the command line. No biggie. Thanks again.[/QUOTE]

Hehe if you want to get clever use ```
gksudo firestarter
``` and it will give you a password dialog then run once you enter it correct.

---

### Post by anil_robo on 2005-10-19
[QUOTE=Dr. Nick]Hehe if you want to get clever use ```
gksudo firestarter
``` and it will give you a password dialog then run once you enter it correct.[/QUOTE]

I feel firewall is an essential component of system connected to the internet. So I make sure Ubuntu runs firewall at bootup. I did this the following way:

1. System --> Preferences --> Sesssions
2. Choose last tab (Startup Programs)
3. Click "add"
4. In the new dialog box that opens, type "gksudo firestarter"
Don't worry about the order - default is 50 anyway and it hardly matters.
5. Now close this window and restart your computer.

When you log in, you will see firestarter popping up and asking you for password. Give it your user password, and it will start.

Sometimes, I've noticed that if the network is not ready, firestarter gives errors. So what I do, I just let firestarter wait for 2 mins and then I enter the password.

Works for me, should work for everyone! :)

---

### Post by dolphinsonar on 2006-12-13
> **aysiu said:**
> Sometimes you have to refresh the Gnome panel to get the shortcuts to appear ```
killall gnome-panel
```

Once again, your help is invaluable.  Thanks.

---

### Post by mcduck on 2006-12-13
By default Firestarter doesn't go to the Applications menu, but instead to System/Administartion.

And you *don't need to have Firestarter running all the time*!

It's just a graphical too to control the actual firewall that is a built-in feature of the Linux kernel. The firewall will be started on boot automatically way before you even get to log in to your machine. In fact it's safer to *not* have Firestarter open when you're not making changes to your firewall settings.

---

