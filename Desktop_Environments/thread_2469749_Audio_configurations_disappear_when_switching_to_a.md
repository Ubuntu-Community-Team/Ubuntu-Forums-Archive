---
title: "Audio configurations disappear when switching to a XRDP session"
date: 2021-12-08
forum: Desktop Environments
---

### Post by coatmor on 2021-12-08
Please forgive me if the question was already answered but I didn't find anything completely relevant.

I have a customer who encounters a problem with Ubuntu and RDS workstations.
As soon as he accesses the computer remotely, via RDS, the audio configuration is lost.
He has to restart the machine to recover a sound card and its configuration for the visios.

Here are two screenshots showing the problem:
- before : the audio card is correctly detected as output:
[IMG]https://i.stack.imgur.com/wDT9q.png[/IMG]
- After : it is replaced by a fictive output:
[IMG]https://i.stack.imgur.com/cBjUw.png[/IMG]
Here are some details about the machines:

Server machine : Ubuntu 20.04.3 LTS (Focal Fossa)
Xrdp server : 0.9.12-1
Desktop : Gnome
The concerned machine is the one that loses its Audio configuration when a remote session is started.

Client machine : Ubuntu 18.04.5
Desktop : Xfce
Client : REMMINA 1.2.0

But several client machines with older configurations encounter the same problem on a desktop (server) machine (also Ubuntu + xfce)

And the solutions we tried:

- killing Puslseaudio with  pusleaudio -k doesn't work

The problem comes from the fact that by default the closing delay of the Pulseaudio daemon is 20 seconds after the closing of a session, whether it is opened on the machine or via XRDP. You must therefore:

- Close the current session;
- Wait 20 seconds or more;
- Open the new session.

This delay can be reduced by performing the following operations:

- Edit the file /etc/xrdp/sesman.ini and add the line PULSE_CONFIG=/etc/xrdp/pulse/daemon.conf (in the SessionVariables section);
- Create the file /etc/xrdp/pulse/daemon.conf and add the line exit-idle-time = 2. This should reduce the delay to 2 seconds;
- Reboot.

This last solution seems to work in my local environment (Ubuntu 20.04 on VirtualBox) but not on my customer's side. Is there any other way to solve this problem? Is there a way to script a process that could reset the audio configuration without needing to reboot the machine?

Many thanks for your help!

---

