---
title: "Login script, just a white screen"
date: 2023-05-30
forum: Desktop Environments
---

### Post by olliecampbell2 on 2023-05-30
Hi All,

I have a bash script (kiosk.sh, script is below) that launches two Brave web browser (v1.51.118) windows on separate screens, full screen on Ubuntu (22.04.2 LTS (GNU/Linux 5.19.0-42-generic x86_64)). I've done this using the 'startup programs' app.

This has been working fine until recently, but since some recent (can't remember which) updates all I now get is 2 blank white screens on reboot. No menu bars etc, but the underlying OS is fine. If I log out and back in again, everything works fine.

I've tried adding a delay to the autostart launch script by adding the following (bolded below):
```

nano ~/.config/autostart/kiosk.sh.desktop

[Desktop Entry]
Type=Application
Exec=/home/username/kiosk.sh
Hidden=false
NoDisplay=false
X-GNOME-Autostart-enabled=true
**X-GNOME-Autostart-delay=60**
Name[en_GB]=Kiosk
Name=Kiosk
Comment[en_GB]=
Comment=

```


I've also checked the permissions for this startup script, and also my custom script:

```

ls -l ~/.config/autostart/kiosk.sh.desktop
-rwxrwxr-x 1 username username 173 May 24 14:33 /home/username/.config/autostart/kiosk.sh.desktop

```

```
 ls -l kiosk.sh-rwxrwxr-x 1 username username 1369 May 30 11:19 kiosk.sh

```

I have also tried re-installing Brave.

But none of this seems to help.

Any ideas where I can look?





My custom browser launch code:

```

#!/usr/bin/bash
export DISPLAY=:0.0


xset s noblank
xset s off


/usr/bin/brave-browser --new-window --noerrdialogs --disable-infobars --kiosk --window-position=0,1920 --user-data-dir="/home/username/Documents/Profiles/0" "http://INTERNAL_URL_1" &


/usr/bin/brave-browser --new-window --noerrdialogs --disable-infobars --kiosk --window-position=0,0 --user-data-dir="/home/username/Documents/Profiles/1" "http://INTERNAL_URL_2" &


sleep 30
xdotool mousemove 1670 1063 click 1
sleep 1
xdotool mousemove 957 19 click 1

```

---

### Post by Holger_Gehrke on 2023-05-30
Shouldn't that bold line read 'X-GNOME-Autostart-delay=60' ? If that doesn't work, you can just put another delay into the script before starting the browser(s). 60 seconds might be a bit much unless you're starting a lot of stuff in the background and you need the system to settle before starting more.

Holger

---

### Post by olliecampbell2 on 2023-05-30
> **Holger_Gehrke said:**
> Shouldn't that bold line read 'X-GNOME-Autostart-delay=60' ? If that doesn't work, you can just put another delay into the script before starting the browser(s). 60 seconds might be a bit much unless you're starting a lot of stuff in the background and you need the system to settle before starting more.

Holger


Apologies it was a typo....I've tried both separately already and it doesn't seem to make a difference.

---

