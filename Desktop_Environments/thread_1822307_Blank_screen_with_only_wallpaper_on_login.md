---
title: "Blank screen with only wallpaper on login"
date: 2011-08-10
forum: Desktop Environments
---

### Post by brendanyounger on 2011-08-10
Running Ubuntu 11.04 Natty.

Through pam_mount, I mount a CIFS share as the user's home directory.  When attempting to log in graphically, however, I get the following error dialog box:

Nautilus could not create the required folders $HOME/Desktop, $HOME/.nautilus
*blah* something about making sure they exist or setting permissions

I can log in via "su USER" just fine from the terminal, so that's not a problem.

My .xsession-errors has this gem:
** (gnome-settings-daemon:1864): WARNING **: Connection failed, reconnecting...
Error setting value: No database available to save your configuration: Unable to store a value at key '/desktop/gnome/applications/window_manager/default', as the configuration server has no writable databases. There are some common causes of this problem: 1) your configuration path file /etc/gconf/2/path doesn't contain any databases or wasn't found 2) somehow we mistakenly created two gconfd processes 3) your operating system is misconfigured so NFS file locking doesn't work in your home directory or 4) your NFS client machine crashed and didn't properly notify the server on reboot that file locks should be dropped. If you have two gconfd processes (or had two at the time the second was launched), logging out, killing all copies of gconfd, and logging back in may help. If you have stale locks, remove ~/.gconf*/*lock. Perhaps the problem is that you attempted to use GConf from two machines at once, and ORBit still has its default configuration that prevents remote CORBA connections - put "ORBIIOPIPv4=1" in /etc/orbitrc. As always, check the user.* syslog for details on problems gconfd encountered. There can only be one gconfd per home directory, and it must own a lockfile in ~/.gconfd and also lockfiles in individual storage locations such as ~/.gconf

And finally, the output of ls -alF on $HOME:
drwx------ 1 byounger domain^users 8192 2011-08-10 11:47 ./
drwx--x--x 4 byounger domain^users 4096 2011-08-10 11:08 ../
-rw------- 1 byounger domain^users   94 2011-08-10 11:45 .bash_history
drwx------ 1 byounger domain^users    0 2011-08-10 11:47 .cache/
drwx------ 1 byounger domain^users 4096 2011-08-10 11:47 .config/
drwx------ 1 byounger domain^users    0 2011-08-10 11:47 .dbus/
drwx------ 1 byounger domain^users 4096 2011-07-29 21:51 Desktop/
-rw------- 1 byounger domain^users   63 2011-08-10 11:47 .dmrc
drwx------ 1 byounger domain^users 4096 2011-07-29 21:51 documents/
drwx------ 1 byounger domain^users    0 2011-08-10 10:38 Downloads/
drwx------ 1 byounger domain^users    0 2011-07-29 17:56 favorites/
drwx------ 1 byounger domain^users    0 2011-08-10 11:47 .gconf/
drwx------ 1 byounger domain^users    0 2011-08-10 11:47 .gconfd/
drwx------ 1 byounger domain^users    0 2011-08-10 11:47 .gnome2/
-rw------- 1 byounger domain^users  172 2011-08-10 11:47 .gtk-bookmarks
drwx------ 1 byounger domain^users    0 2011-08-10 11:47 .gvfs/
-rw------- 1 byounger domain^users  330 2011-08-10 11:47 .ICEauthority
drwx------ 1 byounger domain^users    0 2011-08-10 11:47 .local/
drwx------ 1 byounger domain^users    0 2011-08-10 10:38 Music/
drwx------ 1 byounger domain^users    0 2011-08-10 11:47 .nautilus/
drwx------ 1 byounger domain^users    0 2011-08-10 10:38 Pictures/
drwx------ 1 byounger domain^users    0 2011-08-10 10:38 Public/
drwx------ 1 byounger domain^users    0 2011-08-10 11:47 .pulse/
-rw------- 1 byounger domain^users  256 2011-08-10 11:47 .pulse-cookie
drwx------ 1 byounger domain^users    0 2011-08-10 10:38 Templates/
drwx------ 1 byounger domain^users    0 2011-08-10 10:38 Videos/
-rw------- 1 byounger domain^users    0 2011-08-10 11:47 .xsession-errors
-rw------- 1 byounger domain^users 4008 2011-08-10 11:47 .xsession-errors.XXBKKF0V

Clearly this is some sort of permissions or file locking issue.  Anyone know exactly how to fix it?

---

