---
title: "no samba shares in network in thunar"
date: 2012-08-14
forum: Desktop Environments
---

### Post by ark1-87 on 2012-08-14
Using xubuntu 12.04 i used to be able to click network in thunar and have my share from my readyNAS show up. But now the samba share for the NAS is gone and it just shows 'windows networks' which when I click says no shares found. What is weird is that I can still access the shares by typing smb://[NAS-IP]/[ShareName]. I boot a into xubuntu 12.04 live usb stick and the share appears there in network.  I tried comparing all packages in the live cd with the ones on my install but they are all the same. I think this could have happened when i had broke some packages  when I was trying to install seahorse-plugins; but xubuntu did a --dist-upgrade after and fixed all broken packages. SO if anyone knows the problem pls share.

---

### Post by Toz on 2012-08-14
Do you have the gvfs-backends package installed?

---

### Post by ark1-87 on 2012-08-16
yes gvfs-backends is installed.

---

### Post by ark1-87 on 2012-08-21
bump

---

### Post by ark1-87 on 2012-08-24
bump

---

### Post by bootedguy on 2012-08-24
I have had poor luck with SMB. If your NAS is like many, you can use NFS to mount the NAS as a folder. Also, I have found SSH to be very reliable.

---

### Post by dschaller on 2012-08-24
I think this a name resolution issue. Since 5.10 or so, every time I install Ubuntu I've had to tweak it to see my Samba shares. It just won't view them out of the box. There are two things I usually need to do. 1) Install "winbind" for authentication and directory service and then 2) Edit the file /etc/nsswitch.conf and add "wins" to the hosts line. Mine happens to looks like this:

```
hosts:  files mdns4_minimal [NOTFOUND=return] wins dns mdns4
```

After you've done this, reboot the machine. This has worked for me on many installations when I can't get the file manager to display my Windows shares. Sounds like it might be your problem too.

---

### Post by ark1-87 on 2012-08-26
Well I tried dschaller's suggestion but still can't view the nas from network. I guess my next try will be to mount the folder with nfs.Thanks for the help.

---

### Post by Merrattic on 2012-08-27
Use gigolo to setup the connections?

Also try waiting a bit. Give "Windows Networks" a double click and wait a while the share may then appear after a while. Mine has this behaviour and I also have the "thunar speed fix" in place ([http://xubuntu.org/news/faq-1204-precise/](http://xubuntu.org/news/faq-1204-precise/) Item 2)

---

### Post by dschaller on 2012-08-29
Is the Samba client machine in the same workgroup as the Samba server? I think they need to be in order to see each other. For example, if one is in the "MSHOME" workgroup by default, and the other is in "WORKGROUP" by default there can be trouble.

---

### Post by ark1-87 on 2012-08-30
merrattic: When I click 'windows networks' it  'failed to open windows networks: failed to retrieve share list from server'. I am currently using gigolo to connect to the shares and it does the job well.

dschaller: I have the NAS set to workgroup, I think it should show up under windows networks. I will change the workgroup just to see what happens.

thanks.

---

### Post by ark1-87 on 2012-09-06
Well, I feel dumb, it turned out to be my firestarter firewall. When i disabled the firewall it worked. even when the firewall wasn't running it still blocked the samba connections.

---

### Post by dschaller on 2012-09-08
Very good! Glad you got it sorted out!

---

