---
title: "Why is &quot;xfwm4 --replace&quot; running?"
date: 2018-02-13
forum: Desktop Environments
---

### Post by vasa1 on 2018-02-13
I'm trying out Xubuntu 16.04 as guest OS in a virtual machine with Kubuntu 16.04 as host.

I notice that *xfwm4 --replace* seems to be running continuously. If it's not an artifact of running in a VM, why should *xfwm4 --replace* be running at all?

**Edit**: [s]in *top* the same process appears simply as *xfwm4* which seems logical :???:[/s]

```
vasa1@vasa1-xubu:~$ ps axjf | grep -i xfwm4
 1119  1323  1302  1302 ?           -1 S     1000   0:02          \_ xfwm4 --replace
 1604  1869  1868  1604 pts/1     1868 S+    1000   0:00          |       \_ grep --color=auto -i xfwm4
vasa1@vasa1-xubu:~$ 
```

---

### Post by ajgreeny on 2018-02-13
I get the same output on my hard metal install of Xubuntu 16.04 
```
user@XubuntuXenial:~$ ps axjf | grep -i xfwm4
138: 3447  3620  3596  3596 ?           -1 S     1000   1:21          \_ xfwm4 --replace
153:18617 18637 18636 18617 pts/1    18636 S+    1000   0:00          |           \_ grep -n --color -i xfwm4
user@XubuntuXenial:~$ 
```
so I don't think it has anything to do with yours being a VM.

I will have a look shortly at my 18.04 virtual installation in VBox to see if the same is true of that.

[COLOR="#FF0000"]EDIT:[/COLOR]
Yes, it's the same in 18.04 as well.
Interesting find but I'm not sure what to make of it; I wonder if all the Ubuntu OS DE versions have the same or similar output for whichever WM is used by them.

I have VMs of Ubuntu 18.04 and Lubuntu 18.04 so will check them when I get spare time and report back.

---

### Post by VMC on 2018-02-13
Same with my 17.10 xubuntu:
```
1   844   720   720 ?           -1 S     1000   0:00 xfwm4 --replace
 1304  1317  1316  1304 pts/0     1316 S+    1000   0:00      \_ grep --color=auto -i xfwm4
```
but with my manjaro xfce I don't get "--replace". Its only on ubuntu . Interesting.

xubuntu 17.10
```
$ xfwm4 --version
	This is xfwm4 version 4.12.4 (revision 7844952) for Xfce 4.12
	Released under the terms of the GNU General Public License.
	Compiled against GTK+-2.24.31, using GTK+-2.24.31.


	Build configuration and supported features:
	- Startup notification support:                 Yes
	- XSync support:                                Yes
	- Render support:                               Yes
	- Xrandr support:                               Yes
	- Embedded compositor:                          Yes
	- KDE systray proxy (deprecated):               No
```

---

### Post by vasa1 on 2018-02-13
> **ajgreeny said:**
> ...
Yes, it's the same in 18.04 as well.
Interesting find but I'm not sure what to make of it; I wonder if all the Ubuntu OS DE versions have the same or similar output for whichever WM is used by them.

I have VMs of Ubuntu 18.04 and Lubuntu 18.04 so will check them when I get spare time and report back.
I feel it should just be xfwm4.

If I understand correctly, the "--replace" is used to switch window managers during a session. So if I installed Openbox in Xubuntu and wished to make Openbox handle window management in a current session instead of xfwm4, I'd run *openbox --replace*.

[https://unix.stackexchange.com/questions/298093/switch-window-manager-while-running](https://unix.stackexchange.com/questions/298093/switch-window-manager-while-running)
[https://askubuntu.com/questions/159505/how-to-switch-windows-manager-on-the-fly](https://askubuntu.com/questions/159505/how-to-switch-windows-manager-on-the-fly)

---

### Post by VMC on 2018-02-13
I think its just how it processed and executed the program. Notice the 'S' (sleep) besides 'xfwm4 --replace'
```
 718 ?        S      0:04 xfwm4 --replace  723 ?        Sl     0:00 xfce4-panel
  725 ?        S      0:00 Thunar --daemon
  727 ?        Sl     0:01 xfdesktop
  728 ?        S      0:00 sh -c sleep 13;plank
```

Also notice the sleep I but on 'plank' from the Autostart. That has come and gone and now sleeping 'S'

---

### Post by VMC on 2018-02-13
Here's something strange. I booting non-graphical as stated here:
[https://unix.stackexchange.com/questions/164005/non-graphical-boot-with-systemd/164028#164028](https://unix.stackexchange.com/questions/164005/non-graphical-boot-with-systemd/164028#164028)

Then executed 'startx'. After boot-up I now have 'xf4wm4' without '--replace'

```
746 tty1     S+     0:00 /bin/sh /usr/bin/**startx**
  768 tty1     S+     0:00 xinit /etc/X11/xinit/xinitrc -- /etc/X11/xinit/xserve
  769 tty1     Sl     0:01 /usr/lib/xorg/Xorg -nolisten tcp :0 vt1 -keeptty -aut
  774 tty1     S      0:00 /bin/sh /etc/xdg/xfce4/xinitrc -- /etc/X11/xinit/xser
  784 ?        Ss     0:00 /usr/bin/dbus-daemon --session --address=systemd: --n
  812 ?        Ss     0:00 /usr/bin/ssh-agent /usr/bin/im-launch x-session-manag
  830 tty1     Sl     0:00 xfce4-session
  834 ?        S      0:00 /usr/lib/x86_64-linux-gnu/xfce4/xfconf/xfconfd
  838 ?        Ss     0:00 /usr/bin/gpg-agent --sh --daemon --write-env-file /ho
[COLOR=#ff0000]  840 tty1     S      0:00 xfwm4
[/COLOR]  844 tty1     Sl     0:00 xfce4-panel
  846 tty1     S      0:00 Thunar --daemon
  848 tty1     Sl     0:00 xfdesktop
  849 tty1     S      0:00 sh -c sleep 13;plank
```

---

### Post by vasa1 on 2018-02-13
I've don't understand the intricacies of `ps` but```

vasa1@vasa1-xubu:~$ ppp | grep -Ei "(PPID|xfwm4|firefox)" | cut -c -120
 PPID   PID  PGID   SID TTY      TPGID STAT   UID   TIME COMMAND
 1363  1567  1546  1546 ?           -1 S     1000   0:08          \_ xfwm4 --replace
 4107  4427  4426  4107 pts/2     4426 S+    1000   0:00          |       \_ grep --color=auto -Ei (PPID|xfwm4|firefox)
 1363  4210  1579  1579 ?           -1 Sl    1000   0:28          \_ /usr/lib/firefox/firefox
 4210  4263  1579  1579 ?           -1 Sl    1000   0:51              \_ /usr/lib/firefox/firefox -contentproc -childID 
 4210  4327  1579  1579 ?           -1 Sl    1000   0:00              \_ /usr/lib/firefox/firefox -contentproc -childID 
vasa1@vasa1-xubu:~$ 
```while Firefox was playing a YouTube video.

And re. other desktop environments,```
$ pgrep -a kwin
1775 kwin_x11
$ 
```

---

