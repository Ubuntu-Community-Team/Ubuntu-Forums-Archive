---
title: "SSH vs. SFTP for obtaining files remotely"
date: 2009-03-18
forum: General Help
---

### Post by Nano_ext3 on 2009-03-18
I know you can SSH or use SFTP to enter a remote server to obtain files, using get for SFTP, but If I choose to SSH into my remote server (more commands etc to use), but SCP is giving me issues:

```
scp cinema\ report.doc  user@55.55.555.555:/home/user/

```


In the above the code works, but places the file in the /home/user folder on the remote machine not my local machine.

Help?

Thanks


-Nano

---

### Post by fieroboom on 2009-03-18
> **Nano_ext3 said:**
> I know you can SSH or use SFTP to enter a remote server to obtain files, using get for SFTP, but If I choose to SSH into my remote server (more commands etc to use), but SCP is giving me issues:

```
scp cinema\ report.doc  mikeyd@<edited-ip>:/home/mikeyd/

```


In the above the code works, but places the file in the /home/mikeyd folder on the remote machine not my local machine.

Help?

Thanks


-Nano

You're just doing it a little bit backwards... ;)
```
scp /SOURCE/path/file /DESTINATION/path/file
```
So in order to move cinema\ report.doc to your local machine, you need:
```
scp mikeyd@<edited-ip>:/home/mikeyd/cinema\ report.doc .
```

The period at the end simply specifies the current working directory. Specify the full path if you want it elsewhere:
```
scp mikeyd@7<edited-ip>:/home/mikeyd/cinema\ report.doc /some/other/path/
```

:D
-Paul

---

### Post by adult swim on 2009-03-18
you guys might want to edit those posts that have username and ip address

---

### Post by fieroboom on 2009-03-18
> **adult swim said:**
> you guys might want to edit those posts that have username and ip address

Excellent point. I should've caught that; my apologies.
:D
-Paul

---

### Post by ruel- on 2009-03-18
or you can use gFTP.. it supports SFTP

```
sudo apt-get install gtfp
```

---

### Post by Nano_ext3 on 2009-03-18
This code is still placing the file in my /home/user/ on the remote server:

```
scp -P 4444 user@55.55.555.555:/home/user/Documents/Documents/temp /home/user/

```

Ruel, I use Gftp, I just want to know the Terminal way :)  I can also use SFTP via temrinal as well.  I like ssh for the complete control.

**Keep in mind I am ALREADY ssh'ed into the Remote Server**

---

### Post by ruel- on 2009-03-18
ummm ok, sorry.. well try this:

```
scp -P 4444 /home/user/Documents/Documents/temp user@55.55.555.555:/home/user/
```

---

### Post by fieroboom on 2009-03-18
> **Nano_ext3 said:**
> 

**Keep in mind I am ALREADY ssh'ed into the Remote Server**

Herein lies the problem... ;)
Remember, "local" is relative to where your command prompt is. In other words, if you're ssh'd into a remote machine, then that remote machine is now "local" in that terminal.
My explanation is still correct... source file path first, destination second. Here's an example I just did to get my new profile pic on my virtual private server:
```

root@paul-desktop:~# scp ~/ubuntu-forum-avatar.jpg vps:/var/www/southeast/
ubuntu-forum-avatar.jpg                                                 100% 6675     6.5KB/s   00:00
```

ubuntu-forum-avatar.jpg is in my local home directory, hence the tilde slash (~/). That command pushed my profile pic to my server, which I can now link to: [http://southeastfieros.com/ubuntu-forum-avatar.jpg](http://southeastfieros.com/ubuntu-forum-avatar.jpg)
...and use in my profile.
Let me know if I need to explain it differently.
:D
-Paul

---

### Post by HermanAB on 2009-03-18
You can also use Nautilus to connect to a remote server with SSH (on File menu) and then click-drag-drop files between two Nautilus windows.

Cheers,

Herman

---

