---
title: "Umask 0000 - how to achieve it's functionality on ext3 automatically?"
date: 2009-02-12
forum: Desktop Environments
---

### Post by lores on 2009-02-12
Hello!

My problem concerns Samba. My computer smb-shares an ext3 folder containing films. I chmod 777 -R it and lan-users can access and change it without a problem - that's my goal.

However, whenever I add anything into it, the permissions of the new files are not adequate for multi-user purposes. Therefore, I have to keep chmodding 777 any newly created files and folders in order to make them available for others.

How can I configure the partition to automatically assign 0777 permissions to new files and folders? Currently, only the creator (-user) has rw, the others have ro.

While browsing the web, I have found a similar feature for vfat, ntfs - "umask 0000" (mount's option). It is said to be doing exactly what I wish my partition to, but doesn't work with ext...

Thanks in advance; greets!

---

### Post by digitalbenji on 2009-02-12
You can accomplish this in your /etc/samba/smb.conf file by adding these two lines to the Movies share: ```
        
force create mode = 0777
force directory mode = 0777
```

Let me know if that helps.  Thanks,

---

### Post by lores on 2009-02-12
Hi!

Thx for the reply.

I've had the entries

```

    	create mask = 0777
    	directory mask = 0777

```

in smb.conf already - they seem to just cause the permissions of files created via smb (network users) to get 777, not the ones I am creating locally. Therefore, I assume that the addition of 'force' doesn't change a thing...

---

### Post by digitalbenji on 2009-02-13
Oh, sorry, didn't realize you're creating these locally.  I'm researching how you can do this now, but so far, I'm not finding anything I think will work.  What are the permissions on the root of the share?  (if the share is /data, who owns /data and is /data chmod 777?)

---

### Post by lores on 2009-02-13
It's 0777 and me.

[BTW Ubu 8.10 u-to-d]

---

### Post by lores on 2009-02-14
Anybody's got an idea?

---

### Post by digitalbenji on 2009-02-17
what group owns it?  You should add the samba user people connect as to that group as well, although I'm sure you've done that.

---

### Post by lores on 2009-02-17
Thx for feedback.

The group is actually "lores", the auto-group created with my ubuntu-user (which is also "lores").

I haven't added the network-users to that group, as network computers are to be able to access and change my files without any security measures (there are ones on different layers - restricting IPs, firewalling etc.).

Also, I have some more adjustments:

```

[E]
    	path = /media/Data/
	public = yes
	writable = yes
        browseable = no
        guest ok = yes
	available = yes
	inherit permissions = yes
	guest account = nobody
	force user = nobody
    	force group = nogroup
    	create mask = 0777
    	directory mask = 0777

```

However, I don't think the problem lies therein, because it actually doesn't have anything do to with samba or network at all! It's just the case of LOCAL permissions - when I create a file and e. g. another LOCAL users is willing to access it, they can't!

Therefore, I suppose this issue is quite common to others who use one computer with multiple users. Quite pushing aside, isn't it?

---

