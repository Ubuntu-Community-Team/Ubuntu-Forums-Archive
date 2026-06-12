---
title: "Cannot copy paste within network mounted folder"
date: 2024-04-22
forum: Desktop Environments
---

### Post by ubname on 2024-04-22
Very weird issue (Ubuntu 22.04):

I have a folder mounted from network just like this (fstab map):

//192.168.1.20/shared_folder /home/myuser/my_shared_mounted cifs credentials=/home/myuser/.mysmbcredentials,sec=ntlmv2,uid=1000,gid=1000 0 0

everything works, can create file, folder delete copy/paste(--> from another folder) BUT

while trying to copy from a folder within my_shared_mounted to another folder within my_shared_mounted "gnome file" start to "paste" but gets stuck and never end I must reboot

the same process works with no problems in linux mint LMDE6 (tried it just to test another DE i.e. cinnamon)

Is there a way to solve this and make copy/paste work in gnome?

---

### Post by TheFu on 2024-04-22
Mounting remote storage under your HOME causes problems.  You are seeing that now. 

Best to move the mount location elsewhere, mount it there, and, if you like, create a symbolic link from your HOME directory to that other location.
If you use Ubuntu and allow snap packages to be used, the locations where you would want to mount the remote storage is limited. Do some research about that, since there are other steps required for nearly all snap packaged software to be allowed access.

If your remote file server, 192.168.1.20, supports it, you should consider using NFS instead of CIFS.  But that's completely up to you. There are reasons that NFS is preferred, but only you can decide if also avoiding those issues by using NFS is worth it or not.  Up to you.

---

### Post by Morbius1 on 2024-04-22
I can't seem to be able to reproduce this error so all I can offer is some "try this" ideas.

Edit your fstab declaration and include this option:
```
cache=loose
```
Another possibility if multiple users are accessing the share:
```
nobrl
```

The way you process these things now is to:

Unmount the share:
```
sudo umount /home/myuser/my_shared_mounted
```
Make changes to fstab,

Then run these commands one after the other to make systemd happy:
```
sudo systemctl daemon-reload
sudo systemctl restart remote-fs.target

```

---

### Post by ubname on 2024-04-23
Hi I mounted to /mnt/my_shared_mounted same result, I think it's a gnome bug (?) in Ubuntu 22.04 tried with Ubuntu 24.04 and IT WORKS,
but sadly Ubuntu 24.04 dont behave wint qemu+virt-manager; using 3D acceleration virtio, gnome settings menu are invisible or pink or yellow rectangles.

---

### Post by ubname on 2024-04-23
> **Morbius1 said:**
> I can't seem to be able to reproduce this error so all I can offer is some "try this" ideas.


So you are not using Ubuntu 22.04 or your folder does not contains more than one file, i guess.

---

### Post by Morbius1 on 2024-04-23
If that is what you got from my post I can't help you.

---

### Post by ubname on 2024-04-23
> **Morbius1 said:**
> If that is what you got from my post I can't help you.

Hi, I tried your ideas but did not work, I admit i'm no "fstab expert" but i cannot understand why should I change an fstab entry
perfectly working with another DE

also:

```
cp -r /home/myuser/my_shared_mounted/dir1 /home/myuser/my_shared_mounted/dir2
```

works flawlessly, so I think the problem is within gnome file file manager not with mount options or permissions,
nonetheless thank you for your help, of course, i'm only trying to understand if this is a bug.

---

### Post by TheFu on 2024-04-23
I don't use Gnome, nor 22.04, but if it is a snap packaged program you are using, there are mandated constraints that prevent access to any storage that isn't a locally mounted /home/{username}.

2 non-home locations may be possible to add to each specific snap for access by setting the removable-media flag on the snap.  
The problem is better explained here: [https://askubuntu.com/questions/1033344/how-to-give-snaps-access-to-somedir](https://askubuntu.com/questions/1033344/how-to-give-snaps-access-to-somedir) ... assuming it is caused by snap packaged version.  Use **snap list** to see.  For me, the problem with snap package constraints was sufficient to drive me away from using Ubuntu-based Desktops.  I still use Ubuntu Servers (20.04), but my main desktop is Mint now 100% due to the snap problem.

---

### Post by Morbius1 on 2024-04-23
There are three - at least three - possibilities for this type of error:

Something messed up on the SMB server. Why it would only affect the one client remains a mystery.

Something messed up with mount.cifs. That is Linux kernel based so there may be a difference if all of your clients aren't using the same kernel.

Something messed up with the the gvfs / gio backend that Nautilus / Nemo / Thunar ... uses.

Of all the three the most bug-prone is gvfs so install a file manager that doesn't use it and see if you can accomplish the task without error:

I use xfe as a secondary file manager when I need to use something other than ubuntu's file managers.
```
sudo apt install xfe
```
*[COLOR="#FF0000"]Note: this is xfe - the file manager, not XFCE the desktop environment.[/COLOR]*

If it works in xfe you will know it's not the server or cifs.

---

### Post by ubname on 2024-04-23
> **Morbius1 said:**
> T
I use xfe as a secondary file manager when I need to use something other than ubuntu's file managers.
```
sudo apt install xfe
```
*[COLOR=#FF0000]Note: this is xfe - the file manager, not XFCE the desktop environment.[/COLOR]*

If it works in xfe you will know it's not the server or cifs.

Using xfe I have no problems with copy/paste operations guess it is a gnome problem.

---

