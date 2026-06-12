---
title: "Nexuiz performance suddenly tanked...can't figure out why"
date: 2007-06-12
forum: Gaming &amp; Leisure
---

### Post by timzak on 2007-06-12
Where I was getting in the 80 fps range awhile back, I'm suddenly getting in the teens with unplayable slowness in big open spaces.  Since I dual boot with Windows, I checked Nexuiz in Windows, and its performance has not dropped at all.  Only in Ubuntu has it dropped.  The only things I can think of are some critical updates that have been recently applied via Update Manager, and a different nvidia driver version.  I recently reinstalled Ubuntu and stuck with the default restricted mode driver (9631).  On my previous install, I had installed the glx-new drivers (9755).  So could the driver or any recent critical updates be responsible for a terrible drop in performance in Ubuntu?  Has anyone else noticed this?

I've tried removing and reinstalling Nexuiz from Synaptic.  I've also removed Nexuiz 2.2.3 and installed the latest version (2.3) and that also has terrible performance.  Basically, even the lowest game settings @ 800x600 are slower than what I was getting with nearly maxed out settings at 1280x1024.  I've tried disabling Beryl, disabling nvclock, I double-checked nvidia-settings to see if I accidentally enabled AA, etc.  I can't find anything that would cause this.

Help?

---

### Post by timzak on 2007-06-13
No one else has noticed Nexuiz performance suddenly drop?  I was sure it had to do with a recent Critical Update (perhaps a kernel update).

Are there any hidden settings that stay on your system if you remove Nexuiz?  When uninstalling, I deleted the folder I installed into as well as the hidden .nexuiz folder in my home directory.  Could there be any other files on the system with configuration settings that are screwed up?  

Thanks.

---

### Post by Cappy on 2007-06-13
This has happened to me twice, re-installing the nvidia-glx-new fixed it for me. It was in ut2004 but close enough =P

Here is the code I use to upgrade my drivers:
```

sudo apt-get --purge remove nvidia-glx* nvidia-kernel-common nvidia-settings
sudo rm /etc/init.d/nvidia-*
sudo update-rc.d nvidia-kernel remove
sudo apt-get install nvidia-glx-new linux-restricted-modules-`uname -r`

```

---

### Post by timzak on 2007-06-13
Thanks for the reply.  Last time I tried upgrading video drivers, I ended up losing the -general kernel (it somehow got changed to -i386), so I lost my dual-core processing.  I had to go through another step to get the right kernel back.  And to be honest, I had no idea what I was doing, I just followed directions.  This makes me very nervous about updating the nvidia drivers.  Will I have to go through that again?

I'm going to stand by before I follow the steps you posted, cuz I don't want to get myself stuck again without understanding what I'm getting into.

Thanks.

---

### Post by Cappy on 2007-06-13
Well that's just the basic install you can do. It shouldn't change you to the i386 kernel.

---

### Post by timzak on 2007-06-14
> **Cappy said:**
> Well that's just the basic install you can do. It shouldn't change you to the i386 kernel.

I'll do a Partimage backup before I try.  I seem to remember losing my GUI last time I tried to upgrade drivers.  Then I followed someone's command lines to get me back up and running and somehow through that process I ended up with a different kernel.  I'm not sure how or why it happened, but doesn't the nvidia driver have some kernel elements?  Do they get installed when you change the drivers?

---

### Post by Cappy on 2007-06-14
The nvidia driver installs linux-restricted-modules-`uname -r`
The nvidia-glx* packages REQUIRE this. It's in that code.

So, for instance, mine is
linux-restricted-modules-2.6.20-16-generic

The reason you lost your GUI is because the nvidia install failed. If that happens just go into recovery mode and re-run that code I gave you (and reboot).
If all else fails, you can get back to Gnome by running
```
dpkg-reconfigure xserver-xorg
```
and selecting the "nv" driver on the first step. Press enter for everything else.

---

### Post by timzak on 2007-06-15
First of all, thanks for your help.  I managed to upgrade the drivers without issues.  I think what happened the first time I tried this awhile back, when I ended up with the -386 kernel, was I copied and pasted directions similar to yours, but I didn't replace 'uname -r' with the actual kernel I was using (how's a newbie to know if it's not explicitly stated to do so?).

Now the bad news.  With the new drivers (9755), my performance is still way below what it used to be in Nexuiz.  At 800x600, with everything at default settings, I used to get 103 fps in Ubuntu and 103 fps in Windows.  Now I still get 103 in Windows but in Ubuntu I'm getting 14-15 fps.  This is on a fresh install of Nexuiz 2.2.3 from Synaptic.

Hey, I just discovered why my performance has tanked!  I don't know HOW it happened, but at least I know why.  I just ran nvclock -i  --info and here's the pertinent info:

```
-- AGP info --
Status:         Disabled
Rate:           0X
AGP rates:      4X 8X 
Fast Writes:    Disabled
SBA:            Disabled

```

Why the heck is my AGP disabled???  Whatever is causing it, it is exclusive to Feisty, because performance is normal in Windows.  Weird.  Any ideas?

---

### Post by timzak on 2007-06-15
Okay, I just fixed the AGP issue.  Somehow this line ended up in the nvidia section of my xorg.conf file:

```
Option 		"NvAGP" 		"1"
```

When I comment out that line, I get my AGP 8X back, as well as SBA.  Fast writes remain disabled, though I think they're enabled in my bios.

I keep pretty thorough backups of xorg.conf.  I have the original from a clean Feisty install, I have a version saved from nvidia-settings, and I have my current "good" version (which had this line added in).  None of my backups have this line, so something added it in.  Could it have been nvclock?  That's the only thing I've been experimenting with lately.

---

### Post by Cappy on 2007-06-15
I have no idea what would cause this. I lost half my FPS today in games so I had to re-install the nvidia drivers again. I wonder if my xorg is getting changed and causing this too. Call in Scooby and the Gang!

---

