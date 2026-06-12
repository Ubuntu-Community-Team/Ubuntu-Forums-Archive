---
title: "NFS noob"
date: 2006-07-02
forum: Desktop Environments
---

### Post by iambill on 2006-07-02
i have a few files on my main computer (amd64) that i want on my ibook, both running ubuntu. I figured nfs would be the best way to go.  I have everything setup in shares-admin, but i dont know how to physically get files from one computer to the other.:confused:  Please help me.

---

### Post by echo $USER on 2006-07-02
You can either maount it manually or automatically if you list it in your /etc/fstab.

First, make a directory where you want to mount the shared folder. Then run this command to mount it.

> mount -t nfs 192.168.x.x:/shared/folder /mount/point

To mount it automatically, put something like this at the bottom of your /etc/fstab file

> 192.168.x.x:/shared/folder     /mount/point     nfs     nfsvers=3,ro      0       0 

---

### Post by FLeiXiuS on 2006-07-02
What 'Echo $USER' said is only required on the CLIENT side.  On the SERVER side your going to need to install the following...
```
$ sudo apt-get install nfs-kernel-server nfs-common portmap
```

After that is installed, it's time to edit the NFS export config.  Export basically means the files which will be exported from the NFS server to the NFS clients.  
```
$ sudo gedit /etc/exportfs
/path/to/directory           IP-of-Client(options)

```

[I]Example:
/home/fleixius/shared      192.168.0.10(rw, sync)[/I]

The parameters above will share /home/fleixius/shared to whomever has the IP of 192.168.0.10 with read/write permissions.  The sync option tells NFS to keep the files the client see's in syncronize with the files actually on the server.  

That's about it, any questions let me know!

---

