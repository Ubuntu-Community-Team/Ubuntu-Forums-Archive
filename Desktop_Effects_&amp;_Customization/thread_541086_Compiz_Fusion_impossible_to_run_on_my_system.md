---
title: "Compiz Fusion impossible to run on my system?"
date: 2007-09-02
forum: Desktop Effects &amp; Customization
---

### Post by Havek on 2007-09-02
I installed Compiz Fusion and it all went well, i can go the the manager and mess with the settings, but when i go to start it i get this error.

[PHP]andrew@AndrewsLinuxPC:~$ compiz --replace
Fatal: Failed test: texture_from_pixmap support
Checks indicate that it's impossible to start compiz on your system.
[/PHP]

Why is this impossible to run on my system?

---

### Post by Happy_Man on 2007-09-02
Do you have the proper drivers? If you are on Nvidia, install one of the nvidia-glx drivers from the repos, depending on your graphics card. 

If you have an ATI card, install the xorg-driver-fglrx package from the repos, reboot your computer, and try again.

---

### Post by Inxsible on 2007-09-02
you can check what card you have by
```
lspci | grep VGA
```

Also, you should use the Alt + F2 dialog box to start compiz and not the terminal

---

### Post by Havek on 2007-09-02
> **Happy_Man said:**
> Do you have the proper drivers? If you are on Nvidia, install one of the nvidia-glx drivers from the repos, depending on your graphics card. 

If you have an ATI card, install the xorg-driver-fglrx package from the repos, reboot your computer, and try again.

When Ubuntu installed it asked me if i wanted to load the ati driver and it did.   So i think it is installed.  

When i run lspci | grep VGA this is what i get 
```
01:00.0 VGA compatible controller: ATI Technologies Inc R420 JK [Radeon X800]
```

Is the driver not installed?

---

### Post by Happy_Man on 2007-09-02
Hmm... just to check: ```
sudo apt-get install xorg-driver-fglrx
```

---

### Post by tuxcantfly on 2007-09-02
if you're using the fglrx drivers, then you'll need to use xgl to run compiz-fusion since the fglrx drivers don't support texture-from-pixmap, though if your card is supported by the open-source ati drivers, then you can use those and it will work without xgl since they support texture-from-pixmap

---

### Post by Havek on 2007-09-02
> **Happy_Man said:**
> Hmm... just to check: ```
sudo apt-get install xorg-driver-fglrx
```

I ran this and got this.

```
andrew@AndrewsLinuxPC:~$ sudo apt-get install xorg-driver-fglrx
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
xorg-driver-fglrx is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
andrew@AndrewsLinuxPC:~$ 
andrew@AndrewsLinuxPC:~$ 

```

So do i have to go to xgl?

---

### Post by Happy_Man on 2007-09-03
Yes, I'm afraid you probably will. Use one of the howto's in the Desktop Effects subforum to help you out. Try this one: [http://ubuntuforums.org/showthread.php?t=488385&highlight=xgl](http://ubuntuforums.org/showthread.php?t=488385&highlight=xgl)

---

