---
title: "How to password protect access to an XP share from linux ?"
date: 2009-04-16
forum: General Help
---

### Post by uncle-c on 2009-04-16
Firstly I am not running a samba share on a Linux box nor am I running smbd / nmbd. I have an XP  machine ( 192.168.xxx.xxx ) which holds a lot documentation in pdf and html formats. I have set the directory ( c:\documentation) which contains all this data to be shared over the network. 

From a shell prompt I can do this to access the share

```

uncle-c:~$ smbclient //192.168.xxx.xxx/documantation
Enter uncle-c's password:
DOMAIN=[*******] OS=[**********] SERVER=[***********]
smb: \>

```

I can then enter the ls command to list the files or get command to transfer the files I require. The problem is that even though I am prompted for a password I can just enter nothing at the prompt and then I am allowed access to the share. How can I password protect this access ? Do I have to create a sambauser called uncle-c with a respective password ? 
The same applies to mounting the share via mount / cifs :

```

uncle-c:~$ mount -t cifs //192.168.xxx.xxx/documentation -o username=uncle-c  /mnt/xpshare

```

At present I can mount the share without using a password. I would like this method password protected as well. Any tips ?

Cheers,
UC

---

### Post by lykwydchykyn on 2009-04-16
Security needs to be configured on the XP box.  It would make any sense if one had to configure a client to make the server secure, now would it?

Is the XP box XP home or XP professional?

---

### Post by sedawk on 2009-04-16
As said above, you have to configure the password on the Win box.

If you only need read access to that share an alternative would
be to run a web server on the Win box and browse the documentation
via a browser from any PC on the network. Then you do not
have to bother about SMB security.

---

### Post by uncle-c on 2009-04-16
Thanks gents. What a dodo I am !!!! I'm running XP pro. lykwydchykyn. I'm just messing about on a home network and am just interested how I can password protect this share access.

Thanks again,
uc

---

### Post by lykwydchykyn on 2009-04-16
Admittedly, configuring security on XP confounds me a little bit, but here's what I would try:
 - Open explorer, go to tools=>folder options
 - click over to the view tab and scroll all the way down.  Uncheck "use simple file sharing" if it's checked.
 - I forget if that requires a reboot.  It might.
 - Browse to your shared folder in explorer.  Right-click it and go to "properties"
 - click over to the "sharing" tab and click "permissions". 
 - I *think* the way to do this is to remove the "everyone" group and add back only the users you want to give access to.  See if that works.

---

### Post by uncle-c on 2009-04-16
Sweet as a nut lykwydchykyn ! Worked a treat !!!
Thanks a lot !

uc

---

