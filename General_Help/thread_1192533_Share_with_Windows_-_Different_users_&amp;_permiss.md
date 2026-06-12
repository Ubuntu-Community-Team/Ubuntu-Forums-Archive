---
title: "Share with Windows - Different users &amp; permissions to same share"
date: 2009-06-20
forum: General Help
---

### Post by Heathicus on 2009-06-20
I bet this problem has been asked and answered before and I just haven't been able to find it with the searches I'm doing.  Maybe I'm not good at searching and I'm using the wrong terms or something.  So please forgive me if this has been addressed 100 times already.

I have a file server running Ubuntu that I set up close to a year ago.  I use it to hold all of my media (movies & music) and those shares are accessible from Windows on my other PCs, and the Xboxes running XBMC.  It has worked great and is still working great.  I haven't had to do much at all to the Ubuntu server in the past year.

Now, I have given my son a hand-me-down PC.  I want to give him READ only permission to the media shares.  Currently, I can map a network drive from his computer using the same account used to access them on the other PCs, but that account has full Read/Write permission.  

I can figure out how to create his user account in Ubuntu.  I can edit the smb.conf file to give different shares different permissions on a *per share* basis, but I want to give different Windows users access to the same shares with different  *per user* permissions.  And that's what I can't quite figure out how to do.

Any help?

---

### Post by swerdna on 2009-06-20
> **Heathicus said:**
> I bet this problem has been asked and answered before and I just haven't been able to find it with the searches I'm doing.  Maybe I'm not good at searching and I'm using the wrong terms or something.  So please forgive me if this has been addressed 100 times already.

I have a file server running Ubuntu that I set up close to a year ago.  I use it to hold all of my media (movies & music) and those shares are accessible from Windows on my other PCs, and the Xboxes running XBMC.  It has worked great and is still working great.  I haven't had to do much at all to the Ubuntu server in the past year.

Now, I have given my son a hand-me-down PC.  I want to give him READ only permission to the media shares.  Currently, I can map a network drive from his computer using the same account used to access them on the other PCs, but that account has full Read/Write permission.  

I can figure out how to create his user account in Ubuntu.  I can edit the smb.conf file to give different shares different permissions on a *per share* basis, but I want to give different Windows users access to the same shares with different  *per user* permissions.  And that's what I can't quite figure out how to do.

Any help?
OK, the share is constructed to be generally read-write. It's not a big drama to make restrict access for certain users by defining a "read list".

There are two sorts of shares: If it's a share that was "made" with the click-and-share facility in Nautilus, it's called a "usershare". If it is a share that was "made" by including a stanza in the file smb.conf, then it's called a "classical" share. Usershares are pretty much world-writeable and hard for new users to modify and restrict. Classical shares are easy to restrict.

To save me a whole lot more typing, which type of share is it, a usershare or a classical share? Look into smb.conf to see if the definition is there. Use this command to look:```
testparm /etc/samba/smb.conf
```If it's not there, check in the directory /var/lib/samba/usershares with htis command:```
ls -l /var/lib/samba/usershares

```

So is it classical or usershare? And tell me more about the config of the share.

---

### Post by Heathicus on 2009-06-20
I "made" the shares by editing the smb.conf file.  I found a template on the web (probably in these forums) and edited it to my use. 

Would posting the content of my smb.conf file help?

```

[global]
    ; General server settings
    netbios name = GEEZER
    server string =
    workgroup = FITTSHOME
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = user
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    wins support = yes

    syslog = 1
    syslog only = yes

[Media1]
    path = /media/Media1
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = heath
    force group = heath

[Media2]
    path = /media/Media2
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = heath
    force group = heath

```

Media1 and Media2 are each 500GB hard drives in addition to the boot hard drive.  In the GUI, if I look at the Security tab of the properties, it only says the permissions could not be determined.

I know this is something that is very simple, but I just don't know what I'm doing!

---

### Post by swerdna on 2009-06-20
Thanks -- clear as crystal now.

Put this line in the share/s you want to restrict to read-only for tom and harry and ethel:
```
read list = tom, ethel, harry
```

---

### Post by Heathicus on 2009-06-21
I just knew that was going to do the trick, but it didn't.  :(  

I already had created my son's user account using the GUI in Ubuntu (System - Administration - Users & Groups).  His Windows account on his PC has the same username and password.  I added the line you said to add, but he is still prompted for credentials before he can access the file server.  Manually typing in the username/password doesn't work.  Typing in MY username/password at that prompt DOES give access.  I have restarted Samba (as well as the physical computer itself).

I've done some more reseach which makes me think that using "force user" could be part of the problem?  I also tried using the "valid users = <username>" line but still no change.

---

### Post by swerdna on 2009-06-21
You need to add oyur son'r username to the samba user database before he can access the shares. Open a terminal and enter this command:```
smbpasswd -a sons_username
```follow the bouncing ball from there.

The problem is not prima facie "force user/group" parameters. There could be a problem with conflicting underlying Linux permissions. So please post the returns you get from this terminal command:```
ls -l /media
```

Oh, and when you say "I can map a network drive from his computer", exactly how are you mapping the share?

And if you browse to the Linux computer using Network Neighbourhood in your son's windows computer, is it the same problem as using the mapped share (or am I getting confused by all the terminology here?).

---

### Post by Heathicus on 2009-06-22
It works now!  Thanks so much for the help.  What I ended up doing was connecting a keyboard, mouse, and monitor to the server and actually logging on locally with his account just to make sure his account worked.  When I did that, I got a message saying "Adding user" (or something like that).  I guess that's basically what the "smbpasswd -a" command does?

Again, thanks for the help!

---

