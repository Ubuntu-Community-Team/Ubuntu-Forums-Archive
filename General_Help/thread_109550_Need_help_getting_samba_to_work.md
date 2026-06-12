---
title: "Need help getting samba to work"
date: 2005-12-28
forum: General Help
---

### Post by TrinitronX on 2005-12-28
I've been working on this for a while now, and cannot figure out the problem.  I want to connect to a network share on a windows 98 computer from my ubuntu box, but am having troubles getting samba to connect at all.

Here's what I've done so far: 
1) gotten samba through synaptic
2) added this line to my /etc/fstab file: ```
//XBOX/MY\040MUSIC /media/xbox smbfs credentials=/etc/samba/auth.smb,dmask=777,fmask=777  0 0
```
3) created the samba mount directory '/media/xbox'
4) created a credentials file in /etc/samba/auth.smb, with two lines like: ```
username=myusername
password=mypassword
```
5) changed the file permissions to read/write for only root on the auth.smb file using: ```
chmod 600 /etc/samba/auth.smb
```
6) tried to connect using mount: ```
sudo mount /media/xbox/
12104: Connection to XBOX failed
SMB connection failed

```

This failed as you can see.

I have also tried debugging my issue by using a few other commands:
```
nmblookup -A 192.168.1.100
Looking up status of 192.168.1.100
        XBOX            <00> -         B <ACTIVE>
        WORKGROUP       <00> - <GROUP> B <ACTIVE>
        XBOX            <03> -         B <ACTIVE>
        XBOX            <20> -         B <ACTIVE>
        WORKGROUP       <1e> - <GROUP> B <ACTIVE>
        X               <03> -         B <ACTIVE>
        WORKGROUP       <1d> -         B <ACTIVE>
        ..__MSBROWSE__. <01> - <GROUP> B <ACTIVE>

        MAC Address = REMOVED
```
I can see that my windows 98 box returns the netbios table to me, so I then try listing what shares I have set up on it:
```
smbclient -LXBOX -I 192.168.1.100
Password:

        Sharename       Type      Comment
        ---------       ----      -------
        MY PICTURES     Disk      Pics
        PRINTER$        Disk
        HP LASERJET     Printer   HP LaserJet III
        MY MUSIC        Disk      Home PC Music
        IPC$            IPC       Remote Inter Process Communication

        Server               Comment
        ---------            -------
        XBOX                 Home PC

        Workgroup            Master
        ---------            -------
        MSHOME               ARCTURUS
        WORKGROUP            XBOX

```
I execute the command, and put in the share's password, and it successfully sends me the share list.  So, I try to actually connect to it:
```
smbclient //XBOX/MY\040MUSIC -I 192.168.1.100
Password:
tree connect failed: ERRSRV - ERRinvnetname (Invalid network name in tree connect.)

```
Since the share's name has a space in it, I replaced it with the escape sequence '\040'.  Again, I put in the same password that I used before for the shares.  This time it gives me the error you see above.  I can't figure out why it doesn't like the name I'm giving it.  Am I using the right escape sequence for the space?  I also tried it instead with '\ ' to just directly escape the space, but I get the same thing.

---

### Post by TrinitronX on 2005-12-31
bump

---

### Post by healychan on 2005-12-31
Base on the codes you provided. It seems that you haven't create a share in the smb.conf file. Am I right???

---

### Post by TrinitronX on 2005-12-31
Yes... I haven't created a share on my ubuntu box, I'm merely trying to access my win98 machine's shares from samba.

I think I found my first problem now... I needed to open up firestarter and allow connections from the win98 box.  However, now I'm getting this:

```

sudo mount /media/xbox/
10212: tree connect failed: ERRSRV - ERRbadpw (Bad password - name/password pair in a Tree Connect or Session Setup are invalid.)
SMB connection failed

```

I'm going to go and make sure my username and password for the shares are set up correctly again.

EDIT:  Ok... it turns out I was using the wrong password :p.  I have successfully mounted the share as a smbfs drive now.

---

