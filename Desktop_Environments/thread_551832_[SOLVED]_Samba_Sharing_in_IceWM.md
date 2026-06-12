---
title: "[SOLVED] Samba Sharing in IceWM"
date: 2007-09-15
forum: Desktop Environments
---

### Post by aysiu on 2007-09-15
I've got Samba sharing (System > Administration > Shared Folders) working just fine in Gnome.

I'm getting the itch to switch back to IceWM, though, and I'm wondering what command I would add to the ~/.icewm/startup file in order to get Samba sharing on.

**Just to clarify**: I'm trying to set up sharing so that someone on the network can look at the files on my Ubuntu computer. I am not trying to look at other people's files. I also have this set up perfectly in *Gnome*. I'm trying to figure out how to get it working in IceWM as well.

I've Googled to no avail (maybe I'm searching for the wrong terms). I also did a ```
locate samba
``` to try to find the executable/binary for it, but I couldn't find it. Any ideas?

---

### Post by JKyleOKC on 2007-09-15
If it's working the way you want it to, switching window managers to IceWM ought not need any changes at all. The Samba package involves two daemons, and when you installed the service they were both set up to load at boot time. Samba does not care what window manager you use.

I'm running it under IceWM on two boxes here, and under Xfce (Xubuntu's default) on two others. All work nicely...

---

### Post by aysiu on 2007-09-15
> **JKyleOKC said:**
> If it's working the way you want it to, switching window managers to IceWM ought not need any changes at all. The Samba package involves two daemons, and when you installed the service they were both set up to load at boot time. Samba does not care what window manager you use.

I'm running it under IceWM on two boxes here, and under Xfce (Xubuntu's default) on two others. All work nicely...
Okay. That's what I thought it should be, except that's not the way it's working.

Since the folder sharing is under System > Administration instead of System > Preferences, I thought it was *system*-specific and not *Gnome*-specific, but when I log into Gnome, I can see my Ubuntu share from my wife's computer. When I log into IceWM, I can't see my Ubuntu share from my wife's computer.

Is there any easy way to check to see if the daemon is running?

---

### Post by mocoloco on 2007-09-16
```
ps -A |grep smbd
```
You can also dig through your /etc/samba/smb.conf file to make sure everything is set right, which shouldn't be changing, but strange things sometimes happen.

---

### Post by aysiu on 2007-09-17
Never mind. It does work. I must have been hallucinating.

---

