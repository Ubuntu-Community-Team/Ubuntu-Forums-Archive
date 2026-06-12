---
title: "Ubuntu Mobile on Desktop"
date: 2008-07-05
forum: Desktop Environments
---

### Post by mishathegoat on 2008-07-05
Hey everyone,

I was wondering if any of you had *trully* sucessfully installed Ubuntu Mobile as a desktop environment on their home PC.. (Or hildon-desktop)

If not, what are some alternatives (similar environments). So far, I only know of:
LXLauncher (Only works on EeePC)
Asus Launcher (Also only works on EeePC)

Please, any help is appreciated.

---

### Post by mishathegoat on 2008-07-19
[Bump] There's gotta be *someone*

---

### Post by stylistic on 2008-07-31
I am using UME on a Fujitsu Stylistic 3400, a tablet PC. I was running the system unter XUbuntu Hardy Heron and then installed the UME packages. Installation was no problem at all (at least as soon as I had found a good tutorial :))

Unfortunately I do not find it anymore, but I will try to give you the key issues:

Use apt-get to install the UME packages:
```
sudo apt-get install ubuntu-mobile
```

I was using GDM then, so I lookup up how to add hildon as window manager to the login (see [http://www.linuxquestions.org/questions/fedora-35/adding-an-alternative-window-manager-to-the-gdm-login-132907/]("http://www.linuxquestions.org/questions/fedora-35/adding-an-alternative-window-manager-to-the-gdm-login-132907/")). Basically, this seems to run Matchbox Window Manager with the Plantkon theme.

By now I have added 
```
/usr/local/bin/start-hildon-session
``` 
to the .bashrc to boot automatically into UME. Therefore, I have adapted this wiki for matchbox: [http://www.nextabyte.com/wiki/index.php?title=Autostart_X_with_matchbox]("http://www.nextabyte.com/wiki/index.php?title=Autostart_X_with_matchbox").

Probably there is more information about UME on [https://help.ubuntu.com/community/UMEGuide]("https://help.ubuntu.com/community/UMEGuide").

At the moment, I am looking how to change the menu bar in UME, but I haven't found any information about that yet. So if anybody had a hint for that, I would be very thankful!

I would like to integrate the task switch tool I have seen as a Matchbox UI applet or the task list of icons I have seen in Ubuntu Netbook Remix.

---

