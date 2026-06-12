---
title: "WTF - Gnome networking sucks so much"
date: 2006-06-12
forum: Desktop Environments
---

### Post by el3ktro on 2006-06-12
Ok I love Linux, and I love Gnome, but this really sucks!

I have a desktop computer holding all my data, and a notebook. The desktop machine is basically a file server for the notebook.

First, I tried it with GnomeVFS. I have sshd running on the server, so I used the GnomeVFS for SSH to access /home on my desktp from my notebook. This works fine in Nautilus, but soon I discovered that around 80% of all apps shipping with Gnome/Ubuntu don't support GnomeVFS!! I can't watch my pictures on the desktop, because gThumb doesn't shows GnomeVFS, just as an example.

Ok, I tried and tried - it just didn't work out. So I tried to really mount the remote directory via NFS. I created a mountpoint within /media, added a line to /etc/fstab and mounted the remote dir. Works fine, the remote dir also shows up as a "place" all over in Gnome. Though, Gnome somehow seems to detect that it is a remote dir and uses a NFS icon for this "place" - which again makes many apps not to work with it. Still, in gThumb I can't browse remote directories, but only the ones that have a blank space in them. Totem, and even gedit sometimes fail to load files on the remote dir, no matter if they have blanks or not in their filenames. I can't rename files on the remote directory, but I can delete them.

Whats going on? Why can't I use a remote directory properly in Gnome?? Even Windows does this better!! I definitely want a remote dir to show u as a "place", because it makes things so much easier - especially for my girlfriend. GnomeVFS is often not supported, really mounting a directory also doesn't help. What else can I do? Damn, I though Linux is THE networking OS so why does this suck so much?

How do you correctly mount remote directories? I just want two things: Let the remote dir show up as a "place", and I want to operate on the remote dir the very same way as I do with local directories, and I want it to work in _ALL_ programs.

Can this be done somehow? Sorry for me being so rude, but I'm trying to comfortably connect my two machines for almost years, it did never work right under KDE, and my hope that Gnome does it better has gone :-(

Tom

---

### Post by mgmiller on 2006-06-12
Have you tried gnome-user-share?  If all your repos are turned on, it's in synaptic or a quick apt-get install.  I have been using samba to connect 2 Dapper installs I have in my house.  This works pretty well.  Totem plays accross this kind of share and I can save a bookmark to my shared directories in Places.  It will ask me for my password once a session and then behaves pretty much like a local directory.  Nautilus even lets me browse around from there to the extent of the samba share I have defined.

---

### Post by scxtt on 2006-06-12
you should be able to use "connect to server" from the "Places" menu to ssh into your desktop and then do whatever you want w/ the files on your desktop ... it'll put a folder on your desktop and list it in the "Places" menu ... this is pretty similar to what mgmiller is talking about, but doesn't require the "gnome-user-share" d/l, even the bookmark concept works ...

---

### Post by el3ktro on 2006-06-13
[QUOTE=scxtt]you should be able to use "connect to server" from the "Places" menu to ssh into your desktop and then do whatever you want w/ the files on your desktop ... it'll put a folder on your desktop and list it in the "Places" menu ... this is pretty similar to what mgmiller is talking about, but doesn't require the "gnome-user-share" d/l, even the bookmark concept works ...[/QUOTE]

This is exactly what I have tried in first place. The problem with this is: It works very well in Nautilus, but many, many applications don't support this and don't show the remote "place" in their file open/save dialogs. I can't browse my desktop with gThumb for example, if I do it this way.

If I really mount a remote dir via NFS, and I browse the remote directory with Nautilus everything works well, but when I click on a picture to preview it in gThumb, then it again doesn't work. It works though if I manually brwowse to /media/remote/...... within gThumb. But this only happens when I have blank spaces in file/directory names.

Tom

---

### Post by el3ktro on 2006-06-13
[QUOTE=mgmiller]Have you tried gnome-user-share?  If all your repos are turned on, it's in synaptic or a quick apt-get install.  I have been using samba to connect 2 Dapper installs I have in my house.  This works pretty well.  Totem plays accross this kind of share and I can save a bookmark to my shared directories in Places.  It will ask me for my password once a session and then behaves pretty much like a local directory.  Nautilus even lets me browse around from there to the extent of the samba share I have defined.[/QUOTE]

When I was using Gentoo previously I also had much better experiences with Samba than with NFS, perhaps I should try again to share my files trough Samba, which is well kind of ironic that Samba is better for Linux file sharing than NFS. NFS just sucks honestly. If I have mounted a NFS directory and I put the notebook to sleep it goes totally crazy awhen I wake it up again, but it works very well with Samba. Sad :-(

Tom

---

### Post by el3ktro on 2006-06-13
Well indeed it works _much_ better when I use Samba instead of NFS. When I mount a NFS export in /media, Gnome shows it in "places", but the mountpoint has a NFS icon, which makes it disappear from some applications. When I mount the Samba share, it's seen as a normal harddisk device, which makes it accessible in all applications. Very strange.

One little question though: äöü dont show up correctly, I tried all adding iocharset=utf-8,codepage=utf-8 to /etc/fstab with cifs filesystem, but it doesn't help. What can I do?

Tom

---

### Post by mannheim on 2006-06-13
Another alternative is sshfs. See the user guide [here.]("http://ubuntuguide.org/wiki/Dapper#How_to_mount_remote_folders_into_local_Ubuntu_machine_.28sshfs.29")

(Following the directions in that guide, I think you may have to log out and back in, after adding yourself to the fuse group.)

---

### Post by JackandJohn on 2006-06-25
Here's a quick tip as well; if you define a mount in fstab as being in the /media directory, it will show on the desktop.

For example:

[fstab command to mount smb share in /media/NetworkC using smbfs or cips]

will show "NetworkC" on the desktop (you can remove network shares from the desktop in the config somewhere), and in Places > Removable media

You can also browse, though any program, to /media/NetworkC

and, you can set it to noauto, then make a button that does "gksudo mount /media/NetworkC"



I'm sketchy on details because there are lots of howtos/info in the forum on mounting network shares

---

