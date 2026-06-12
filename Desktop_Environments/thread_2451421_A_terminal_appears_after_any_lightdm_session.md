---
title: "A terminal appears after any lightdm session"
date: 2020-10-04
forum: Desktop Environments
---

### Post by Freiklite on 2020-10-04
Hi,
The Xubuntu 20.04 Release displays a terminal for two or three seconds after the lightdm session.
Then the desktop appears normaly.
Which file drives the process?
Can I rewrite it?
Thanks very much for your help,
D.B.

N.B.:
$ uname -a
Linux SATELLITE-C70D-B 5.4.0-48-generic #52-Ubuntu SMP Thu Sep 10 10:58:49 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux

~$ dpkg --status lightdm
Package: lightdm
Status: install ok installed

Hardware:
Toshiba  SATELLITE-C70D-B

---

### Post by Freiklite on 2020-10-05
This excerpt touches upon  the xfce4 theme with regard to xubuntu running process.
The "pstree command" says:
&#9500;&#9472;2*[kerneloops]
        &#9500;&#9472;lightdm&#9472;&#9516;&#9472;Xorg&#9472;&#9472;&#9472;12*[{Xorg}]
        &#9474;         &#9500;&#9472;lightdm&#9472;&#9516;&#9472;xfce4-session&#9472;&#9516;&#9472;Thunar&#9472;&#9472;&#9472;2*[{Thunar}]
        &#9474;         &#9474;         &#9474;               &#9500;&#9472;agent&#9472;&#9472;&#9472;2*[{agent}]
        &#9474;         &#9474;         &#9474;               &#9500;&#9472;applet.py
        &#9474;         &#9474;         &#9474;               &#9500;&#9472;blueman-applet&#9472;&#9472;&#9472;3*[{blueman-appl+
        &#9474;         &#9474;         &#9474;               &#9500;&#9472;kdeconnectd&#9472;&#9472;&#9472;5*[{kdeconnectd}]
        &#9474;         &#9474;         &#9474;               &#9500;&#9472;nm-applet&#9472;&#9472;&#9472;3*[{nm-applet}]
        &#9474;         &#9474;         &#9474;               &#9500;&#9472;polkit-gnome-au&#9472;&#9472;&#9472;2*[{polkit-gnom+
        &#9474;         &#9474;         &#9474;               &#9500;&#9472;ssh-agent
        &#9474;         &#9474;         &#9474;               &#9500;&#9472;update-notifier&#9472;&#9472;&#9472;3*[{update-noti+
        &#9474;         &#9474;         &#9474;               &#9500;&#9472;xfce4-panel&#9472;&#9516;&#9472;panel-1-whisker&#9472;&#9472;&#9472;2+
        &#9474;         &#9474;         &#9474;               &#9474;             &#9500;&#9472;panel-4-systray&#9472;&#9472;&#9472;2+
        &#9474;         &#9474;         &#9474;               &#9474;             &#9500;&#9472;panel-5-notific&#9472;&#9472;&#9472;2+
        &#9474;         &#9474;         &#9474;               &#9474;             &#9500;&#9472;panel-8-power-m&#9472;&#9472;&#9472;2+
        &#9474;         &#9474;         &#9474;               &#9474;             &#9500;&#9472;panel-9-pulseau&#9472;&#9472;&#9472;2+
        &#9474;         &#9474;         &#9474;               &#9474;             &#9500;&#9472;redshift-gtk&#9472;&#9516;&#9472;reds+
        &#9474;         &#9474;         &#9474;               &#9474;             &#9474;              &#9492;&#9472;2*[{+
        &#9474;         &#9474;         &#9474;               &#9474;             &#9492;&#9472;2*[{xfce4-panel}]
        &#9474;         &#9474;         &#9474;               &#9500;&#9472;xfce4-terminal&#9472;&#9516;&#9472;4*[bash]
        &#9474;         &#9474;         &#9474;               &#9474;                &#9500;&#9472;bash&#9472;&#9472;&#9472;pstree
        &#9474;         &#9474;         &#9474;               &#9474;                &#9492;&#9472;2*[{xfce4-termin+
        &#9474;         &#9474;         &#9474;               &#9500;&#9472;xfdesktop&#9472;&#9472;&#9472;2*[{xfdesktop}]
        &#9474;         &#9474;         &#9474;               &#9500;&#9472;xfwm4&#9472;&#9472;&#9472;13*[{xfwm4}]
        &#9474;         &#9474;         &#9474;               &#9500;&#9472;xiccd&#9472;&#9472;&#9472;2*[{xiccd}]
        &#9474;         &#9474;         &#9474;               &#9500;&#9472;xscreensaver
        &#9474;         &#9474;         &#9474;               &#9500;&#9472;zeitgeist-datah&#9472;&#9472;&#9472;6*[{zeitgeist-d+
        &#9474;         &#9474;         &#9474;               &#9492;&#9472;2*[{xfce4-session}]
        &#9474;         &#9474;         &#9492;&#9472;2*[{lightdm}]
        &#9474;         &#9492;&#9472;2*[{lightdm}]
        &#9500;&#9472;networkd-dispat

The bug may be at that level:
&#9472;lightdm&#9472;&#9516;&#9472;xfce4-session&#9472;&#9516;&#9472;Thunar&#9472;&#9472;&#9472;2*[{Thunar}]

Thank you for your attention.
Any suggestion is welcome.

---

### Post by &amp;KyT$0P# on 2020-10-08
In Settings > Session and Startup, do you have a "Saved Sessions" tab?
What do you have enabled under Application Autostart?

---

