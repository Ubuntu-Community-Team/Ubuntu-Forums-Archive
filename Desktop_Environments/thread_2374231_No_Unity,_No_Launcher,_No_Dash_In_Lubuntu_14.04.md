---
title: "No Unity, No Launcher, No Dash In Lubuntu 14.04"
date: 2017-10-13
forum: Desktop Environments
---

### Post by Dreadsen on 2017-10-13
Hello I followed some directions that led me to change my desktop environment from Ubuntu 14.04 to Lubuntu without uninstalling and doing a clean install. I wanted to leave all applications intact. 

[https://www.geek.com/chips/dont-uninstall-ubuntu-just-change-the-interface-1542514/2/](https://www.geek.com/chips/dont-uninstall-ubuntu-just-change-the-interface-1542514/2/)
 
The problem is now that I have lubuntu I have no launcher, do dashboard on the footer or header of the screen and nothing from the right mouse click.

All I have is lubuntu wallpaper, a mouse pointer and the only terminal I have access to is TTYL from CTRL + ALT+F1 

So i'm looking to get full functionality of lubuntu through TTYL since that's the only terminal I have access to

---

### Post by Frogs Hair on 2017-10-13
There is no dash or launcher in Lubuntu.When installed properly there should be a top panel with a traditional menu. Can you provide the commands you used ? You could also reinstall Lubuntu from tty. 

```
   sudo apt install --reinstall lubuntu-desktop
``` ```
sudo reboot
```

---

### Post by Dreadsen on 2017-10-13
> **Frogs Hair said:**
> There is no dash or launcher in Lubuntu.When installed properly there should be a top panel with a traditional menu. Can you provide the commands you used ? You could also reinstall Lubuntu from tty. 

```
   sudo apt install --reinstall lubuntu-desktop
``` ```
sudo reboot
```


This is the command I used

sudo apt-get -y install lubuntu-desktop

I have no top panel or traditional menu. Just wall paper and a mouse pointer.

I just reinstalled using your suggestion. I ended up in the same position.

The top bar is there at the sign in but as soon as I sign in it disappears

---

### Post by deadflowr on 2017-10-13
Up in the panel in the login screen, click on the Ubuntu icon.
That's where/how you switch sessions.
Choose the new lubuntu (or even lxde) session to run lubuntu or lxde.

---

### Post by Dreadsen on 2017-10-14
> **deadflowr said:**
> Up in the panel in the login screen, click on the Ubuntu icon.
That's where/how you switch sessions.
Choose the new lubuntu (or even lxde) session to run lubuntu or lxde.

I've tried that. No matter which one I select I end up with the same thing :/

---

### Post by vasa1 on 2017-10-14
Lubuntu 14.04 [is no longer supported]("https://wiki.ubuntu.com/Releases#End_of_Life_.28EOL.29"). If you don't have bandwidth restrictions, back-up your important data and do a clean install via a live USB of whichever distro you like. Mixing desktop environments *could* lead to complications.

---

### Post by ajgreeny on 2017-10-14
You may have some processes autostarting in your home's unity configuration that are causing this problem.

Assuming you are the admin user, try creating a new user, give that user admin rights when you create it, then login as that new user to the Lubuntu session available from the login screen.

None of your old /home configs will now be used so you may well see a normal Lubuntu desktop, and with this new user having admin rights you will be able to copy across all the data folders and files, change their ownership to your new user, and start again from scratch with this new DE.

However, as mentioned by vasa1, Lubuntu 14.04 is no longer supported, and whilst you will still get some of the security upgrades to the common packages that are still supported in Ubuntu, the specific Lubuntu packages will get no further updates.

---

### Post by Dreadsen on 2017-10-15
> **ajgreeny said:**
> You may have some processes autostarting in your home's unity configuration that are causing this problem.

Assuming you are the admin user, try creating a new user, give that user admin rights when you create it, then login as that new user to the Lubuntu session available from the login screen.

None of your old /home configs will now be used so you may well see a normal Lubuntu desktop, and with this new user having admin rights you will be able to copy across all the data folders and files, change their ownership to your new user, and start again from scratch with this new DE.

However, as mentioned by vasa1, Lubuntu 14.04 is no longer supported, and whilst you will still get some of the security upgrades to the common packages that are still supported in Ubuntu, the specific Lubuntu packages will get no further updates.

You are right. When I signed in under guest It went to KDE plasma workspace with everything. So that means there is something wrong with my main user account

---

### Post by ajgreeny on 2017-10-16
I suspect a conflict in the configuration files (the hidden ones starting with . or in hidden folders in your home) between the two DEs, 

Start by disabling compiz if it is in your autostart list.

---

### Post by Dreadsen on 2017-10-20
> **ajgreeny said:**
> I suspect a conflict in the configuration files (the hidden ones starting with . or in hidden folders in your home) between the two DEs, 

Start by disabling compiz if it is in your autostart list.

Thanks everyone

Okay this is where i'm at.

I created a 2nd user that has admin privileges.

I upgraded to Kubuntu 16.04 

Now the 2nd user actually can open up Ubuntu session or Kubuntu session.

But the first user even after upgrade still has just the wallpaper and a mouse arrow. No matter what environment I choose with the first user it's the same thing.

The 2nd user works well it can open up ubuntu or kubuntu desktop environments no problem.

So I tried to access the root folder of the 1st user so I could attempt what you suggested but it will not let me access that folder. Even though both users have admin privileges.

---

