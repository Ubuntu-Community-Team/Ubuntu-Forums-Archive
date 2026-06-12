---
title: "Minimal ubuntu install w/LXDE - lost Shutdown/Restart options"
date: 2010-09-04
forum: Desktop Environments
---

### Post by kpatz on 2010-09-04
I'm working on getting a stripped down Ubuntu Lucid installed on an old POS HP PC for a friend.  Because it only has 256 MB RAM, I used a minimal CD and the installed lxde as the GUI.

Today I was working on it and installed the latest updates and Openoffice-Writer.  After rebooting, the shutdown button only gives me Hibernate, Log Out and Cancel.  I lost Shut Down and Restart.  Searching w/Google shows solutions for other distros such as Arch and Mint, but none that worked for Ubuntu w/LXDE.  Either the files to edit don't exist, the groups don't exist (one site said to add the user to the "power" group, no such thing in 'buntu) or the options don't exist (such as System->Administration, which isn't in the menu at all).

HAL and dbus are running, which was the other thing some sites mentioned.

So, how do I get the shutdown and restart buttons back?  The people that will be getting this machine aren't going to know how to go to a terminal and type "sudo shutdown -h now" everytime they want to shut down.

I know the buttons existed before installing the latest updates.  Any suggestions?

---

### Post by kerry_s on 2010-09-04
why don't you just install lubuntu. all the works done for you.
[http://lubuntu.net/](http://lubuntu.net/)

the reason stuff is missing is because you didn't install them, that is the concept of "minimal", **you** decide what you want.

---

### Post by JohnnyC35 on 2010-09-04
Try out Peppermint OS. It's almost minimal and has LXDE.

---

### Post by kpatz on 2010-09-05
> **kerry_s said:**
> the reason stuff is missing is because you didn't install them, that is the concept of "minimal", **you** decide what you want.The shutdown and restart options weren't missing before I did an update.  And besides, I don't think there's an apt package for installing "shutdown and restart buttons".  They're supposed to appear in lxsession-logout, but they don't for me.

I'll try lubuntu and peppermint, but I'm really looking for minimal, no unnecessary fluff, which is why I went with a "mini" CD and then installed just the essential stuff.

---

### Post by gbestrada on 2010-09-05
you can right click on the top panel and on the menu that appears choose add to panel
look for the shutdown option select it and click add.

:pHope it helps:p

---

### Post by kpatz on 2010-09-05
> **gbestrada said:**
> you can right click on the top panel and on the menu that appears choose add to panel
look for the shutdown option select it and click add.

:pHope it helps:pThat's not the problem.  I have that button.  But when I click it, a window pops up (via lxsession-logout) and the only choices it gives me are logout, hibernate and cancel.  There's supposed to be shutdown and restart options in that window as well, but they disappeared after doing an update.

Anywho, I'm burning a Lubuntu ISO right now and will try it.

---

### Post by volkswagner on 2011-06-05
I have a fresh install of 11.04 >minimal which I added LXDE.  I also don't have available shutdown and restart options.  Even logging in as root, these options are not displayed.  The shutdown screen does a quick flash like it wants to display, but quickly reverts to only two choices (logout and cancel).

In Debian the solution is add users to the powerdev group.  Ubuntu has dropped this way back.  

What is the proper solution to get users allowed to reboot/shutdown, using LXDE without a login manager?  

Using Lubuntu is not an option for me, as I only have a 512MB hard drive.  Upgrading the internal Flash Module on my Webdt366 is a little expensive compared to the cost of the device.  Lubuntu seems to not support a "true" alternate install (minimal = 2.7Gig HD required).

---

### Post by volkswagner on 2011-06-11
Update and a bump before I try a new thread.

Since I have a minimal install of Natty, plus used --without-recommends when installing lxde, I figured at least one package was not installed, but required.

I checked back through my notes and here is the list of packages not installed, but recommended when installing LXDE.

```
The following packages are RECOMMENDED but will NOT be installed:
  arj arora chimera2 chromium-browser edbrowse elinks elinks-lite elvis elvis-console epiphany-browser firefox galculator gdm gksu gvfs-backends 
  gvfs-fuse hicolor-icon-theme kdm konqueror libgtk2.0-bin lightdm links links2 lxdm lxmusic lynx-cur manpages-dev menu-xdg midori netrik netsurf 
  openbox-themes p7zip-full policykit-1-gnome rekonq rpm scrot seamonkey-browser slim unzip uzbl w3m wdm x-ttcidfont-conf xdg-utils xdm xemacs21-mule 
  xemacs21-mule-canna-wnn xemacs21-nomule xscreensaver xserver-xorg zip
```

I have since installed policykit-1-gnome, which helped, as root now has the reboot, shutdown options inside LXDE logout menu options.  I have also installed consolekit which added the messagebus group to /etc/group.

So I ask, how do I get a regular user with sudo privileges to get the options?

I am trying to do this without lxdm, slim, gdm or others to keep disk footprint down, and the unit will autologin anyway.

Again I have had this setup with Debian5, but Natty does not seem to have powerdev group.

---

### Post by YardCamel on 2012-08-27
Yikes, what a mess. I think I have found the solution to this. First, a recap.
 
After upgrading a minimal installation using lxde, the lxsession-logout applet stopped showing buttons to permit hibernate, reboot, and shutdown. Running lxsession-logout from the command line resulted in error message stating that the name org.freedesktop.Hal was not provided by any .service files and org.freedesktop.UPower was not provided by any .service files. Starting lxde from the command line using the ConsoleKit ck-session-launcher seemed to alleviate the problem, but it's difficult and unclear how to get ConsoleKit to launch correctly using slim, xdm, and other display managers.
 
I was able to correct the issue by installing upower and hal packages from the repository by...
 
$ sudo apt-get install upower hal
 
It wasn't necessary to log out or reboot; the shutdown, reboot, and hibernate buttons were restored to lxsession-logout immediately after installing upower and hal.
 
Hope this helps everyone. I'm running 12.04 in a VirtualBox vm instance. YMMV. Good luck.

---

### Post by YardCamel on 2012-08-27
I'm glad I still had this in my browser history.  There's something else you need to do to make this work.  If you don't the buttons will appear, but they throw an error if you click on one of them.
 
First, create a group in /etc/group called "power" and add your users to it.
 
Next, edit /etc/dbus1/system.d/hal.conf and add the following to the bottom of the file:
[INDENT]<policy group="power">
   <allow send_interface="org.freedesktop.Hal.Device.SystemPowerManagement"/>
   <allow send_interface="org.freedesktop.Hal.Device.LaptopPanel"/>
</policy>
[/INDENT]That finally fixed me up.  The fix was immediate, and I was able to use it to reboot the machine.

---

### Post by slixz85 on 2013-01-27
this is only a 1 package problem. i ran into it and quickly found it in synaptic. all that is needed is menu-xdg and it should work. i know this was a long time ago but just posting for others to see in future. later

---

### Post by xtdv on 2013-08-02
I have the same problem with yours and solve by allow excuting dbus-daemon-launch-helper
```
sudo chmod +x /usr/lib/dbus-1.0/dbus-daemon-launch-helper
```

Hope this help.

---

### Post by bapoumba on 2013-08-02
Thanks for posting a solution. This thread is quite old, so I'm closing. Please report this post if you want it be reopened (with a good reason).

---

