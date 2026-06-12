---
title: "Need to turn off X server in order to install drivers WTF"
date: 2008-12-23
forum: Desktop Environments
---

### Post by coolethan on 2008-12-23
i'm trying to install some nvidea drivers for my graphics card and it won't install unless i turn of X. i found two commands on google

telinit 3
telinit 0

telinit 3 didn't work and telinit 0 shut down my computer. how do i shut of the X server so i can install the drivers

---

### Post by s3gfault on 2008-12-23
switch to a console (ctrl-alt-F1) and log in.  Stop the service:
```
sudo /etc/init.d/x11-common stop
```
should do the trick.

---

### Post by coolethan on 2008-12-23
> **s3gfault said:**
> switch to a console (ctrl-alt-F1) and log in.  Stop the service:
```
sudo /etc/init.d/x11-common stop
```
should do the trick.
you'd think it would wouldn't you but it didn't, thanks for the speedy reply btw.

---

### Post by s3gfault on 2008-12-23
> **coolethan said:**
> you'd think it would wouldn't you but it didn't, thanks for the speedy reply btw.

when you do this, your screen will go all black and the entire X/Gnome desktop disappears. Ctrl-Alt-F1.  Then stop the services like i said, or you can even go through and `sudo kill -9 ####` where the #### is a pid number for a running process.  Kill or stop GDM, Xorg, or any other process that is using the nvidia drivers.

---

### Post by mikewhatever on 2008-12-23
Just boot into recovery mode (second boot option), this way you don't have to stop xserver because it doesn't get started in the first place.

---

### Post by coolethan on 2008-12-23
> **mikewhatever said:**
> Just boot into recovery mode (second boot option), this way you don't have to stop xserver because it doesn't get started in the first place.

what do i do after that, it won't open a terminal to actually install the drivers. i just get some thing that pops up asking what i want to do, the first option being continue to boot normally, fix broken packages and some other ones.

---

### Post by cb951303 on 2008-12-23
> **coolethan said:**
> you'd think it would wouldn't you but it didn't, thanks for the speedy reply btw.

by switch to a console he meant "ctrl+alt+f1"
don't  forget to remove old drivers first ;)

---

### Post by coolethan on 2008-12-23
> **cb951303 said:**
> by switch to a console he meant "ctrl+alt+f1"
don't  forget to remove old drivers first ;)
well i did that and it's definately not stopping any processes. how do i get rid of the old drivers and if their are old drivers why do i need to install new ones like it thinks it needs.

---

### Post by cb951303 on 2008-12-23
> **coolethan said:**
> well i did that and it's definately not stopping any processes. how do i get rid of the old drivers and if their are old drivers why do i need to install new ones like it thinks it needs.

If this is a fresh ubuntu install then you don't have NVIDIA drivers installed yet. You can simply activate/install drivers by menu>system>admin.>hardware drivers -> select the recommended one and click activate

that's it. you don't have to bother with nvidia-installer

PS: If you really want to install it manually then I can walk you through it but, the driver version in the screenshot you sent is really really old.
PS2: Or not, there is 177.82 on your desktop but installer shows 71.86 ???

---

### Post by coolethan on 2008-12-23
well when i tried to install 177.8 an error came up that said something about 71.8 or whatever so i tried installing that which actually got me a lot farther than installing 177.8. when i go to system-admin-drivers there are no drivers in the list. what the deuce? i will have to install them manually so i guess you can walk me through that. i have the 177.8 downloaded now i type in 'sudo sh NVIDIA-Linux-x86-177.82-pkg1.run' i'm pretty sure

---

### Post by coolethan on 2008-12-23
ok ya i tried that it turns out i don't have a GPU supported by that driver but apparently the one i have is supported by 71.8, i'm working with outdated hardware here btw

---

### Post by cb951303 on 2008-12-23
> **coolethan said:**
> ok ya i tried that it turns out i don't have a GPU supported by that driver but apparently the one i have is supported by 71.8, i'm working with outdated hardware here btw

what is your graphics card? which NVIDIA GPU?

To manually install:
1. Reboot your computer
2. Press ESC and go the grub menu.
3. Select 2.6.27-9-generic (recovery mode)
4. Wait for a blue menu to show up
5. Select "root"
6. Go to the directory where NVIDIA setup is
7. sh NVIDIA-blablabla.sh
8. Ignore the warning and continue (It will look to internet for a driver and it won't find any then it will compile it from scratch, don't panic)
9. At the end select yes for nvidia-xconfig
10. Reboot normally CTRL+ALT+DEL

voila!

---

### Post by coolethan on 2008-12-23
everything works up to step 8, it configures the NVIDEA kernal from scratch and then it tells me it was unable to build the kernal so ya. i'm thinking of just going back to my old ATI graphics card which i have heard have been the underdogs to NVIDEA since the beginning of time so thats why i decided to switch graphics cards. all i'm trying to do is run wine faster without everything lagging and everyone in the wine forum all pointed me towards graphics card drivers which for the ATI card i had installed i never had any and i couldn't figure out how to get them.

---

### Post by inxygnuu on 2008-12-23
I have the same problem, just I don't have any ati, all Nvidia and i really need this working. Not trying to hijack the thread, just need a solution.

