---
title: "cannot log in"
date: 2010-03-19
forum: Dell Ubuntu Support (CLOSED)
---

### Post by vishal060 on 2010-03-19
hi friends
i am in a great dileama
i just updated my system ..
after a few restarts i got error messages as follow
#could not update ICE authoriy file /home/prakash/.ICEauthority


#there is a problem with configuration server (/usr/lib/libconfg/2-4/gconf-sanity-check=2 excited with status 256


 and so on..

please help me with it

---

### Post by ronnielsen1 on 2010-03-19
Here's a similar post

[http://ubuntuforums.org/showthread.php?t=1061084](http://ubuntuforums.org/showthread.php?t=1061084)

>  				 				**Re: /usr/lib/libgconf2-4/gconf-sanity-check-2 exited with  error status 256** 			
 			 			 		   		 		 		Hi

I just did chmod 1777 /tmp and gnome rocks again ...


---

### Post by vishal060 on 2010-03-19
> **ronnielsen1 said:**
> Here's a similar post

[http://ubuntuforums.org/showthread.php?t=1061084](http://ubuntuforums.org/showthread.php?t=1061084)



could you tell me what chmod 1777/temp  is

---

### Post by ronnielsen1 on 2010-03-19
I'm not a programmer or anything, just an user but it appears that tmp (not temp) gets permissions changed to where only root can write to /tmp and sudo chmod 1777 /tmp will change this back to allow users to also write to /tmp. The 1 being the sticky part (Not sure) and the 777 changes the file to writable

---

### Post by wojox on 2010-03-19
> **ronnielsen1 said:**
> I'm not a programmer or anything, just an user but it appears that tmp (not temp) gets permissions changed to where only root can write to /tmp and sudo chmod 1777 /tmp will change this back to allow users to also write to /tmp. The 1 being the sticky part (Not sure) and the 777 changes the file to writable

Correct and "777" means let the owner, group, and every one else have read, write and execute permision to this folder.

---

### Post by vishal060 on 2010-03-19
i tried it but it does not solve any problem
i cannot login 
also my login mode is set to automatic so i cannot access any other user account

---

### Post by wojox on 2010-03-19
When you boot hold down the left Shift key and choose recovery mode. Then drop into a root shell and issue:

```
nano /etc/gdm/custom.conf
```

You can then disable automatic login. I don't use auto login so here's what mine looks like:

```

[daemon]
timedloginenable = False
automaticlogin = None
automaticloginenable = False
timedlogindelay = 30
timedlogin = None

```

Press Ctrl+O to save and Ctrl+X to exit nano. Then reboot and see what happens.

---

