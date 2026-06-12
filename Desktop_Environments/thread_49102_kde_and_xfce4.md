---
title: "kde and xfce4"
date: 2005-07-15
forum: Desktop Environments
---

### Post by kylenewton on 2005-07-15
Hi all,

I had installed Kubuntu from CD and all was good. I was curious about XFCE4 and the possibility of an improvement in speed (being a more compact window manager). Well, after installing XFCE4 and associated libraries through kynaptic, I logged into it. I'd been using it all day, and it was alright.

Upon logging out of XFCE and trying to log into KDE I've come upon a problem. I get a popup box with the following error message >>

```
The following installation problem was detected while trying to start KDE:

No write access to '/home/myaccount/.ICEauthority'.

KDE is unable to start  [OK]
```

And now I can't start XFCE either. I've tried reinstalling KDE as well as XFCE4 but no luck. I can start up a failsafe session. I'm relatively new to the distro, so how can I get around this problem?

Thanks in advance. Kudos to any responses.


[edit: this may be of some importance]

When I click the OK button I get another popup >>

```
Could not start ksmserver. Check your installation. [okay]
```

Then back to the login gui.

When I logged in to failsafe and reinstalled ksmserver from the Kubuntu CD, still the same problem. So I'm staring at a brick wall ](*,)

[edit: It's all better]

What a wonderful repository of information these forums are. I'd randomly read through other recent posts in this forum and stumbled across a solution to my problem. Here's how I fixed it

```
login to failsafe

sudo chown myaccount:myaccount /home/myaccount/.ICEauthority
```

And all was better. Thanks for nothing  :grin:

---

### Post by skyboy on 2005-07-15
try that : $ sudo chown username:username ~/path/to/.ICEAuthority

---

### Post by sifion on 2007-07-26
hi kylenewton,

i've tripped into this problem too, more than once...
apparently, when on xfce desktop, running certain kde apps under sudo, may cause the change of owner for .ICEauthority...
i don't know if it's some kind of bug or a configuration issue, but it seems to be avoidable by using gksu or kdesu...

a very simple way to avoid this, even if you want to use the sudo (there's some things i don't want to change...), is to make a shutdown script to delete the file on as you leave the system... next startx, will be created a new .ICEauthority file..

---

