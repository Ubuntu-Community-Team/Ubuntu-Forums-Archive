---
title: "Can't display remote X program on local display"
date: 2005-11-05
forum: Desktop Environments
---

### Post by gnerdman on 2005-11-05
I need to run Bacula's "bacula-console-gnome" program on a remote computer as root, and display it on my normal user's local desktop.  I have sshd's X11Forwarding turned on on the remote machine.  On the local desktop, I enter "xhost +" and it tells me everyone has access.  I ssh to the remote machine with "ssh -X -l lsat" and get logged in.  I export the DISPLAY variable to <my_local_machine>:0.0 and enter "sudo bacula-console-gnome".  After providing the password, there's a pause, and the remote machine comes back with:  "(gnome-console:6674): Gtk-WARNING **: cannot open display:".  The fact that there's nothing after that last colon tells me Gtk isn't seeing the DISPLAY variable.  I've been through just about every google hit on that error, and nothing works.  Both machines are Ubuntu running Gnome.  Can anyone provide the magic bullet?  Thanks in advance!

---

### Post by apolyak on 2005-11-05
[QUOTE=gnerdman]I need to run Bacula's "bacula-console-gnome" program on a remote computer as root, and display it on my normal user's local desktop.  I have sshd's X11Forwarding turned on on the remote machine.  On the local desktop, I enter "xhost +" and it tells me everyone has access.  I ssh to the remote machine with "ssh -X -l lsat" and get logged in.  I export the DISPLAY variable to <my_local_machine>:0.0 and enter "sudo bacula-console-gnome".  After providing the password, there's a pause, and the remote machine comes back with:  "(gnome-console:6674): Gtk-WARNING **: cannot open display:".  The fact that there's nothing after that last colon tells me Gtk isn't seeing the DISPLAY variable.  I've been through just about every google hit on that error, and nothing works.  Both machines are Ubuntu running Gnome.  Can anyone provide the magic bullet?  Thanks in advance![/QUOTE]

Hi,
- Check System->Administration->Login Screen Setup->Security_Tab->Deny TCP connection ... is unchecked.

- It is bettery to use xhost +your_remote_host, you may edit /etc/hosts, /ets/hosts.allow, /ets/hosts.deny

- ssh login: ssh -X user_name@remote_host

- export display as user: export DISPLAY=your_local_host_name:0.0

- run application as user: bacula-console-gnome &

good luck

PS. check if openssh server is installed

---

### Post by gnerdman on 2005-11-05
[QUOTE=apolyak]Hi,
- Check System->Administration->Login Screen Setup->Security_Tab->Deny TCP connection ... is unchecked.

- It is bettery to use xhost +your_remote_host, you may edit /etc/hosts, /ets/hosts.allow, /ets/hosts.deny

- ssh login: ssh -X user_name@remote_host

- export display as user: export DISPLAY=your_local_host_name:0.0

- run application as user: bacula-console-gnome &

good luck

PS. check if openssh server is installed[/QUOTE]


Apolyak, you rock!  The combination of turning off Deny TCP Connection in the Login Screen Setup and putting an allow entry in hosts.allow did the trick.  Thanks!

---

