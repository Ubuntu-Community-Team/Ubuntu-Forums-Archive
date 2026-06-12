---
title: "Sharing folders between Windows XP and Ubuntu?"
date: 2006-02-17
forum: Desktop Environments
---

### Post by TailsAndy on 2006-02-17
I'm trying to share a folder from Windows XP and my Ubuntu computer. These computers are on the same network, and in the same workgroup. I've set up the folders to be shared, but it isn't showing up on smb://.

In the terminal, I ran sudo gedit /etc/samba/smb.conf and added the following lines:
workgroup = MORTON [the group name]
server string = shared folder

When I open smb://, I get this: [[img=http://img153.imageshack.us/img153/9568/screenshot0zn.th.png]](http://img153.imageshack.us/my.php?image=screenshot0zn.png)
And the file is a text file.

Any help?

EDIT: The text in the file is:
[Desktop Entry]
Encoding=UTF-8
Name=morton
Type=Link
URL=smb://morton/
Icon=gnome-fs-network

---

### Post by kenweill on 2006-02-17
The problem is in your Windows XP. Try to use the wizard to connect to a workgroup.

And im not sure of that smb:// coz im not using it. Just Click Places > Network Servers. From there, you can browse on the Networks, both your MORTON workgroup and other workgroups.

But sharing Ubuntu to Windows, thats another story. Theres a GUI to set that in Ubuntu but it doesn't work. It doesn't work for me. After using the GUI, you still have to modify the configuration files of Samba, which lead to my idea that the GUI for Samba is useless. But its just my opinion.

---

### Post by TailsAndy on 2006-02-17
Thanks a lot! :)

The Places --> Network Servers thing worked.

---

