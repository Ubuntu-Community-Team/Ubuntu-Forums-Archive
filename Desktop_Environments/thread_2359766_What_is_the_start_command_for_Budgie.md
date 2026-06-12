---
title: "What is the start command for Budgie?"
date: 2017-04-27
forum: Desktop Environments
---

### Post by sc4s2cg on 2017-04-27
Hello,

I'm trying to start Budgie in a headless VNC but having some troubles. I am able to start xfce using startxfce4, is there an equivalent command to start Budgie from the terminal? I've tried a multitude of commands so far:

[LIST]
[*]start budgie-desktop
[*][start-budgie]("https://github.com/budgie-desktop/budgie-desktop/issues/308") (looks like that script was never implemented)
[*]exec budgie-desktop
[*]exec budgie
[*]exec gnome-session --session=budgie-desktop (this one just closes the terminal without bringing up a GUI)
[*]startxbudgie-desktop
[*]budgie-desktop
[/LIST]

I've been Googling for a couple hours now but no luck.

---

### Post by SantaFe on 2017-04-27
Have you tried startx?

---

### Post by sc4s2cg on 2017-04-27
> **SantaFe said:**
> Have you tried startx?

Yes, I get the following:

```
@ubuntu18:~$ startx


X.Org X Server 1.18.4
Release Date: 2016-07-19
X Protocol Version 11, Revision 0
Build Operating System: Linux 4.4.0-45-generic x86_64 Ubuntu
Current Operating System: Linux ubuntu18 4.4.0-62-generic #83-Ubuntu SMP Wed Jan 18 14:10:15 UTC 2017 x86_64
Kernel command line: console=ttyS0 BOOT_IMAGE=/vmlinuz-4.4.0-62-generic root=/dev/mapper/ubuntu18--vg-root ro
Build Date: 02 November 2016  10:06:10PM
xorg-server 2:1.18.4-0ubuntu0.2 (For technical support please see http://www.ubuntu.com/support)
Current version of pixman: 0.33.6
        Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/home/peter/.local/share/xorg/Xorg.0.log", Time: Thu Apr 27 13:38:31 2017
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
(EE)
Fatal server error:
(EE) parse_vt_settings: Cannot open /dev/tty0 (Permission denied)
(EE)
(EE)
Please consult the The X.Org Foundation support
         at http://wiki.x.org
 for help.
(EE) Please also check the log file at "/home/peter/.local/share/xorg/Xorg.0.log" for additional information.
(EE)
(EE) Server terminated with error (1). Closing log file.
xinit: giving up
xinit: unable to connect to X server: Connection refused
xinit: server error
Couldn't get a file descriptor referring to the console

```

Not sure what to make of it. The log file is a copy-paste of the output above. If I try to chmod /tty0 I get a permission denied error.

---

### Post by Bashing-om on 2017-04-27
sc4s2cg; Hello;

I have not seen budgie - so my knowledge base is lacking . But
We can find out !
What is the initiate system we have here ?
show :
```

ps -p1 | grep systemd && echo systemd || echo upstart

```
what release base is this ?
```

lsb_release -a

```
display manager ?
```

cat /etc/X11/default-display-manager
echo $DESKTOP_SESSION

```
with the thought that systemctl can handle this nicely.

[INDENT][INDENT]good little budgie, good budgie
[INDENT][INDENT][INDENT]tell it what to do and how
[INDENT][INDENT][INDENT]will do !
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by ajgreeny on 2017-04-27
If I make two assumptions, first that budgie uses lightdm as display manager, and second, that it uses systemd like most other *buntu distros, I believe that you will need to use command ```
systemctl start lightdm service
```
Try that but edit it if budgie uses some other display manager to see if that gets you anywhere.

---

### Post by sc4s2cg on 2017-04-27
> **Bashing-om said:**
> sc4s2cg; Hello;

I have not seen budgie - so my knowledge base is lacking . But
We can find out !
What is the initiate system we have here ?
show :
```

ps -p1 | grep systemd && echo systemd || echo upstart

```
what release base is this ?
```

lsb_release -a

```
display manager ?
```

cat /etc/X11/default-display-manager
echo $DESKTOP_SESSION

```
with the thought that systemctl can handle this nicely.

[INDENT][INDENT]good little budgie, good budgie
[INDENT][INDENT][INDENT]tell it what to do and how
[INDENT][INDENT][INDENT]will do !
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

Thanks! Here is what I got based on your suggestions:

```
sc@ubuntu18:~$ ps -p1 | grep systemd && echo systemd || echo upstart
    1 ?        00:00:01 systemd
systemd
sc@ubuntu18:~$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 16.04.2 LTS
Release:        16.04
Codename:       xenial
sc@ubuntu18:~$ cat /etc/X11/default-display-manager
cat: /etc/X11/default-display-manager: No such file or directory
sc@ubuntu18:~$ echo $DESKTOP_SESSION

sc@ubuntu18:~$

```

So it looks like I'm missing some packages?

> **ajgreeny said:**
> If I make two assumptions, first that budgie uses lightdm as display manager, and second, that it uses systemd like most other *buntu distros, I believe that you will need to use command ```
systemctl start lightdm service
```
Try that but edit it if budgie uses some other display manager to see if that gets you anywhere.

