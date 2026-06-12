---
title: "Nvidia settings"
date: 2005-08-31
forum: Desktop Environments
---

### Post by darkrad on 2005-08-31
Hello, i succesfully installed nvidia drivers on kubuntu. The only problem i notice is that each time i boot kubuntu, the brightness/contrast modifies i did on nvidia settings doesn't apply untill i open the nvidia settings application: quite boring to open it each time i boot kubuntu, as first action. any way to fix it? thanks in advance.

---

### Post by JOKe on 2005-08-31
i was try to use nvidia-glx and nvidia-settings but i have boot problems too so .. i remove them
i install nvidia drivers from nvidia.com 
( before installing them you will need sudo apt-get install gcc and g++ maybe )
and everythink was fine

---

### Post by gnutux on 2005-09-01
Yes, the NVIDIA installers from the site is much better because it customizes the settings to the system's configuration. apt-getting it will leave it to the packager's machine configuration and might not be able to be useful for you.

gnutux

---

### Post by darkrad on 2005-09-01
i intalled them using apt-get and the procedure written in ubuntuguide site. how to uninstall them before install the ones from nvidia site? should i run kynaptic and uninstall all entries that start with nvidia*? thanks

---

### Post by darkrad on 2005-09-01
i opened kynaptics, i uninstalled the 2 entries that started with nvidia*, then i exited X using ctrl-alt-backspace, and in dos-like mode i installed nvidia driver from nvidia site. Installation completed succesfully. but after "reboot" the system, it's still in dos-like mode. how to switch back to gui mode? thanks

---

### Post by darkrad on 2005-09-01
now i tried to: 

> 
nvidia-installer --uninstall
apt-get install nvidia-glx
apt-get install nvidia-settings


but when i "startx", i get:

Error: API mismatch: the NVIDIA kernel module is version 1.0.7676, but this X module is version 1.0.7174. Please be sure that your kernel module and all NVIDIA driver files have the same driver version.
(EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module!
(EE) NVIDIA(0):  *** Aborting ***
(EE) Screen(s) found, but none have a usable configuration.
Fatal server error: no screens found

Anybody have a clue of what should be done at this point?  :neutral:

---

### Post by darkrad on 2005-09-01
finally in some way i was able to install the new drivers. but still, after booting, they don't set brightness and contrast choosen untill i open/close "nvidia settings".. any way to apply values without open/close "nvidia settings" each time?

---

### Post by berserker on 2005-09-01
[QUOTE=darkrad]finally in some way i was able to install the new drivers. but still, after booting, they don't set brightness and contrast choosen untill i open/close "nvidia settings".. any way to apply values without open/close "nvidia settings" each time?[/QUOTE]

I've read that the settings are lost each time you logout/reboot unless someone has figured out a workaround.

---

### Post by ykpaiha on 2005-09-01
I don't remember the right way to use the panel but at a time I could do it (since I change my monitor)
but mayby you should find some help here it worked for me....
[http://www.nvnews.net/vbulletin/forumdisplay.php?s=&forumid=14](http://www.nvnews.net/vbulletin/forumdisplay.php?s=&forumid=14)
 :-x

Just to help I found this:

Loading Settings Automatically

    The NVIDIA X driver does not preserve values set with nvidia-settings
    between runs of the X server (or even between logging in and logging
    out of X, with xdm, gdm, or kdm).  This is intentional, because
    different users may have different preferences, thus these settings
    are stored on a per user basis in a configuration file stored in
    the user's home directory.

    The configuration file is named "~/.nvidia-settings-rc".  You can
    specify a different configuration file name with the "--config"
    commandline option.

    After you have run nvidia-settings once and have generated a
    configuration file, you can then run:

        nvidia-settings --load-config-only

    at any time in the future to upload these settings to the X
    server again.  For example, you might place the above command in
    your ~/.xinitrc file so that your settings are applied automatically
    when you log in to X.

    Your .xinitrc file, which controls what X applications should
    be started when you log into X (or startx), might look something
    like this:

        nvidia-settings --load-config-only &
        xterm &
        evilwm

    or:

        nvidia-settings --load-config-only &
        gnome-session

    If you do not already have an ~/.xinitrc file, then chances are that
    xinit is using a system-wide xinitrc file.  This system wide file
    is typically here:

        /etc/X11/xinit/xinitrc

    To use it, but also have nvidia-settings upload your settings,
    you could create an ~/.xinitrc with the contents:

        nvidia-settings --load-config-only &
        . /etc/X11/xinit/xinitrc

    System administrators may choose to place the nvidia-settings load
    command directly in the system xinitrc script.

    Please see the xinit(1) manpage for further details of configuring
    your ~/.xinitrc file.

here:
[ftp://download.nvidia.com/XFree86/Linux-x86/1.0-6106/nvidia-settings-user-guide.txt](ftp://download.nvidia.com/XFree86/Linux-x86/1.0-6106/nvidia-settings-user-guide.txt)

---

