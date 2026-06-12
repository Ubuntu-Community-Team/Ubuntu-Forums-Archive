---
title: "Remote Desktop (vino) - Generating password from CLI?"
date: 2006-10-08
forum: Desktop Environments
---

### Post by motin on 2006-10-08
I am getting rather frustrated. 

I have both the included vino-server running (port 5900) and a vnc4server started via xinetd on port (5901). The first one shares my logged in desktop and the second shares a second X session in where I can log in to if i please. Problem is, I can't remember the passwords I used when I set them up!

But vino-preferences doesn't really comply with Putty... (need X!). And this trick didn't work:

```

gconftool-2 -s -t bool /desktop/gnome/remote_access/enabled true
gconftool-2 -s -t string /desktop/gnome/remote_access/vnc_password `mkpasswd qwerty`

```

Solution: I ran "vnc4passwd" over SSH and successfully set the vnc4 password. Then I connected to port 5901 and logged in as myself - ran vino-preferences and set my password. 

But how is this done if you haven't a vnc4server running? Ie from CLI?

---

### Post by morton2002 on 2006-10-13
[This page]("http://www.gnome.org/~bmsmith/gconf-docs/C/gnome.html") indicates that the passwords are base64 encoded (search for vnc_password).  I've not tried generating any to test, but I'd love to hear if this works for you.

That page has lots of other interesting information for remote Vino configuration (via SSH) to enable the Vino VNC-style server without having to have an X connection.

**Update: **I found [this other useful page]("http://www.gnome.org/~markmc/remote-desktop.html") that describes how the password is base64 encoded for obscurity-security, but that the real security is derived from user-only privleges to read the configuration files.  So using a password hash like mkpasswd won't work, and I believe it's as simple as running your password through [an online base64 encoder such as this one]("http://makcoder.sourceforge.net/demo/base64.php").

Doing that encoding for 'qwerty' produces this string: cXdlcnR5 ...which is exactly what another user confirmed for the experimental settings in [the parent thread]("http://ubuntuforums.org/showpost.php?p=1598761&postcount=6") from which this was spun off.

---

### Post by motin on 2006-10-14
Thanks morton! I think this thread now can serve as a great help to others who tries to reach their remote desktop by these means.

---

### Post by chele on 2007-09-07
This post from Daniel Pierres Berrange
[http://berrange.com/personal/diary/2007/09/remotely-setting-up-remote-access-to](http://berrange.com/personal/diary/2007/09/remotely-setting-up-remote-access-to) has an example of how to create a base64 password:```
# Enable password auth
gconftool-2 --type list --list-type string --set /desktop/gnome/remote_access/authentication_methods '[vnc]'
PW=`echo 'mypassword' | base64`
gconftool-2 --type string --set /desktop/gnome/remote_access/vnc_password $PW
```However, there is no base64 command on my system. Anyone know where to get that from?

---

### Post by remidub on 2008-03-11
Excuse me for my english, i'm french ... :p

So, in a wonderful world, the base64 command would be in the core-utils package, but it seems that the version of this package is not the last one in my ubuntu (7.10) ... 
You can find the base64 program here : [http://josefsson.org/base64/](http://josefsson.org/base64/)

I downloaded this version : [http://josefsson.org/base64/releases/base64-1.3.tar.gz](http://josefsson.org/base64/releases/base64-1.3.tar.gz)
./configure ... make ... make instal ... and it works ! I changed my vino password ...

(the last problem, is that this version (1.3) of base64 is no more maintained ... indeed it's include in core-utils)

---

### Post by tanascar on 2008-04-02
To change the password, I logged in via SSH and went here:

[http://makcoder.sourceforge.net/demo/base64.php]("http://makcoder.sourceforge.net/demo/base64.php")

Generated the base64 encoding and then type:

gconftool-2 --type string --set /desktop/gnome/remote_access/vnc_password #####

replace ##### with the encoded string that the site generated.

---

### Post by happynix on 2008-05-24
After noting that my base64 encoded password did not match the same base64 encoded password from various websites I came to the conclusion that a slight modification is needed to commands to reset you vino password from an ssh session
```
# 
gconftool-2 --type list --list-type string --set /desktop/gnome/remote_access/authentication_methods '[vnc]'
PW=`echo -n 'mypassword' | base64`
gconftool-2 --type string --set /desktop/gnome/remote_access/vnc_password $PW
## --or--
gconftool-2 --type string --set /desktop/gnome/remote_access/vnc_password $(echo -n 'mypassword'|base64)
```

the -n option for echo does not send the newline character which the base64 command happily encodes :-o

---

### Post by a94060 on 2008-06-29
thanks a lot everyone for the help. I am 900+ miles away from my computer and figured out the problem was with the server not being up (something stupidly prompted me to restart remotely which logged me out) I found how to set it to autologin, now i am just trying to generate a password,thanks though for all the help

---

