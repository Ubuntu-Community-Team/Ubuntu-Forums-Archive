---
title: "Mounting Network File Sysyem (plz help)"
date: 2006-10-04
forum: Desktop Environments
---

### Post by marufsiddiqui on 2006-10-04
Can I mount network file system?

I have found a way by reading book "Ubuntu Hacks".
as instructed there all i need to do is to add the following command line in fstab

**//hostname/sharename /mnt/share smb defaults 0 0**

then **mount -a** in terminal

& i got the following error

**unknown filesystem type 'smb'**

but the book says i was supposed to write "smb" for SMB Network Fileshare

I can see the share drive icon on desktop but when i try to mount it it says "unknown filesystem "smb""


plz plz help how to resolve this

-----------
another thing I need help on "Adding a network folder" on Kubuntu? where can i get help on this?

plz suggest me a book to learn command line or terminal

---

### Post by marufsiddiqui on 2006-10-04
all right i have got a solution by writin following command

**sudo smbmount /hostname/sharename /mnt/anyname**

but now there's another problem suppose a share name is "English Audio" in a windows XP PC then how can i write "English Audio"?

If i write "English Audio" it says cant resolve Audio
u know what i mean linux taking ENglish & Audio 2 diff thing

all i wanna know how to write these type of folder name (name with space) in linux

plz atleast help me

---

### Post by kjpus on 2006-10-04
You can either use escape ("English\ Audio") or use single quote ('English Audio') in your share name.

---

### Post by marufsiddiqui on 2006-10-04
oh dude thanks for this. it works now. now i can enjoy directly from LAN

---

### Post by dwasifar on 2006-10-04
> **marufsiddiqui said:**
> Can I mount network file system?

I have found a way by reading book "Ubuntu Hacks".
as instructed there all i need to do is to add the following command line in fstab

**//hostname/sharename /mnt/share smb defaults 0 0**

then **mount -a** in terminal

& i got the following error

**unknown filesystem type 'smb'**

but the book says i was supposed to write "smb" for SMB Network Fileshare


The book is a little wrong.  Try it this way in /etc/fstab:

```
//hostname/sharename /mnt/share smbfs auto,rw 0 0
```

You can also add additional parameters to connect in the way you want.  For example, from my own /etc/fstab:

```
//192.168.0.25/misc /remote/misc smbfs username=****,password=****,dmask=777,fmask=777,auto,rw 0 0
```

This mounts the "misc" share at my local network address 192.168.0.25 at /remote/misc in my filesystem; logs on to that share using the appropriate username and password; and sets the permissions for that share to allow any user to read, write, and execute.  (You can also store the username and password in a protected file if you want to, instead of leaving them in clear text within your /etc/fstab file.)

Also, in case your book didn't tell you, you need to have smbfs installed for this to work.  Look in Synaptic and see if it is.  If not, install it.

One last thing: to mount all devices, in Ubuntu, you need to type:

```
sudo mount -a
```

not just mount -a as you tried.

---

