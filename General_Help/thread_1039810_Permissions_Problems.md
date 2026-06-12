---
title: "Permissions Problems"
date: 2009-01-14
forum: General Help
---

### Post by Knuffle on 2009-01-14
I was following the Advanced SSH Ubuntu guide and changed some of the file permissions like it told me to. After rebooting, I could not even log in using the GNOME desktop environment. It gave me some error saying something about how GNOME could not do something with my home folder, so I did:
> 
chmod +rw ~

Now I can no longer update or use the apt-get program. When I do, I get the following error. 

> E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Any help is appreciated. Thanks.

---

### Post by iaculallad on 2009-01-14
For your home directory's permission:

```
[COLOR="Navy"]sudo chmod 644 /home/your_user_name/.dmrc
sudo chown your_user_name /home/your_user_name/.dmrc[/COLOR]
[COLOR="DarkRed"]sudo chmod -R 700 /home/your_user_name
sudo chown -R your_user_name /home/your_user_name[/COLOR]
```

For the apt-get error being prompted, do what the message says:

```
sudo dpkg --configure -a
```

---

### Post by Knuffle on 2009-01-15
Thanks. It worked until the

> sudo chmod -R 700/home/user_name

I got the error
> 
chmod: cannot access `/home/my_user_name/.gvfs': Permission denied

---

