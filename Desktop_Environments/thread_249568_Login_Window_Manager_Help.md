---
title: "Login Window Manager Help"
date: 2006-09-02
forum: Desktop Environments
---

### Post by SirShaggy on 2006-09-02
I recently tried to install Xgl Compiz, not realizing what it really was. I decided to uninstall it due to lack of hardware quality. After I did, I had to reconfigure GDM to work again. All is fine now except, the login screen manager. I wanted to change the login screen to a personal choice. I had it before and liked it.
Now, when I go to System>Administration>Login Window and click, nothing happens.
If I open a terminal and type gksu gdmsetup, it says "Could not access GDM" configuration file.
Not sure what I have done here, Any Ideas?
Not a huge issue, I want it to work though.
SirShaggy

---

### Post by gotthardt on 2006-09-09
I had the same prob - here is my fix:
check in  /etc/gdm - (ls /etc/gdm) look for the file gdm.conf-custom if it is not there then you need it!

(You might have to run gdmsetup to change defaults in this file)
save this as /etc/gdm/gdm.conf-custom (must have root priv - use sudo):

# GDM Configuration Customization file.
#
# This file is the appropriate place for specifying your customizations to the
# GDM configuration.   If you run gdmsetup, it will automatically edit this
# file for you and will cause the daemon and any running GDM GUI programs to
# automatically update with the new configuration.  Not all configuration
# options are supported by gdmsetup, so to modify some values it may be
# necessary to modify this file directly by hand.
#
# To hand-edit this file, simply add or modify the key=value combination in
# the appropriate section in the template below.  Refer to the comments in the
# gdm.conf file for information about each option.  Also refer to the reference
# documentation.
#
# If you hand edit a GDM configuration file, you should run the following
# command to get the GDM daemon to notice the change.  Any running GDM GUI
# programs will also be notified to update with the new configuration.
#
# gdmflexiserver --command="UPDATE_CONFIG <configuration key>"
#
# For example, the "Enable" key in the "[debug]" section would be specified by
# "debug/Enable".
#
# You can also run gdm-restart or gdm-safe-restart to cause GDM to restart and
# re-read the new configuration settings.  You can also restart GDM by sending
# a HUP or USR1 signal to the daemon.  HUP behaves like gdm-restart and causes
# any user session started by GDM to exit immediately while USR1 behaves like
# gdm-safe-restart and will wait until all users log out before restarting GDM.
#
# For full reference documentation see the gnome help browser under
# GNOME|System category.  You can also find the docs in HTML form on
# [http://www.gnome.org/projects/gdm/](http://www.gnome.org/projects/gdm/)
#
# NOTE: Lines that begin with "#" are considered comments.
#
# Have fun!

[daemon]

[security]

[xdmcp]

[gui]

[greeter]
Browser=true
GraphicalTheme=debian

[chooser]

[debug]

[servers]

---

### Post by SirShaggy on 2006-10-01
That was it. I got it working well now, Thank You! I am sorry it took so long to reply, I got into setting up my laptop. It just took me a while.
SirShaggy

---

