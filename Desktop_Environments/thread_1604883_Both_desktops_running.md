---
title: "Both desktops running?"
date: 2010-10-24
forum: Desktop Environments
---

### Post by jsvaughan on 2010-10-24
Hi,

On this machine I was originally running std desktop ubuntu but I wanted a speedier desktop so I unstalled xfce by doing an:

sudo aptitude install xubuntu-desktop

Xfce doesn't start up correctly.  During startup (after login) the desktop flicks relatively quickly  between the Gnome version and the XFCE version 3 or 4 times.  Sometimes you end up with Gnome, sometimes XFCE.  Where can I go to suppress the Gnome startup?

Thanks for any help

Jon

---

### Post by jsvaughan on 2010-10-24
Yeah there definitely are two; I just tried right clicking them as it switched back and forward and there are two different right click menus (and I can set a desktop background on one, not have it on the other etc). 

Did a bit more research and it doesn't matter whether I select xfce or xubuntu session at login, the same behaviour occurs.   The reverse doesn't though - if I login to ubuntu desktop I only get gnome, no xfce flicking in and out.

---

### Post by ankspo71 on 2010-10-25
Hi,
If you don't want to have both desktops, then here is some info you can use:

This link shows you how to completely remove the default packages that make up the Ubuntu (Gnome) desktop, then it reinstalls Xubuntu to make sure you have a working desktop when you are done. [http://www.psychocats.net/ubuntu/purexfce](http://www.psychocats.net/ubuntu/purexfce)

Then if you ever decide that Xubuntu is not right for you, you can then do the opposite by removing Xubuntu then reinstalling Ubuntu by following the instructions on a similar link [http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

Hope this helps.

---

### Post by jsvaughan on 2010-10-25
Hi,

Thanks very much for replying.  

It is useful to know how to remove gnome altogether but I don't really want to do that (plus I guess there are no guarantees that that package list is 100% up to date).  

Do you know why gnome is starting at all?  At some point in the past I had a similar gnome/kde set-up and I don't remember there being a similar crossover at that point.

Thanks again

Jon

---

### Post by ankspo71 on 2010-10-25
Hi,
Go to the XCE start menu menu then -> Settings -> Xfce 4 Settings Manager -> Session and Startup -> then under the General tab, make sure the "Automatically Save Session On logout" option is disabled. This will stop XFCE from remembering what was running on the desktop when you log in next time.

Now that the above is done, take a look at the hidden .dmrc file in your home folder. If you logged into an XFCE session, it should only say this:
```
[Desktop]
Session=xfce
```
This is your default session file. It should only have one session (aka Desktop) listed. If it has gnome and xfce then that could be the problem. Also check the permissions of the file. Mine shows it has a permissions of (0600/-rw-------) which means that only I have read and write access to the file, and it is non executable. You can check this by right clicking on the file, then click on properties, then look inside the permissions tab. Or you can use the command below to compare it:
```
stat ~/.dmrc
```
Other than this I don't know what it could be. Someone else here might know though.
Hope this helps.

---

### Post by jsvaughan on 2010-10-25
Mmm well I have that option unticked and my dmrc looks like:

[Desktop]
Session=xubuntu
Language=en_GB.UTF-8
Layout=gb

And it is 644

So the mystery continues...  (but thank you again!)

---

### Post by jsvaughan on 2010-10-31
Another piece of potentially relevant information is that the final resulting desktop tends to be Gnome when running just on laptop but XFCE when using an external monitor.  Could just be coincidence but has been that way the last 4-5 times.

---

