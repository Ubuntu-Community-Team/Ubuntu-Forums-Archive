---
title: "How do i make NFS mounts appear in the places menu?"
date: 2009-03-30
forum: Desktop Environments
---

### Post by SwedishWings on 2009-03-30
Hi,

i want to make my NFS shares appear in the places menu, and mount on demand. I've searched for hours, but can't find no info about this.

Thanks in advance!

/Mike

---

### Post by inobe on 2009-03-30
clicking network would be an icon.

is the service enabled for nfs. 

i am currently running kubuntu and trying to picture this from memory, but  trying....


if something is up with nfs not starting automatically' i believe almost all apps can be setup to start from sessions.

old info [https://help.ubuntu.com/7.04/user-guide/C/prefs-system.html](https://help.ubuntu.com/7.04/user-guide/C/prefs-system.html)

it would give an idea at least

---

### Post by Jose Catre-Vandis on 2009-03-30
On Xubuntu the xfce4 places menu shows the shortcuts from Thunar, so if I send a shortcut to the left hand pane in Thunar of an NFS share, it shows up in Places. However, I mount all my NFS shares through /etc/fstab on start up. If I don't mount them this way all I get is an empty folder. Is there a reason you want to mount on demand? if so you will probably want to unmount on demand to. Seems like best you could do is write some scripts and set up a multiple launcher (or two, the second for the umounts) "next" to Places. I feel some bash scripting coming on....:)

---

### Post by inobe on 2009-03-30
> **Jose Catre-Vandis said:**
> On Xubuntu the xfce4 places menu shows the shortcuts from Thunar, so if I send a shortcut to the left hand pane in Thunar of an NFS share, it shows up in Places. However, I mount all my NFS shares through /etc/fstab on start up. If I don't mount them this way all I get is an empty folder. Is there a reason you want to mount on demand? if so you will probably want to unmount on demand to. Seems like best you could do is write some scripts and set up a multiple launcher (or two, the second for the umounts) "next" to Places. I feel some bash scripting coming on....:)

haha' something from a few years ago, don't mean to bring up unwanted past, this howto has mounting info.

[http://ubuntuforums.org/showthread.php?t=249889&highlight=nvidia](http://ubuntuforums.org/showthread.php?t=249889&highlight=nvidia)

---

### Post by Jose Catre-Vandis on 2009-03-30
> **inobe said:**
> haha' something from a few years ago, don't mean to bring up unwanted past, this howto has mounting info.

[http://ubuntuforums.org/showthread.php?t=249889&highlight=nvidia](http://ubuntuforums.org/showthread.php?t=249889&highlight=nvidia)

:) You'll see I was second poster on that thread!

---

### Post by SwedishWings on 2009-03-31
Thanks for all replies! :)

My problem is that this is a laptop, and i have three different offices with different NFS servers and shares. If i use static mounts in fstab i have to reboot every time i change office, so that is not a smart way to do it.

What i want to achieve is the same functionality as Gnome offers with local partitions, samba shares etc, for mounting drives on demand only when i choose them from the locations menu. But i can't make the mounts appear in the locations menu and mount on demand.

Any further help would be most welcome!

Thanks in advance!

/Mike

---

### Post by timzak on 2009-04-02
Have you tried navigating to the mount point through Nautilus, then creating a bookmark?  You could probably also click and drag the mount folder to the lefthand area where shortcuts display in Nautilus.

---

### Post by SwedishWings on 2009-04-03
> **timzak said:**
> Have you tried navigating to the mount point through Nautilus, then creating a bookmark?  You could probably also click and drag the mount folder to the lefthand area where shortcuts display in Nautilus.

Thanks,

Yes i have tried that, but opening the mount point does not mount the NFS drive. So i'm prety much back in square one.

/Mike

---

