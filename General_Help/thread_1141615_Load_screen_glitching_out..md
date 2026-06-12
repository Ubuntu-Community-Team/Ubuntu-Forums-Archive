---
title: "Load screen glitching out."
date: 2009-04-28
forum: General Help
---

### Post by kooldino on 2009-04-28
The other day I installed Kubuntu 9.04 on my machine.  Everything installed just fine.

I have an ATI card in it (an X700, IIRC), so I wanted to install the fglrx driver so I could use compositing.  I tried to, but it didn't work.  

I removed the driver, and all was well.

Yesterday I booted the machine again.  The Kubuntu screen started loading, and about a minute later after the screen tried to change resolution modes, the machine would essentially "lock up" and display a distorted purple-ish kubuntu logo (like at the load screen).  

I tried doing the dpkg xserver phigh reconfig, tried setting the xorg.conf back to default, you name it - it won't come back up in KDE.

What do I do now?

---

### Post by kooldino on 2009-04-29
Help?

---

### Post by kooldino on 2009-04-30
Someone has to have a clue here...

---

### Post by delcypher on 2009-04-30
I don't think the proprietary ATI driver works with Ubuntu 9.04 yet (The [ATI page]("http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.36&lang=English") says it supports up to [X.Org 7.4]("http://www.x.org/wiki/Releases/7.4") which corresponds to X.Org X server 1.5 - which is what Ubuntu 8.10 uses but 9.04 uses the newer [1.6]("http://www.x.org/wiki/Releases/7.5"))

So I don't think the proprietary ATI driver will work.

As for the screen "glitching out" something might of went wrong when you "removed" the driver. How did you remove the driver?

Here's a few things to try that might get you up and running again. I take no responsibility if this doesn't work. ALWAYS MAKE A BACKUP OF YOUR Xorg.conf file.

Boot up your machine and choose (recovery mode) from your GRUB menu (I think 9.04 asks you to press ESC at boot up to see this menu).

Once it's loaded there will be an options menu to "fix X". Try it.

If that doesn't work then try the option to "Drop to root shell prompt" (it might not be called that exactly).

First thing to try is to try and make a new xorg.conf file. At the prompt type:
```
Xorg -configure
```

That should create a Xorg.conf.new file in the directory you are in (probably the root home directory - /root). 

Now make a backup of the current Xorg.conf file and put the new Xorg.conf file in the /etc/X11 directory.

```
mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
cp xorg.conf.new /etc/X11/xorg.conf

```

Now exit (by typing exit). You should have the menu re-appear select "Continue booting" (I can't remember if it's called that exactly but it's along those lines). 

Let us know if that works.

If that doesn't work you can try editing your xorg.conf file to have the driver set to "vesa" and seeing if that works.
```

Section "Device"
        Identifier  "..."
        Driver      "vesa"
...       


```

If that doesn't work read your /var/log/Xorg.0 log file and seeing if it reports any problems.

Hope this useful to you.

---

### Post by kooldino on 2009-05-02
> **delcypher said:**
> I don't think the proprietary ATI driver works with Ubuntu 9.04 yet (The [ATI page]("http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.36&lang=English") says it supports up to [X.Org 7.4]("http://www.x.org/wiki/Releases/7.4") which corresponds to X.Org X server 1.5 - which is what Ubuntu 8.10 uses but 9.04 uses the newer [1.6]("http://www.x.org/wiki/Releases/7.5"))

So I don't think the proprietary ATI driver will work.

As for the screen "glitching out" something might of went wrong when you "removed" the driver. How did you remove the driver?

I can't recall.  I probably disabled it in the hardware manager and possible removed it from the package manager.

> Here's a few things to try that might get you up and running again. I take no responsibility if this doesn't work. ALWAYS MAKE A BACKUP OF YOUR Xorg.conf file.

Boot up your machine and choose (recovery mode) from your GRUB menu (I think 9.04 asks you to press ESC at boot up to see this menu).

Once it's loaded there will be an options menu to "fix X". Try it.

I had already tried that a bunch of times with no luck.

> If that doesn't work then try the option to "Drop to root shell prompt" (it might not be called that exactly).

First thing to try is to try and make a new xorg.conf file. At the prompt type:
```
Xorg -configure
```

That should create a Xorg.conf.new file in the directory you are in (probably the root home directory - /root). 


It failed when I ran it.  It gave me some message about having multiple displays or something (which I don't).

> Now make a backup of the current Xorg.conf file and put the new Xorg.conf file in the /etc/X11 directory.

```
mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
cp xorg.conf.new /etc/X11/xorg.conf

```

Now exit (by typing exit). You should have the menu re-appear select "Continue booting" (I can't remember if it's called that exactly but it's along those lines). 

Let us know if that works.

Negative.  Even if I did the dpkg reconfigure xorg phigh it still wouldn't work.

> If that doesn't work you can try editing your xorg.conf file to have the driver set to "vesa" and seeing if that works.
```

Section "Device"
        Identifier  "..."
        Driver      "vesa"
...       


```

If that doesn't work read your /var/log/Xorg.0 log file and seeing if it reports any problems.

Hope this useful to you.

Great idea, but that didn't work either.

After chasing this for hours, I just gave up and re installed and it's working again (with a default driver).

I even tried deleting a bunch of session files and such from /etc/X11/ in case something was awry with them.  Nothing.

---

