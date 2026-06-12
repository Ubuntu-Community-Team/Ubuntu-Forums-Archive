---
title: "10 minutes into life with ubuntu"
date: 2007-12-04
forum: Desktop Environments
---

### Post by chriscooney on 2007-12-04
And i've already broke it. 
 
I just made the switch, well trying, from Windows to Ubuntu 7.10. 

I right clicked the desktop, went to customise background and clicked on the advanced tab (or something similar) and enabled advanced or expert/improved graphics, it wanted to enable 3d on my gfx card (Nvidia 7950 GT), it installed something and asked to reboot, to which i did.

Now when it loads up, it goes through the motions and then gives me signal out of range as if its gone into some crazy resolution my monitor can't handle? Im using a 20" widescreen LCD.

Any help would be appreciated, thanks.

PS. Please break it down into idiot friendly speak, tyvm :D

---

### Post by Levant on 2007-12-04
Is your monitor configured correctly? Look for the Screens settings located in System -> Administration. I'm not sure I understand your problem (are you getting a popup that says "signal out of range"?), but double check that first I suppose. You can also try adjusting your resolution in System menu.

---

### Post by maybeway36 on 2007-12-04
Go in recovery mode and try
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by aysiu on 2007-12-04
> **chriscooney said:**
> 
Any help would be appreciated, thanks.

PS. Please break it down into idiot friendly speak, tyvm :D

> **maybeway36 said:**
> Go in recovery mode and try
```
sudo dpkg-reconfigure xserver-xorg
``` "Idiot-friendly speak"?

Newcomers who have used Ubuntu for 10 minutes are not going to know what recovery mode is or what to do with a random string of code.

To break it down, first of all, you don't need to go into recovery mode, so forget about that.

**Step 1**
Press Control-Alt-F1

This will switch you to a virtual terminal (a full-screen text mode)

**Step 2**
Log in (when you type your password, there won't be any visual feedback--don't panic; your password is still being accepted)

**Step 3**
At the prompt (something like *username@ubuntu:~$*), type ```
sudo dpkg-reconfigure xserver-xorg
``` You'll then get a series of questions. If you know the answer, select the appropriate option. If you don't, just go with the default and hit *Enter*

**Step 4**
When you've finished that "wizard," type ```
sudo /etc/init.d/gdm restart
``` This will restart the graphics server with the new settings... and will hopefully work.

---

### Post by dbott67 on 2007-12-04
> **chriscooney said:**
> ... Now when it loads up, it goes through the motions and then gives me signal out of range as if its gone into some crazy resolution my monitor can't handle? Im using a 20" widescreen LCD.

In previous versions of Ubuntu, my 20" LCD would also go out of range.  I needed to add the refresh rate to my xorg.conf file:

```
Section "Monitor"
    Identifier     "DELL 2007FP"
    [COLOR=Red]VertRefresh     60.0 - 60.0[/COLOR]
    Option         "DPMS"
EndSection
```So, in friendly terms, you will need to do the following:

1. Login to Ubuntu in terminal/safe mode
2. Backup the /etc/X11/xorg.conf file
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_bak
```3. Edit the /etc/X11/xorg.conf file to add the line in red above to the section called **Section "Monitor"**:
```
sudo nano /etc/X11/xorg.conf
```
4. Save & reboot.

-Dave

---

### Post by aysiu on 2007-12-04
What's the model of your 20" monitor?

---

### Post by chriscooney on 2007-12-04
Hi guys, 

Thanks for the replies, i was setting it up at work on my desk. Anyway having travelled home and connected it up to my home 20" ws lcd it now works? :) so there's the first thing fixed.

When i say idiot speak, im an idiot as far as linux goes :P

---

