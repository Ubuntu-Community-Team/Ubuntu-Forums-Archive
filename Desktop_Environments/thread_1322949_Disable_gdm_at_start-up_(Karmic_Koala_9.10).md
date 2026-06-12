---
title: "Disable gdm at start-up (Karmic Koala 9.10)"
date: 2009-11-11
forum: Desktop Environments
---

### Post by ch90045 on 2009-11-11
Is it possible to disable gdm at start-up in Karmic (login in a shell after boot)? I know there are some changes from previous versions of Ubuntu.

It was already proposed to do 

sudo update-rc.d -f gdm remove

But thats not right anymore

TIA

Christian

---

### Post by mrawji on 2009-11-23
Hi Christian,

Don't know if you've already found the solution, but here's what I came up with.
the issue is that GDM is run from Upstart instead of the old way...

I couldn't find the "official" way to do it, but, here goes:

1) edit the /etc/init/gdm.conf
2) comment out the "start on" line, so that it looks like this
```

#start on (filesystem
#          and started hal
#          and tty-device-added KERNEL=tty7
#          and (graphics-device-added or stopped udevtrigger))


```This essentially prevents the service from starting up automatically.

Now, you should be able to start gdm by calling
```

$ sudo start gdm

```If you just want to start X without starting GDM,
```

$ startx

```Hope this helps!
Marc

---

### Post by komputes on 2010-02-05
I had a hard time because I was following guides that were not tested on 9.10. In fact you don't need to mess with GDM's configuration as GRUB2 is the easiest way to get this done. Here are the steps:

1 - Edit the GRUB2 configuration defaults

```
$ sudo gedit /etc/default/grub
```

2 - Change the line **GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"** to

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash text"
```

3 - Save and close the grub file

4 - Update grub so that the changes are propagated to grub's configuration file (to all current and future kernels)

```
$ sudo update-grub
```

That it! Simple right? :)

If you ever need to log into gnome, use the **startx** command. If you want GDM to start use the **sudo gdm start** command.

Hope this helps people from wasting hours of trying to disable GDM on 9.10 using older guides that suggest editing gdm.conf, moving gdm.conf, using update-rc.d, rcconf or sysv-rc-conf - none of those worked for me. This was the cleanest/best way I found of doing this.

Cheers!

:guitar:

---

### Post by savanna on 2010-02-20
A better method.

Check your current runlevel:

[FONT="Courier New"]% runlevel
N 2[/FONT]

Edit /etc/init/gdm.conf, and change:

[FONT="Courier New"]stop on runlevel [016][/FONT]

to:
[FONT="Courier New"]
stop on runlevel [0216][/FONT]

Better to manipulate the runlevels correctly, as in the long-term other services will probably start to use Upstart :p

[URL="http://soniahamilton.wordpress.com/"]
http://soniahamilton.wordpress.com/[/URL]

---

### Post by argos3016 on 2010-02-20
I did that , but now i haven't sound.

---

### Post by argos3016 on 2010-02-21
[SIZE=6]For people that the sound doesn't work:
[SIZE=2]-Put start-pulseaudio-x11 in the .xinitrc.

That's all!!
[/SIZE][/SIZE]

---

### Post by Yanno on 2010-02-24
> **komputes said:**
> I had a hard time because I was following guides that were not tested on 9.10. In fact you don't need to mess with GDM's configuration as GRUB2 is the easiest way to get this done. Here are the steps:

1 - Edit the GRUB2 configuration defaults

```
$ sudo gedit /etc/default/grub
```2 - Change the line **GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"** to

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash text"
```3 - Save and close the grub file

4 - Update grub so that the changes are propagated to grub's configuration file (to all current and future kernels)

```
$ sudo update-grub
```That it! Simple right? :)

If you ever need to log into gnome, use the **startx** command. If you want GDM to start use the **sudo gdm start** command.

Hope this helps people from wasting hours of trying to disable GDM on 9.10 using older guides that suggest editing gdm.conf, moving gdm.conf, using update-rc.d, rcconf or sysv-rc-conf - none of those worked for me. This was the cleanest/best way I found of doing this.

Cheers!

:guitar:


I'd appreciate it.But I've still got a problem now in Karmic.I installed both kdm and gdm,after typing "startx" in the command line,I've only to login into Gnome,how could I login kde?Thx!

---

### Post by afrodeity on 2010-03-09
I can't seem to get GDM to reinstall properly. I somehow borked it, and the only manager that is working is KDM. The new Grub2 setup is very confusing, how does one go about installing GDM?

---

### Post by mfdc1969 on 2010-03-11
I am also looking for a way to boot my old desktop (now being used as a  server) into a lower runlevel. If I use this method:

```
Check your current runlevel:

% runlevel
N 2

Edit /etc/init/gdm.conf, and change:

stop on runlevel [016]

to:

stop on runlevel [0216]
```


With the lower runlevel I assume I will be able to use ssh and my NFS will still mount but how will I start up X and Gnome should I need to?

---

### Post by asmoore82 on 2010-03-11
> **mfdc1969 said:**
> With the lower runlevel I assume I will be able to use ssh and my NFS will still mount but how will I start up X and Gnome should I need to?

to get into Gnome as the current console user: ```
startx
```

to start the gdm service manually to get a GUI login screen: ```
sudo start gdm
```

---

### Post by mfdc1969 on 2010-03-11
Thank you for the info - it works like a charm! When I typed in the command to start the GDM it replied:
```

$ sudo start gdm
[sudo] password for michael: 
gdm start/running, process 1731
```

Now, after I have used Gnome is there a command that will shutdown the X server and Gnome and return to the lower runlevel?

I'm not sure but will one of these work:

[INDENT] sudo killall X
 sudo kill -9 1731
 sudo /etc/init.d/gdm stop[/INDENT]

I have been using Ubuntu for 5 years now and I'm confident in my limited CLI abilities but I would still like the ability to use Gnome on occasion.

---

### Post by not_a_phd on 2010-03-11
> **savanna said:**
> A better method.

Check your current runlevel:

[FONT=Courier New]% runlevel
N 2[/FONT]

Edit /etc/init/gdm.conf, and change:

[FONT=Courier New]stop on runlevel [016][/FONT]

to:
[FONT=Courier New]
stop on runlevel [0216][/FONT]

Better to manipulate the runlevels correctly, as in the long-term other services will probably start to use Upstart :p


I did a variation on this theme, by setting my default runlevel to 3, and stopping the GDM on runlevel [0136]. This was a pain in the rear. The suggested modifications to the grub defaults look like a simpler method. I don't understand why that technique is not as good as changing the Upstart configuration files. Will the linux kernel not always accept command line options?

---

### Post by ctdesing on 2010-11-10
> **Yanno said:**
> I'd appreciate it.But I've still got a problem now in Karmic.I installed both kdm and gdm,after typing "startx" in the command line,I've only to login into Gnome,how could I login kde?Thx!

# /etc/init.d/kdm restart

---

