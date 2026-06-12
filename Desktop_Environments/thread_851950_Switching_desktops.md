---
title: "Switching desktops"
date: 2008-07-07
forum: Desktop Environments
---

### Post by josephmo on 2008-07-07
How do I know which desktop I have? and how do I switch desktops?

---

### Post by rogier.de.groot on 2008-07-07
What do you mean by desktop? Like Gnome, KDE, XFCE?
It can be hard to tell by just looking at them; try opening a command line and doing "ps aux" (process list), look at the process names.
Alternatively, open synaptic and check which packages are present.

---

### Post by jw5801 on 2008-07-07
If you installed base Ubuntu then you have Gnome, if you installed Kubuntu then you have KDE, if you installed Xubuntu then you have Xfce. You can install any of them on top of any of the others through synaptic. Say for example you wanted to install KDE, you could use: ```
sudo apt-get install kubuntu-desktop
```

You can then log into KDE by clicking on the sessions button at the login screen.

---

### Post by sayakb on 2008-07-07
Are you talking about virtual desktop? Right click on panel and add the **Workspace switcher** applet. Press **Ctrl+Alt+Left/Right** to switch between adjacent desktops.

---

### Post by James Willis on 2008-07-27
I have installed Ubuntu 8.04 with the Gnome desktop and would like to install KDE also.  If installed, could I choose which one to use on bootup?  If so, how?  I do not want to loss the Gnome desktop. 
Thanks,
Jim

---

### Post by jw5801 on 2008-07-27
Yes, if you install it you can pick which one you want at login (not at bootup, everything is still identical until the graphical interface) by clicking on sessions and choosing which you want to login to.

---

### Post by James Willis on 2008-07-28
I installed the kubuntu-desktop, however, at login I do not have an option to select desktops.  It's nice to have the extra programs that KDE provides, but I would like to be able to switch back to the Gnome desktop. How do you activate the feature that allows you to select desktop at login?  

Thanks,
Jim
Note: Rebooted and discovered at the bottom left hand corner of screen an options button.  Pressed it and was given a number of selections including type of session.

---

### Post by mkclarke on 2008-07-31
I'm running kubuntu and wanted to try out the gnome desktop.  However, if I try to request install in the adept manager, it shows "BREAK (Install)" and it won't install because it says the commit may break packages.  I also tried *sudo apt-get install gnome-desktop*, and I get the following errors:

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

I did install the gdm and set it as default, however I still don't have the gnome desktop installed.  Can anyone tell what's wrong from the above errors?

Thanks!

Mikey

---

### Post by mkclarke on 2008-07-31
Oh boy!  :lolflag:  that's right... I'm a newb.  I just realized that I was getting those errors from apt-get because I was already running adept manager.  So I closed it and ran *sudo apt-get install gnome-desktop* again and it just tells me there is no gnome-desktop package.  So I'll keep searching for clues.

If you can explain the BREAK (Install) part, though, that would be great.

Thanks again!

Mikey

---

### Post by jw5801 on 2008-07-31
That's because there is no gnome-desktop package! If you also want all the applications that Ubuntu installs alongside Gnome, try```
sudo apt-get install ubuntu-desktop
``` Otherwise```
sudo apt-get install gnome
``` will give you a base gnome install.

Also, installing gdm isn't going to help all that much. gdm is the Gnome Display Manager, it basically handles starting X and giving you a graphical login screen. You already have kdm to do pretty much the same thing.

---

### Post by mkclarke on 2008-08-01
Thanks jw!  :KS  Right on... I ran *sudo apt-get install ubuntu-desktop* and I'm now in business.  

Much appreciated!

Mikey

---

### Post by rodh on 2008-08-17
I found this thread interesting because I just removed KDE4 and now have to log in in BASH,  Although to get my GUI running again is simple enough 
      Command:  "sudo gdm" and the desktop is back,  when I try to set it as default I get 
      Message:  Not starting Gnome Display Manager (gdm); it is not the default display manager. 
This one sounds right up the right alley,  Can you tell me how to reset gdm to default display manager

---

### Post by pparks1 on 2008-08-17
The commands for the most popular desktops are;
sudo apt-get install ubuntu-desktop
sudo apt-get install xfce-desktop
sudo apt-get install fluxbox
sudo apt-get install kubuntu-desktop


To pick the desktop, From Logon screen, click on Options, Choose Select Session and pick your desktop environment. When you then logon, it will ask if you want to use the new session 1 time or make it permanent.

---

### Post by jw5801 on 2008-08-17
> **rodh said:**
> I found this thread interesting because I just removed KDE4 and now have to log in in BASH,  Although to get my GUI running again is simple enough 
      Command:  "sudo gdm" and the desktop is back,  when I try to set it as default I get 
      Message:  Not starting Gnome Display Manager (gdm); it is not the default display manager. 
This one sounds right up the right alley,  Can you tell me how to reset gdm to default display manager

Probably removing kdm would be your best route.
```
sudo apt-get remove kdm kdm-kde4 #I put both as I'm unsure which one you'll have
```

---

### Post by rodh on 2008-08-20
Thanks, But I managed to fix it before I got back to the thread,  I reinstalled gdm.  Thanks again.

---

