---
title: "smb and fstab strangeness"
date: 2006-02-06
forum: Desktop Environments
---

### Post by jezjones on 2006-02-06
Hi everyone,

I have set up a local web server and i am trying to connect to the shared drives with samba.... all is installed and working but now i am trying to add the drives to my fstab so i dont have to manually mount them.
(I am using samba as there are windows clients on the network that want to connect to the web server).

If i go to the command line and put 
```

sudo smbmount //159.92.60.132/web /media/rgDevServer -o credentials=/home/ulap/linbox-credentials.txt -t smbfs

```

then the share is mounted no problem but if i put the following line in my fstab then i get an error saying 'bad line in fstab' when i mount -a
```

//159.92.60.132/web     /media/rgDevServer smbfs rw,credentials=/home/ulap/linbox-credentials.txt, uid=1000,gid=1000 0 0

```

note 1000 is the right gid and uid for the main user i log in as on this machine.


Can anyone point out where i am going wrong?

I have other smb filesystems in my fstab, the only difference with this one is that is really is a samba server and not an NT server.


Thanks

---

### Post by el3ktro on 2006-02-06
Try two things:

Put the "credentials" argument into "" signs, like credentials="/home/ulap..." and remove the white space before the uid=1000.


Tom

---

### Post by jezjones on 2006-02-07
Thanks for that, the fix was the white space before UID.
Using "" threw and error about reading the credentials file.

Jez

---