Hm, it looks like budgie doesn't use lightdm? Is there anyway I could find out what it uses?

Edit: it looks like [Budgie is using]("https://github.com/budgie-desktop/budgie-desktop/issues/760") libmutter, however I am unable to start the service. I get the same error as below.

```
sc@ubuntu18:~$ systemctl start lightdm service
==== AUTHENTICATING FOR org.freedesktop.systemd1.manage-units ===
Authentication is required to start 'lightdm.service'.
Authenticating as: sc,,, (sc)
Password: 
==== AUTHENTICATION COMPLETE ===
Failed to start lightdm.service: Unit lightdm.service not found.
==== AUTHENTICATING FOR org.freedesktop.systemd1.manage-units ===
Authentication is required to start 'service.service'.
Authenticating as: sc,,, (sc)
Password: 
==== AUTHENTICATION COMPLETE ===
Failed to start service.service: Unit service.service not found.
sc@ubuntu18:~$ 
```

---

### Post by Bashing-om on 2017-04-27
sc4s2cg; Well !

Let's try another  way to find the display .
```

ls -al /usr/share/xsessions/

```

[INDENT][INDENT]if at 1st you do not succeed
[/INDENT][/INDENT]

---

### Post by ajgreeny on 2017-04-28
So what output do you get from command ```
cat /etc/X11/default-display-manager
```

Perhaps you do not have a display manager for some reason, which could be why you are having these problems.

---

### Post by sc4s2cg on 2017-04-28
> **Bashing-om said:**
> sc4s2cg; Well !

Let's try another  way to find the display .
```

ls -al /usr/share/xsessions/

```

[INDENT][INDENT]if at 1st you do not succeed
[/INDENT][/INDENT]

Hm, for this one I got:

```
r@ubuntu18:~$ ls -al /usr/share/xsessions/
total 32
drwxr-xr-x   2 root root  4096 Apr 27 11:30 .
drwxr-xr-x 211 root root 12288 Apr 27 17:54 ..
-rw-r--r--   1 root root  4613 Apr 23 06:56 budgie-desktop.desktop
-rw-r--r--   1 root root  5465 May 25  2015 xfce.desktop

```

> **ajgreeny said:**
> So what output do you get from command ```
cat /etc/X11/default-display-manager
```

Perhaps you do not have a display manager for some reason, which could be why you are having these problems.

For that I get 

```
/usr/sbin/lightdm
```

That's weird, since I couldn't start lightdm using one of the above commands. I was able to start an xfce DE using startxfce4 however.

---

### Post by ajgreeny on 2017-04-28
Let's see if the whole DM startup thing is backwards compatible with command ```
sudo service lightdm start
```
It may also be worth trying to reconfigure lightdm with ```
sudo dpkg --configure lightdm
```

---

### Post by sc4s2cg on 2017-04-28
Looks like lightdm did start with that first command, didn't get any errors, although no GUI yet. I tried the 

```
systemctl start lightdm service
```

command again, but got hit with a "Failed to start service.service: Unit service.service not found" error again. 

The second command hit me with an error:

```
r@ubuntu18:~$ sudo dpkg --configure lightdm
dpkg: error processing package lightdm (--configure):
 package lightdm is already installed and configured
Errors were encountered while processing:
 lightdm
r@ubuntu18:~$ 
```

Wanted to update with latest result. I installed gnome DE to see if I could start it, but I couldn't. Eventually I got an error message that led me to the following:

```
r@ubuntu18:~$ systemctl status lightdm.service
&#9679; lightdm.service - Light Display Manager
   Loaded: loaded (/lib/systemd/system/lightdm.service; enabled; vendor preset: 
  Drop-In: /lib/systemd/system/display-manager.service.d
           &#9492;&#9472;xdiagnose.conf
   Active: inactive (dead) (Result: exit-code) since Sat 2017-04-29 10:41:22 EDT
     Docs: man:lightdm(1)
 Main PID: 1553 (code=exited, status=1/FAILURE)

Apr 29 10:41:22 ubuntu18 systemd[1]: lightdm.service: Main process exited, code=
Apr 29 10:41:22 ubuntu18 systemd[1]: lightdm.service: Unit entered failed state.
Apr 29 10:41:22 ubuntu18 systemd[1]: lightdm.service: Failed with result 'exit-c
Apr 29 10:41:22 ubuntu18 systemd[1]: lightdm.service: Service hold-off time over
Apr 29 10:41:22 ubuntu18 systemd[1]: Stopped Light Display Manager.
Apr 29 10:41:22 ubuntu18 systemd[1]: lightdm.service: Start request repeated too
Apr 29 10:41:22 ubuntu18 systemd[1]: Failed to start Light Display Manager. 
```

---

### Post by Bashing-om on 2017-04-30
sc4s2cg; Well !!

So lightdm is not able to start . I have no access to a budgie desktop, so not able to establish/confirm a path directly. Hunt and peck and see what we can learn ?
Maybe start at :
```

ls -al /usr/share/xsessions/

```
to get the name of the desktop we are trying to start .

And also, if worse comes to worse, can we re-install "that" desktop ?
what shows for:
```

apt list budgie-desktop budgie-core

```

[INDENT][INDENT]in a process of learning
[INDENT][INDENT][INDENT]inquiring minds want to know
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

