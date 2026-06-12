---
title: "Allow a user to switch different panel configurations in xubuntu session"
date: 2014-12-29
forum: Desktop Environments
---

### Post by Josep_Mulet on 2014-12-29
I am wondering if is there any simple way to allow a given user to switch between different desktop configurations in a machine running xubuntu. The only installed window manager is xfce4.

i have tried to create additional  sessions in /usr/share/xsessions with different names but mantaining the exec startxfce4. then i have created the default style for this session in /etc/xdg/xdg-mysession.

I choose the session from greeter and, the first time i login, it generates the correct .config for the session.

The problem is that when i log out and choosing another session from greeter, results in a login in which the previous configuration is displayed since the same .config dir is used by xfce.

is there any simple way to force xfce4 to use different .config dirs when different sessions are choosen at lighdm greeter?

i have tried modifying the xfce4initrc file, changing the variable XDG_CONFIG_HOME according to the selected DESKTOP_DIR but i have obtained no satisfactory result so far.

---

### Post by Josep_Mulet on 2014-12-31
I found myself a workaround. It is not very elegant but it works. It is based on symbolic links:

These are the steps:

1. cp /usr/share/xsessions/xubuntu.desktop /usr/share/xsessions/macosx.desktop
    cp -r /etc/xdg/xubuntu /etc/xdg/macosx 

2. Edit the name and description in file /usr/share/xsessions/macosx.deskop

3. Copy the contents of .config and .cache to .config_macosx and .cache_macosx
    Make another copy for the default session .config_xubuntu and .config_xubuntu
Delete the directories .config and .cache

4. Edit the file /etc/xdg/xfce4/xinitrc
    somewhere in this script add the following code
      rm $HOME/.cache
      rm $HOME/.config
      ln -s $HOME/.config_$DESKTOP_SESSION $HOME/.config
      ln -s $HOME/.cache_$DESKTOP_SESSION $HOME/.cache

5. Now You can login with one session (xubuntu or macosx) and proceeding customizing your desktops independently.

PD: Probably it would be also necessary to create symbolic links for the directory .gconf

---

