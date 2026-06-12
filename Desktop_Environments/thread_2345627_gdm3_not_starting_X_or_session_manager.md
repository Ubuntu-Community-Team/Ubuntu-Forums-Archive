---
title: "gdm3 not starting X or session manager"
date: 2016-12-06
forum: Desktop Environments
---

### Post by adrhc on 2016-12-06
Hi, I have:


# uname -a
Linux adr-desktop 4.4.0-51-generic #72-Ubuntu SMP Thu Nov 24 18:29:54 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux
# lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.1 LTS
Release:    16.04
Codename:    xenial
# ls -l /etc/alternatives/x-session-manager
lrwxrwxrwx 1 root root 19 Apr 27  2016 /etc/alternatives/x-session-manager -> /usr/bin/startxfce4
# ls -l /etc/alternatives/x-window-manager
lrwxrwxrwx 1 root root 16 Dec  5 01:33 /etc/alternatives/x-window-manager -> /usr/bin/openbox
# update-alternatives --list x-window-manager
/usr/bin/cinnamon-session-cinnamon
/usr/bin/cinnamon-session-cinnamon2d
/usr/bin/marco
/usr/bin/mutter
/usr/bin/openbox
/usr/bin/xfwm4


GDM3 is not working; luckily lightdm is working and I try to fix GDM3.


I do:
sudo systemctl stop lightdm
sudo dpkg-reconfigure gdm3
sudo systemctl start gdm
and I get nothing in .xsession-errors
When I access tty7 I get a blank black screen.
When I go to tty1 and write startx I get the XFCE fine working session.


