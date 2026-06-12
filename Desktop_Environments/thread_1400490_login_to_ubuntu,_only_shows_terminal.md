---
title: "login to ubuntu, only shows terminal"
date: 2010-02-07
forum: Desktop Environments
---

### Post by codycook on 2010-02-07
I restarted my ubuntu today and when I logged in, it only brought up a TERMINAL window. Gnome did not start or anything. I cannot find any kind of article to fix this.
 
I am using the 10.04 Lynx with the latest updates.
 
I need to know some commands or something to get gnome started. I can't work out of a terminal window forever lol
 
Thank you.

---

### Post by mushwars on 2010-02-07
try this 
```
sudo /etc/init.d/gdm start
```if that doesnt work try this 
```
startx
```

if that first one works do this
```
sudo update-rc.d gdm defaults
```

---

### Post by codycook on 2010-02-07
> **mushwars said:**
> try this 
```
sudo /etc/init.d/gdm start
```if that doesnt work try this 
```
startx
```if that first one works do this
```
sudo update-rc.d gdm defaults
```
sudo /etc/init.d/gdm start told me that 
> 'rather than invoking init scripts through /etc/init.d, use the service(8) utility e.g service gdm start

since the script you are attemping to invoke has been converted to an upstart job, you may also use the start(8) utility, e.g., start gdm'

i tried service gdm start and start gdm also with sudo and it said that gdm was already running.

startx said i didn't have permission so i sudo'd it and it just sat there with a fatal server error "server is already active on display 0"

sudo update-rc.d gdm defaults  tells me that im missing LSB information and directs me to a website and then says that etc/init.d/gdm already exists.

---

### Post by jskala on 2011-02-05
Hello, I have exactly the same problem. Running the suggested commands had the same result. I'm afraid a did something wrong when uninstalling Evolution last night.

---

### Post by wojox on 2011-02-05
> **jskala said:**
> Hello, I have exactly the same problem. Running the suggested commands had the same result. I'm afraid a did something wrong when uninstalling Evolution last night.

You have to be careful what you uninstall from Evolution. Try reinstalling the whole meta-package again:

```
sudo apt-get update; sudo apt-get install --reinstall ubuntu-desktop
```

---

### Post by jskala on 2011-02-05
Thanks for the prompt response, wojox. I already tried
```
sudo aptitude install gnome
```Aptitude said that the gnome package is broken (missing dependencies). It installed about 20 packages and the desktop is working again. Got to be more careful next time.

---

### Post by wojox on 2011-02-05
Good to here.:p

---