---

### Post by jerome1232 on 2008-12-23
> **coolethan said:**
> everything works up to step 8, it configures the NVIDEA kernal from scratch and then it tells me it was unable to build the kernal so ya. i'm thinking of just going back to my old ATI graphics card which i have heard have been the underdogs to NVIDEA since the beginning of time so thats why i decided to switch graphics cards. all i'm trying to do is run wine faster without everything lagging and everyone in the wine forum all pointed me towards graphics card drivers which for the ATI card i had installed i never had any and i couldn't figure out how to get them.

Well missed a step and this is actually easier than it seems.

hit ctrl+alt+f1, then login.

```
sudo -i
apt-get install build-essential
/etc/init.d/gdm stop
./NVIDIA-(well you know hit tab to autocomplete the rest)
###say yes to everything, make sure you say yes to the last option (default is no I think)
reboot
```

---edit---

As an alternative easier solution you can try envyng
```
sudo apt-get install envyng-gtk
sudo envyng -t
```

---

### Post by coolethan on 2008-12-23
ok something is drastically wrong, every time i type sudo apt-get install anything it says
E: unable to find anything

this includes envyng-gtk and build essential. for build essential maybe you have to adjust your code a little to make sure it looks in the cd rom drive or soemthing

i've gone through the process of installing build essentials before and it worked all the time but this is weird.

---

### Post by jerome1232 on 2008-12-23
Try doing a sudo apt-get update and post any errors.

---

### Post by coolethan on 2008-12-23
there were no errors whatsoever. oh i reffered back to an old post of mine where i couldn't compile anything and it turns out i have to type in

sudo apt-get install build-essential gcc libc6 g++ libstdc++6

and it's working. is that what the problem was, the thing couldn't compile the kernal because there were no compilers installed?

---

### Post by coolethan on 2008-12-23
damn kernal still doesn't want to build after installing build essentials.

---

### Post by Xiong Chiamiov on 2008-12-24
Although I haven't updated it since Intrepid came out, you may find [my guide]("http://ubuntuforums.org/showthread.php?p=4978329#post4978329") on installing the nvidia drivers helpful.

---

### Post by soundcheck on 2008-12-24
Hi folks.

I have a similar issue under Gnome and ATI.

I am setting up a headless audio client.
I want to shutdown Gnome when I close the lid of my Notebook 
through /etc/acpi/events/lid.sh (I've rewritten it)

I'd just need the commands of how to get X and Gnome down

/etc/init.d/gdm stop doesn't work

THX

---

### Post by mikewhatever on 2008-12-24
> **soundcheck said:**
> Hi folks...

I'd just need the commands of how to get X and Gnome down and down

/etc/init.d/gdm stop doesn't work

THX

Well, what about the recovery mode? See post #5.

---

### Post by soundcheck on 2008-12-24
> **mikewhatever said:**
> Well, what about the recovery mode? See post #5.

That would be too easy.;) If this machine would be a pure audio-client
it'd be OK. My idea is to make it an audio client by closing the lid.
It's actually working great already, except that resources consuming 
Gnome is still up. 

Google is telling me that people have issues with "gdm stop" for years. :(

What's actually executed if I run Ctrl-Alt-Backspace ? 
It looks to me like a "gdm restart". Is there an ACPI event defined?

Below is the init.d/gdm stop command - my screen gets off and Gnome down. No further actions possible for now:

start-stop-daemon --stop  --quiet --oknodo --pidfile /var/run/gdm.pid --name gdm --exec /usr/sbin/gdm --retry 30 

This is how I get it up'n running as ACPI controlled event, controlled by my  /etc/acpi/lid.sh only!!!!!

start-stop-daemon --start --quiet --oknodo --pidfile /var/run/gdm.pid --name gdm --exec /usr/sbin/gdm -- --config=/etc/gdm/gdm-cdd.conf

Example:

```

#!/bin/bash
# 12.24.2008 written by soundcheck
# /etc/acpi/lid.sh 
# This script is supposed to turn off the front-end and Gnome.
# PC is used as headless audio client based on Music Player Daemon  

grep -q closed /proc/acpi/button/lid/*/state

if [ $? = 0 ]
then
    vbetool dpms off
    start-stop-daemon --stop --quiet --oknodo --pidfile /var/run/gdm.pid --name gdm --exec /usr/sbin/gdm --retry 30 
else

    start-stop-daemon --start --quiet --oknodo --pidfile /var/run/gdm.pid --name gdm --exec /usr/sbin/gdm -- --config=/etc/gdm/gdm-cdd.conf
    vbetool dpms on
fi


```


Cheers

---

### Post by soundcheck on 2008-12-25
Hi folks.

How about this one?

sudo fgconsole

is giving you a value. In my case 7.

Now do a 

sudo chvt 6

Now you'll get a text login. Login.

Now you type 

sudo chvt 7

Here we go! You are back at your Gnome terminal.

Cheers

---

### Post by coolethan on 2008-12-25
I've switched back to my old ATI graphics card because nvidea was pissing me off and even after using envygt it still didn't work. i have an ATI drivers disc but i can't seem to find any of the drivers on the disc and using Wine they don't want to install either.

---

