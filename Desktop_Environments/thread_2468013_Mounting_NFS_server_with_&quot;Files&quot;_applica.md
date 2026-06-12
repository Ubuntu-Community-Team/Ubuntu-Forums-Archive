---
title: "Mounting NFS server with &quot;Files&quot; application (getting &quot;mount point does not exist&quot;)"
date: 2021-10-15
forum: Desktop Environments
---

### Post by pep37619 on 2021-10-15
I have an NFS server on my network, and I would like to access it using the "Files" application on Ubuntu.  I go to "Other Locations" and I can see my server:

[IMG]https://i.stack.imgur.com/m9rtg.png[/IMG]
But when I click on "WhiteAndNerdy (nfs)", I get this error:

[IMG]https://i.stack.imgur.com/oL62S.png[/IMG]

I tried [asking this question on AskUbuntu]("https://askubuntu.com/q/1369300/527568"), but the answer I got was to create the mount point by right-clicking on the server and choosing "Preferences".  There is no "Preferences" on the right-click menu:

[IMG]https://i.stack.imgur.com/aHrvf.png[/IMG]

What can I do?

Thanks!

---

### Post by yancek on 2021-10-16
Did you create a mount point "WhiteandNerdy" and if so, where?  What happens when you "enter server address" shown at the bottom of that window?i

---

### Post by pep37619 on 2021-10-16
> **yancek said:**
> Did you create a mount point "WhiteandNerdy" and if so, where?  What happens when you "enter server address" shown at the bottom of that window?

I did not create a mount point for "WhiteAndNerdy".  Where am I supposed to create it?

If I enter "nfs://WhiteAndNerdy.lan/" in the "enter server address", I get the exact same error message as I do when I click on "WhiteAndNerdy (nfs)".

---

### Post by yancek on 2021-10-17
I generally create mount points for external drives or nfs mounts under the /mnt directory.  You aren't required to do that you can mount it elsewhere.  Are you following some tutorial on setting up an nfs server/client system?  Is this a business or home computer sysem on a LAN?  To create a mount point under the /mnt directory you would simply navigate there in a terminal or in your file manager and as root/sudo type:  mkdir WhiteAndNerdy

Understand that in Linux when you are in a terminal, case matters.  I don't know what level of expertise you have, but if this is something new to you I would suggest you get a good tutorial on the subject.  The link below is pretty useful.

