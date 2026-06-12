---
title: "GUI login failure"
date: 2012-02-17
forum: Desktop Environments
---

### Post by gwm on 2012-02-17
Since my last reboot, I can't login to Ubuntu 11.10 (32 bit).

When prompted,
[LIST]
[*]  I enter the **correct password**, the screen goes blank for as few seconds and then it asks me for my password again.
[*]If I deliberately enter a **wrong password**, it tells me - wrong password etc.
[*]If I hit **ctl-alt-f1**, it accepts my user name and password correctly,
[/LIST]

Something about the gui interface has been corrupted.
What led up to it was:
To fix a networking problem "nautilus cannot handle "network:///" one post suggested the following:
```
#apt-get remove --purge nautilus
#apt-get install nautilus
```
I did that and it seemed to fix my problem. Only I had forgotten that I had nautilus open on another screen while I was doing this. Nautilus seemed to be working ok but then vanished from my screen and I rebooted.

That was when I found I couldn't get back in to the gui. So after much faffing - I had to boot with live cd to remove an indestructible /var/apt/dpkg/lock file - I ended up in tty mode where I removed and reinstalled nautilus again, using the above code.

But that hasn't fixed my problem. I still can't log in to the gui interface.

What has happened? Please can someone help me?

---

### Post by cwklinuxguy on 2012-02-17
Well this is probably overkill (there might be a much better way to fix this), but the first thing that comes to mind for me is just to uninstall and reinstall Unity (assuming that is the GUI you are talking about). Do you have shell access to your system?

---

### Post by gwm on 2012-02-17
Are you asking whether I can login using ctl-alt-f1?

If so, as stated above, I can do that successfully.

That raises two questions
[LIST=1]
[*]How do I do it?
[*]Will the apps I have already installed be erased?
[/LIST]
Thanks for coming back so promptly.

---

### Post by cwklinuxguy on 2012-02-17
Well, if I'm not mistaken, APT could be used in the same way to remove packages as you normally would using

```
 
sudo apt-get remove (insert package name) 
```

I'm rather sure that the process should leave your applications mostly intact, but someone else would need to confirm that.

---

### Post by gwm on 2012-02-17
Thank you once again.
While waiting for your second reply I did some googling and so I installed the gnome shell from the tty terminal and rebooted.

That seems to have fixed everything magically and now I have both shells.

I haven't ventured into these waters in the past and so this kind of solution didn't occur to me.

Thank you once again.
:popcorn:

---

