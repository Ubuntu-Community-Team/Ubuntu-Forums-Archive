---
title: "Unity not starting in Ubuntu 14.04"
date: 2014-07-30
forum: Desktop Environments
---

### Post by shaansweb on 2014-07-30
Hello, 

Unity in my Ubuntu installation is not starting properly. After booting up, I only see my cursor and my desktop wallpaper. This first started after my computer suddenly shut off due to an unrelated hardware glitch, possibly in the midst of am update. Some googleing has led me to numerous threads where people are having similar problems, but none of the answers seem to work for my PC. Here is what I have tried so far:

1. Using tty1 to launch ccsm and enabling the unity desktop plugin, as well as the plug-ins it relies on. They were disabled, but enabling them had not fixed the problem. 

2. Running:

    rm -rf ~/.config/compiz-1/compizconfig/*

This has no effect 

3. Running the following commands:

    dconf reset -f /org/compiz
    setsid unity

This gives me the following error:

    "GLib-GIO-ERROR **: Settings schema 'org.compiz.scale' does not contain a key named 'dnd-timeout-spinner'
    Trace/breakpoint trap"

Does anybody have any other suggestions or know how to proceed because I've been computer-less for two days now and am starting to get frustrated.

---

### Post by prankstar008 on 2014-07-30
Have you tried using GDM instead of lightdm? 

$ sudo apt-get install gdm

If asked, make gdm default during installation, if not asked, or to switch back later 
$ sudo dpkg-reconfigure gdm

edit: fixed typo

---

