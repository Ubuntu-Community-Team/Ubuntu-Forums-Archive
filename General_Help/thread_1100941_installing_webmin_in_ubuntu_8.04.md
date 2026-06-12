---
title: "installing webmin in ubuntu 8.04"
date: 2009-03-19
forum: General Help
---

### Post by pr4y on 2009-03-19
i made the choice of purchasing a dedicated server through softlayer, of which i chose ubuntu 8.04 for an O/S.  The cPanel / WHM addon was an extra 25/month, so I figured I'd just forget that and go with Webmin, as I'd heard good things about it.

I've installed webmin fine, the webmin portal login page comes up fine in my web browser, but when I try to log in, I get invalid username and password.


At this point, I know some of you are thinking... "WTF, go to webmin and ask for their support".  The problem here is, this is a UBUNTU specific problem.  Ubuntu doesn't allow you to log in as the ROOT username, and in this case, webmin is looking for the root user to log in.

When you try to log in, it just throws invalid password errors (when I know it isn't invalid).


The only resources I could find online on this topic were ones stating that:

"Ubuntu in particular don’t allow logins by the root user by default. However, the user created at system installation time can use sudo to switch to root. Webmin will allow any user who has this sudo capability to login with full root privileges."



So at this point, I tried to create a new user and put it under the sudo group (via command line) and try to log into Webmin using this new "SUDO" username, but still no luck.

I'm guessing Webmin takes the root/password during installation and uses that as its default login, but users created by the Ubuntu system after that have to somehow be added to Webmin manually.

I tried finding resources for THIS online, and turned no results.  Webmin uses its own encryption method for passwords, thus making manual user additions impossible.





ANY help at all would be GREATLY appreciated!  Thanks all!


P.S. Ubuntu 8.04 and Webmin 1.4.7.0

---

### Post by amadeus266 on 2009-03-19
Nevermind. I didn't read the whole post. I use webmin on Ubuntu as my standard username and password. I haven't tried adding a new user.

---

### Post by pr4y on 2009-03-19
I don't have a standard username/password given at installation time, all I have is the root password supplied by softlayer (the dedicated server host)

---

### Post by stanz on 2009-03-19
> **pr4y said:**
> I don't have a standard username/password given at installation time, [COLOR=DarkRed]*_**all I have is the root password supplied by softlayer**_*[/COLOR] (the dedicated server host)
softlayer user/pw for webmin? I don't think so...
You've tried your ubuntu user & root pw's...?

might be their system.

---

### Post by pr4y on 2009-03-19
-.-

It is the server root password.

This is a ubuntu specific problem, not a user input error ;)


Webmin works by assigning the ROOT SERVER password as the default portal password.  In this case, ubuntu not being able to literally log IN to the root account, webmin has problems.  I know there are people here that are using Webmin with Ubuntu 8.04, and I'm just wondering if anyone has encountered this situation with a dedicated server.

---

### Post by fieroboom on 2009-03-19
> **pr4y said:**
> -.-

It is the server root password.

This is a ubuntu specific problem, not a user input error ;)


Webmin works by assigning the ROOT SERVER password as the default portal password.  In this case, ubuntu not being able to literally log IN to the root account, webmin has problems.  I know there are people here that are using Webmin with Ubuntu 8.04, and I'm just wondering if anyone has encountered this situation with a dedicated server.

Eh... Sounds to me like you're getting ripped... If they gave you a root password, then that's a root password. Period. However, if they gave you a super-user password, then you might need to run something like:
```
sudo passwd
```
and actually set the *root* password...
Personally, I prefer a server that doesn't limit me, so I got a VPS. ;)

If that doesn't work, then you're gonna need to contact their TS. (unless I spontaneously think of something else)
:D
-Paul

EDIT:
Ubuntu disallows graphical root logins. Terminals are a completely different story. For ssh, you can check in /etc/ssh/sshd_config and verify that 'PermitRootLogin' is uncommented and set to 'yes'. AFAIK, logging into webmin as root is irrelevant in regards to the graphical limitation.
I run webmin on just about every box I have, and I've never run into that issue.

---

### Post by stanz on 2009-03-21
> **pr4y said:**
> -.-
  It is the server root password. not a user input error ;)
Didn't imply user error....:shock:

> This is a ubuntu specific problem
I don't think so...have you at least brought this issue to their $ support?

As fieroboom typed...

:D

---

