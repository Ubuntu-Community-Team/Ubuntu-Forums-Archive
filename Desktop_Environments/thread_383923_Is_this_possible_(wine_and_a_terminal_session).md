---
title: "Is this possible? (wine and a terminal session)"
date: 2007-03-13
forum: Desktop Environments
---

### Post by tee2 on 2007-03-13
What I want to do is seamlessly run an application with wine from a terminal session. Basically what I want to do is boot into a terminal session and then run wine without doing 'startx' and then 'wine ...' in the new X session if that makes sense.

---

### Post by daengbo on 2007-03-13
Wine will require an xserver, so you'll need one running, but you won't need a desktop environment or even a window manager if you don't want one, saving a lot of memory in the process. What you CAN do is create a new session type (under /usr/share/xsessions, I believe), setting environmental variables, starting X, and starting your app in wine (specifying full screen, if you want. I did that many years ago with VMWare and Win98 for my GF who didn't want to learn Gnome or KDE.

Then you simply log into your account using the newly created session. 

Best of luck.

---

### Post by tee2 on 2007-03-13
Could you point me to a resource on creating a new session type? I don't know where to begin doing that.

---

### Post by daengbo on 2007-03-13
Just copy the default gnome session over to a new file and edit that. Take out the references to gnome-session and everything like that, then add the commands you want run. It's just a Bash script. Figure out what to do on the cmmand line, then throw that stuff in the new session.

---

### Post by tee2 on 2007-03-13
OK this is what I have,
```
[Desktop Entry]
Version=1.0
Encoding=UTF-8
Name=WoW
Comment=This session starts WoW without a window manager
Exec=/usr/bin/xterm && wine /home/tee/.wine/drive_c/Program\ Files/World\ of\ Warcraft/WoW.exe
Icon=
Type=Application
X-Ubuntu-Gettext-Domain=gnome-session-2.0
GenericName=

```

When I log in I get a message saying, "All updates are complete." and after I click OK I get a default gnome session. What am I doing wrong?

---

### Post by daengbo on 2007-03-14
I assume you have everything set up to run correctly in wine to begin with. Given that, your script should work. Try to log into Gnome and see if you have the same issues with the wine command.

Is the WoW installation depending on anything in the Gnome environment, like gnome-vms or anything?

---

