---
title: "Screens not mirroring on login mode"
date: 2020-04-25
forum: Desktop Environments
---

### Post by iamtheeggman2 on 2020-04-25
Hi,

I have two screens, one is a monitor on the normal cable and the other is a TV screen on HDMI. I set the screens to mirror each other in the ubuntu desktop environment however I need them to be mirror mode on the login screen too. Is there a way I can do this? I had  a browse around the settings on the login screen butt it didn't have anything relating to it from what I could see. Thanks in advance.

---

### Post by iamtheeggman2 on 2020-04-26
Well I have tried this trick and it hasn't worked, though there was no error message given when I did the copy.

[https://askubuntu.com/questions/1043337/ubuntu-18-04-login-screen-display-settings](https://askubuntu.com/questions/1043337/ubuntu-18-04-login-screen-display-settings)


[LIST=1]
[*]Go into Settings > Devices > Displays and  configure your monitors the way you want for your login screen (in your  case, internal laptop display disabled).  Click the "Save" button when  done. 
[*]Copy your user's monitors.xml file into the home folder for gdm user. 
[/LIST]
  To copy the monitors.xml file, open a terminal and perform the following:
  sudo cp ~/.config/monitors.xml ~gdm/.config/monitors.xml
sudo chown gdm:gdm ~gdm/.config/monitors.xml

Furthermore I tried to manually copy it using the files program but it wouldnt let me, when I went to open files in a terminal so I could get sudo mode it wouldn't recognise it either?

EEdit: I eventually installed Thunar, run it as sudo, copied it into usr/share/gdm but problem persists. I boot up and the logi screen is on one monitor only.

---

### Post by iamtheeggman2 on 2020-04-26
I ended up installing MATE as a desktop, things worked out fine in the end.

---

