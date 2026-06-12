---
title: "Gnome session crashes only when being launched through systemd service?"
date: 2019-09-17
forum: Desktop Environments
---

### Post by dereksmilees on 2019-09-17
I have been googling and googling and am at the end of my rope here looking for some sort of explanation.



I've been trying to follow [this]("https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-vnc-on-ubuntu-18-04") guide and [this]("https://www.tecmint.com/install-and-configure-vnc-server-on-ubuntu/") guide to get vnc running as a system service using the gnome desktop on Ubuntu 18.04. I've been struggling, and am honestly quite surprised how hard this has been.

I've got the initial vnc server running - if I run "vncserver :1 -localhost no -geometry 1920x1080 -depth 32", for example, it does spin up a vnc server. I can connect to it, it displays things, no problem. [Here]("https://pastebin.com/zDcF1NLS") is my xstartup file. My issue is with the systemd unit file and getting it to work as a system service.



[Here]("https://pastebin.com/utZ914YG")is my current "/etc/systemd/system/vncserver@.service" file. The vnc log file (~/.vnc/testvm01.domain.local\:1.log) shows no errors.  "Systemctl status [EMAIL="vncserver@1.servic"]vncserver@1.servic[/EMAIL]e" even shows the vnc server as active (running), and I am able to connect to it, but I only get a black screen.



The following is the error from my systemctl status page:



    Sep 17 23:32:55 testvm03 gnome-session[3901]: gnome-session-binary[3901]: WARNING: App 'org.gnome.Shell.desktop' exited with code 1
    Sep 17 23:32:55 testvm03 gnome-session-binary[3901]: WARNING: App 'org.gnome.Shell.desktop' exited with code 1
    Sep 17 23:32:55 testvm03 org.gnome.Shell.desktop[3977]: Window manager warning: Unsupported session type
    Sep 17 23:32:55 testvm03 gnome-session[3901]: gnome-session-binary[3901]: WARNING: App 'org.gnome.Shell.desktop' exited with code 1
    Sep 17 23:32:55 testvm03 gnome-session-binary[3901]: WARNING: App 'org.gnome.Shell.desktop' exited with code 1
    Sep 17 23:32:55 testvm03 gnome-session[3901]: gnome-session-binary[3901]: WARNING: App 'org.gnome.Shell.desktop' respawning too quickly
    Sep 17 23:32:55 testvm03 gnome-session-binary[3901]: WARNING: App 'org.gnome.Shell.desktop' respawning too quickly
    Sep 17 23:32:55 testvm03 gnome-session-binary[3901]: Unrecoverable failure in required component org.gnome.Shell.desktop
    Sep 17 23:32:55 testvm03 gnome-session[3901]: gnome-session-binary[3901]: CRITICAL: We failed, but the fail whale is dead. Sorry....
    Sep 17 23:32:55 testvm03 gnome-session-binary[3901]: CRITICAL: We failed, but the fail whale is dead. Sorry....

Why does this happen only when the vnc is launched through the service, and not when launched through the normal command line method? And how can I stop gnome from crashing?




Thanks for the help! I've posted on reddit, googled, I've been struggling with this for a few days now.

---

### Post by iuridiniz on 2019-09-21
I've exactly the same problem, it does not work if I starting by using systemd (only gnome3 has this failure, lxde and fluxbox works fine with systemd). If I start manually gnome3 works.

---

### Post by iuridiniz on 2019-09-21
It's seems a issue with systemd, if I use a beta version (1.9.80) or a old version (1.8.0), the server start but I get a black screen. There's a issue for this on github: [https://github.com/TigerVNC/tigervnc/issues/684](https://github.com/TigerVNC/tigervnc/issues/684)

---

### Post by iuridiniz on 2019-09-22
Well, I give up this method, so I'm using lightdm, it just works
I've followed this guide: [https://wiki.archlinux.org/index.php/LightDM#VNC_Server](https://wiki.archlinux.org/index.php/LightDM#VNC_Server)
This is my config:
```

# /etc/lightdm/lightdm.conf

[LightDM]
start-default-seat=false

[VNCServer]
enabled=true
command=Xvnc -rfbauth /etc/vncpasswd
port=5900
listen-address=0.0.0.0
width=2560
height=1080

```

---

