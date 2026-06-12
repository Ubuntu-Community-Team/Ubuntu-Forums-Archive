---
title: "Gnome 3 and Oneiric"
date: 2011-11-24
forum: Desktop Environments
---

### Post by brimble2010 on 2011-11-24
Hey All,

I've been dabbling with Ubuntu for a few years now and I think I've got the basics down.

I've just updated my work laptop to Oneiric (never updating until a release is >6 months old again) and I absolutely hate Unity.

My aim is to install Gnome 3 and I thought that is what I have done, but my desktop look nothing like any of the screenshots that I have seen. Specifcially there isn't the new dock or activties bar.

I was told that it was just a simple case of ```
sudo aptitude install -DV gnome
``` but I guess I am wrong.

I'm posting a screenshot of what my desktop looks like as I don't know what other information to provide.

Hope someone can help :)

Thanks,
Kristian

---

### Post by typhoon_tip on 2011-11-24
That's not the command I knew...

```
sudo apt-get install gnome-shell
```

---

### Post by lolpenguin on 2011-11-24
Your desktop (there's nothing wrong with it) is running GNOME FALLBACK, which is loaded when your computer does not support GNOME Shell (assuming that's what you wanted).
Run
```
/usr/lib/nux/unity_support_test -p
```
If you get "yes" to all you can run GNOME Shell (the test is for Unity 3D, but they have similar hardware requirements).
To install GNOME Shell
```
sudo apt-get install gnome-shell
```
In LightDM click the session cog and select _GNOME_ **NOT** GNOME Classic and you will be greeted with the GNOME Shell.

---

### Post by brimble2010 on 2011-11-24
```
kbrimble@castillo:~$ sudo /usr/lib/nux/unity_support_test -p
[sudo] password for kbrimble: 
Error: OpenGL rendering is not supported by the root visual
```

I guess that means no Gnome 3 for me then?

---

### Post by brimble2010 on 2011-11-25
Could it be that I am not using the correct nVidia drivers?

```

kbrimble@castillo:~$ lspci | grep -i nvidia
01:00.0 VGA compatible controller: nVidia Corporation Device 1057 (rev a1)
01:00.1 Audio device: nVidia Corporation HDMI Audio stub (rev a1)

```

---

### Post by 3Miro on 2011-11-25
> **brimble2010 said:**
> Could it be that I am not using the correct nVidia drivers?

```

kbrimble@castillo:~$ lspci | grep -i nvidia
01:00.0 VGA compatible controller: nVidia Corporation Device 1057 (rev a1)
01:00.1 Audio device: nVidia Corporation HDMI Audio stub (rev a1)

```

This doesn't show which Nvidia card is installed on your system. Try the command:
```
sudo lshw -C display
```

For Unity 3D you would need at least GeForce 8xxx or newer. To see which driver you have installed, you can go to "Additional Drivers". The best  Nvidia driver is the closed-source proprietary one.

---

### Post by brimble2010 on 2011-11-25
Here is the output of that command. Doesn't really give much away:
```
kbrimble@castillo:~$ sudo lshw -C display
[sudo] password for kbrimble: 
  *-display               
       description: VGA compatible controller
       product: nVidia Corporation
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:16 memory:f2000000-f2ffffff memory:e0000000-efffffff memory:f0000000-f1ffffff ioport:5000(size=128) memory:f3080000-f30fffff

```

I tried to install the proprietary nVidia drivers but I get an error. I've put the logs here: [http://pastebin.com/GfExarrx](http://pastebin.com/GfExarrx)

Thanks,
Kristian

---

### Post by brimble2010 on 2011-11-27
bump!

---

### Post by LinuxFan999 on 2011-11-27
> **brimble2010 said:**
> Hey All,
 
I've been dabbling with Ubuntu for a few years now and I think I've got the basics down.
 
I've just updated my work laptop to Oneiric (never updating until a release is >6 months old again) and I absolutely hate Unity.
 
My aim is to install Gnome 3 and I thought that is what I have done, but my desktop look nothing like any of the screenshots that I have seen. Specifcially there isn't the new dock or activties bar.
 
I was told that it was just a simple case of ```
sudo aptitude install -DV gnome
``` but I guess I am wrong.
 
I'm posting a screenshot of what my desktop looks like as I don't know what other information to provide.
 
Hope someone can help :)
 
Thanks,
Kristian
According to the screenshot, it looks as if you are running gnome 2.32.1 customized to look like Gnome 3 fallback, not the actuall Gnome 3 fallback.

---

### Post by brimble2010 on 2011-11-27
Hmm, how would I go about installing Gnome 3 and getting rid of Gnome 2 then?

Installing gnome-shell didn't seem to work.

---

### Post by sammiev on 2011-11-27
With 11.10 at the login screen select the little gear like icon to the right of the user-password and click on gnome. :)

---

### Post by brimble2010 on 2011-11-27
That's what I am doing...

From what I can see, the reason that I can't use Gnome3 is the lack of the proprietary nVidia drivers which I can't install due to an error I get when I try (one of my previous posts has a pastbin of the jockey log)

---

### Post by brimble2010 on 2011-11-29
Bump

---

### Post by coffeecat on 2011-11-29
> **brimble2010 said:**
> I can't use Gnome3 is the lack of the proprietary nVidia drivers which I can't install due to an error I get when I try

You do have a proprietary nvidia driver installed:

> **brimble2010 said:**
> 
```
kbrimble@castillo:~$ sudo lshw -C display
[sudo] password for kbrimble: 
  *-display               
       description: VGA compatible controller
       product: nVidia Corporation
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: [COLOR="Red"]driver=nvidia[/COLOR] latency=0
       resources: irq:16 memory:f2000000-f2ffffff memory:e0000000-efffffff memory:f0000000-f1ffffff ioport:5000(size=128) memory:f3080000-f30fffff

```

