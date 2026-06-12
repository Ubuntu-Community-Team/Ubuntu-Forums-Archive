---
title: "Thunar still can't mount network drives in Xubuntu 11.10?"
date: 2011-10-21
forum: Desktop Environments
---

### Post by Cryptog on 2011-10-21
I read the thunar file manager in XFCE 4.8 would be able to mount network drives.

I frequently mount servers via SSH in Gnome, but I would like to ditch Gnome because I don't like the direction it is headed. 

I can't seem to make it work in the newest thunar. I do CTRL-L, then ssh://1.2.3.4. There is no network in the side bar. 

Am I doing something wrong or is it broken? Can I specify a custom port, userid and password (I have some servers that aren't on port 22)?

Do I need to install any additional packages to make it work that way?

---

### Post by gwillem on 2011-10-21
Hi. Same here, just switched over to Xubuntu. You need to manually install gvfs-backends. And use sftp:// not ssh://

I still don't have it completely cooperating with my ssh-agent though. Under gnome2/natty a keyphrase dialogue for the right ssh key popped up (I have many under ~/.ssh). But now it just asks for a password. I'm not sure where to begin searching. I have gnome-keyring and libpam-gnome-keyring installed.

---

### Post by Cryptog on 2011-10-21
I reinstalled using ubuntu-alternate 11.10 which installs Gnome. Then I installed xfce4 and logged in with xfce. Now it works, with ssh://1.2.3.4.  It also has the network listed in the thunar side bar. Something that gets installed with Gnome makes it work correctly with xfce. 

I had already tried installing the gvfs-backends and it didn't make any difference in the "pure" xubuntu install.

On the xubuntu install, only gvfs was installed. Looking at my bastardized gnome-xfce install, I have the following:

dpkg -l | grep gvfs
ii  gvfs                                   1.10.0-0ubuntu1                         userspace virtual filesystem - server
ii  gvfs-backends                          1.10.0-0ubuntu1                         userspace virtual filesystem - backends
ii  gvfs-bin                               1.10.0-0ubuntu1                         userspace virtual filesystem - binaries
ii  gvfs-fuse                              1.10.0-0ubuntu1                         userspace virtual filesystem - fuse server

---

### Post by gwillem on 2011-10-21
I have the same debs installed under Xubuntu and it works for me ;) 

However in reply to my passphrase problem: the SSH_AUTH_SOCK as set by ssh-agent doesn't work with me in cooperation with gnome-keyring which (I think) is required by the gvfs passphrase thing. Even though "gnome-keyring (SSH AGENT)" is enabled under sessions (settings -> sessions). 

I found out that you need the Gnome startup services enabled (also under sessions) before gnome-keyring takes over SSH_AUTH_SOCK. Now it works like a charm! Hurray for Xubuntu/Xfce.

---

### Post by peridotfaceted on 2011-11-24
I fooled around with this for a bit but could never get thunar to satisfactorily mount remote filesystems. Instead I use the unfortunately-named tool "gigolo", which manages gvfs mounts of remote filesystems. You can automount them on startup or mount them on demand.

Comfortable handling of the ssh keys is something I'm still working on; ideally gnome-keyring-daemon would load them all into its internal ssh agent on login.

---

