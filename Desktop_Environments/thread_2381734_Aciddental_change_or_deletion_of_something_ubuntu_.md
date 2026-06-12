---
title: "Aciddental change or deletion of something ubuntu needs..."
date: 2018-01-04
forum: Desktop Environments
---

### Post by cstaffords on 2018-01-04
I'll just lay this out straight. I have absolutely no idea what I did to Ubuntu, and I'd like to fix it. 
I had installed Plymouth on my device (Ubuntu 16.04). It looked like it was messed up, so I removed it and reinstalled it. I rebooted my device, only to see that I get the startup terminal asking for my login info. Knowing what to do, I put in my username, password, and I executed the startx command. 


When the graphical view loaded, I saw all my desktop files and the background. That was it. No launcher, lock screen, status bar, dashboard, fonts, nothing. I opened up one of the folders on my desktop, and the title bar buttons were on the right! From what it looked like, I think I might have uninstalled Unity. How on earth do I get everything back?

If I can't fix it, it's not a really big deal. I am running Ubuntu 16.04 on a VirtualBox.

---

### Post by Xian on 2018-01-04
What happens if you from the startup terminal try to start gdm?

Login with user/pass then:

$ sudo gdm3

---

### Post by flocculant on 2018-01-05
> **Xian said:**
> What happens if you from the startup terminal try to start gdm?

Login with user/pass then:

$ sudo gdm3

Isn't ubuntu at 16.04 using lightdm?

---

### Post by cstaffords on 2018-01-05
I'll try that.

---

### Post by cstaffords on 2018-01-05
First of all, It didn't work with sudo.
Second of all, I needed to run ```
sudo apt-get install gdm3
``` THEN I ran gdm3 in the terminal, and rebooted. When it camp up, I was using 17.10, and I couldn't unlock it.

I had been running 16.04.

---