I tried to install the proprietary nVidia drivers but I get an error. I've put the logs here: [http://pastebin.com/GfExarrx](http://pastebin.com/GfExarrx)


The log includes this:

> nvidia_current is not the alternative in use

Which suggests you may have already installed a nvidia driver, but not from Jockey. Did you download a driver from the nvidia site? 

Unfortunately, your nvidia card is being extremely taciturn about its own identity which is not helping you:

> **brimble2010 said:**
> 
```

kbrimble@castillo:~$ lspci | grep -i nvidia
01:00.0 VGA compatible controller: nVidia Corporation Device 1057 (rev a1)
01:00.1 Audio device: nVidia Corporation HDMI Audio stub (rev a1)

```

Another question - a long shot: do you have hybrid graphics on that laptop? That is, both Intel + Nvidia. A "lspci | grep VGA" might tell us.

---

### Post by brimble2010 on 2011-11-29
```
kbrimble@castillo:~$ lspci | grep VGA
01:00.0 VGA compatible controller: nVidia Corporation Device 1057 (rev a1)
```

I guess that means no to the hybrid drivers?

I get an error when I try to activate the driver through the jockey-gtk but you say that I already have it installed?

---

### Post by coffeecat on 2011-11-29
> **brimble2010 said:**
> ```
kbrimble@castillo:~$ lspci | grep VGA
01:00.0 VGA compatible controller: nVidia Corporation Device 1057 (rev a1)
```

I guess that means no to the hybrid drivers?

Not hybrid drivers - hybrid graphics. But you don't, so that's OK.

> **brimble2010 said:**
> I get an error when I try to activate the driver through the jockey-gtk but you say that I already have it installed?

According to the information you've posted, you have some sort of proprietary nvidia driver installed. When you open Jockey/Additional Drivers, what does it tell you?

---

### Post by brimble2010 on 2011-11-29
It tells me that the nVidia driver is available to activate and when I press activate, I get a dialog telling me to check the jockey log (the one I pastebin'd)

---

### Post by typhoon_tip on 2011-11-29
> **brimble2010 said:**
> It tells me that the nVidia driver is available to activate and when I press activate, I get a dialog telling me to check the jockey log (the one I pastebin'd)

It's half installed, I suggest you get rid totally of the current driver before attempting any more installation.

- Install Synaptic (if not yet installed)
```
sudo apt-get install synaptic
```

- Open it and wait for it to rebuild the index

- Search for nvidia

- Right click and pick "Mark for complete removal" anything that is marked as installed (green box) that starts with **nvidia-** (attention ! do not remove anything else that is in the list when you search nvidia and does not start with "nvidia-")

- Click apply, and wait for it to complete

- Restart the computer

- **Open additional driver again, and tell us how many nvidia driver versions appear in your list** :)

---

### Post by brimble2010 on 2011-11-29
> **typhoon_tip said:**
> 
- **Open additional driver again, and tell us how many nvidia driver versions appear in your list** :)

None!

---

### Post by coffeecat on 2011-11-29
> **brimble2010 said:**
> None!

Did Synaptic uninstall any nvidia* packages. If so, what were they called? If you can't remember, look in File -> History.

---

### Post by gordintoronto on 2011-11-29
What brand and model is your computer?

---

### Post by brimble2010 on 2011-11-29
Nope, just removals:

```

Commit Log for Tue Nov 29 23:54:57 2011


Completely removed the following packages:
nvidia-173-modaliases
nvidia-96-modaliases
nvidia-common
nvidia-current
nvidia-settings

```

---

### Post by brimble2010 on 2011-11-29
We can mark this one as solved :)

What fixed it in the end was a driver update:

Removing all of the nvidia-* packages and then doing:

```

sudo apt-add-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get install nvidia-current

```

Thanks for all your help guys!

---

### Post by coffeecat on 2011-11-29
> **brimble2010 said:**
> Nope, just removals:

```

Commit Log for Tue Nov 29 23:54:57 2011


Completely removed the following packages:
nvidia-173-modaliases
nvidia-96-modaliases
nvidia-common
nvidia-current
nvidia-settings

```

That's an interesting set of removals. The two modaliases packages are not in the Oneiric repos that I can find, so I wonder if they were remnants from a previous version and were part of the problem. nvidia-current is the current most up-to-date nvidia driver in the repository so that explains the "driver=nvidia" in your lshw output. You need nvidia-common for nvidia drivers to show in Jockey so that's why nothing is showing at the moment. nvidia-settings is the nvidia configuration utility.

I suggest you do one of two things.

1 - Re-install nvidia-common and then see if Jockey will install the nvidia driver for you.

2 - Re-install all three of nvidia-common, nvidia-current and nvidia-settings from Synaptic.

**EDIT**: I see you posted that you've solved it with a ppa as I was typing my post.

---

### Post by brimble2010 on 2011-11-29
I upgraded (twice) from 10.10 so the modaliases could well be left over.

After removing these packages I just added the x-swat PPA and then installed nvidia-current (which installed settings and common). That seemed to fix it all. I now have a proper Gnome 3 desktop :)

---

### Post by brimble2010 on 2011-11-29
> **gordintoronto said:**
> What brand and model is your computer?

Lenovo Thinkpad T420 (work laptop)

---

### Post by typhoon_tip on 2011-11-29
> **brimble2010 said:**
> Lenovo Thinkpad T420 (work laptop)

Nice one :) Just bought a monster top of range T420 for one client of mine (the most expensive one) and he's running Win 7 at the moment, but plan to test Ubuntu on that one as well, should be lightning fast ! Win 7 is lightning fast too on that machine and trust me, is not the OS that is fast.

I personally have a ThinPad T400.

---

