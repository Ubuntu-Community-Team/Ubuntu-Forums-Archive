---
title: "Adding programs to startup/login"
date: 2005-12-19
forum: General Help
---

### Post by dandezille on 2005-12-19
I am running ubuntu 5.10, I have installed xubuntu-desktop and network-manager. 

I need to start the nm-applet when I logon to xfce, however the only way I seem to be able to find to add things to the startup/login is throught a configuration screen launched from the gnome menu under

System -> Preferences -> Sessions

Is there a way to get to this from xfce or is there an equivalent? I am sure there will be a way to add programs to the startup from the command line and if anyone could point me in the right direction this would be really helpful

Cheers
Dan

PS I know this is the gnome section but I wasn't sure where else this should go, if this is wrong please let me know

---

### Post by maglis on 2005-12-19
If you login into your X session from a Display Manager like GDM (Ubuntu default) then you need to take a look to ```
man Xsession
```.
You really need to create an /home/<USERNAME>/.xsession script file that will contain any code you need to run at X session startup.

>   $HOME/.Xsession
              is  a sequence of commands invoking X clients (or a session man&#8208;
              ager such as xsm(1x)).  See the manual  page  for  xinit  and/or
              /usr/share/doc/xfree86-common/examples/xsession   for   tips  on
              writing an .Xsession file.

---

