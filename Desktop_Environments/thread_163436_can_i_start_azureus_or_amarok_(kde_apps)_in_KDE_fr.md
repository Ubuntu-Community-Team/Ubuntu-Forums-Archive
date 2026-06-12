---
title: "can i start azureus or amarok (kde apps) in KDE from remote ssh terminal?"
date: 2006-04-20
forum: Desktop Environments
---

### Post by jetpeach on 2006-04-20
Is it possible to login to my machine remotely on a terminal, and start an application in KDE such that when I next go physically to my machine the application will be running in KDE?  It seems like this should be a relatively simple command in the terminal, but I'm uncertain if it's possible and have had trouble finding the answer (I have searched).

The reason for desiring this is, for example, so I can start azureus in KDE, control it using the webControl plugin in my browser from afar, then when I get home and sit down at my computer I see azureus running in KDE and can maximize and interface easily in KDE.   Another similar example is Amarok, where I may want to start it in KDE remotely so I can have access to the web control plugins for it as well.

Obviously, the simplest solution would be to just leave the apps running all the time in KDE, but azureus can be memory heavy and I've found my machine too slow when I leave many apps running.  I have also tried installing VNC and NX view- I didn't have success with VNC some difficult x-config issues where I couldn't get past a gray screen, and with NXview I have nice access but it runs on :0  or session 0 or whatever you call that (instead of :7 where KDE is running).  So then when I go home and am not using NXview I can't close or access the applications that I was running remotely without using top or ps to find and kill the process...

Ok, I think that is more than enough information, thanks in advance for any help,
jet

---

### Post by Parkotron on 2006-04-21
I don't know much about SSH so I can't really help you there. (Although I do believe there's a way to specify which display you'd like an app to open on when launched from the command line.) VNC, on the other hand, I'm fairly handy with. For your needs I would reccomend using KDE's built in VNC client, KRFB. (It's installed in Kubuntu by default.)

Most VNC clients create a separate display and launch a brand new session when you log into them remotely. This has its uses, but the majority of the I'd rather just use the existing session/display. For that you have to use either x11vnc (a very powerful command line VNC server) or one of the more modern GUI applications. For basic needs, KRFB is perfect. Just open up the settings, set a password and configure it to accept uninvited connections without prompting and you should be all set.

---

### Post by jetpeach on 2006-04-21
Thanks for mentioning X11vnc.  I looked around some and found this guide:

[http://blog.andrlik.org/2006/03/09/howto-access-your-desktop-remotely-in-linux/](http://blog.andrlik.org/2006/03/09/howto-access-your-desktop-remotely-in-linux/)
It was very useful and set me up fast and easily using tightvnc viewer and X11vnc as the server.  Now I get to control the actually desktop of my KDE install, so it works nice.  His guide was wrong on the command for storing the password though, but besides that works well.
jet

---

