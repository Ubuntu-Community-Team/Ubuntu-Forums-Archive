---
title: "No desktop environment?"
date: 2011-01-27
forum: Desktop Environments
---

### Post by Skyhawk5421 on 2011-01-27
This may seem like a dumb question, but is there a way to start my computer with no desktop environment? I have xubuntu 10.10 and more often than not I'm doing everything I need to do in the terminal while xfce4 is using precious system resources. 
In my mind there is something similar to autoexec.bat in windows that I could just take a few lines out of, but I know it's never that simple :)

Thanks!

---

### Post by NightwishFan on 2011-01-27
If you do not want to "uninstall xfce" and just use the command line most of the time, at the login screen, simply press "CTRL+ALT+f5" and login there. Then type:
```
sudo stop gdm
```

This will kill Xorg and your display manager and leave with you command line only. To start the login screen again simply type:
```
sudo start gdm
```

If you want to remove xfce and etc entirely it might be easier to just reinstall using the alternate install CD and choosing "Command Line Install" at the boot prompt for it. Or you could try to manually remove Xorg and etc from the command line. I suggest my way above with just stopping the GUI when you do not need it.

Note though that even with a GUI like XFCE running it is likely just using a few mb of RAM while running and not impacting performance much. Only just using the CLI might be overkill unless you have a slow machine.

---

### Post by dileepm on 2011-01-27
Is it that you have to set up your init in run level 5?

---

### Post by ronnielsen1 on 2011-01-27
**[20 Most Nimble and Simple X Window Managers for Linux]("http://www.junauza.com/2008/08/20-most-nimble-and-simple-x-window.html")**

Xubuntu is almost as heavy as gnome or kde IMHO. Here's some alternatives you might also try.

---

### Post by Forlong on 2011-01-27
> **Skyhawk5421 said:**
> This may seem like a dumb question, but is there a way to start my computer with no desktop environment? I have xubuntu 10.10 and more often than not I'm doing everything I need to do in the terminal while xfce4 is using precious system resources. 

By default you are only booting into GDM (GNOME and Xfce's login manager). That's before any desktop environment is loaded.
There should be a terminal-only session available called "Recovery Console".
It will only boot xterm and nothing else for you.

You are able to configure what session you boot into by default in
```
gdmsetup
```
(that's a graphical interface)

Hope this helps.

---

### Post by sisco311 on 2011-01-27
> **Skyhawk5421 said:**
> This may seem like a dumb question, but is there a way to start my computer with no desktop environment? I have xubuntu 10.10 and more often than not I'm doing everything I need to do in the terminal while xfce4 is using precious system resources. 
In my mind there is something similar to autoexec.bat in windows that I could just take a few lines out of, but I know it's never that simple :)

Thanks!

You can disable the display manager (*login screen*) in many ways. The preferred method is to boot with the **text** kernel parameter. You have to edit /etc/default/grub and replace **GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"** with **GRUB_CMDLINE_LINUX_DEFAULT="quiet splash text"**. 
Then generate a new Grub2 config file:
```
sudo update-grub
```

You can remove the **quiet** and **splash** kernel parameters in order to make the boot process verbose and disable the boot screen.

Once logged in you can start the gui with:
```
startx
```

---

### Post by Skyhawk5421 on 2011-01-27
Thanks for all the replies, but none have worked perfectly. The closest I got was adding "text" into the configuration file and updating grub. When it boots it will sit there forever unless I press alt+ctrl+F1. 

Also, startx starts xfce, is there any way to start an xubuntu session from the command line?

---

### Post by sisco311 on 2011-01-28
> **Skyhawk5421 said:**
> Thanks for all the replies, but none have worked perfectly. The closest I got was adding "text" into the configuration file and updating grub. When it boots it will sit there forever unless I press alt+ctrl+F1. 


Did you try to disable the splash screen?

> **Skyhawk5421 said:**
> 
Also, startx starts xfce, is there any way to start an xubuntu session from the command line?

I think you can change the default session with:
```
sudo update-alternatives --config x-session-manager
```

HTH

---

