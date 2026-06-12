---
title: "Switched to kubuntu - X will not launch"
date: 2017-12-11
forum: Desktop Environments
---

### Post by thisismyusername4now on 2017-12-11
Per the title. I upgraded from 17.04 to 17.10 running the Ubuntu desktop. I found I was frustrated and not satisfied with the Gnome environment so after hearing friends rant about kubuntu being awesome I wanted to try it. I installed kubuntu-desktop and rebooted. I now get an error after login:

Xsession: X session started for <username> at <date>
Xsession: unable to launch "filec" X session --- "filec" not found; falling
back to default session

The screen remains black with a cursor and responds to nothing.

I downloaded an image of kubuntu and reinstalled. But my home directory is on a separate drive. I tried it once with /home on the main drive (second drive removed) and all was well. I retried with /home on the second drive and got the same error. I backed up my .cache, .local, .config, and .profile and then copied them out of the default directory but all to no avail. I cannot find any mention of "filec" in any online forums or help locations. I am at my wits end and am now running Windows 10 as my daily driver. Please help me figure this out so I can return to the happy world of Ubuntu.

Thanks

---

### Post by thisismyusername4now on 2017-12-12
OMG!! I figured this out. 4 or 5 years ago I did some contract development. The client's build tools required "filec" to be set in the build environment or it would fail. Very poor design but this is what it required. I had a list in my .bashrc that was specifically "set filec"

This for some reason is not enjoyed by X and it was causing KDE to fail to load. Commenting the line out totally fixed everything. Sigh.

---

