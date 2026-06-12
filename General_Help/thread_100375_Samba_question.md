---
title: "Samba question"
date: 2005-12-07
forum: General Help
---

### Post by frost_ad on 2005-12-07
Ok here is what I have:
Dual boot desktop with Ubuntu and Windows(for school, I have to :mad: )
Laptop with Ubuntu only
XBOX (modded)

I need to setup a network between these three. I think it has to be samba so that my xbox can see it and stream videos/music from it. 

My questions:

1. Am I correct that it needs to be Samba for the xbox's sake?
2. Can I set this up so the desktop will be in the network when it's in Ubuntu and when it's in Windows
3. Can someone give me the basics about setting the network up. Any packages I need from synaptic etc. I don't need detail (I don't think) just the basics and I will research/figure it out from there. 

Thanks for any help you can give!

---

### Post by jliedeka on 2005-12-08
I've mainly used Samba as a network filesystem.  I don't know anything about setting up WINS or any of that.  If your XBOX needs to be able to mount a remote filesystem, then Samba is probably what you want.

If you are serving up the files from the desktop, I would put them on the Windoze side and make that folder shareable.  On the linux side I would mount the windows filesystem at boot and create a Samba share for that directory.

You create the share in smb.conf.  If this will be on a private network, you can configure the share to not require a password.

If you are also serving up files from the laptop, create the samba share there as well.  I haven't done Samba under Ubuntu but most packagers separate the client stuff from the server stuff.  Make sure you have both parts.

To have your linux machines automagically mount the samba shares on boot, you need a line in /etc/fstab that looks something like this:

//winhost/sharename  /mnt/samba/sharename  smbfs  username=remoteuser%remotepass,uid=localuser,gid=localgroup 0  0

The username bit will not be necessary if your share doesn't require a password.  If you do use passwords, assign them under samba with the smbpasswd utility.

Note: the mount point for your samba share needs to be an existing empty directory.  Before the above fstab entry will work, you need to sudo mkdir /mnt/samba and sudo mkdir /mnt/samba/sharename.  You can manually mount the share with the smbmount command.

---

### Post by frost_ad on 2005-12-08
Ok, great. You've got me on the diving board, now all I need to do is jump. 

Thanks!

---

### Post by zoiks on 2005-12-09
I would add one or two thinks if you are new to samba.

Firstoff, there are two ways (maybe more?) of accessing your files shared on a windows host via cifs/smb from a Linux client.

One is, you can add a line in fstab that mounts a share (or do it at the command line if you like) to your file system when you boot.  I used to do this but found my system would hang if the network was sketchy or the host was rebooted.  Things may be different now, this was 1-2 years ago on SuSE.  The basic thing was if the connection was not reliable, then the client computer would act funny, hang, etc.

Another way is to access your fileshares via a URL in nautilus (works in konqueror, too, for kde).  For example, start up a nautilus window (i.e. accessories|file browser), then hit ctrl-L, and in the address bar, type

```
smb://serverhostname/sharename
```

This will allow you to make on-the-fly connections to your shared files.  You can even put your username in the link, as in

```
smb://user@serverhostname/sharename
```

and even your password (less secure) with

```
smb://user:password@serverhostname/sharename
```

This method, accessing smb shares via a URL, is what I use now.  I save links to various shares on my desktop and double-click them when I want to access the shared folders.

---

