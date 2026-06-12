---
title: "How can i use gftp to connect to an ssh server that only uses key authentication"
date: 2009-02-11
forum: General Help
---

### Post by sefs on 2009-02-11
I have a ssh server setup where authentication is via keys only.  I want to use gftp so i can have a gui to easily copy files back and forth.  I know of know other gui to do this. 

Is it possible to setup the gftp client to use the key?

---

### Post by spiderbatdad on 2009-02-11
sftp is used for connecting to ssh server. If the key is where it should be in your user folder...there is nothing to do. It should just work. Test by typing into the address bar of your firefox browser sftp://ipaddress. Where ipaddress is your actual ip address.

So you might look into vsftp. But nautilus handles this already just fine.
Go to Places>>Connect To Server. Select ssh in the server type window...input the ip address and thats all you need to mount the file system on your desktop. You can even bookmark the connection with nautilus.
Unmount the volume by right clicking the file system and choose Unmount Volume.

---

### Post by sefs on 2009-02-11
Thank you so very much.

I just discovered too that filezill3 supports key authentication.  Good stuff.

---

### Post by riger99 on 2011-03-30
> **sefs said:**
> Thank you so very much.

I just discovered too that filezill3 supports key authentication.  Good stuff.

Nice to read, but where do I enter the path to the key?

I've not yet been able to configure FileZilla 3.3.1 to use .key files.

Thanks

---

### Post by riger99 on 2011-03-30
> **riger99 said:**
> Nice to read, but where do I enter the path to the key?

I've not yet been able to configure FileZilla 3.3.1 to use .key files.

Thanks

For others who may need this. The .key file can be added via:

Edit >> Settings >> SFTP

As of FileZilla 3.3.1, it will convert the .key file into a format that FileZilla can understand and use. In this case, I had to enter the passphrase for the key and FileZilla stored that key in an unprotected format. Granted, this is poor security, but at least I can get it to work.

---

