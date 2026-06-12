---
title: "How To Restart Samba"
date: 2009-06-05
forum: General Help
---

### Post by Russell_S on 2009-06-05
Hi, I'm sure I'm doing something wrong but, for the life of me, I don't know what.

After some Googling, I was following some advice (from these very forums) on editing my smb.conf file to put Ubuntu into the same workgroup as the rest of my Windows PC's and my FreeBSD server running Samba.

Having edited the file it said to execute the following comand....

```
sudo /etc/init.d/samba restart
```....however, when I enter this the terminal returns the following

```
sudo: /etc/init.d/samba: command not found
```I've browsed the /etc/init.d directory but there doesn't appear to be a samba file in there. Obviously, I could just reboot the PC but that's not the point and I wouldn't learn anything.

Could someone show me where I'm going wrong please.


Regards

Russell

P.S. This is refering to Ubuntu v9.04

---

### Post by bacardiandwatermelon on 2009-06-05
Weird... that command works for me.. maybe backup the smb.conf and reinstall samba?

---

### Post by Celauran on 2009-06-05
```
whereis samba
```

---

### Post by munky99999 on 2009-06-05
Freebsd might have a different way; in other words 

/etc/rc.d/init.d/smb restart

might be the location.

---

### Post by Russell_S on 2009-06-05
Thanks for the replies.

munky99999: you misunderstand. The FreeBSD server on my network is another PC acting as a fileserver, not the one I'm trying to configure. The machine I'm trying to configure is Ubuntu 9.04

Celauran: whereis samba returns this:
```
russell@ubuntu-desktop:~$ whereis samba
samba: /etc/samba /usr/lib/samba /usr/share/samba /usr/share/man/man7/samba.7.gz
russell@ubuntu-desktop:~$ 

```

Does this help at all?


Russell

---

### Post by Celauran on 2009-06-05
I don't have any 9.04 machines, so I don't think posting my /etc/init.d/samba would necessarily help you. Have you tried backing up your smb.conf and reinstalling the package?

---

### Post by Russell_S on 2009-06-05
The funny thing is that I have another install of Ubuntu 9.04 on my laptop and it is exactly the same. Both machines were freshly installed yesterday.

Incidentally, this is how long I've been experienced with Linux, since yesterday :).


Russell

---

### Post by Russell_S on 2009-06-05
I think I may know where I've been going wrong, and I now feel a bit stupid.

Am I right in thinking that Samba is only responsible for creating SMB/CIFS shares and NOT accessing them. I've just checked and Samba isn't even installed which would explain why it couldn't find it.

So, in view of that, how do I put my Ubuntu box into the same workgroup as the other machines on my network or doesn't it matter. Or, would I still be better off installing Samba in any case.

Sorry to have led you astray and given duff information.



Regards

Russell

---

### Post by Celauran on 2009-06-05
The Samba client should be installed by default, and this should show you available Windows networks. To access your Linux machines from Windows, the Linux machines need a Samba server running.

---

