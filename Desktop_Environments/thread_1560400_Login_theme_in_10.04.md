---
title: "Login theme in 10.04"
date: 2010-08-24
forum: Desktop Environments
---

### Post by Z.K. on 2010-08-24
I have a touch screen and I want to enable the onboard onscreen keyboard during login.  From some instructions that refer to Ubuntu versions below 9.04, I need to enable the plain theme for the keyboard to display during login, but 10.04 no longer has a login preferences GUI so how do I do this in 10.04?

Or, does anyone know of another way to do this?  I set the Assistive properties to display the keyboard on login, but nothing is displayed.

:(

---

### Post by sisco311 on 2010-08-24
According to the [documentation]("http://library.gnome.org/admin/gdm/"), you have to set the value of the /desktop/gnome/applications/at/screen_keyboard_enabled gconf key to true:
```
sudo -u gdm gconftool-2 --type bool --set /desktop/gnome/applications/at/screen_keyboard_enabled "true"
```

---

### Post by Z.K. on 2010-08-25
> **sisco311 said:**
> According to the [documentation]("http://library.gnome.org/admin/gdm/"), you have to set the value of the /desktop/gnome/applications/at/screen_keyboard_enabled gconf key to true:
```
sudo -u gdm gconftool-2 --type bool --set /desktop/gnome/applications/at/screen_keyboard_enabled "true"
```

Thanks, that worked.  Now, if only I could figure out how to keep my touch screen settings at login.  Right now I am setting them in the user profile.  I would like to set them system wide and before login, but I have not figured out how to do that as yet.

Thanks again.

:D

---

### Post by sisco311 on 2010-08-25
You're welcome!

I'm not familiar with touch screens. What procedure do you have to follow to set it up?

---

### Post by Z.K. on 2010-08-25
> **sisco311 said:**
> You're welcome!

I'm not familiar with touch screens. What procedure do you have to follow to set it up?

I found a generic program called xinput_calibrator and seems to work fairly well.  I just add the xinput command with its arguments to the /etc/Profile file and it remembers the value after the user logs in.  I am not that familiar though with how Ubuntu boots and where I would put these values so that they would be preserved at the login screen.  I would like them to be system wide, independent of a login.

---

### Post by jtarin on 2010-08-25
Try placing the command in the /etc/rc.local file.

---

### Post by sisco311 on 2010-08-26
Upstart often executes the rc.local file too soon. You may have to add a sleep before the command:
```
 #!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

sleep 8     # wait 8 seconds 
**command [OPTIONS]**

exit 0

```

or write an Upstart job.

/etc/init/touchscreen.conf:
```

# touch screen
#
# xinput_calibrator 

description     "whatever"

start on starting gdm

stop on runlevel [016]

script
  **command [OPTIONS]**
end script

```

But, if you have to run it as a non-privileged user, then create a .desktop file in GDM's autostart directory.

/usr/share/gdm/autostart/LoginWindow/touchscreen.desktop:
```
[Desktop Entry]
Encoding=UTF-8
Name=touchscreen
Comment=xinput_calibrator 
Exec=**command [OPTIONS]**
Terminal=false
Type=Application

```

---

### Post by Z.K. on 2010-08-30
> **sisco311 said:**
> Upstart often executes the rc.local file too soon. You may have to add a sleep before the command:
```
 #!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

sleep 8     # wait 8 seconds 
**command [OPTIONS]**

exit 0

```

or write an Upstart job.

/etc/init/touchscreen.conf:
```

# touch screen
#
# xinput_calibrator 

description     "whatever"

start on starting gdm

stop on runlevel [016]

script
  **command [OPTIONS]**
end script

```

But, if you have to run it as a non-privileged user, then create a .desktop file in GDM's autostart directory.

/usr/share/gdm/autostart/LoginWindow/touchscreen.desktop:
```
[Desktop Entry]
Encoding=UTF-8
Name=touchscreen
Comment=xinput_calibrator 
Exec=**command [OPTIONS]**
Terminal=false
Type=Application

```

Thanks for the help, but that did not work either.  The touch screen is still not calibrated at the login screen.

---

