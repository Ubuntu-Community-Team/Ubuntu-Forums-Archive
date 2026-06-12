---
title: "accessing shares from windows"
date: 2007-10-24
forum: Desktop Environments
---

### Post by hilo4321 on 2007-10-24
Lo all, been using these forums for a long time, just never needed to start my own post for anything.

So here's the deal:

I have been working for a couple hours on making my files available to another computer on the network, but to no avail.  i have samba installed and all that, and have added an extra user to my ubuntu setup in order to allow it to become an SMB user.  The problem is, when I enter the username and password on the windows machine, it just closes the box, and reopens it, with no description or reason for doing so.  I am wondering if I did something wrong, or if I am just screwed.  I have been using SWAT for editing, and let me know if you need any more info.

Thanks a lot for any help, time to restart, and boot into gutsy....wish me luck.

---

### Post by TeaSwigger on 2007-10-24
Do be sure to check out this "How to" which was very helpful to me:

[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

Luck :)

---

### Post by hilo4321 on 2007-10-24
well, ive worked my way through much of that stuff, but mainly, my question is why can i not enter a username/password when it is recognozed by samba?

i realize that i can map a drive, but will that circumvent the necessity of entering a password?

---

### Post by TeaSwigger on 2007-10-24
To question two, if I understand you rightly, no it wouldn't, unless the share has permissions allowing it. To question one, if windows isn't configured to find the WINS server and the samba share is set as a WINS server, that might make the login fail, at least it was doing that on me... I also have these settings for the share (in the " [MyFiles] " section at bottom of the example config in the tutorial)
    available = yes
    public = yes
    writable = yes

of course not suggested if there are security concerns. It's hard (for me anyway) to describe or figure it out, the samba networking was easily the hardest part of my linux experience to date. It sort of fell into place one day. Hope this works out easier for you.

---

### Post by hilo4321 on 2007-10-26
well, ive gone over the given thread, and mapped drives, both with and without WINS enabled, and the login still fails every time.

any ideas? im pretty much at a loss here

---

### Post by airtonix on 2007-10-27
> **hilo4321 said:**
> well, ive gone over the given thread, and mapped drives, both with and without WINS enabled, and the login still fails every time.

any ideas? im pretty much at a loss here

The standard operation with windows is a reinstall. simply becuase updates and hotfixes to a already compiled binary executable are unrealiable in their results...

---

### Post by hilo4321 on 2007-10-27
so what you're telling me is i have to reinstall windows to share files?

or am i missing something from your post?

sorry, wasn't that clear

---

### Post by hilo4321 on 2007-11-01
ive been lurking these boards long enough to know that someone out there can help me, come on now

all i can do at this point is upload to the windows folder and retrieve things from the windows machine

---

### Post by TeaSwigger on 2007-11-01
> **hilo4321 said:**
> ive been lurking these boards long enough to know that someone out there can help me, come on now

But did you say please? Is that a fifty dollar bill waving in your hand? ;)

> all i can do at this point is upload to the windows folder and retrieve things from the windows machine

You can access the windows share from your gutsy user account, and can copy files from the windows share to your gutsy user's home folder. You can see the gutsy share from windows. You can't access the gutsy share from your windows account, being stopped at logon (without a clue of why thanks to typically useful windows behavior). Is this correct? If so, sounds like it's working, but your user permissions aren't set up right. 

Assuming this is a secure environment for this configuration, in your /etc/samba/smb.conf file, is the following true:

> passdb backend = tdbsam
security = user
null passwords = true
username map = /etc/samba/smbusers
name resolve order = hosts wins bcast
wins support = yes

Is your share specified like so:

> [share_name]
path = /share/path/from/root
read only = no
guest ok = yes
create mask = 0644
directory mask = 0755
force user = i_i_me_me_mine
force group = the_beatles
available = yes
browsable = yes
public = yes
writable = yes

Have you configured windows so it knows there's a WINS server in the network? Does your gutsy user and the user you're attempting to log on as from windows have permissions to read and write to the share folder and files on gutsy? Did you add the users and passwords, including that which you are using to log on from windows with to samba, with:
```
sudo useradd -s /bin/true your_username
```
then
```
sudo smbpasswd -L -a your_username
```
and then
```
sudo smbpasswd -L -e your_username
``` ?

---

