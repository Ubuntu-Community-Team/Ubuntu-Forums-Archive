---
title: "General KDE problem"
date: 2006-02-28
forum: Desktop Environments
---

### Post by livingtarget on 2006-02-28
Well i've switched from gnome a while back, because i personally liked the KDE programs more. Amarok, Kopete, Kwin etc.

I still have a couple of things that bug me.

First I want to run a couple of commands when kde starts, for example:
nvidia-settings, firestarter, script to launch my internet connection, gnome-settings-daemon and so on.

I remember in gnome you could add programs through a session interface and just pop them in there. In kde I tried kcron first, but it didn't really work. I've got it working now with the kde autostart folder, but it starts asking passwords all the time and shows up in the task bar as loading which i'd rather have hidden.

Any kde interface that i've overlooked for this?

Secondly i still dislike my Konqueror browser. It's mainly filebrowsing and the interface takes a while to get to my liking. I'd like the split bar to auto hide to the side, but i know that's a tough ask.

I dislike the way it's a browser and file browser. I mean it's got a home button which goes to the home folder by default. When I go browse i'd like it to switch to my internet home page not press home and go to my home folder again. So I cut my losses and set it to my internet home page.

---

### Post by Jucato on 2006-02-28
How about trying to setup your desktop the way you like it (run the programs that you want to be run at start up), then save the session through session manager: KControl/System Settings > KDE Components > Session Manager. Also, doesn't firestarter (or guarddog, it's KDE equivalent) have settings to let it start on startup? If your internet connection is DSL, pppoeconfig would let you decide whether to start it up on boot. As for nvidia-settings, why do you want to have it start up when you log in? 

Konqueror issues: after a few tinkering around, I think you'll find Konqueror to be one of the most customizable apps in KDE. not only can it be your file manager or browser, it can also be your document reader (not editor), give you sound/video previews, etc. But anway:
1. what split bar are you talking about? do you mean the navigation panel? If it is, it remembers the last setting you left it when you closed the Konqueror window. If it's hidden at the side, it will be hidden when you open another window. Also, you can hide/unhide that panel by pressing F9.
2. I guess you've figures out how to change the Home page? Settings > Configure Konqueror > Behavior > Home URL. If you want Konqueror to start up on your Home URL whenever you open it, you can do this: display your Home Page, then Settings > Save View Profile "what ever profile you are using" > make sure that "Save URL's in Profile" is enabled > Save.

Hope that helps a bit.

---

### Post by livingtarget on 2006-02-28
Thanks for the advice, it's just taking a bit longer to set up then I thought it would. "KControl/System Settings > KDE Components > Session Manager" is probably what i was looking for.

I'll have a look at guard dog, probably better using that.

I'm running 'nvidia-settings --load-config-only' to set my Anti Alias settings (x2) for games as it doesn't seem remember that normally.

---

### Post by ajgreeny on 2006-02-28
You can also add links to programs (and I presume scripts) to the .kde/Autostart folder in your home folder.

---

### Post by Jucato on 2006-02-28
Well, KDE is generally known to have more options upfront compared to GNOME, so wading through those menus, tabs, and configs can be a bit daunting at first. But not really that hard. Kubuntu is my first ever distro, and there are still a lot I need to learn. :D

---

### Post by MartinG on 2006-02-28
Even if you use the session manager suggestion you'll still be asked for passwords for any program that runs as root.  It's a security feature; you could run chown on the relevant programs, but that would leave a big security hole.

Once Firestarter has been set up, your firewall will automatically start whenever you start the computer.  You only need to run Firestarter itself if you want to change the settings, so I'd advise against having it autostart.

---

### Post by niviche on 2006-02-28
[QUOTE=livingtarget]First I want to run a couple of commands when kde starts, for example:
nvidia-settings, firestarter, script to launch my internet connection, gnome-settings-daemon and so on.

I remember in gnome you could add programs through a session interface and just pop them in there.[/QUOTE]

I use [this](http://www.kde-apps.org/content/show.php?content=35038), and it works just fine.

---

### Post by livingtarget on 2006-02-28
I was running v0.1 (that is an old version from the repositories) of auto start just now and it looks like this will do fine. It's a bit buggy as in adding a new item and pressing cancel all the way through still adds a new item. Anyhow i'll try v0.2 when I get back home.

---

### Post by msak007 on 2006-02-28
Hmm I'll have to give this a try. I was also looking for something like the Ubuntu startup manager ever since I switched to Kubuntu. Saving the session seems to work for most everything, but for the life of me I can't get AMSN to start up with the session even if I save it with the app running. Maybe this'll do the trick. Thanks for the tip.

---

