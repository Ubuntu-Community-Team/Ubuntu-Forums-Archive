---
title: "Theme being reverted on every system start"
date: 2011-03-29
forum: Desktop Environments
---

### Post by sathoro on 2011-03-29
Whenever I restart my computer or turn it on the top panel is not the nice default dark 10.10 theme, it is an ugly gray. Same thing with any applications I open. What I have to do is run

```

sudo -u gdm gconftool-2 --set --type string /desktop/gnome/interface/gtk_theme HumanLogin

```and then logout and login again. Then when I login it is STILL the grey theme and when I repeat that command and logout and login it is then the default dark theme. Not really sure what is going on here =/ Any suggestions? Thanks in advance :)

Edit: I'm using Gnome 2.23 and Ubuntu 10.10 like I mentioned

---

### Post by sathoro on 2011-03-29
Nevermind, fixed it!

Here is my solution for anyone who is also having this problem:

```
sudo mkdir /usr/share/gdm/nostart
sudo mv /usr/share/gdm/autostart/LoginWindow/gnome-settings-daemon.desktop /usr/share/gdm/nostart/
```from here: [http://ubuntuforums.org/showthread.php?t=1594682](http://ubuntuforums.org/showthread.php?t=1594682)

but this will make the login screen quite ugly, so run

```
sudo cp /usr/share/applications/gnome-appearance-properties.desktop /usr/share/gdm/autostart/LoginWindow
```and when you logout a window will appear asking for you to choose a login theme. do this and login. then run:

```
sudo unlink /usr/share/gdm/autostart/LoginWindow/gnome-appearance-properties.desktop
```to not get that box to popup everytime you login :)

from here: [http://ubuntuforums.org/showthread.php?t=1604399](http://ubuntuforums.org/showthread.php?t=1604399)

Hope this helps someone

---

