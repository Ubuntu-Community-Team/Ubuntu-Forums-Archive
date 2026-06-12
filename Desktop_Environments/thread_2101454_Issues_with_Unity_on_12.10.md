---
title: "Issues with Unity on 12.10"
date: 2013-01-04
forum: Desktop Environments
---

### Post by lads on 2013-01-04
Hello everyone,

I took the time this past holidays to give a try at 12.10. I installed it in an available partition in a laptop. Everything went went fine the first couple of times I booted into it, but I'm now experiencing some odd behaviour.

First of all, the Launcher isn't shown after the login, I have the Dash and the super key menu, but not the pretty icon list on the left. On occasion it appears back again (not clear what triggers it) but most of the time it simply doesn't show up through out the session.

Another problem are the appearance settings. Every time I log in they seem to be automatically reset to the defaults; the wallpaper, for instance, has to be re-selected each time I log in.

Any hints on possible causes of these behaviours would be much appreciated.

Thank you.

---

### Post by jgm4305 on 2013-01-04
You can have the Launcher on the desktop all the time. Go to Dash, Applications, Appearance and look at the top of the page for Behaviour. Click on it and you can see there a way to have the Launcher on all the time by clicking the OFF sign on the right.

---

### Post by lads on 2013-01-04
> **jgm4305 said:**
> You can have the Launcher on the desktop all the time. Go to Dash, Applications, Appearance and look at the top of the page for Behaviour. Click on it and you can see there a way to have the Launcher on all the time by clicking the OFF sign on the right.

Hi jgm, thanks for answering. I'm not referring to the auto-hide behaviour, the Launcher simply isn't shown, weather auto-hide is on or off.

---

### Post by grahammechanical on 2013-01-05
Do you get the top panel?

There have been issues with Nvidia drivers where both the top panel and the Launcher did not appear. Another issue was where the Nvidia driver did not understand where the left edge of the screen ended and was putting the Launcher a few centimetres outside the left screen edge and hence out of sight.

I experienced these issues during the development of 12.10 when the Nvidia drivers where updated.

I use Nouveau drivers all the time. I got fed up with busted Nvidia drivers. Made my testing of 12.10 development branch unusable at one point.

For the record. All the Ubuntu maintainers can do is pass the bug reports up to Nvidia and wait. They may be able to put in a work-around but that can be broken by a Nvidia update. Ubuntu developers cannot fix proprietary code.

Regards.

---

### Post by lads on 2013-01-06
Hi grahammechanical, thanks for stopping by.

> **grahammechanical said:**
> Do you get the top panel?

Yes, no problem with that.

> **grahammechanical said:**
> There have been issues with Nvidia drivers where both the top panel and the Launcher did not appear.

My graphics card is a Radeon HD 3650; I don't have any proprietary drivers installed.

> **grahammechanical said:**
> I use Nouveau drivers all the time. I got fed up with busted Nvidia drivers.

Where/how can I get these for my laptop? 

Thanks.

---

### Post by lads on 2013-01-10
Any further hints on these issues are welcome. Thanks.

---

### Post by stinkeye on 2013-01-10
You could try setting all the compiz settings back to default.
In Quantal the terminal command is...
```
dconf reset -f /org/compiz/ 
```
Then logout/in.

---

### Post by lads on 2013-01-10
> **stinkeye said:**
> You could try setting all the compiz settings back to default.
In Quantal the terminal command is...
```
dconf reset -f /org/compiz/ 
```
Then logout/in.

Hi stinkeye, that didn't do it, but *apt-get upgrade* apparently did (only logged in once after that). Thanks in any case.

I still have the issue with the wallpaper, though.

---

### Post by lads on 2013-01-11
The Launcher is gone again today. This is driving me nuts.

---

### Post by stinkeye on 2013-01-11
Make sure you have the latest updates...
```
sudo apt-get update && sudo apt-get upgrade
```


What gfx drivers are you using?
```
lspci -nnk | grep -iA2 vga
```

eg
> [COLOR="SeaGreen"]glen@Quantal:~$[/COLOR] lspci -nnk | grep -iA2 vga
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GF116 [GeForce GTX 550 Ti] [10de:1244] (rev a1)
	Subsystem: Giga-byte Technology Device [1458:351a]
	[COLOR="Red"]Kernel driver in use: nouveau[/COLOR]

P.S. Next time the launcher disappears, if ctr+alt+t works to open the terminal, reload unity to see if the launcher appears.
```
setsid unity
```

---

### Post by lads on 2013-01-11
Hi again stinkeye.

```
$ lspci -nnk | grep -iA2 vga
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI RV635 [Mobility Radeon HD 3650] [1002:9591]
	Subsystem: Sony Corporation Device [104d:9035]
	Kernel driver in use: radeon
```

The *setsid* command did restart Unity, but didn't brought back the Launcher :(

Thanks for the help in any case.

---

### Post by lads on 2013-01-17
Ok, after a few days banging my head I'm finally arriving somewhere. I had to take the laptop somewhere and noticed that the Launcher reappeared. Back home I set out to try different configurations and here's what I got:

[LIST]
[*]Internal monitor on (external off): Launcher present;
[*]Desktop **shared** between internal and external monitor: Launcher present;
[*]Desktop **mirrored** into both internal and external monitors: no Launcher;
[*]External monitor on (internal off): Launcher present.
[/LIST]

At home I usually boot with the the external monitor linked and the laptop lid closed, by some reason Ubuntu was mirroring the image with this configuration and the Launcher would be gone. So for now I can work with one of the monitors turned off, the only issue is when I need to mirror the image in a presentation.

As for the wallpaper, Ubuntu is failing to mount at start up the drive where it is stored .

---

