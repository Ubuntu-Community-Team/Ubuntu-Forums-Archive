---
title: "Permissions?  Settings not being saved, launching as SUDO?"
date: 2009-03-19
forum: General Help
---

### Post by u.2 on 2009-03-19
Hi,
Sort of newbie, new to ubuntu :)  So far things are great but a couple issues.

I have 2 systems, 1 with an intel video card and 1 with an NVIDIA.

I setup up multiple displays, a primary as my monitor and then a desktop monitor, things are fine but then whenever I reboot the settings go back?  It asks me for my password when I make the changes.

A few other settings don't save either, so I don't know if that is because I am not running the programs (using the gui) as the "root" which I know is disabled by default.

How do you launch the gui interfaces as root?  And how do you save video settings for resolution, etc.?

---

### Post by loomsen on 2009-03-19
Hello.

Ubuntu has his own policy to grant admin access to users.

Within a terminal you may use sudo, if you want to start a GUI'd application as root prepend a gksudo to the command. You should be able to save your resolution settings then. (These are saved and configured in your /etc/X11/xorg.conf)

There are a lot of options you may specify there, depending on your card.

Try (in a terminal:)

whatis xorg.conf
man xorg.conf
apropos xorg.conf

[Heres the link to a wiki about xorg.conf](http://en.wikipedia.org/wiki/Xorg.conf)

Enjoy :)

*edit*

[color=red]HINT: Try and avoid sudo/gksudo'ing. Most configuration settings can be done as a normal user and saved in your home folder, no need for sudo at all. Mind, if you create a file as SuperUser, this file will have root:root as owner. Eventually you will change your /home/&USERs permissions and gdm wont let you log back into your next session. So, make sure you dont use it 2 often.[/color]

---

### Post by jlochhead on 2009-03-19
> **u.2 said:**
> Hi,
Sort of newbie, new to ubuntu :)  So far things are great but a couple issues.

I have 2 systems, 1 with an intel video card and 1 with an NVIDIA.

I setup up multiple displays, a primary as my monitor and then a desktop monitor, things are fine but then whenever I reboot the settings go back?  It asks me for my password when I make the changes.

A few other settings don't save either, so I don't know if that is because I am not running the programs (using the gui) as the "root" which I know is disabled by default.

How do you launch the gui interfaces as root?  And how do you save video settings for resolution, etc.?

Find the name of the program you want to launch. If it is in the menu right click on applications, select edit menu, browse to the entry and click properties to find the command.

To open an application as root (the easy way) press alt+f2 and type gksudo <application command>

---

### Post by u.2 on 2009-03-20
Thx, I am a bit confused, so I went to the apps menu, found one I wanted to run as sudo, and then highlighted it, entered alt + F2, but not sure what the command is I type after that?

Is there any other way to configure the NVIDIA stuff without editing the file?

I want to do dual monitors.

Also I noticed I setup my wired eth0 card with a static, at each reboot it turns itself back to DHCP?

---

### Post by loomsen on 2009-03-25
OK, I assume u want to configure it using nvidia-settings.

Do it like this (safe way:)

1. Open up nvidia-settings (Either from the menu or Alt+F2: nvidia-settings)
2. Configure
3. When done, choose to save X configuration file
4. Change the default location to $HOME [color=blue](=/home/<your_user>)[/color]
5. Place it there.

[color=red] NO SUDO or GKSUDO SO FAR![/color]

U will get a notification if u don't uncheck the merge with existing file option, just close that window and go on.

OK, I assume u hereby created ur desired xorg.conf file, and that it is located:

$HOME/xorg.conf[color=blue](=/home/<your_user>/xorg.conf)[/color]

again:
[color=red] NO SUDO or GKSUDO SO FAR![/color]

####################
####################

Now, open a terminal, and do this:
```

[color=blue]## Backup ur current xorg.conf with:[/color]
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.template
[color=blue]## Move ur desired xorg.conf into place:[/color]
sudo cp $HOME/xorg.conf /etc/X11/xorg.conf

```

*DONE*

Now connect ur second monitor and restart ur X-server (or simply ur computer)

You shouldnt run into trouble that way (like messing up ur home directories permissions and being unable to login upon next boot)

Enjoy.

---

### Post by loomsen on 2009-03-25
> **u.2 said:**
> 
Also I noticed I setup my wired eth0 card with a static, at each reboot it turns itself back to DHCP?

You may configure this in 

/etc/network/interfaces

Again, I'd suggest u back ur existing up:
```

sudo cp /etc/network/interfaces /etc/network/interfaces.template
```

Then edit the file:

[color=blue]In a Terminal:[/color]
```
sudo nano /etc/network/interfaces 
```

[color=blue]If you prefer GUIs, type this into a Terminal:[/color]
```
gksudo gedit /etc/network/interfaces 
```
 
The manual page for interfaces will show options you may specify, for some examples type:
```
zcat /usr/share/doc/ifupdown/examples/network-interfaces.gz
```

DRAFT:
```

# We always want the loopback interface.

 auto lo
 iface lo inet loopback

# An example ethernet card setup: (broadcast and gateway are optional)

 auto eth0
 iface eth0 inet static
     address 192.168.0.42
     network 192.168.0.0
     netmask 255.255.255.0
     broadcast 192.168.0.255
     gateway 192.168.0.1

```

Your /etc/network/interfaces file should look sth like that. Adjust the IPs and you should be fine.


When done save and close the file (/etc/network/interfaces), and simply restart ur network module:

```

sudo /etc/init.d/networking restart
```

Your interface should be configured how you specified it should be.

---

### Post by u.2 on 2009-03-25
I am just confused on why settings don't save when you launch the apps through the "gui" and believe me, I am all for getting into the command line as well.  But on other distro's I have tried you just get prompted for root and then make your changes.

So what do most people do when running the gui's and making system settings?

I don't know why the network connection let's me set it and then after a reboot it is gone?

---

### Post by norwoods on 2009-03-25
the ubuntu philosophy is to operate at minimal privilege, not admin mode, unless necessary.  ubuntu is intelligent enough to remember I am an admin and open settings programmes with the right privileges if you set them.  
open System-->Preferences-->Main Menu
under Menus:, click System Tools
under Items:, click NVIDIA X Server Settings
click properties
in the Command: text box, insert "gksu " in front of  /usr/bin/nvidia-settings
click close
click close
now when you open Applications-->System Tools-->NVIDIA X Server Settings, it will ask for a password and you will be in admin mode.

when the nvidia gui interface is running, click X Server Display Configuration. 
click Configure...
click the TwinView radio button
click OK
set up anything you want
click Save to X Configuration File
click Quit

---

### Post by loomsen on 2009-03-25
> **u.2 said:**
> "gui"

GUI=Graphical User Interface

Networking interfaces are configured during system boot tho, so your choices are:

1) Configure it manually like I wrote above

(deprecated if you choose 1) )
2) Let it be autoconfigured after your display manager (x-server) started.


Root login is disabled by default in gdm. So only users may login to a x-server

You can change this settings, tho I wouldnt recommend it. 

/etc/gdm/gdm.conf

is where the config takes place.

Tho I basically wrote a step by step howto for you above. So, y don't follow?
I even posted the most appropriate example for you. Wont get easier than that.

If you want to permanently change user to root in a terminal u can do so by:

```
sudo su - 

```

MIND THE - (actually, avoid getting root...)


Or enable root login in gdm...

I dont recommend any of these tho.

---

