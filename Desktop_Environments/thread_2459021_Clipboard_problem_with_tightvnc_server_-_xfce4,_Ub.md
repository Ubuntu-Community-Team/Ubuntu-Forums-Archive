---
title: "Clipboard problem with tightvnc server - xfce4, Ubuntu 18.04"
date: 2021-03-08
forum: Desktop Environments
---

### Post by madbrain on 2021-03-08
I am running tightvnc server on Ubuntu 18.04, configured as follows :

madbrain@server10g:/etc/systemd/system$ cat vncserver@.service 
[Unit]
Description=Start TightVNC server at startup
After=syslog.target network.target

[Service]
Type=forking
User=madbrain
Group=madbrain
WorkingDirectory=/home/madbrain

PIDFile=/home/madbrain/.vnc/%H:%i.pid
ExecStartPre=-/usr/bin/vncserver -kill :%i > /dev/null 2>&1
ExecStart=/usr/bin/vncserver -depth 24 -geometry 2560x1600 :%i
ExecStop=/usr/bin/vncserver -kill :%i

[Install]
WantedBy=multi-user.target

[EMAIL="madbrain@server10g:~/.vnc"]madbrain@server10g:~/.vnc[/EMAIL]$ cat xstartup
#!/bin/sh
unset SESSION_MANAGER
unset DBUS_SESSION_BUS_ADDRESS
autocutsel -s CLIPBOARD -fork
dbus-launch xfce4-session

When using VNC clients on a Windows machine - either RealVNC or tightvnc client - I cannot paste into any Ubuntu window.
I can copy from the Ubuntu machine in the VNC session to the Windows machine, however. In other words, the clipboard works only in one direction.

Can anyone help with this ? I have done Google searches, and read well over a hundred posts for many hours, but nothing works.
I have tried various command lines for autocutsel, and none made any difference.

Help would be very much appreciated on this.

---

### Post by madbrain on 2021-03-12
Help, anyone ?

---

### Post by ActionParsnip on 2021-03-14
As a work around you can paste into a file using SSH then open the file in the GUI. You can use Filezilla or WinSCP to copy files over to the remote system as well

---

### Post by madbrain on 2021-03-15
> **ActionParsnip said:**
> As a work around you can paste into a file using SSH then open the file in the GUI. You can use Filezilla or WinSCP to copy files over to the remote system as well

Thanks. I already have Samba setup for file transfer. I don't think this is a very practical workaround.

Is there really no fix for this ?

---

### Post by ActionParsnip on 2021-03-16
> **madbrain said:**
> Thanks. I already have Samba setup for file transfer. I don't think this is a very practical workaround.

Is there really no fix for this ?

If you have SSH enabled, you don't need Samba :). OpenSSH Server gives you an SFTP server. I guess it a bit quicker if your client system is Windows based.

I don't use VNC so not sure how it gels with the clipboard of the client OS. Maybe others can advise

---

### Post by madbrain on 2021-03-16
> **ActionParsnip said:**
> If you have SSH enabled, you don't need Samba :). OpenSSH Server gives you an SFTP server. I guess it a bit quicker if your client system is Windows based.

I don't use VNC so not sure how it gels with the clipboard of the client OS. Maybe others can advise

Yes my client is Windows based. And I map my NAS to a drive letter on Windows.  While SFTP servers can be mounted in Explorer, that doesn't work in any other Windows application, so it is fairly useless.

Anyway, my post is only concerned with the VNC clipboard, and not anything to do with file sharing.

I appear I have found a way to make it work.

1) I set SendInitialClipboard to TRUE in RealVNC client (Windows)
2) I restarted the VNC server with "sudo systemctl restart vncserver@1"
3) Now the paste function works in gnome-terminal with SHIFT-CTRL-V, or from the "Edit/paste" menu.
In Firefox, paste works with SHIFT-INSERT or from the "Edit/paste" menu.
I'm not sure why the paste hotkeys are inconsistent, but at least I have a way to make it work now.
This is all working using the same xstartup and systemd config files as in my original post on top of this thread.

I would think this would be a FAQ given how many people must be running Ubuntu headless.

---

