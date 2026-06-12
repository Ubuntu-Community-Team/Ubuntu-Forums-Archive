---
title: "How to make Brightness Keys work on LXDE."
date: 2015-06-15
forum: Desktop Environments
---

### Post by kagashe on 2015-06-15
I am using Ubuntu 14.04.2 on Lenovo G50-45 and the Brightness Fn keys (they are at no 11 and 12) work well on it.

Due to 2 GB RAM (only 1716 left after video) I have added LXDE Desktop.
The Brightness is too much and I have set it in /etc/rc.local by adding the following line before exit 0
```
echo 75 > /sys/class/backlight/radeon_bl0/brightness
```

But I would like to adjust it through Fn 11 Fn 12 keys as I do on Unity Desktop.

I know that I need to add the keybindings on ~/.config/openbox/lxde-rc.xml to make the Fn keys work but need the exact syntax to be added.

Kamalakar

---

### Post by vasa1 on 2015-06-15
> **kagashe said:**
> ..
I know that I need to add the keybindings on ~/.config/openbox/lxde-rc.xml to make the Fn keys work but need the exact syntax to be added.

Kamalakar
See if this offers any hints:```
    <!-- Keybindings for Multimedia Keys and LCD Backlight -->
    <keybind key="C-F7">        # turn off screen immediately
      <action name="Execute"><command>sleep 2;xset dpms force off</command></action>
    </keybind>
    <keybind key="C-F10">        # decrease screen brightness
      <action name="Execute"><command>xbacklight -dec 10</command></action>
    </keybind>
    <keybind key="C-F11">        # increase screen brightness
      <action name="Execute"><command>xbacklight -inc 10</command></action>
    </keybind>

```

---

### Post by kagashe on 2015-06-15
> **vasa1 said:**
> See if this offers any hints:```
    <!-- Keybindings for Multimedia Keys and LCD Backlight -->
    <keybind key="C-F7">        # turn off screen immediately
      <action name="Execute"><command>sleep 2;xset dpms force off</command></action>
    </keybind>
    <keybind key="C-F10">        # decrease screen brightness
      <action name="Execute"><command>xbacklight -dec 10</command></action>
    </keybind>
    <keybind key="C-F11">        # increase screen brightness
      <action name="Execute"><command>xbacklight -inc 10</command></action>
    </keybind>

```
The following command does not work in the Terminal:
```
S xbacklight -dec 10
```
Therefore this is not going to work.
I think Unity Desktop is doing it differently.

Kamalakar

---

### Post by kagashe on 2015-06-16
I have done some googling. 

xbacklight does not work for radeon driver.

only solution is to echo the required value to /sys/class/backlight/radeon_bl0/brightness file as root user (even sudo does not work).

I wonder what command the Fn key is using. Is there any way to know on Ubuntu Unity Desktop?

Kamalakar

---

### Post by kagashe on 2015-06-16
> **kagashe said:**
> 
I wonder what command the Fn key is using. Is there any way to know on Ubuntu Unity Desktop?

Kamalakar
I got the command from auth.log after pressing the keys:
```
pkexec[8165]: user: Executing command [USER=root] [TTY=unknown] [CWD=/home/vidya] [COMMAND=**/usr/lib/unity-settings-daemon/usd-backlight-helper --set-brightness 28**]

```It is executed as root.

Kamalakar

---

### Post by kagashe on 2015-06-17
Finally I could solve the problem as follows:

Since the command to be executed required root privileges I created two bash shell files on my desktop:

File ~/home/Desktop/Brightness1
```
#! /bin/bash

# script to set the initial brightness on login

[ "$UID" -eq 0 ] || exec gksu bash "$0" "$@"
/usr/lib/unity-settings-daemon/usd-backlight-helper --set-brightness 12
```

File ~/home/Desktop/Brightness2
```
#! /bin/bash

# script to set the initial brightness on login

[ "$UID" -eq 0 ] || exec gksu bash "$0" "$@"
/usr/lib/unity-settings-daemon/usd-backlight-helper --set-brightness 24
```

I made the files executable and tested them. The script asked for sudo password and set the required brightness.

Then I inserted following Keycodes in ~/.config/openbox/rc.xml
```
<!-- Keybindings for LCD Backlight -->
    <keybind key="XF86MonBrightnessDown">        # decrease screen brightness
      <action name="Execute"><command>/home/user/Desktop/Brightness1</command></action>
    </keybind>
    <keybind key="XF86MonBrightnessUp">        # increase screen brightness
      <action name="Execute"><command>/home/user/Desktop/Brightness2</command></action>
    </keybind>
```

and it works by pressing Fn+F11 and Fn+F12 i.e. it asks for sudo password and sets the required brightness.

However writing the command
```
gksu /usr/lib/unity-settings-daemon/usd-backlight-helper --set-brightness 12
```
directly in ~/.config/openbox/rc.xml does not work.

Marking the thread as solved, I hope it is useful.

Kamalakar

---

