---
title: "cdrom access problems"
date: 2009-03-02
forum: General Help
---

### Post by ralfarof on 2009-03-02
Im new with Linux, im trying to switch from Windows but it only give me headaches :-({|= Im have Ubuntu 8.10 installed, im trying to access the cdrom drive but i get the message: **Folder contents could not be displayed. You do not have the permissions necessary to view the contents of "cdrom0"**
I'd googled the message and found thousands of "workarounds" that doesn't work :mad:
I don't get it, why a simple task as accessing a cdrom have to be a pain in the neck, that is not helping Linux popularity, the graphic mode should be easier to use, not everybody is a Linux expert, simple tasks as open a cdrom shouldn't be complicated to accomplish.

---

### Post by khelben1979 on 2009-03-02
Maybe the Gnome enviroment isn't very user friendly? Try with KDE instead to see if you have better luck:

```
sudo apt-get install kde
```

Then start [KDE]("http://en.wikipedia.org/wiki/Kde") after this and try the same thing. The alternative is if you decide to add the cdrom group to your user:

```
sudo addgroup [user] cdrom
```
that should give your user the right permissions to access the cd-rom.

Good luck. :popcorn:

---

### Post by ralfarof on 2009-03-02
> **khelben1979 said:**
> Maybe the Gnome enviroment isn't very user friendly? Try with KDE instead to see if you have better luck:

```
sudo apt-get install kde
```

Then start [KDE]("http://en.wikipedia.org/wiki/Kde") after this and try the same thing. The alternative is if you decide to add the cdrom group to your user:

```
sudo addgroup [user] cdrom
```
that should give your user the right permissions to access the cd-rom.

Good luck. :popcorn:

thanks for the reply!

My user is on the cdrom group already, seems like everytime i change disks it only allows access to them after a reboot, it is a fresh install :-k

---

### Post by khelben1979 on 2009-03-02
What happens if you restart the x-server each time instead of rebooting the system?

Pressing```
ctrl + alt + backspace
```
terminates the X session and brings you to the login manager.

I definitely agree that the way things are at the present isn't acceptable. I don't know how you should fix it, but rebooting the system all the time feels a bit too much for a Linux system.

Sometimes different processes can get stuck and by typing:
```
sudo ps -A | less
```
gives you a list of all running processes in the system and from there you can always try to kill processes to free up locked processes:
```
sudo kill -9 [process number]
```

---

### Post by ralfarof on 2009-03-02
Thanks again for your help! :guitar: 
the log off, log on stuff didn't work. Attached is the process list.
Is there a way to use ISO files instead of cd's/dvd's? [-o<

---

### Post by khelben1979 on 2009-03-02
I'm curious. What is the type of media on the discs which are getting mounted on to the system?

---

### Post by ralfarof on 2009-03-02
It's an .sh installer

---

