---
title: "openbox session won't start"
date: 2007-04-28
forum: Desktop Environments
---

### Post by dbbolton on 2007-04-28
i decided to make a custom openbox session. here's what i did. first, i made a bash script.
```
gksudo gedit /usr/bin/openbox.sh
```
then
```
#!/bin/bash 
gnome-settings-daemon & 
gnome-volume-manager & 
fspanel & 
exec openbox
```
then
```
sudo chmod a+x /usr/bin/openbox.sh
```

ok, next i edited the desktop entry for Openbox:
```
gksudo gedit /usr/share/xsessions/openbox.desktop
```
and added this:
```
[Desktop Entry]
Encoding=UTF-8
Name=Openbox
Comment=Use this session to run Openbox as your desktop environment
Exec=/usr/bin/startob.sh
Icon=
Type=Application
```

when i logged in, i chose openbox from the sessions, and it worked fine. then i simply changed the line in the script from "fspanel &" to "perlpanel &", and the next time i logged in, it wouldn't load. the xsession errors said "couldn't load /usr/bin/openbox.sh- no such file or directory"! there clearly is such a file. 
so, i thought there might some naming conflict. i made a new script called "/usr/bin/startob.sh" with the exact same content as my old script, made it executable for all users, and added it in the openbox.desktop file. and the next time i tried to log in: "couldn't load /usr/bin/startob.sh no such file or directory"

why the hell is it saying that my scripts don't exist?

---

### Post by llamakc on 2007-04-28
Scratch what I said (twice now). Have you restarted GDM yet? 

sudo /etc/init.d/gdm restart

---

### Post by dbbolton on 2007-04-28
i did the same thing for both scripts:

```
sudo chmod a+x ...
```

---

### Post by dbbolton on 2007-04-28
i'm going to try putting the script in my home folder.

---

### Post by llamakc on 2007-04-28
You need to reload gdm after adding any customized sessions. The script is fine in /usr/bin if you have done `chmod a+x` on it. Restart GDM.

sudo /etc/init.d/gdm stop
sudo /etc/init.d/gdm start

---

### Post by dbbolton on 2007-04-28
> **llamakc said:**
> You need to reload gdm after adding any customized sessions. The script is fine in /usr/bin if you have done `chmod a+x` on it. Restart GDM.

sudo /etc/init.d/gdm stop
sudo /etc/init.d/gdm start

i ran  'sudo /etc/init.d/gdm restart', but it froze my comp. (there was a black screen with a blinking underscore, and when i tried ctrl+alt+backspace, it just printed ^H so i did a hard reboot) 

it STILL says that the script file can't be found. i triple checked everything.

here is .xsession-errors
```
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "daniel"
/etc/gdm/Xsession: Beginning session setup...
SESSION_MANAGER=local/mephista:/tmp/.ICE-unix/5240
I/O warning : failed to load external entity "/home/daniel/.config/openbox/debian-menu.xml"
I/O warning : failed to load external entity "/etc/xdg/openbox/debian-menu.xml"

(openbox:5331): ObParser-WARNING **: unable to find a valid menu file 'debian-menu.xml'
Gnome-Message: gnome_execute_async_with_env_fds: returning -1
Gnome-Message: gnome_execute_async_with_env_fds: returning -1
You can only run one xsettings manager at a time; exiting
** Message: plugin_get_value 1 (1)

** Message: plugin_get_value 2 (2)

** Message: plugin_get_value 1 (1)

** Message: plugin_get_value 2 (2)

** Message: plugin_get_value 1 (1)

** Message: plugin_get_value 2 (2)

** Message: plugin_get_value 1 (1)

** Message: plugin_get_value 2 (2)

** Message: plugin_get_value 1 (1)

** Message: plugin_get_value 2 (2)
```i definitely didn't delete or move those xml files. i really dont know what that refers to

---

### Post by llamakc on 2007-04-28
Those .xml errors are irrelevant. Openbox always throws them if you have not installed the 'menu' package.

Your .xsession-errors says nothing about a missing script or 'not found' when it comes to your openbox script.

You don't have Desktop Effects running, do you? 

I'm going to install openbox and try to recreate your error. BRB.

---

### Post by llamakc on 2007-04-28
Works for me. I installed "openbox obconf menu". I copied /usr/share/xsessions/openbox.desktop to /usr/share/xsessions/openbox-alt.desktop and edited it to call a script that I created in /usr/bin that had only the line "exec openbox".

I restarted gdm and am logged in right now inside of openbox.

PS: I didn't use a shebang of #!/bin/bash b/c sh works just fine. Here's what mine was:

#!/bin/sh
exec openbox

```

ken@llamakc 10:32:08:~$ ls -lh /usr/bin/openbox.sh 
-rwxr-xr-x 1 root root 23 2007-04-28 22:25 /usr/bin/openbox.sh

``````

#!/bin/sh
exec openbox

``````

[Desktop Entry]
Encoding=UTF-8
Name=Openbox-alt
Comment=Use this session to run Openbox as your desktop environment
Exec=/usr/bin/openbox.sh
Icon=
Type=Application

```

---

### Post by dbbolton on 2007-04-28
after following your example, the custom session works.

thank you very much !

---

