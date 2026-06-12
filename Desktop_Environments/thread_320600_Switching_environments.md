---
title: "Switching environments"
date: 2006-12-17
forum: Desktop Environments
---

### Post by earthdragon on 2006-12-17
I am running Kubuntu edgy right now. I want to also be able to run Gnome. How do I install gnome without messing up my system? Can I have both?

---

### Post by taurus on 2006-12-17
From a terminal
```
sudo aptitude update
sudo aptitude install ubuntu-desktop
```
Then pick which environment you want to use at the GUI login screen...

---

### Post by earthdragon on 2006-12-17
Thanks, that seemed to work perfectly. Is there anyway I can change the loading screen I see at start up from a Kubuntu one to an Ubuntu one?

---

### Post by taurus on 2006-12-17
You can try installing the gdm login screen...

```
sudo aptitude update
sudo aptitude install gdm
sudo /etc/init.d/gdm start
```
Or reboot and see if GDM starts.

---

### Post by kanna1620 on 2007-01-15
> **taurus said:**
> You can try installing the gdm login screen...

```
sudo aptitude update
sudo aptitude install gdm
sudo /etc/init.d/gdm start
```
Or reboot and see if GDM starts.
Im a new bie to Ubuntu and i installed KUbuntu and my default login screen has changed to the KUbuntu login screen but I wanted it remain the Ubuntu default screen the GNome only.But i cant open the **System>Administration>Login Window**
It is not opening at all.So I ran the above said command to start the GNome Desktop Manager(gdm) but it failed giving the error:
** * Not starting GNOME Display Manager (gdm); it is not the default display manager.**
But I want the Gnome screen as my default display manager.
What should I do now?
Thanks for help.

---

### Post by floundered on 2007-01-19
I have  a similar problem with probably the same solution:  I first installed Ubuntu 6.10 on an older machine, felt it was too slow so I installed the xfce desktop, didn't like xfce so I removed it with apt-get, but now I'm stuck with the xubuntu login screen (which I thought would have been removed with the rest of the xfce desktop).

How can I remove the Xubuntu login screen and get back to the GNOME one?  I've read some suggestions elsewhere to reinstall the entire gnome desktop, but that sounds a little overkill.

---

### Post by taurus on 2007-01-19
What happens if you run these from a terminal?

```
sudo aptitude update
sudo aptitude install gdm
sudo /etc/init.d/gdm start
```
Or reboot and see if GDM GUI login screen comes up?

---

### Post by floundered on 2007-01-19
In my case, where I have the undesired Xubuntu login screen but the desired GNOME desktop, it made no difference.  After running aptitude to (re)install gdm, it declared that 0 packages were upgraded, installed, moved, not upgraded, etc.  After rebooting I still have the Xubuntu login screen.

My guess is that this would be a single config setting somewhere, but I can't find it.  Is there a particular name for the (executable?) file that produces the Xubuntu login screen?

---

### Post by taurus on 2007-01-19
Perhaps you have xdm running instead of gdm!  Log in and paste the output of this command here.

```
ps -A
```

---

### Post by floundered on 2007-01-19
Ack!  Here I go replying to myself...

It's weird (if not a wee buggy) that the Xubuntu screen stuck around after xubuntu-desktop was removed.

Thankfully, it appears that using aptitude to update & re-install gdm got back my login screen tool.  I've noticed that I now have the System/Administration/Login_Screen GUI app, which I didn't have before (honest!).  So I selected the desired Ubuntu screen and life is good again.

Thanks.

---

