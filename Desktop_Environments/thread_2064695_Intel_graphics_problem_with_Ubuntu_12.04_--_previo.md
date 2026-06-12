---
title: "Intel graphics problem with Ubuntu 12.04 -- previously had Nvidia"
date: 2012-09-30
forum: Desktop Environments
---

### Post by garuhhh on 2012-09-30
I bought a new PC, i5 cpu with built-in intel graphics. 

I just plugged in my old harddisk from my old laptop with ubuntu 12.04 installed on it. I just plugged in the old harddisk and everything went well, except for the graphics, I guess. This is what is said in the Graphics section of the System Details:

> Driver
Experience Fallback

The old laptop had an nvidia graphics card on it, and now my new hardware has a built-in Intel graphics.

When I try to run glxinfo, it gives me this error:
```
name of display: :0.0
Error: couldn't find RGB GLX visual or fbconfig

```

I tried purging all Nvidia drivers by:
```
sudo apt-get purge nvidia*
```
which went well by the way, and re-installed xserver-xorg-video-intel, xserver-xorg-core, mesa-utils.

But when I try to reconfigure xserver by:
```
sudo dpkg-reconfigure xserver-xorg
```
nothing happens. it seems it's not being executed at all. I have tried executing it while "lightdm"is stopped, but still no result.
You have any idea why it's not working?


From one post in a forum, he experienced the same thing, and I was able to find out the following error from Xorg log by doing
```
less /var/log/Xorg.0.log | grep "gl"
```
and it gives me this:
```
[    30.432] (II) LoadModule: "glx"
[    30.432] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/libglx.so
[    30.432] (EE) Failed to load /usr/lib/x86_64-linux-gnu/xorg/extra-modules/libglx.so: libnvidia-tls.so.295.49: cannot open shared object file: No such file or directory
[    30.432] (II) UnloadModule: "glx"
[    30.432] (II) Unloading glx
[    30.432] (EE) Failed to load module "glx" (loader failed, 7)

```

Any ideas how to go about this?

---

### Post by kansasnoob on 2012-09-30
I think typically a machine with nVidia creates an "/etc/X11/xorg.conf" file whereas Intel typically does not.

So you can look by running:

```
cd /etc/X11
```

Then:

```
ls
```

If that shows a file named "xorg.conf" I'd try renaming it by running:

```
sudo mv xorg.conf xorg.conf_OLD
```

Then close the terminal, reboot, and keep your fingers crossed.

---

### Post by garuhhh on 2012-09-30
Oh,  I have already removed xorg.conf before and it didn't help :(

---

### Post by garuhhh on 2012-10-03
bump!

---

### Post by jrog on 2012-10-03
Did you notice in the error message you posted that it is still looking for nvidia-related files? You might be able to force it to stop doing this by generating an xorg.conf file for your current hardware and putting it in /etc/X11/. 

Xorg can auto-generate this file for you by probing your hardware. You can get it to do this by closing everything X-related (so, log out of your desktop, switch to a terminal use CTRL+ALT+F1, and then stop or kill any X-related processes (lightdm, etc.) -- let us know if you need help doing this) and then typing:

```
Xorg -configure
```

That command (you may need to put 'sudo', without the quotes, in front of it) will create an xorg.conf file in your current working directory, which you can then move to /etc/X11/. After doing that, restart and see whether X is working with no problems.

---

### Post by garuhhh on 2012-10-03
Hello! thanks for the reply jrog.

I tried Xorg -configure, while lightdm is stopped, but it gave me the following error:
```
(++) Using config file: "home/garu/xorg.conf.new"
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
Number of created screens does not match number of detected devices.
Configuration failed.
ddxSigGiveUp: Closing log
Server terminated with error (2). Closing log file.
```

---

### Post by garuhhh on 2012-10-03
I don't know what happened, but everything worked after trying out the commands from [this link]("http://lkubuntu.wordpress.com/2011/08/30/quick-and-easy-way-to-fix-x11-issues/").

although it gave the same error, and the "dpkg-reconfigure" part still didn't seem to work.

After trying out those commands, it worked!

I'm thinking it must be this command:
```
[ -f xorg.conf* ] && sudo mv xorg.conf* /etc/X11/xorg.conf
```
what does it do? I understand, there is this xorg.conf.new being generated in the Home directory, and it seems it is just copied to /etc/X11/xorg.conf. am I right?

---

### Post by jrog on 2012-10-03
> **garuhhh said:**
> I don't know what happened, but everything worked after trying out the commands from [this link]("http://lkubuntu.wordpress.com/2011/08/30/quick-and-easy-way-to-fix-x11-issues/").

although it gave the same error, and the "dpkg-reconfigure" part still didn't seem to work.

After trying out those commands, it worked!

I'm thinking it must be this command:
```
[ -f xorg.conf* ] && sudo mv xorg.conf* /etc/X11/xorg.conf
```what does it do? I understand, there is this xorg.conf.new being generated in the Home directory, and it seems it is just copied to /etc/X11/xorg.conf. am I right?
Yes, you're right. The link tells you to do exactly what I told you to do (albeit with some more detail and the added step of reconfiguring some packages). :) I'm glad it worked! Please mark the thread as solved (using "Thread Tools" toward the top of the page), when you get the chance!

---

### Post by garuhhh on 2012-10-03
Thank you jrog!!

---

