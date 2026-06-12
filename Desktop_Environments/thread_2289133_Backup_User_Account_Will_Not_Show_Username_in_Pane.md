---
title: "Backup User Account Will Not Show Username in Panel 14.04"
date: 2015-08-01
forum: Desktop Environments
---

### Post by coljohnhannibalsmith on 2015-08-01
Hello,

When I log into my backup account, I've noticed that my username is not shown in the panel.
I'm in a Flashback Compiz session.  Is there a place where I can change this setting?

Thanks, Hannibal

---

### Post by TheFu on 2015-08-01
Please be more exact. 
* what is the exact userid? This is a number.
* what is the exact username?

If you login with the username, the **id** cmd will tell us what we need to know.  Or you can **su - username** and run **id**.

---

### Post by steeldriver on 2015-08-01
whether or not you supplied a GECOS fullname when you created the account may be significant as well: the command

```

getent passwd *username*

```

may help shed light

---

### Post by coljohnhannibalsmith on 2015-08-01
Here's the terminal output:

sophie@sophie-Inspiron-1545:~$ id hannibal
uid=1001(hannibal) gid=1001(hannibal) groups=1001(hannibal),125(debian-tor)
sophie@sophie-Inspiron-1545:~$ sudo username hannibal
[sudo] password for sophie: 
sudo: username: command not found
sophie@sophie-Inspiron-1545:~$ sudo hannibal
sudo: hannibal: command not found
sophie@sophie-Inspiron-1545:~$ sudo username
sudo: username: command not found
sophie@sophie-Inspiron-1545:~$ su username
No passwd entry for user 'username'
sophie@sophie-Inspiron-1545:~$ su hannibal
Password: 
hannibal@sophie-Inspiron-1545:/home/sophie$ getent passwd hannibal
hannibal:x:1001:1001:hannibal,,,:/home/hannibal:/bin/bash
hannibal@sophie-Inspiron-1545:/home/sophie$ 


Thanks, Hannibal

---

### Post by deadflowr on 2015-08-01
Use dconf-editor and change 
apps >> indicator-session >> show-real-name-on-panel change it from false to true (click on it to add a checkmark; checkmark = true)

I think the default is suppose to be set to off, anyway.

Alternatively you can try dconf command line, if installing dconf-editor is a bit much.(As sometimes installing a single app to do a single function is little underwhelming, imo)
dconf command
```
dconf read /apps/indicator-session/show-real-name-on-panel
```
to see the current setting state (probably set as false)
and ```
dconf write /apps/indicator-session/show-real-name-on-panel true
``` 
will change the setting to true, if not set as such already.

See if that works
Don't know if this what you want , but I'm guessing it is.
(Or close to what you want)

---

### Post by TheFu on 2015-08-01
I know that for userids under 1000 (or is it 500), the login manager doesn't show them in the list.  Depending on the login manager being used, there are ways in the config file to enable or disable a selection. In some corporate environments, showing a list of possible userids would be against corporate security --- not to mention having a list of 1,000 wouldn't really work.

When I run ```
dconf read /apps/indicator-session/show-real-name-on-panel
```
Nothing is returned.

Guess a DE is required, which my system doesn't have.

---

### Post by coljohnhannibalsmith on 2015-08-01
Thank You,

This worked like a charm.

hannibal

---

