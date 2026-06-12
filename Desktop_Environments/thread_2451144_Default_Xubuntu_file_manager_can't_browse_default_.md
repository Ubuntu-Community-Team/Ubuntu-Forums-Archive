---
title: "Default Xubuntu file manager can't browse default Samba shares"
date: 2020-09-28
forum: Desktop Environments
---

### Post by metacell on 2020-09-28
I did a fresh install of Xubuntu 20.04, and installed samba (sudo apt install samba).

I then attempted to browse my local computer over SMB using Thunar. My workgroup and computer showed up, but it was not possible to enter my own computer and view the shares.

I solved it by adding the line
```
server min protocol = NT1
```
to /etc/samba/smb.conf, to make the Samba server compatible with the Samba version 1 protocol.

So from what I understand, the default file manager in Xubuntu 20.04 can't use the default Samba configuration.

Should this be reported as a bug in Xubuntu?

---

### Post by Morbius1 on 2020-09-28
> So from what I understand, the default file manager in Xubuntu 20.04 can't use the default Samba configuration.
Depends on the definition of "can't use". 

I added a "test_file.txt" file to my Public folder then shared it through samba on my Xubuntu20 machine. I can access this share from myself if I ask for it explicitly by hostname and share name in Thunar:
[ATTACH=CONFIG]287032[/ATTACH]

What I cannot do is discover ( Browse Network ) that server and get a list of shares:[ATTACH=CONFIG]287033[/ATTACH]
>  Should this be reported as a bug in Xubuntu?         
It is a bug to be sure but it is not in Xubuntu or Thunar. It's in gvfs - specifically gvfsd-smb-browse. You can add a " so when the hell is this going to get fixed" in the existing bug if you want: [URL="https://bugs.launchpad.net/gvfs/+bug/1828107"]https://bugs.launchpad.net/gvfs/+bug/1828107

[/URL]

---

### Post by metacell on 2020-09-28
> **Morbius1 said:**
> I can access this share from myself if I ask for it explicitly by hostname and share name in Thunar:

Thanks, that helps for now.

---

### Post by ActionParsnip on 2020-09-28
Is there no scope to use SFTP/SSHFS? Samba is awful

---

### Post by metacell on 2020-09-29
> **ActionParsnip said:**
> Is there no scope to use SFTP/SSHFS? Samba is awful

I'll probably try NFS instead, if that is too hard to get working I'll try SSHFS.

I only use Samba because it always comes up first when you search for Linux file sharing. The guides never warn you about these glaring incompatibility problems.

---

### Post by Morbius1 on 2020-09-29
Just to keep the record straight the "glaring incompatibility" is for gvfs not samba. Before they started mucking up gvfs the gnome developers needed the assistance of a Samba subject matter expert which is probably not available in the limited gnome gene pool. And remember you can do a CIFS mount which bypasses gvfs completely.

Anyhoo ..... As for SSH / SFTP give this a shot:

[1] Install ssh:
```
sudo apt install ssh
```
[2] Go to the other Linux machine and access the ssh server in Thunar:
```
ssh://hostname.local
```

You will get something like this:
[ATTACH=CONFIG]287043[/ATTACH]

Select log in anyway. You will get a prompt for credentials.

And as my wife's Irish grandmother would say ... Bada Bing Bada Boom:
[ATTACH=CONFIG]287044[/ATTACH]

You can get fancy with this if you want and create an avahi announcement for it so it shows up under "Browse Network".

---

### Post by metacell on 2020-09-29
Thanks, @Morbius, that helps a lot.

---

