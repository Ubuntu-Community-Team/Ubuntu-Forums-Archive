---
title: "Unable to save /etc/X11xorg.conf for writing"
date: 2022-01-12
forum: Desktop Environments
---

### Post by makem2 on 2022-01-12
I am using Ubuntu 21.10 with an XFCE desktop on two monitors. I have an ASUS TUF Z590 gfx card installed using nvidia drivers 'nvidia-driver-470 (proprietary tested)' from the repository Additional Drivers. The card and drivers are working correctly.

I want to set up the two monitors and for this I use nvidia-settings. When I have completed the settings I select 'Save to X Configuration File' where I am required to authorise and get an error:

Unable to open X config file '/etc/X11/xorg.conf' for writing.

I notice that there is a 'Browse' button to allow me to select an alternative location but I have no idea where to put the settings file. I tried Desktop and again need to authorise, but again get the same error.

When these settings are saved I understand I also need to make sure XFCE settings match.

It seems strange that nvidia-settings allows you to change the settings but not be able to save them. There must be a reason for this so, can anyone enlighten me please?

The contents of the terminal are:

```

makem@makems-TUF:~$ nvidia-settings

(nvidia-settings:3600): GLib-GObject-CRITICAL **: 13:42:40.007: g_object_unref: assertion 'G_IS_OBJECT (object)' failed
** Message: 13:42:40.159: PRIME: No offloading required. Abort
** Message: 13:42:40.159: PRIME: is it supported? no

WARNING:  Unable to parse X.Org version string.


WARNING:  Unable to parse X.Org version string.

Package xorg-server was not found in the pkg-config search path.
Perhaps you should add the directory containing `xorg-server.pc'
to the PKG_CONFIG_PATH environment variable
No package 'xorg-server' found
Error executing /usr/share/screen-resolution-extra/nvidia-polkit: Permission denied

ERROR: Unable to open X config file '/etc/X11/xorg.conf' for writing.


WARNING:  Unable to parse X.Org version string.


WARNING:  Unable to parse X.Org version string.

Package xorg-server was not found in the pkg-config search path.
Perhaps you should add the directory containing `xorg-server.pc'
to the PKG_CONFIG_PATH environment variable
No package 'xorg-server' found

WARNING:  Unable to parse X.Org version string.

Package xorg-server was not found in the pkg-config search path.
Perhaps you should add the directory containing `xorg-server.pc'
to the PKG_CONFIG_PATH environment variable
No package 'xorg-server' found
Error executing /usr/share/screen-resolution-extra/nvidia-polkit: Permission denied

ERROR: Unable to open X config file '/home/makem/Desktop/20-nvidia.conf' for writing.

makem@makems-TUF:~$

```

Edit: Solved thanks to this post:

[URL="https://ubuntuforums.org/showthread.php?t=1482283"]https://ubuntuforums.org/showthread.php?t=1482283

But, I would still like to know why we have to use a workaround.
[/URL]

---

### Post by TheFu on 2022-01-12
Linux uses Unix file and directory permissions.  Your useid isn't allowed to write to system file locations.
There are 500 solutions, but if it was me, I'd write the xorg file to my HOME directory, then copy that file into the necessary location using sudo from a terminal.

For example, I have a custom xorg-conf file for nvidia. It belongs here:
```
$ ll /etc/X11/xorg.conf.d/
-rw-r--r--  1 root root 3646 Mar 23  2019 20-nvidia.conf
```

so when I create the file, I save it to ~/20-nvidia.conf in that GUI program.  I think there is a required format to the name of the file, so follow {number}-{whatever}.conf as the pattern.  Next, I enter
```
$ sudo cp ~/20-nvidia.conf  /etc/X11/xorg.conf.d/
```
It is always good to keep a backup of important files, hence the cp.

Check that the file has the correct owner, group and permissions (see **ll** command above), then **reboot**.
If there aren't any errors in the conf file, you are done.

---

### Post by makem2 on 2022-01-12
Thank you for that explanation. The solution I chose was copy the file contents to a file anywhere and then copy the contents of that file to xorg.conf. I was a bit worried about replacing the contents of xorg.conf so as you say, I made a backup first.

Now on to the next problem lol.

---

