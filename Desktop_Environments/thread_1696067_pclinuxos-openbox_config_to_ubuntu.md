---
title: "pclinuxos-openbox config to ubuntu?"
date: 2011-02-26
forum: Desktop Environments
---

### Post by rcayea on 2011-02-26
Hi Everyone,

I have recently tried the distro PCLinuxOS-Openbox on live cd and basically love the look, feel, and everything else about it. 

My question is, is it somehow possible to move the configuration files from that distro to my ubuntu openbox setup? I have never configured openbox so I am not sure if I would need to make too many adjustments for this to be worthwhile. 

If you have any helpful tips or comments I appreciate them in advance.

Randy

---

### Post by urukrama on 2011-02-27
That should be possible. Openbox' configuration is stored in three text files: an rc.xml that configures Openbox' behaviour and a menu.xml that configures the desktop menu, and an autostart.sh file which tells Openbox what applications to start when Openbox starts. These are stored either in /etc/xdg/openbox (for the default, system-wide settings) or /home/USERNAME/.config/openbox (for user specific settings).

If you have a PCLinuxOS system (either an installed system or the installation disk), you should be able to get the configuration files from there (in /etc/xdg/openbox) and copy those to your /home/USERNAME/.config/openbox directory.

Next is are the themes PCLinuxOS uses. The Openbox theme is Island Caye, the Gtk theme is Elegant Aurora. Search for those online or get them from the PCLinuxOS system (copy them from /usr/share/themes to your own /home/USERNAME/.themes). 

Openbox manages only the windows, and relies on other applications for everything else (panels, wallpaper, etc.). Here you can find out what other applications PCLinuxOS relies on: [http://meylodie.wordpress.com/2010/11/23/pclinuxos-bonsai-en/](http://meylodie.wordpress.com/2010/11/23/pclinuxos-bonsai-en/)

Copy the configuration files from those applications and you should be all set.

---

### Post by rcayea on 2011-02-27
Thank you a whole bunch! Great Stuff! I am off to put your knowledge to work...

Thanks,
Randy

---

