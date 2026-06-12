---
title: "Which desktop?"
date: 2009-01-30
forum: Desktop Environments
---

### Post by TFerg53 on 2009-01-30
I recently installed Ubuntu but am not able to come up with a desktop to use.  Do I need to download one or doesn't Ubuntu come with it's own?  Where did I need to look?

I appreciate any and all assistance.

Thanks,
Tim

---

### Post by taurus on 2009-01-30
Did you install Ubuntu using either the desktopCD (LiveCD)/alternate CD or did you use the server CD?

What do you see after Ubuntu finished booting?

---

### Post by 73ckn797 on 2009-01-30
> **TFerg53 said:**
> I recently installed Ubuntu but am not able to come up with a desktop to use.  Do I need to download one or doesn't Ubuntu come with it's own?  Where did I need to look?

I appreciate any and all assistance.

Thanks,
Tim

What is it doing? No desktop at all?

---

### Post by TFerg53 on 2009-01-30
I installed the Ubuntu server.  The server screen stops at the log-in prompt when it's finished loading.

---

### Post by Maheriano on 2009-01-30
> **TFerg53 said:**
> I installed the Ubuntu server.  The server screen stops at the log-in prompt when it's finished loading.

It's done. The server edition doesn't include a desktop. If you want it (GNOME or KDE) then you have to install the desktop edition or simply install your choice on top of the server.....which might be pretty pointless.

---

### Post by TFerg53 on 2009-01-30
Well, that answers that.  Thank you.  This may sound pretty dumb, but am I looking at this wrong?  Where the Ubuntu desktop is to Windows XP as the Ubuntu server is to Windows Server?  Or am I way out in left field?

Thanks,
Tim

---

### Post by Hooya on 2009-01-30
The sever edition is deliberatly stripped down in order to save resources.  It therefore defaults to a command line only interface.

Unless you're actually running a server on your comptuer there's no reason to not go with regular Ubuntu or Kubuntu.  It's not like Windows that has the different levels that are specified at the core of the OS.  Linux in general is more modular - anything can run on anything else depending on what you set up.

---

### Post by Maheriano on 2009-01-30
What are yuo trying to do? You can always install Apache2 or LAMP on the Desktop Edition and have it run in the background.

I currently have 2 boxes.....1 is my main desktop that I use and it's serving webpages that you'd be able to view if I post my IP.....however I don't have Apache secured yet so I won't. I also have a separate desktop computer with the Server Edition on it that I will be going live with next week. You can do it both ways, I just need a dedicated box to unload the processes from my main machine.

---

### Post by taurus on 2009-01-30
If you want a window manager like Gnome, you don't have to reinstall if you don't want to.  You can install it (after you have logged in) with

```
sudo apt-get update
sudo apt-get install ubuntu-desktop gdm
sudo /etc/init.d/gdm start
```

---

### Post by TFerg53 on 2009-01-30
I set up this particular server to run Mailman and do have Mailman installed but was wanting to set a static IP on this box as I have my other Linux boxes for management sake. However, this is my first Ubuntu server and it takes a little bit to get accustomed to the feel of each "flavor" and, although I've checked the network file and see the interface is set on DHCP, I wanted to get the syntax correct.  So any help along those lines as well as running Mailman would be most welcome.  Otherwise I'll play with it until I get it.

Thanks,
Tim

---

### Post by Maheriano on 2009-01-30
Sounds like you just need to SSH into it from another machine, no need to put a desktop on that.

---

