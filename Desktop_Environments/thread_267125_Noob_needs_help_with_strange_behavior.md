---
title: "Noob needs help with strange behavior"
date: 2006-09-28
forum: Desktop Environments
---

### Post by knichel on 2006-09-28
I am running the latest of Dapper and I use kde.  I was giving a presentation last night and my laptop went to sleep during the presentation.  Since then strange behavior.

1)  My Storage Media applet has disappeared and when I try to add it back and configure it, no devices show up for me to mount  (I have an external HD (firewire) and a usb flash drive).

2)  My Battery Monitor is cookey.  My battery indicator goes between full and empty randomly.  The screen occasionally goes black and there is some error messages on the top, but they go away too quickly for me to read them and the screen comes back.  Almost like it is going to sleep and waking right back up.  The battery monitor tells me that there  is no battery present, but currently my AC adapter is unplugged to test this notion.  I like not having a power sourcce ;) .

3)  When I go to the KDE Control Center, there are not items on the left side of  the screen.  I created a new user and launched the KDE Control Center and it worked fine.  I have been using the System Settings program to configure my laptop. 

I do not know what to do short of formatting and reinstalling.  With Windows I used to just re-install over top and it usually fixed the problems.  I understand that with linux this is not possible (or am I mistaken)?

Thanks in advance for any assistance.

Mike

---

### Post by sgbeamer on 2006-09-28
I don't know much about KDE because I use Gnome but it's unlikely that you need to re-install.  Check your logs and see if anything is going on that looks strange. All the logs are located in /var/log.  Check messages and Xorg.0.log.   If none of that works try re-installing the KDE base package (this will keep all your settings, files, etc).  If all else fails load up the XFCE window manager xfwm4 and see if your problems go away running that. That will at least help you narrow down to whether it's a system problem or a KDE problem.

---

### Post by ingo on 2006-09-28
If I were you I'd delete the ~/.kde directory. So if you start KDE again it will come up as it did after your first install and with any luck all your problems should have gone...

HTH

---