What is the problem?  :(

Here is the end of the log (see the entire log attached):

Dec  6 13:27:19 adr-desktop /usr/lib/gdm3/gdm-x-session[11354]: (**) Option "config_info" "udev:/sys/devices/virtual/input/input24/event8"
Dec  6 13:27:19 adr-desktop /usr/lib/gdm3/gdm-x-session[11354]: (II) XINPUT: Adding extended input device "G15 Extra Keys" (type: KEYBOARD, id 15)
Dec  6 13:27:19 adr-desktop /usr/lib/gdm3/gdm-x-session[11354]: (**) Option "xkb_rules" "evdev"
Dec  6 13:27:19 adr-desktop /usr/lib/gdm3/gdm-x-session[11354]: (**) Option "xkb_model" "pc105"
Dec  6 13:27:19 adr-desktop /usr/lib/gdm3/gdm-x-session[11354]: (**) Option "xkb_layout" "us"
Dec  6 13:27:19 adr-desktop /usr/lib/gdm3/gdm-x-session[11354]: Activating service name='org.a11y.Bus'
Dec  6 13:27:19 adr-desktop /usr/lib/gdm3/gdm-x-session[11354]: Successfully activated service 'org.a11y.Bus'
Dec  6 13:27:19 adr-desktop org.a11y.Bus[11362]: Activating service name='org.a11y.atspi.Registry'
Dec  6 13:27:19 adr-desktop org.a11y.Bus[11362]: ** (process:11370): WARNING **: Failed to register client: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files
Dec  6 13:27:19 adr-desktop org.a11y.Bus[11362]: Successfully activated service 'org.a11y.atspi.Registry'
Dec  6 13:27:19 adr-desktop org.a11y.atspi.Registry[11375]: SpiRegistry daemon is running with well-known name - org.a11y.atspi.Registry
Dec  6 13:27:19 adr-desktop /usr/lib/gdm3/gdm-x-session[11354]: Activating service name='org.gnome.ScreenSaver'
Dec  6 13:27:19 adr-desktop org.gnome.ScreenSaver[11362]: ** (gnome-screensaver:11386): WARNING **: Couldn't get presence status: The name org.gnome.SessionManager was not provided by any .service files
Dec  6 13:27:19 adr-desktop /usr/lib/gdm3/gdm-x-session[11354]: Successfully activated service 'org.gnome.ScreenSaver'
Dec  6 13:27:19 adr-desktop gnome-session-binary[11365]: Entering running state
Dec  6 13:27:19 adr-desktop gnome-session[11365]: openConnection: connect: No such file or directory
Dec  6 13:27:19 adr-desktop gnome-session[11365]: cannot connect to brltty at :0
Dec  6 13:27:23 adr-desktop /usr/lib/gdm3/gdm-x-session[11354]: (II) AIGLX: Suspending AIGLX clients for VT switch
Dec  6 13:27:23 adr-desktop /usr/lib/gdm3/gdm-x-session[11354]: (II) systemd-logind: got pause for 13:72
Dec  6 13:27:23 adr-desktop /usr/lib/gdm3/gdm-x-session[11354]: (II) systemd-logind: got pause for 13:68
Dec  6 13:27:23 adr-desktop /usr/lib/gdm3/gdm-x-session[11354]: (II) systemd-logind: got pause for 13:67
Dec  6 13:27:23 adr-desktop /usr/lib/gdm3/gdm-x-session[11354]: (II) systemd-logind: got pause for 13:70
Dec  6 13:27:23 adr-desktop /usr/lib/gdm3/gdm-x-session[11354]: (II) systemd-logind: got pause for 13:66
Dec  6 13:27:23 adr-desktop /usr/lib/gdm3/gdm-x-session[11354]: (II) systemd-logind: got pause for 13:84
Dec  6 13:27:23 adr-desktop /usr/lib/gdm3/gdm-x-session[11354]: (II) systemd-logind: got pause for 13:69
Dec  6 13:27:23 adr-desktop /usr/lib/gdm3/gdm-x-session[11354]: (II) systemd-logind: got pause for 13:64
Dec  6 13:27:23 adr-desktop /usr/lib/gdm3/gdm-x-session[11354]: (II) systemd-logind: got pause for 226:0
Dec  6 13:27:23 adr-desktop /usr/lib/gdm3/gdm-x-session[11354]: (II) systemd-logind: got pause for 13:71
Dec  6 13:27:23 adr-desktop /usr/lib/gdm3/gdm-x-session[11354]: (II) systemd-logind: got pause for 13:65
Dec  6 13:27:46 adr-desktop /usr/lib/gdm3/gdm-x-session[11354]: (II) systemd-logind: got resume for 13:72
Dec  6 13:27:46 adr-desktop /usr/lib/gdm3/gdm-x-session[11354]: (II) systemd-logind: got resume for 13:68
Dec  6 13:27:46 adr-desktop /usr/lib/gdm3/gdm-x-session[11354]: (II) systemd-logind: got resume for 13:67
Dec  6 13:27:46 adr-desktop /usr/lib/gdm3/gdm-x-session[11354]: (II) systemd-logind: got resume for 13:70
Dec  6 13:27:46 adr-desktop /usr/lib/gdm3/gdm-x-session[11354]: (II) systemd-logind: got resume for 13:66
Dec  6 13:27:46 adr-desktop /usr/lib/gdm3/gdm-x-session[11354]: (II) systemd-logind: got resume for 13:84
Dec  6 13:27:46 adr-desktop /usr/lib/gdm3/gdm-x-session[11354]: (II) systemd-logind: got resume for 13:69
Dec  6 13:27:46 adr-desktop /usr/lib/gdm3/gdm-x-session[11354]: (II) systemd-logind: got resume for 13:64
Dec  6 13:27:46 adr-desktop /usr/lib/gdm3/gdm-x-session[11354]: (II) systemd-logind: got resume for 226:0
Dec  6 13:27:46 adr-desktop /usr/lib/gdm3/gdm-x-session[11354]: (II) AIGLX: Resuming AIGLX clients after VT switch
Dec  6 13:27:46 adr-desktop /usr/lib/gdm3/gdm-x-session[11354]: (II) intel(0): switch to mode 1680x1050@60.0 on HDMI1 using pipe 0, position (0, 0), rotation normal, reflection none
Dec  6 13:27:46 adr-desktop /usr/lib/gdm3/gdm-x-session[11354]: (II) systemd-logind: got resume for 13:71
Dec  6 13:27:46 adr-desktop /usr/lib/gdm3/gdm-x-session[11354]: (II) systemd-logind: got resume for 13:65
Dec  6 13:27:49 adr-desktop /usr/lib/gdm3/gdm-x-session[11354]: (II) AIGLX: Suspending AIGLX clients for VT switch
Dec  6 13:27:49 adr-desktop /usr/lib/gdm3/gdm-x-session[11354]: (II) systemd-logind: got pause for 13:72
Dec  6 13:27:49 adr-desktop /usr/lib/gdm3/gdm-x-session[11354]: (II) systemd-logind: got pause for 13:68
Dec  6 13:27:49 adr-desktop /usr/lib/gdm3/gdm-x-session[11354]: (II) systemd-logind: got pause for 13:67
Dec  6 13:27:49 adr-desktop /usr/lib/gdm3/gdm-x-session[11354]: (II) systemd-logind: got pause for 13:70
Dec  6 13:27:49 adr-desktop /usr/lib/gdm3/gdm-x-session[11354]: (II) systemd-logind: got pause for 13:66
Dec  6 13:27:49 adr-desktop /usr/lib/gdm3/gdm-x-session[11354]: (II) systemd-logind: got pause for 13:84
Dec  6 13:27:49 adr-desktop /usr/lib/gdm3/gdm-x-session[11354]: (II) systemd-logind: got pause for 13:69
Dec  6 13:27:49 adr-desktop /usr/lib/gdm3/gdm-x-session[11354]: (II) systemd-logind: got pause for 13:64
Dec  6 13:27:49 adr-desktop /usr/lib/gdm3/gdm-x-session[11354]: (II) systemd-logind: got pause for 226:0
Dec  6 13:27:49 adr-desktop /usr/lib/gdm3/gdm-x-session[11354]: (II) systemd-logind: got pause for 13:71
Dec  6 13:27:49 adr-desktop /usr/lib/gdm3/gdm-x-session[11354]: (II) systemd-logind: got pause for 13:65

---

