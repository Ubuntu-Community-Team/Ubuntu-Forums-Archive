---
title: "Install deb files from the right click menu in Gnome"
date: 2006-03-31
forum: Desktop Environments
---

### Post by sellotape on 2006-03-31
Install Nautilus Actions from [http://www.grumz.net/?q=taxonomy/term/6/9](http://www.grumz.net/?q=taxonomy/term/6/9)

There is a ubuntu deb on there.  

You may have to log out of Gnome for the Nautilus Actions Configuration Editor to appear in your Preferences menu.

Once installed do the following.

I've made a script to install deb files from the right click menu. Please be kind it's my first Linux script. Very easy to use, with progress bar.

Copy and paste the following script into a file call it "installer" and save it in your home folder, then make it executable.

#!/bin/bash
#
# nautilus-deb-installer

package_name=`basename $1`

if zenity --question --title "Alert" --text "Do you wish to install the package $package_name?"
then
foo=`gksudo -u root -m "Please enter your password to install $package_name" /bin/echo "0"`
sudo dpkg -i "$1" | zenity --progress --pulsate --title "Please Wait" --text $"Installing $package_name"
zenity --info --title "Installation Complete" --text "The package $package_name has been installed"
else
zenity --info --title "Installation aborted" --text "The package $package_name was not installed"
exit 1
fi

Then in Nautilus Actions within the Preferences menu.

Label: Install Package
Path: /home/<your username>/installer
Parameters: %M
File Pattern: *.deb
Files only


Once this is done open a terminal window and type:

[COLOR="Blue"]killall nautilus[/COLOR]

**or**

log out of gnome and then log back in again.

Then when you right click on a deb file you will be able to install it.

Good luck!!

---

### Post by halitech on 2006-04-02
Thanks for this, makes life alot easier. I had to reboot after installing the Nautilus Actions package so I could see it in the Prefs menu, is that normal?

---

### Post by manicka on 2006-04-03
[QUOTE=halitech]I had to reboot after installing the Nautilus Actions package so I could see it in the Prefs menu, is that normal?[/QUOTE]

Just logging out and back in would achieve the same result :)

---

### Post by sellotape on 2006-04-03
Yes, you will need to log out or you type:

killall nautilus in a terminal and when the desktop reloads it will appear.

I'll update the original post i think.

---

