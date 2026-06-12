---
title: "how to make start up script? ideas?"
date: 2005-05-28
forum: Desktop Environments
---

### Post by Digitallysick on 2005-05-28
I need to setup some type of script to startup on ubuntu to start a totally transparent terminal, i had a post a while back that adv of ETERM (so it looks as if its part of the desktop) any ideas? i would like for it start up everytime, from useing Eterm it seems a little shotty, is it a good idea??  and xfce is it better than gnome? any advantages? disadvantges?

---

### Post by metasyntax on 2005-05-28
from the gnome menu:
system->Preferences->Sessions

click on the "Startup Programs" tab, put in the eterm commandline that you want to use.

HTH,
meta

---

### Post by Digitallysick on 2005-05-28
i did that, it didn't work, i just paste my script in the start up session? the terminal didn't come or anything, so i assume i did not do it correctly, or do i have to specify that i want it ran through the terminal?

---

### Post by ar0d on 2005-05-29
paste your script

---

### Post by lorap on 2005-05-30
read this friend:

Init scripts

Init scripts are the scripts located in /etc/init.d. These scripts are
part of the bootup sequence of Ubuntu. During boot, they are not
called directly, but through a structure of symbolic links which
manage the services which are to be started in a particular runlevel.
The scripts which are symlinked from /etc/rcS.d are executed first.
Then the scripts in /etc/rcN.d/ are executed, with N being the chosen
runlevel (default 2).

The LSB specifies some scripts that are used for displaying the output
of the initscripts. To change how the init script's startup is
displayed look in to /lib/lsb/init-functions

Deactivating init-scripts

1. Method one: Deleting the rc*.d links
To deactivate a script (meaning that it will not be executed at
bootup), remove the corresponding symlink from /etc/rc?.d. Do not use
the update-rc.d command for this purpose! It is only used in package
installation scripts, and not designed for this kind of runlevel
management.

Some people on the mailinglist complained on boot-delays because of
the NTP-Server sync. To remove this issue the following command:

sudo rm /etc/rcS.d/S51ntpdate

 Problem:
To restore the links with the right S?? or K?? values you have to look
up those values on another system or take a look at the deb-Package
install scripts ...

2. Method two: Use chmod to deactivate a service
A more straightforward way is to make the init script non-executable.
You do that with the *chmod* command.

 sudo chmod -x /etc/init.d/myscript

After this the service will no longer be able to run.

Reactivate the service with:

sudo chmod +x /etc/init.d/myscript

 Problem
 Now you'll get an error message at boot time saying that init can't
execute /etc/init.d/myscript.

Solution
To avoid this error msgs you have to modify the /etc/init.d/rc and the
/etc/init.d/ scripts a bit. To do this simply download and apply the
following diffs.

cd /tmp
wget [http://www.ubuntulinux.org/wiki/rc.diff](http://www.ubuntulinux.org/wiki/rc.diff)
wget [http://www.ubuntulinux.org/wiki/rcS.diff](http://www.ubuntulinux.org/wiki/rcS.diff)

cd /etc/init.d
sudo patch -p3 < /tmp/rc.diff
sudo patch -p3 < /tmp/rcS.diff

3. Method three: Use sysvconfig to deactivate a service
Enable/Disable Services with sysvconfig
Install sysvconfig
System > Administration > Synaptic Package Manager
With All packages selected (the default) scroll down to sysvconfig and
check the box, selecting Mark for Installation. You will be prompted
to "Mark additional required changes ?" for "dialog" to be installed;
click Mark.
In the menu bar of Synaptic, click Apply. When prompted to apply the
changes, click the Apply button.
Wait for the software to install, then File > Quit from Synaptic.
Run sysvconfig
Start up a root terminal (Applications > System Tools > Root Terminal).
Type sysvconfig
With the blue bar on Enable/Disable a service, press the Enter key.
Move the scroll bar up and down the list of services. Use the space
bar to toggle a service on or off.
Scroll down to Finished and press the Enter key to save your changes.
Press return again to return to the main menu, then select Quit.

Installing custom init-scripts
To install your own script, copy it to /etc/init.d, and make it executable.

sudo cp myscript /etc/init.d
sudo chmod +x /etc/init.d/myscript

To make the script run at startup:

sudo update-rc.d myscript start 51 S .

(Do not forget the dot: . )

For more information on the usage of update-rc.d

man update-rc.d

------------------------------------------------------------------------------------------------------------------

Instead of removing the rc*.d links, move them
Instead of removing, I create a directory in my home dir, where I
placed all the links I removed from the /etc/rc*.d

Instead of removing, renaming
If I want to disable initscript temporarily, I simply rename it from
Sxxname to sxxname (without capital) It doesn't start, and the
starting order information remains

Why don't simply use rcconf?
Try sysv-rc-conf (text based) or ksysv (KDE based). sudo apt-get
install sysv-rc-conf
Try sysvconfig as well - it's also quite handy.

runlevel with networking and without graphical interface?
I would like to have a runlevel with basic networksupport (and
services like ssh and sftp) but without the graphical interface. This
is not implemented in /etc/init.d/rcS
When I run: apt-get install rcconf
I get the message that rcconf package could not be found.
apt-get install sysv-rc-conf
tells me that the package is not available although another package points to it
I would like to put this runlevel in the (grub) bootmenu, so that I
can choose it at boot and not need to chmod files.

---

