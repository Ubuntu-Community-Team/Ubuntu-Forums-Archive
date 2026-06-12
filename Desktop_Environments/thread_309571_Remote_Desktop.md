---
title: "Remote Desktop"
date: 2006-11-29
forum: Desktop Environments
---

### Post by ricop on 2006-11-29
Hi everyone,
New to Ubuntu, please go easy on me.

Situation:
Installed Ubuntu with LAMP then Moodle. All working great!

Need Solution:
We run a MS environment with XP PRO workstations and 2003 Servers. The test Ubuntu server is at my desk and it's great as I can do everything on the server itself. The real server which will be installed soon, will be in a different room. I need some help with remote desktop.

Is it possible:
1. From my XP PRO workstation to remote desktop to the Ubuntu server?
2. What exactly do I need to do? (commands or screen dumps will help)

Tried so far:
- Installed rdesktop. Don't know what to do next
- Installed Ultravnc on XP PRO. Cannot connect to Ubuntu server.
- Read the forum and googled for answers. Didn't get far as some users just said that they're using Ultranvnc and it's working. I'd love to know more and I'm sure every beginners will really appreciate maybe the commands to get it to work.;) 

Any help will be greatly appreciated. Thanks.

---

### Post by dcstar on 2006-11-29
> **ricop said:**
> Hi everyone,
New to Ubuntu, please go easy on me.

Situation:
Installed Ubuntu with LAMP then Moodle. All working great!

Need Solution:
We run a MS environment with XP PRO workstations and 2003 Servers. The test Ubuntu server is at my desk and it's great as I can do everything on the server itself. The real server which will be installed soon, will be in a different room. I need some help with remote desktop.

Is it possible:
1. From my XP PRO workstation to remote desktop to the Ubuntu server?
2. What exactly do I need to do? (commands or screen dumps will help)

Tried so far:
- Installed rdesktop. Don't know what to do next
- Installed Ultravnc on XP PRO. Cannot connect to Ubuntu server.
- Read the forum and googled for answers. Didn't get far as some users just said that they're using Ultranvnc and it's working. I'd love to know more and I'm sure every beginners will really appreciate maybe the commands to get it to work.;) 

Any help will be greatly appreciated. Thanks.

Graphical remote clients need to connect to systems with graphical environments, does the Ubuntu server run X or just character logins?

Ubuntu has remote connections disabled by default, you need to enable this in the Login screen preferences setting.

---

### Post by ricop on 2006-11-29
The Ubuntu server has a GUI (XUbuntu).
Remote Connection is enabled.

Can remote desktop from Ubuntu to XP but not the other way around. My understanding is that I need to have vnc server running on Ubuntu. Is this right? How do I do that?

---

### Post by yuanfangcan on 2006-11-30
I made it work once(remote connect linux from windows).  But forget how I did that.  what I remember is that it seems the linux respond my mouse a little bit slow.

---

### Post by dbott67 on 2006-11-30
I'm running Gnome (not XFCE) but you'll need to find where the "Remote Desktop" application is and ENABLE remote connections.  In Gnome, it's **SYSTEM > PREFERENCES > REMOTE DESKTOP**.

Ubuntu uses a variant of VNC called 'vino'.  If it's running correctly, you should see the following process:
```
dbott@edgy:~$ ps aux | grep vino
dbott     4513  0.0  1.5  26220 14332 ?        S    Nov28   0:35 /usr/lib/vino/vino-server --oaf-activate-iid=OAFIID:GNOME_RemoteDesktopServer --oaf-ior-fd=17
dbott    11125  0.0  0.0   2796   748 pts/0    R+   14:54   0:00 grep vino

```
On the XP computer, you'll need to install UltraVNC (just the viewer, if you only need to connect to other computers).  Start VNC Viewer, enter the IP address of the server.  You should be prompted for whatever password you entered in the "Remote Desktop" configuration screen (screenshot #2 below).

Here are some screenshots showing the setup in Ubuntu, followed by a couple from a Windows XP Pro computer connecting to it via UltraVNC.
1. Location of **Remote Desktop** application in Gnome
2. **Remote Desktop** settings
3. VNC Viewer on Windows XP
4. Connected to Ubuntu from XP

-Dave

---

### Post by ricop on 2006-11-30
Thanks Dave,
The screenshots were very useful. I had the same settings as yours but still couldn't connect.

I tried using Gnome as the default and it connected straight away. While Xubuntu was good for one purpose it caused a problem with the remote desktop.

Thank you very much for all your help and hope that this will help someone else.

Cheers

---

