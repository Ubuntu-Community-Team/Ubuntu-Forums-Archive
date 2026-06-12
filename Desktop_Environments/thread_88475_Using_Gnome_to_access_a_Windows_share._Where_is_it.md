---
title: "Using Gnome to access a Windows share. Where is it in the filesystem"
date: 2005-11-10
forum: Desktop Environments
---

### Post by siennalizard on 2005-11-10
Hello.
When Gnome is used to create a link to a windows share, I assume Samba is used to mount it. Where does it then appear in the filesystem, as I can't seem to use shell commands like cp, mv with the new connections?

I have tried to search for an answer, but the best search term for this problem is not coming to mind!

Cheers,
J.

---

### Post by Dr. Nick on 2005-11-10
is the windows a network share? samba is only usefull for networks. If you have windows installed on the same computer and then installed ubuntu check under  Places-Computer-Filesystem for a folder called windows, I believe mine was autocreated for me. If not you will need to look into /etc/fstab for how to mount them on boot.

---

### Post by siennalizard on 2005-11-10
Thanks to StephiBear in the chatroom, I've got this sussed:

1) you can't access shares through the filesystem created in the manner above, because the gnome-vfs is the intermediary, not smbfs, so:

2) install smbfs with "sudo apt-get install smbfs" or use synaptic, then

3) create a directory under /media to be your mountpoint with something like "sudo mkdir /media/sharename"

4) mount the share like this: "sudo mount //server/sharename /media/sharename". When prompted for a password, just press enter (assuming your shares are from XP Home or simply don't have passwords)

Hope that works for you!
J.

---

### Post by Dr. Nick on 2005-11-10
Oh, I see what you are doing now, I want sure what you menat by share. Was sorta confused if you were doing over a network or just another local partition. You can also try to use the Places-Connect to server option which will put a link on the desktop. But either way works its just a matter of prefrence.

Glad you got it.

---

