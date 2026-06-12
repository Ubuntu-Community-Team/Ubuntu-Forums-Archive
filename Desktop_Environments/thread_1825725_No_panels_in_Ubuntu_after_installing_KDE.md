---
title: "No panels in Ubuntu after installing KDE?"
date: 2011-08-15
forum: Desktop Environments
---

### Post by Shbek on 2011-08-15
So I'm trying to have both Gnome and KDE desktop environments available on my laptop, easy, right? Well, apparently not....

On a fresh install of Kubuntu 11.04 I installed all the system updates and my graphics driver. Everything worked fine. Then I did:

> sudo apt-get install ubuntu-desktop 

To get Gnome. Everything completed just fine, then I logged out, selected Gnome (I believe they call it Ubuntu in the menu, but whatever), logged in, and was greeted by... a wallpaper. That's literally it. I can right click and get the Gnome menu, but there aren't any panels or anything. The KDE environment is still working just fine.

I tried a few things, I don't remember all what now, I was following a thread of a similar problem, but I guess the guy had a load of dependency problems due to random uninstalling, so most solutions didn't exactly apply. Anyway, I ended up installing Ubuntu 11.04, Everything worked fine, got my updates and whatnot. Then I installed kubuntu-desktop. Logged into KDE, everything worked fine. Logged back into Ubuntu, and magically the panels are gone again. 

Am I missing something, or what? Any ideas/suggestions? 
I used this exact method a few years back on a desktop. I think with Ubuntu 8.04, and it worked flawlessly. 

This really isn't a major problem as I use Kubuntu primarily. I just thought it would be cool to mess with Ubuntu occasionally.

Edit: Oh, I can right click, select create launcher, then navigate to usr/lib and such to make an icon on the desktop to start programs. How I managed to post this actually. Although I can't use Terminal because I get 
> There was an error creating the child process for this terminal
Failed to execute child process "/usr/share/app-install/desktop/Terminal.desktop" (Permission denied)

---

