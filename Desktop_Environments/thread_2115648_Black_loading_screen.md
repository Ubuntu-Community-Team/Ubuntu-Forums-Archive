---
title: "Black loading screen"
date: 2013-02-13
forum: Desktop Environments
---

### Post by LadyLove on 2013-02-13
Hi to everybody!
This is the first time that I use Xubuntu and I'm experiencing a problem with it. D:
I've just installed Xubuntu 12.10 desktop 64-bit on my laptop alongside with Windows 8.
When  I choose Ubuntu from grub loader, the screen goes black and the LCD  backlight goes off: the white-bar-on-blue-background Xubuntu loading  screen doesn't appear, but after a few seconds the Xfce login window  materializes and the desktop enviroment after login works fine. When I shutdown or restart the system, the white-bar-on-blue-background Xubuntu loading  screen magically appears! :)
I know that is only an aesthetic bug, but how can I bring back the Xubuntu loading screen on boot?
Please notice that my video card is the Nvidia NVS 2100M, and that I'm NOT experiencing any problem with Xfce's desktop.
A huge kiss to anyone who will help me! :*

---

### Post by ACubed10 on 2013-02-13
are there any additional drivers available for your graphics card?  Meaning when you get to the desktop and go to system settings and then Additional drivers, is there one available for your Nvidia card?

attached is a screenshot of my system settings...under hardware you can see Additional Drivers

---

### Post by ACubed10 on 2013-02-14
any luck or updates?

---

### Post by LadyLove on 2013-02-15
I was using the open source nouveau driver, now that I changed to Nvidia proprietary driver (from nvidia-current) the loading screen is the awful black and white version, but it shows up when booting and when shutting down... Now for the blue nice version what I have to do?

---

### Post by schragge on 2013-02-15
What are the GRUB settings in */etc/default/grub*? Can you please post the output of
```
grep '^[^#]' /etc/default/grub
```

---

### Post by LadyLove on 2013-02-16
> **schragge said:**
> What are the GRUB settings in */etc/default/grub*? Can you please post the output of
```
grep '^[^#]' /etc/default/grub
```

Here you are
```
GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
```

---

### Post by Ravi5kumar on 2013-02-16
I have the same problem in both ubuntu 12.04 and kubuntu 12.04 with latest update installed. The splash screen looks weird but when I shut down my computer it looks very nice. I am using open source driver.

Output for grep '^[^#]' /etc/default/grub :
```
GRUB_DEFAULT="Kubuntu 12.04"
GRUB_HIDDEN_TIMEOUT_QUIET="true"
GRUB_TIMEOUT="10"
GRUB_DISTRIBUTOR="`lsb_release -i -s 2> /dev/null || echo Debian`"
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
GRUB_GFXMODE="1024x768x24"
GRUB_SAVEDEFAULT="false"

```

---

### Post by zombifier25 on 2013-02-16
The solution: [http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml](http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml)

---

### Post by Ravi5kumar on 2013-02-16
> **zombifier25 said:**
> The solution: [http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml](http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml)


Its very old and btw it doesn't work!:sad:

---

### Post by schragge on 2013-02-16
Try to add the line
```

GRUB_GFXPAYLOAD_LINUX="1024x768"

```
to */etc/default/grub*, then
```

sudo update-grub

```

---

### Post by zombifier25 on 2013-02-16
> **Ravi5kumar said:**
> Its very old and btw it doesn't work!:sad:

Weird. I'm on 12.04, using a recent NVIDIA card with the proprietary driver and it works for me.

---

### Post by LadyLove on 2013-02-17
I found a script based on the solution from softpedia, and it worked for me:
[http://kyleabaker.com/2010/07/11/how-to-fix-your-ubuntu-boot-screen/](http://kyleabaker.com/2010/07/11/how-to-fix-your-ubuntu-boot-screen/)

Thanks to anyone!

---

### Post by Ravi5kumar on 2013-02-20
> **LadyLove said:**
> I found a script based on the solution from softpedia, and it worked for me:
[http://kyleabaker.com/2010/07/11/how-to-fix-your-ubuntu-boot-screen/](http://kyleabaker.com/2010/07/11/how-to-fix-your-ubuntu-boot-screen/)

Thanks to anyone!

Your link displays a 404 error lol!

> Not Found

The requested URL /2010/07/11/how-to-fix-your-ubuntu-boot-screen/ was not found on this server.

Additionally, a 404 Not Found error was encountered while trying to use an ErrorDocument to handle the request.

---

