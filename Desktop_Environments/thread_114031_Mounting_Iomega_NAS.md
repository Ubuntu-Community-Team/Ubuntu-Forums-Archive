---
title: "Mounting Iomega NAS"
date: 2006-01-07
forum: Desktop Environments
---

### Post by 1337G33K on 2006-01-07
Hi all, I've recently switched over from WinXp to Breezy and found that I can no longer access my Iomega Network HDD.  I've searched around and found FAQs that refers to editing /etc/fstab.

Assuming my drive name is titan and the shared folder is NetHDD:
***//titan/NetHDD     /mnt/titan     smbfs     defaults,defaults     0    0***

Since there's no need for a username and password to access this drive, I've put in "defaults".

Unfortunately, when I tried to to re-mount devices in fstab using
***sudo mount -a***

I get:[I]
mount: wrong fs type, bad option, bad superblock on //titan/NetHDD,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so[/I]

Can someone tell me what I'm doing wrong?  Thanks in advance.

---

### Post by Stormbringer on 2006-01-07
Hi!

You need to install 'smbfs' in order to access SMB shares on the network. Fire up Synaptic, search for 'smbfs' and install the package. Alternatively you may reach the same goal by typing "sudo apt-get install smbfs" in the terminal.

To mount the share you're trying to access automagically at system startup you better follow these steps:

- Make sure the mountpoint exists!
  Open a terminal and type...

```

# ls /mnt

```

Now you should see at least one directory - following your example it should be called "titan". If it doesn't exist you better create it right away...

```

# sudo mkdir /mnt/titan

```

- Let's create the required credentials file we need to authenticate ourselves against the smb-server...

```

# sudo gedit /root/credentials

```

Insert the following two lines:

```

Username=1337G33K
Password=IAM1337

```

**NOTE:** Replace the examples with your User/Password combination you've set on your iomega NAS.

Save the file and exit gedit.

```

# sudo chmod 0700 /root/credentials

```

- Now we need to put the appropriate line into fstab...

```

# sudo gedit /etc/fstab

```

The following needs to be written in ONE LINE (just in case it gets wraped in the post)!

```

//TITAN/NetHDD  /mnt/titan  smbfs  credentials=/root/credentials,uid=1337G33K,gid=1337G33K  0  0

```

**NOTE:** Replace "1337G33K" with your actual UBUNTU username and group! If you fail to do so the share will get mounted with wrong access permissions!

Save the file and exit gedit.

- Does it mount ... ?!?

```

# sudo mount -a

```

Shouldn't throw any errors on you if you've done it right.

- IF it says "Invalid Username" or "Invalid Password" then you specified the wrong WINDOWS username/password combination in /root/credentials
- IF you cannot write to the mounted share you specified the wrong UBUNTU user/group in /etc/fstab

---

### Post by 1337G33K on 2006-01-08
That worked like a charm.  Thanks!

One more question though, if I want every user on this computer to have rw access to the NAS, setting "group" to users would do the trick, right?

Thanks again for your help.  :KS

---

### Post by 1337G33K on 2006-01-10
Hmmm, it seems like there's a slight problem with what I'm doing.  Since the NAS does not actually require authentication, I had the following parameters in /etc/fstab:

```
//titan/NetHDD  /mnt/titan      smbfs   defaults,defaults,uid=gene,gid=users    0       0
```

But now it asks me for a password on every bootup.  Is there a way I can bypass this?

---

