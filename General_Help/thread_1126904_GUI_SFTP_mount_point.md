---
title: "GUI SFTP mount point"
date: 2009-04-15
forum: General Help
---

### Post by LiNuXaDDiKt on 2009-04-15
Hi all,

This may be a dumb question but I just can't figure it out...

I have a Ubuntu desktop and and server.  I Access the file system of the server trough a shortcut that I created using GUI tools on the desktop that use this url type "sftp://username@server/".  This process creates an icon on the desktop that permits me to access the file system of the server.

That said, is there a way to access this path on the desktop but with cli tools?

If I recall mounting a cd-rom at cli it mounts somewhere in your file system according to the specified path in your mount command.

I'm kinda looking for the mount point of that gui sftp sortcut.

Robert.

---

### Post by Titan8990 on 2009-04-15
I don't think the gnome file manager actually mounts that location on your filesystem. All it is doing is placing a folder on your desktop that is pointing the address of the remote server. However, it is possible to mount a ssh share using fuse. It would be more common to use NFS for mounting remote directories but really, most file sharing protocols can be mounted via fuse.

A quick google search found this guide but I have not tested it: [http://ubuntu.wordpress.com/2005/10/28/how-to-mount-a-remote-ssh-filesystem-using-sshfs/](http://ubuntu.wordpress.com/2005/10/28/how-to-mount-a-remote-ssh-filesystem-using-sshfs/)

---

### Post by Yashiro on 2009-04-15
You can mount SSH directories in a more traditional sense by installing 'sshfs'.

Then using a terminal you can mount the server with something like:
> mkdir /home/yourname/Public/ssh
sshfs yourname@192.168.4.80:/home /home/yourname/Public/ssh

If you open nautilus now it should be there in the side bar with the rest of your drives.

---

### Post by LiNuXaDDiKt on 2009-04-15
Outch I'm impressed by the speed of your answers !!!

Thanks I've installed sshfs/fuse and it does the trick.  But still have a small issue...

I log to the server using a regular user because it's not necessarily a good idea to permit root login even trough ssh.

Since I need from time to time to edit files as root I just can't kinda "sudo" since I suspect that ssh uses the user I've used to log in to the server.

Is there a way to bypass this without allowing root login?

Robert.

---

### Post by squigish on 2012-08-29
I realize this thread is over 3 years old, but I thought I'd answer the OP's last question anyways, for other people who come here from google.

The short answer is that no, there's no good way to do what you want.  If you need to edit files as root, you'll have to do it using a ssh command-line interface, logging in as a user with sudoer privileges (by default, anyone in the adm group).  If you want to do your editing on your local computer, instead of the remote server, I'd recommend opening the file through your GUI, if that's what you're most comfortable with, saving it somewhere you have write privileges, and than copying it to the appropriate destination using sudo in your ssh terminal.  Don't forget to chown root and set chmod to the appropriate permissions.

---

