---
title: "Su'ing into root..."
date: 2006-06-04
forum: Desktop Environments
---

### Post by anxietyzone on 2006-06-04
Hi

Using the terminal, I want to create a symbolic link to the Java plugin in my Firefox plugin folder just like I've been doing for years and years on a myriad of other Linux flavors but I seem unable to do this because a root password was never created at install-time. Is there a quick and easy way to do this?. I have to have root for compilation, working with permissions, creating sym-links and a myriad of other admin functions. 

- Much appreciated!

---

### Post by philetus on 2006-06-04
[QUOTE=anxietyzone]Hi

Using the terminal, I want to create a symbolic link to the Java plugin in my Firefox plugin folder just like I've been doing for years and years on a myriad of other Linux flavors but I seem unable to do this because a root password was never created at install-time. Is there a quick and easy way to do this?. I have to have root for compilation, working with permissions, creating sym-links and a myriad of other admin functions. 

- Much appreciated![/QUOTE]

There is no root password.
In terminal, type "sudo bash" or "sudo su" and put in your password.

---

### Post by Stereotypical Rage on 2006-06-04
sudo -s
Is what I use.

the password you use is the password you created during install for your user account. Alternatively you can use gksudo

---

### Post by anxietyzone on 2006-06-04
Excellent forum here. You folks answered my question and solved my problem all within about 3 minutes. I think I'm going to like this place :).

- Thank's!

---

### Post by jgcamp99 on 2006-06-04
This threw me for a loop in Ubuntu, I chose to re-enable root and allow root to login so that I could install applications and copy files to any folders as root (I know Ubuntu highly recommends that root not have this power, but really, root is the administrator, why should it be crippled ?) I had to reenable root to install a Firefox plugin for flashplayer 7 for Linux manually:

This can be done this way:

[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

Going back to a traditional root account

Enabling the root account

To enable the root account (i.e. set a password) use:

sudo passwd root

Enter your existing password
Enter password for root
Confirm password for root
Disabling the root account

If you have enabled a root password and wish to disable it again. To disable the root account after you have enabled it use:

sudo passwd -l root

This locks the root account. 
===============================================
Then you can enable root to login from the splash screen:

Enabling graphical root login

In Gnome

    *

      Open System --> Administration --> Login Screen Setup
    *

      Click on the security tab
    *

      Check Allow root login

In KDE

    *

      Open Konqueror and open the /etc/kde3/kdm/ folder
    *

      Right click the kdmrc file and then Actions --> 'Edit as root'
    *

      On line 246 should be AllowRootLogin=false change it to 'true'
    *

      Save and exit.

From the Linux Console

    *

      Switch to a virtual terminal with Ctrl+Alt+F1 (or F2, F3, ..., F6). You can get back to your X session with Ctrl+Alt+F7.
    *

      Log in as yourself.
    *

      Become root with "sudo -i".
    *

      Start a new X server on display :1 with "startx -- :1".
          o

            You can run a different window manager (say, fvwm) with something like "startx fvwm -- :1".
          o

            You must use display :1 because the default (display :0) is already being used by you.
    *

      Be careful, you're the superuser. Don't forget to logout as soon as you're done, from both X and the console.

---

