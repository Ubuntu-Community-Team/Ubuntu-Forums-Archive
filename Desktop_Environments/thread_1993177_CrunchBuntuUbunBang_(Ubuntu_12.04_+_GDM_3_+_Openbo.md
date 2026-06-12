---
title: "CrunchBuntu/UbunBang (Ubuntu 12.04 + GDM 3 + Openbox) how-to tips"
date: 2012-06-01
forum: Desktop Environments
---

### Post by Fernando Negro on 2012-06-01
The folks at [Crunchbang]("http://crunchbanglinux.org/") have made a great work in producing a distro with Openbox installed by default, but it's based on Debian. For those of you who want some of Ubuntu's functionalities - like automatic encryption of your home folder and such - in an as-light-as-possible operating system, with Openbox as your desktop environment (or window manager), I have elaborated the following set of tips (or instructions) to try to imitate the same type of build made by the CrunchBang folks in their "Statler 10" version. Here are some simple steps you have to follow:

(I don't know if it's necessary or not - since I don't have the usual warning on the desktop environment panel - but, for each important "apt-get" operation, I reboot the computer next - "sudo reboot" - to make sure everything goes OK...)


**1.** Install only a comand-line version of Ubuntu, by using one of the Alternate CD and pressing the F4 key, at the part where it shows the boot menu options, to choose the "Install a command-line system" option and then choosing to "Install Ubuntu".


**2.** With Ubuntu installed, update your software, by executing "**sudo apt-get update && sudo apt-get upgrade**".


**3.** Install Xorg, GDM and Openbox - "**sudo apt-get install xorg gdm metacity openbox**".

(If you don't install the "metacity" package, the mouse cursor at the GDM login screen is left eternaly waiting for something... You can use the LightDM or SLiM login managers - which are more light - but, in my case, they messed up the GTK 2 theme I wanted to use, so I chose GDM instead.)


**4.** Install a terminal emulator, a web browser, a text editor and other programs you find necessary, at least for a start.

(Example: "**sudo apt-get install xfce4-terminal leafpad firefox**")


**5.** Configure your network, if you need to.

(Assuming you have installed Ubuntu with a wired connection to a router and want to use a wifi connection on your computer,)

Install the necessary drivers for your wifi card and then install the "nm-applet", as well as a panel for Openbox - such as "tint2" - to use this network applet ("**sudo apt-get install tint2 network-manager-gnome**").

After this, edit the "**/etc/network/interfaces**" file and disable the automatic wired connection, to let the "nm-applet" manage the connections, by commenting out some of the lines,

from this:
> # This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

to this:
> # This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
# auto eth0
# iface eth0 inet dhcp

And then, configure your wifi connection by executing the "nm-applet" program as root ("**sudo nm-applet**"), after you have started the "**tint2**" panel inside Openbox.


**6.** Be sure to install the volume managers you want and to activate your sound ("volumeicon" is a good choice as a front-end in the "tint2" panel) and then configure the rest at your own will. You can copy the menu, shortcut keys, conky etc configuration files, if you want, either from the [CrunchBang]("http://crunchbanglinux.org/") or [ArchBang]("http://archbang.org/") distribution.


**7.** You might want to install the "xubuntu-artwork" and other packages for icons. The Ubuntu plymouth splash screen, displayed at boot in a regular Ubuntu installation, is in the "plymouth-theme-ubuntu-logo" package. For other theming, use "lxappearance" and "obconf" for the programs and "nitrogen" for the background. To make the Qt applications use the GTK theme, use the "qt4-qtconfig" tool. You can also **theme the GDM 3** login screen theme and font, by altering the "**/usr/share/glib-2.0/schemas/ubuntu-artwork.gschema.override**" file, and the GDM background image, by altering the "**/usr/share/glib-2.0/schemas/10_gsettings-desktop-schemas.gschema.override**" file, and then executing the command "**sudo dpkg-reconfigure libglib2.0-0**".


That's it. From here on, you are on your own.

I think you'll be able to manage to do the rest of the customization by yourselves, searching the Internet for answers to any doubts you may have.

Happy installations.

---

### Post by Fernando Negro on 2012-09-23
But, by the way...

One much **simpler** alternative to all of this...

You can always just install **Lubuntu** 12.04 and, at the login screen, choose Openbox, instead of LXDE, in the session type menu.

That way, you can also have a "fallback" option, consisting of a full DE, in case something goes wrong with Openbox.

---

