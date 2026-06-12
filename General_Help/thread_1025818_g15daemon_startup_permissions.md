---
title: "g15daemon startup permissions"
date: 2008-12-30
forum: General Help
---

### Post by BuudWeizErr on 2008-12-30
Hi there.

I'm a windows crossover, still getting settled in on 8.10.  I've installed g15daemon for media information display on my Logitech G15 keyboard.

Everything works fine, I just can't get the daemon to start with X when I boot up.  I've added g15daemon to the sessions dialog box, but with just g15daemon, it doesn't start.  The only way I can get it to start is to change the command to 'gksu g15daemon' and enter my password whenever it prompts me.

I tried changing the permissions on /usr/sbin/g15daemon to 774 and it hasn't had any effect.

tia.

---

### Post by cariboo on 2008-12-30
Try using update-rc.d. The following command must be run in a Applications-->Accessories-->terminal, type:

```
sudo update-rc.d g15daemon defaults
```

This should start the deamon at start up.

Jim

---

### Post by BuudWeizErr on 2008-12-31
getting this in response:

```

buudweizerr@hardcore:~$ sudo update-rc.d g15daemon defaults
update-rc.d: /etc/init.d/g15daemon: file does not exist

```

so i tried this:

```

buudweizerr@hardcore:~$ sudo update-rc.d /usr/sbin/g15daemon defaults
update-rc.d: /etc/init.d//usr/sbin/g15daemon: file does not exist

```

the app is in /usr/sbin/g15daemon, what is the proper way of pointing it to the correct file?

---

### Post by BuudWeizErr on 2009-01-02
bump.

---

### Post by BuudWeizErr on 2009-01-04
buuuuuump.

---

### Post by Skripka on 2009-01-04
> **BuudWeizErr said:**
> buuuuuump.

How did you install g15daemon?  IIRC, all I did was install the debian package-and BAM, it worked....I'll dig to be sure-but I don't think I had to do anything special....

---

### Post by BuudWeizErr on 2009-01-04
> **Skripka said:**
> How did you install g15daemon?  IIRC, all I did was install the debian package-and BAM, it worked....I'll dig to be sure-but I don't think I had to do anything special....

It's been a while, but that sounds pretty close.  I remember not having to do much to get it to work, once i had the dependencies installed ok.

however it installed, it neglected to allow itself to be started normally :(.

thanks.

---

### Post by Skripka on 2009-01-04
> **BuudWeizErr said:**
> It's been a while, but that sounds pretty close.  I remember not having to do much to get it to work, once i had the dependencies installed ok.

however it installed, it neglected to allow itself to be started normally :(.

thanks.

One thing to try, I think I did do this the one time I installed all of the G15 utils from source....

```

sudo gedit /etc/rc.local

```and add:

```

g15daemon -d

```at the bottom.  You'll need to reboot to see if there is workingness happening.  

For the daemon to be run as a daemon it needs the "-d" after it in (ku,u,xu)buntu--IIRC it doesn't need a graphical sudo command to run it from the Terminal anyway....I'm operating by memory here..

---

