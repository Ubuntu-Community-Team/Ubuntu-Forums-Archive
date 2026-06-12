---
title: "Selecting a graphics card"
date: 2012-03-22
forum: Desktop Environments
---

### Post by xdominex on 2012-03-22
Hello all!
I am having a problem with my graphics cards. I have an hp tm2t-1100 CTO. It has two graphics cards, an Intel integrated gpu and an AMD Radeon 5450. Installing the AMD graphics driver breaks xorg, and I suspect that this is because the vgaswitcheroo by default selects my Intel gpu for use by xorg. What I want to know is how to have my AMD gpu active and in use BEFORE xorg loads. There are a couple things I already have in mind to try, but I do not know how to do those things (that's why I'm here). Those things include

[LIST]
[*]loading and configuring the vgaswitcheroo kernel module to select my AMD gpu before lightdm loads
[*]configuring lightdm itself to select the AMD gpu to be active before xorg loads
[*]configuring xorg to run off of the AMD gpu by default
[/LIST]
I know you may think I'm barking up the wrong tree, but please do not shoot me down if you have not personally tried and thoroughly troubleshooted these methods already.


I am running Ubuntu 12.04 Beta 1, but since it's not fully supported yet, you are free to post instructions based on the operation of Ubuntu 11.10 instead. If I have to, I will install Oneiric to try anything that won't work on 12.04 beta 1 but that might work in Oneiric.


Thank you so much for taking the time to read and respond to my problem! You guys who help us troubled people are the best!

---

### Post by xdominex on 2012-03-27
anyone?

---

### Post by papibe on 2012-03-27
Hi xdominex.

May be a long shot but... Is there a way to disable the Intel card from the BIOS?

Just a thought.
Regards.

---

### Post by xdominex on 2012-03-28
Unfortunately no; HP's BIOS settings are much too sparse for my liking, and that is one feature I wish they had included but did not.

---

### Post by Favux on 2012-03-28
Hi xdominex,

Alright from:  [http://ubuntuforums.org/showthread.php?t=1616327](http://ubuntuforums.org/showthread.php?t=1616327)  I see the way to get the TM2t to start X is to turn off (power off) vgaswitcheroo before X starts by using this command in /etc/rc.local:
```
echo OFF > /sys/kernel/debug/vgaswitcheroo/switch
```
So that command tells me there's vgaswitcheroo.c file somewhere that has CLI switches.  Sure enough in a 3.2 rc2 kernel I happen to have lying around I found vga_switcheroo.c in /drivers/gpu/vga what seem to be at least some of the CLI switches:
```
			   vgasr_priv.clients[i].id == VGA_SWITCHEROO_DIS ? "DIS" : "IGD",
			   vgasr_priv.clients[i].active ? '+' : ' ',
			   vgasr_priv.clients[i].pwr_state ? "Pwr" : "Off",
```
Need to figure out what they are, although from the above command we've got a good handle on Pwr and Off:  turn off or power up the discrete video card.

And this code snippet seems to indicate you might to be able to start X with the ATI running:
```
	/* swap shadow resource to denote boot VGA device has changed so X starts on new device */
	active->pdev->resource[PCI_ROM_RESOURCE].flags &= ~IORESOURCE_ROM_SHADOW;
	new_client->pdev->resource[PCI_ROM_RESOURCE].flags |= IORESOURCE_ROM_SHADOW;
	return 0;
```
Not sure how you'd go about it though.

There's some cryptic comments at the beginning of the file that probably tell us something.  What I don't know but "switchto" intrigues me.

---

### Post by xdominex on 2012-03-28
Excellent! Looks like you are on to something here! I wish I understood more about how linux and X11 start up so I could pursue this myself more easily; that being said, I intend to do some research about that to perhaps learn what I need to know. I've already been able to start x fine and get in; I can even get into X, switch cards, and restart X to get my ATI card active and running, but this is all without the proprietary graphics driver. I can't do any of this with my proprietary graphics driver, unfortunately, and that is my whole goal. Anyway, so I'll try to do some research on your find about maybe starting X with the ATI card active, but I don't hold out much hope of learning enough to use it with my currently-limited knowledge of the matter. This is a step in the right direction, though! Maybe others can come in and use what you found to help me solve my problem.

---

### Post by jockyburns on 2012-03-28
My HP computer has the ability to turn off the onboard GPU in bios and use a GPU card and vice-versa. A few months ago, my NVidia graphics card decided to shuffle off this mortal coil, so I plugged my monitor into the onboard graphics output, entered bios when it was starting up and selected "Use onboard graphics" in the bios settings.

---

### Post by vedovatti on 2012-05-05
Hi there!
I have a HP tm2 hybrid ATI/Intel
The solution for me was to turn off the card before the session starts:
type in a terminal:  ```
sudo gedit /etc/rc.local
```
at the end copy and paste
```
chown -R $USER:$USER /sys/kernel/debug
echo OFF > /sys/kernel/debug/vgaswitcheroo/switch
exit 0
```
The first command gives the users permission to modify the vgaswitcheroo, the second one turns off the discrete card.
Restart the system and with the command:
```
sudo cat /sys/kernel/debug/vgaswitcheroo/switch
```you should get something similar to this:
```
0:DIS: :Off:0000:01:00.0
1:IGD:+:Pwr:0000:00:02.0
```that indicates you IGD (integrated) is Pwr (powered) DIS (discrate) is off.
I haven't manage to switch between cards. There used is a good script [http://asusm51ta-with-linux.blogspot.de/](http://asusm51ta-with-linux.blogspot.de/) but works for Ubuntu 10.10, I havent been able to adapted to other versions.

---

### Post by vedovatti on 2012-05-13
Hi finally I got the solution to manage switchable graphics on this computer. I just solved the main problem I had,that was to switch hybrid graphics with a script. The solutions is on the comment 9 in the [http://ubuntuforums.org/showthread.php?t=1927317](http://ubuntuforums.org/showthread.php?t=1927317) . Just as additional info I have a HP tm2 (Intel/ATI) and Ubuntu 12.04. Finally I can manage both cards. The only difference from the solution above is that I used added on the /etc/rc.local the following commands (the last command is to turn on the backlight that on every boot is off):```
modprobe radeon
chown -R $USER:$USER /sys/kernel/debug
echo OFF > /sys/kernel/debug/vgaswitcheroo/switch
echo 7 > /sys/class/backlight/acpi_video0/brightness
```

---

### Post by electronbee on 2012-05-15
Awesome-sauce! I did the changes to my rc.local and I'm about to reboot. Hope this works! Actually, I just want dual displays active...

---