[https://www.digitalocean.com/community/tutorials/how-to-set-up-an-nfs-mount-on-ubuntu-20-04](https://www.digitalocean.com/community/tutorials/how-to-set-up-an-nfs-mount-on-ubuntu-20-04)

---

### Post by Morbius1 on 2021-10-17
I haven't used NFS since the Korean War so I'm way out of my comfort zone here but it looks like a bug(?) with the gvfs backend:

gio mount nfs fails/ nautilus fails to connect to NFSv4 share : [https://gitlab.gnome.org/GNOME/gvfs/-/issues/564](https://gitlab.gnome.org/GNOME/gvfs/-/issues/564)

---

### Post by pep37619 on 2021-10-17
> **Morbius1 said:**
> I haven't used NFS since the Korean War so I'm way out of my comfort zone here but it looks like a bug(?) with the gvfs backend:

gio mount nfs fails/ nautilus fails to connect to NFSv4 share : [https://gitlab.gnome.org/GNOME/gvfs/-/issues/564](https://gitlab.gnome.org/GNOME/gvfs/-/issues/564)

I don't think so, because my server supports NFS versions 2 and 3:

```
whiteandnerdy:~ ppelleti$ rpcinfo -u localhost nfs
program 100003 version 2 is ready and waiting
program 100003 version 3 is ready and waiting
```

But yeah, I went through some of this yesterday after my last post, and I found it a bit horrifying that Nautilus is using its own userspace NFS client, rather than using the kernel's NFS client.  So I think I am just going to mount my NFS server from the command line.  (I'd been assuming Nautilus was just acting as a GUI front end to the "mount" command, but apparently not.)

---

### Post by TheFu on 2021-10-17
NFS is a server-to-server protocol.  Trying to use it as a user-to-server protocol will end in failure.
Typcially, NFS mounts are handled in the /etc/fstab file or using something like autofs (you can search for a how-to).  NFS storage appears like local storage to everyone on the computer.

All mounts need something called a "mount point".  That is typically an empty directory and can be mounted almost anywhere, but there are standards for where it should be mounted, depending on the purpose of the NFS storage.

First, let's try to get it mounted somewhere temporary. Run these commands, in order. If there is an error, STOP. Do not continue.
```
sudo mkdir /mnt/temp-nerdy
sudo mount -t nfs WhiteAndNerdy.lan:/[COLOR="#FF0000"]{share name} [/COLOR] /mnt/temp-nerdy
ls /mnt/temp-nerdy
```

Are there files where you expect?
We don't know the share name, so you'll need to fill that in above.  

WhiteAndNerdy.lan is the mDNS name (from Avahi).  It can be the IP address or LAN DNS address for the NFS server too. Your choice.  BTW, in general, it is best to keep all hostnames on the LAN either all UPPERCASE or all lowercase.  While it shouldn't matter and most programs don't care, some may care and may fail.  The same applies to usernames - stay 100% lowercase.  
Because Linux is case sensitive for directories and filenames, you can mix case as you like for those ... which includes the share name.  However, it is best to never, ever, ever, have spaces or punctuation in directories or share names.  You can if you really want to, but it will be a hassle and prone to human error.

So ... assuming the mount command above worked and the **ls** is showing a few files, now we know exactly what to add to our /etc/fstab.
Add a new line that looks like this to the fstab file:
```
WhiteAndNerdy.lan:/[COLOR="#FF0000"]{share name}[/COLOR] /media/wAndNery  nfs  rw,nofail,noatime,proto=tcp,nconnect=4    0    2
```
Also, run these commands:
```
sudo umount /mnt/temp-nerdy
sudo mkdir /media/wAndNery
sudo systemctl daemon-reload
sudo systemctl restart remote-fs.target
sudo mount -a
ls /media/wAndNery
```
Are the files you saw before returned by the ls command?
Can you create a file there or not?  If not, you'll probably need to modify the permissions on the NFS server. Fix those now.

If the NFS server isn't available, don't try to access that mount location.
Inside any program on Ubuntu, you can read and save files to the NFS location like it was local storage.  It won't show up as a special mount location. It will show up in the directory like any other storage inside the computer.  I think there could be an x-show..... option to make a file manager show it special, but I don't use that.

I keep my NFS storage mounted under /d/D1 - /d/D7 and create symbolic links into it from different systems as needed to simplify my access.  We can also use the cdpath environment variable to make accessing the directories in bash easier/faster.

I've made a number of assumptions with the steps above, like that the NFS server is relatively new and supports NFSv4.x and that the nfs-client is installed on the Ubuntu system. There are probably others.

The main thing that is missing is the share name.  NFS doesn't support "browsing" like Windows does. You need to know the name of the share BEFORE trying to mount it. There is a **showmount -e** command, which can help with that. Try 
```
$ showmount -e WhiteAndNerdy.lan
```
to get a list of available NFS shares from the NFS server, WhiteAndNerdy.lan.

Good luck.

---

### Post by pep37619 on 2021-10-17
> **yancek said:**
> I generally create mount points for external drives or nfs mounts under the /mnt directory.  You aren't required to do that you can mount it elsewhere.  Are you following some tutorial on setting up an nfs server/client system?  Is this a business or home computer sysem on a LAN?  To create a mount point under the /mnt directory you would simply navigate there in a terminal or in your file manager and as root/sudo type:  mkdir WhiteAndNerdy

Sure, I can create a mount point *somewhere*, but the question is, where does Nautilus expect the mount point to be?

Since my last post, I successfully mounted my NFS server from the command line, so I think I am just going to do that, and forget the GUI.  On the command line, I can specify where the mount point is.  But since Nautilus doesn't let me specify the mount point, and doesn't tell me what mount point it has in mind, the GUI seems useless.

Nautilus *seemed* to provide a very Mac- or Windows-like experience, by auto-discovering my NFS server (presumably through mDNS?) and putting it tantalizingly in the "Other Locations" screen, as if I could just click on it.  But then that Mac- or Windows-like experience breaks down when it expects the user to create a mount point manually.

---

### Post by pep37619 on 2021-10-17
> **TheFu said:**
> NFS is a server-to-server protocol.  Trying to use it as a user-to-server protocol will end in failure.
Typcially, NFS mounts are handled in the /etc/fstab file or using something like autofs (you can search for a how-to).  NFS storage appears like local storage to everyone on the computer.

NFS is a client-server protocol.  I'm trying to share files between two laptops, so I'm using my Mac laptop as the server, and my Linux laptop as the client.

Thanks for all the detailed instructions, but I did get NFS working from the command line over the past day.  So I'm good there, and I think I will just use the command line instead of the GUI.

But I'm puzzled why Nautilus displays the NFS server in "Other Locations", as if I could click on it, if it can't follow through on that promise.

---

### Post by Morbius1 on 2021-10-17
> But then that Mac- or Windows-like experience breaks down when it expects the user to create a mount point manually.
For everything else ( afp, sftp, smb, etc... ) the gvfs backend creates the mount point automatically and doesn't require user intervention.

So if I access my SMB server with a smb://vubsrv2004.local/public gvfs ( gio ) will create a mount point here:
> /run/user/1000/gvfs/smb-share:server=vubsrv2004.local,share=public

Don't know why it doesn't work for nfs. To be honest I never realized there was a gvfsd-nfs backend.

---

### Post by Morbius1 on 2021-10-17
>  But I'm puzzled why Nautilus displays the NFS server in "Other  Locations", as if I could click on it, if it can't follow through on  that promise.                 
Because the two subsystems were developed without anyone talking to each other. It's a Linux Desktop thing.

I can create an avahi service file on my server that looks like this:
> tester@vub2004:~$ cat /etc/avahi/services/nfs.service
<?xml version="1.0" standalone='no'?>
<!DOCTYPE service-group SYSTEM "avahi-service.dtd">
<service-group>
  <name replace-wildcards="yes">%h (nfs)</name>
  <service>
    <type>_nfs._tcp</type>
    <port>2049</port>
    <txt-record>path=/data/shared/Music</txt-record>
  </service>
</service-group>
I can see it automatically in Nautilus but when I click on it I get:
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=289301&stc=1[/IMG]
Since I don't have nfs itself set up here I would have expected a different error message but ...

---

### Post by TheFu on 2021-10-17
> **pep37619 said:**
> NFS is a client-server protocol.  I'm trying to share files between two laptops, so I'm using my Mac laptop as the server, and my Linux laptop as the client.
You are correct, of course. I was trying to point out the difference in computer-to-computer authentication vs user-to-computer authentication.  There is not user-specific authentication to access NFS shares. It is just the NFS-client  to the NFS-server doing the authentication without regard to any userids.  Well ... that isn't completely true, since uid/gid numbers are used inside the NFS protocol to control directory and file access following the Unix standards.
The NFS-client can be setup to use Kerberos server-to-serve tickets for authentication to the NFS-server, if you like. Also, encryption can be used as well - between the client machine and the server.  Again, this happens between the machines/OS, not any specific userid.

> **pep37619 said:**
> 
Thanks for all the detailed instructions, but I did get NFS working from the command line over the past day.  So I'm good there, and I think I will just use the command line instead of the GUI.

But I'm puzzled why Nautilus displays the NFS server in "Other Locations", as if I could click on it, if it can't follow through on that promise.

If you have the command like working, putting that into the fstab will make the mount happen at boot, every time.  That is a real convenience. You've already done the hard part, really.

I don't think I've used Nautilus in at least 5 yrs.  I typically use Caja, but really only to do file management over a USB connection to a phone or tablet, never for file management on the same computer.

Unrelated, but if you have ssh setup between a workstation or laptop and another Unix system, it is very likely that the file manager will support the SFTP:// protocol. This would be considered secure enough for use over the internet, provided you don't use passwords, but have ssh-keys exchanged from the client to the remote server.  That can be very convenient when outside your home LAN.

---

