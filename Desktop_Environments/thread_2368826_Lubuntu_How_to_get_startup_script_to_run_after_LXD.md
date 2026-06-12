---
title: "Lubuntu: How to get startup script to run after LXDE/Openbox Desktop loaded /running"
date: 2017-08-15
forum: Desktop Environments
---

### Post by keyz on 2017-08-15
I am running 
- Lubuntu latest version 16.04.3 LTS with 32-bit kernel 4.4.0-92-generic (i686)
- The desktop environment is LXDE / Openbox.

I am struggling to find a way to run a start-up script **after** the  Desktop environment has loaded.

This may be a version dependent problem as I have tried a number of solutions after a reasonably broad look across the internet using Google.

I have tried putting a text file named **autostart**, that contains only 
@/path_to/start_up.sh 
in a number of different directories with no success. 

I do not wish to use
'Menu > Preferences > Default applications for LxSession'
as this does not reliably run my start-up.sh, nor does it always autostart my default start-up apps.

Can anyone provide a tried and tested solution for autostart that will run a script called start-up.sh after the LXDE desktop is loaded.

(Ideas tested include placing autostart in
 /home/user/.config/autostart
or
/home/user/.config/openbox
or
/etc/xdg/autostart
or
/etc/xdg/lxsession/Lubuntu
etc
Also tried modifying /etc/rc.local which did not work either)

---

### Post by again? on 2017-08-16
Check you're in the Lubuntu session.
```
echo $DESKTOP_SESSION
```

```

```The file to use in the default Lubuntu session is ~/.config/lxsession/Lubuntu/autostart
and the entry doesn't require the "@" prefix, just the full path to the script.
eg
```
/home/**username**/scripts/start-up.sh
```

Make sure script is executable
```
chmod +x /path/to/start-up.sh
```

---

### Post by Claus7 on 2018-06-14
Hello,

just to mention that the procedure proposed by *guber2* does not work if the command requires root privileges. This was tested under lubuntu 18.04. 
In that case sudo visudo is proposed.

Regards!

---

