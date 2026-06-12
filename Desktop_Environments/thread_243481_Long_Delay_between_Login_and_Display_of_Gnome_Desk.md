---
title: "Long Delay between Login and Display of Gnome Desktop"
date: 2006-08-25
forum: Desktop Environments
---

### Post by dapperjohndoe on 2006-08-25
I start my computer, sooner or later, the Ubuntu login screen appears. After the login, there's a notice window that tells me that Metacity is being loaded. Well, and then, I have to wait for about weo minutes until the rest of the desktop is loaded... what could cause that problem?

John

---

### Post by JKoder on 2006-08-25
What release are u using ?
Is your sound working corectly ?

---

### Post by vavoem on 2006-08-25
Same here
Sound is working
Do you have XGL installed i have

---

### Post by dapperjohndoe on 2006-08-29
Sound is fine, I don't use XGL, just the standard desktop.

John

---

### Post by dsvensson on 2007-03-13
> **dapperjohndoe said:**
> I start my computer, sooner or later, the Ubuntu login screen appears. After the login, there's a notice window that tells me that Metacity is being loaded. Well, and then, I have to wait for about weo minutes until the rest of the desktop is loaded... what could cause that problem?

John

I can confirm this problem. It's definatly some timeout, perhaps something trying to contact something over the net, and net is down until I've entered my pass to gnome-keyring. 

You don't happen to use a wireless connection, or any connection that you have to setup after you've logged in?

I got this problem after upgrading to Ubuntu Feisty a while back.

---

### Post by nimphelos on 2007-03-21
Check out [this post]("http://www.ubuntuforums.org/showthread.php?t=307038&highlight=gnome+delay") . I used yo have both of these problems (application delay and desktop delay). I changed my /etc/hosts file and both of them fixed ;)

---

