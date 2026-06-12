---
title: "\\hostname\username folder in home directories"
date: 2010-07-14
forum: Desktop Environments
---

### Post by kiddm on 2010-07-14
I'm pretty new to Ubuntu though I have multi-platform Unix experience from 15 years ago. Recently we setup an Ubuntu 10.04 server instance that we want to work in what is primarily a Windows environment. Joining the Ubuntu box to our Server 2003 Windows domain (GHC) seemed to go fine. Domain users can log in. SAMBA works. Remote Desktop via XRDP and VNC also basically works but with some seemingly odd issues.

The first thing I noticed is that both ~root and ~josh (a local account created during the installation) contained the odd looking folder names \\blx02\root and \\blx02\josh respectively where BLX02 is our host name. These are legitimate Unix file names but sort of odd ones that have to be enclosed in single quotes in shell commands to avoid the \\ being treated as an escaped slash. These odd looking folders contained folders names like Desktop, Documents, Downloads, Music, Pictures, Public, Templates, and Videos that are presumably created by GNOME. But for the domain accounts the same folders were created in the user's home directory rather than the strange \\hostname\user subdirectory.

When logging on locally as root or josh everything seemed to work fine. But Remote Desktop connections produced strange errors and didn't seem to full finish, e.g. the GNOME menubar and taskbar would not appear and ultimately I had to kill the appropriate sessvc process via an SSH connection. After poking around a bit I found a the following errors in ~/.xsession-errors.old for each account, repeated many times. 

ERROR:nautilus-file.c:657:nautilus_file_get_internal: assertion failed: (location != NULL)

(nautilus:24089): GLib-GIO-CRITICAL **: g_file_new_for_uri: assertion `uri != NULL' failed

Thinking perhaps that the initial account configuration during installation had gone awry, I renamed the \\blx02\root folder, and tried Remote Desktop again. Now everything worked great and new folders like Documents and Downloads were created at the top level of the ~root.

But my joy did not last long. As soon as I ran the Update Manager or Synaptic I ran into this error:

E: ERROR: could not create configuration directory \\blx02\root/.synaptic - mkdir (2: No such file or directory)
E: Can't write \\blx02\root/.synaptic/selections.proceed

Gedit and other programs complain as well if \\blx02\root does not exist.

So damned if I have the \\blx02\root folder and damned if I don't.

So what is going on here? Is there supposed to be a \\blx02\root folder? And if so what is supposed to go in it? Is there some issue with XRDP or VNC? It's very confusing.

---

