---
title: "Issue with VLC and SMB network paths"
date: 2020-08-31
forum: Desktop Environments
---

### Post by sremick on 2020-08-31
Xubuntu 20.04.1
VLC 3.0.11

I have media on my NAS available via an SMB share as clients with  multiple OSes need to access it, so SMB provides the most cross-platform  accessibility. In Xubuntu, I can browse to this path just fine in the  Thunar file manager using the path smb://freenas.local/media/Movies/ and  see the list of content.

Directly from Thunar, I can open videos on the NAS using Parole and they  play just fine. But if I try to open them in VLC, they fail.

I tried installing the SMB plug-in with ```
sudo apt-get install -y vlc-plugin-samba
``` and it installed without error. However, when I go to Input / Codecs > Access Modules I don't see "SMB"

I DO see dsm ("libdsm SMB input") but I saw that before installing the above plugin.

I see network paths are a common problem with VLC and I'm not really  clear why it's such a problem w/ VLC and not other players like Parole,  Gnome Videos (Totem, which I also tried), etc. I'd really like to get  VLC to work as it provides me useful CODEC information about the current  video which I often need.

---

### Post by TheFu on 2020-08-31
If you mount the storage using the fstab or autofs, then it will appear as local directories. Plus, you have better control over the mount options and can use performance options freely, unlike the point-n-click mounts.

Many NAS devices support NFS which is the native file sharing protocol for all Unix systems. Use that if you can.  Both NFS and CIFS can be shared by NAS devices concurrently for the same storage.

VLC has been shipped as a snap package recently. There are many good things about this, but some things, like access to storage outside the HOME for the user have been impacted or completely broken, due to the increased constraints forced on all snap packages to be more secure.  First, determine if you are using the normal package for VLC or using a snap.

```
$ snap list
```

If it is a snap, you may need to specifically allow some "connections" to access any files outside the userid HOME.

```
$ sudo snap connections vlc
```

Next, you'll need to learn about each connection type that may be possible to allow access to remote storage.  I don't know if that is even possible.

I go out of my way to avoid snaps. If I want to constraint applications, there are other tools which provide more local control.

---

