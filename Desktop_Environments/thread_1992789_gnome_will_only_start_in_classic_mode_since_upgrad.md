---
title: "gnome will only start in classic mode since upgrade to 12.04"
date: 2012-05-31
forum: Desktop Environments
---

### Post by Mrenief78 on 2012-05-31
Like the title. 
Gnome was working before the upgrade just fine. Now it can only start up in classic mode.
Unity works too.
Any ideas how to make gnome run on my machine again?
thanks,
mike

---

### Post by Mrenief78 on 2012-06-01
I have updated my Nvidia Driver and restarted - still keeps falling back to classic gnome.
How is this possible if it had worked on the earlier version?

---

### Post by kansasnoob on 2012-06-01
Were you using gnome-shell from a PPA?

I at least guess you're talking about gnome-shell since you say you can use both unity and a classic session.

What does the terminal tell you if you run:

```
sudo apt-get install gnome-shell
```

---

### Post by Mrenief78 on 2012-06-01
> **kansasnoob said:**
> Were you using gnome-shell from a PPA?

I at least guess you're talking about gnome-shell since you say you can use both unity and a classic session.

What does the terminal tell you if you run:

```
sudo apt-get install gnome-shell
```

Thanks, I will let you know as soon as I'm back on that machine.
Do I need to be in gnome to run this or in unity or will it matter?
Yes, I was talking about gnome-shell not working anymore since upgrade.
If I log into with gnome it falls back to classic.
But I can run unity ok.

---

### Post by kansasnoob on 2012-06-01
> **Mrenief78 said:**
> Thanks, I will let you know as soon as I'm back on that machine.
Do I need to be in gnome to run this or in unity or will it matter?
Yes, I was talking about gnome-shell not working anymore since upgrade.
If I log into with gnome it falls back to classic.
But I can run unity ok.

It won't matter what session you're running when you run that command. Just watch the output of the terminal for possible problems.

You may very well have a graphics card problem that prevents Mutter from running but we need to go a step at a time ;)

---

### Post by Mrenief78 on 2012-06-01
> **kansasnoob said:**
> It won't matter what session you're running when you run that command. Just watch the output of the terminal for possible problems.

You may very well have a graphics card problem that prevents Mutter from running but we need to go a step at a time ;)

Just says that it's already installed..:
mike@mike-Vostro-200:~$ sudo apt-get install gnome-shell
[sudo] password for mike: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gnome-shell is already the newest version.
The following packages were automatically installed and are no longer required:
  libunity6 libglew1.5 libglewmx1.5 libdee-1.0-1
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
mike@mike-Vostro-200:~$

---

### Post by kansasnoob on 2012-06-02
I need to study some old notes but thought I'd at least give you a free bump.

One question though, what options show up in the login screen?

---

### Post by Mrenief78 on 2012-06-03
> **kansasnoob said:**
> I need to study some old notes but thought I'd at least give you a free bump.

One question though, what options show up in the login screen?

I get all options (i think..)
gnome
gnome classic
gnome no effects
unity
unity 2d

i'm sure it's to do with the driver. I have the geforce 8300
hope they will release a new driver soon. Seems like lots of other people have problems with that driver.

---

### Post by VanillaMozilla on 2012-06-04
> **Mrenief78 said:**
> I get all options (i think..)
gnome
gnome classic
gnome no effects
unity
unity 2d
In other words, the first choice gets you Gnome Classic, Gnome Classic (No effects) or Unity (I forget which).  Correct?

I don't know the cause, but for what it's worth, that makes two of us, so it must be pretty common.  ;)  In my case I think it's because my old computer just doesn't have the mojo any more.

---

### Post by traditionalist on 2012-06-04
> **Mrenief78 said:**
> Like the title. 
Gnome was working before the upgrade just fine. Now it can only start up in classic mode.
Unity works too.
Any ideas how to make gnome run on my machine again?
thanks,
mike

It only ran on mine after I removed unity ( or most of it ), see here;

[http://blogs.operationaldynamics.com/paul/opensource/not-unified-removing-unity-from-ubuntu-12-04-lts](http://blogs.operationaldynamics.com/paul/opensource/not-unified-removing-unity-from-ubuntu-12-04-lts)

Of course you do this at your own risk.  All the "GNOME"flavours now run on my machine, but I use GNOME Classic.

---

### Post by Mrenief78 on 2012-06-30
Had time to try to get it to work again.
Finally!
sudo apt-get purge nvidia* sudo nvidia-uninstallbasically had to get rid of nvidia drivers. I'm not sure which ones are being used now..
But I can use GS again and no more freezing (so far..)
Thanks for everybody who puts info like this on the forums!

---

