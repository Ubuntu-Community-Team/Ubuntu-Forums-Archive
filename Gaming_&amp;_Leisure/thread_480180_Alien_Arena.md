---
title: "Alien Arena"
date: 2007-06-21
forum: Gaming &amp; Leisure
---

### Post by phizikal on 2007-06-21
Alien Arena is running very slow, but I looked at my system performance logs and noticed processor wasn't getting pass 60%.

Please help! I really want to play a game.

---

### Post by Cappy on 2007-06-21
You should have posted relevant information from the last thread you posted on or posted back to that one.
I can't believe it got to 3 pages and your problem wasn't solved.

Run this:
```
sudo apt-get --purge remove nvidia-glx* nvidia-kernel-common nvidia-settings
```

```

sudo rm /etc/init.d/nvidia-*
sudo update-rc.d nvidia-kernel remove
sudo apt-get install nvidia-glx-legacy linux-restricted-modules-`uname -r`
```

reboot.

```
glxinfo | grep direct
```
should now return
direct rendering: Yes

---

### Post by phizikal on 2007-06-21
Ok, thank you very much. The last dude made it like way worst. Much appreciated. :)

---

### Post by phizikal on 2007-06-21
Meh... I though it was working.

```

root@admin-roothackers:/home/admin# glxinfo | grep direct
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".

```

---

### Post by Cappy on 2007-06-21
Copy and paste each block of text into your terminal again and reboot. (I call it magic voodoo)
Errors are supposed to happen due to it triple checking but make sure that the last line "sudo apt-get install ..." line is definitely doing something; you may have to hit enter after pasting to run it.

If it still isn't working you should goto (System-->Administration-->Restriced Drivers Manager) and click on the checkbox there.

---

### Post by phizikal on 2007-06-21
I am watching it all install and everything. It completely and all. But when i check to see if its direct rendering, its doing the same thing.

So, I duno. =/

I am probably get a new gfx card soon.

---

### Post by Cappy on 2007-06-21
It should work if you rebooted.

Also:
"If it still isn't working you should goto (System-->Administration-->Restriced Drivers Manager) and click on the checkbox there." (and then reboot)

---

### Post by phizikal on 2007-06-21
It's really not working. I rebooted and all. And I do not have restricted drivers manager.

---

### Post by dannyboy79 on 2007-06-21
I guess i'd first like to know how Cappy auotmagically knew that the author of this thread has a nvidia card? if so, then great, if not, could you please paste the output from 

lspci -v

FYI:
I have a XFX GeForce 6200 AGP 8X 128mb RAM and the restricted modules manager chose the nvidia-glx driver instead of the nvidia-glx-new, so I chose to uncheck the rmm, then restart, then install the nvidia-glx-new from the command line using synaptic, then add "nv" in the quotes within the /etc/defaults/linux-restricted-modules file and then you should be set!

UPDATE: disregard first couple statement as I see you 2 communicated in another thread.

---

### Post by Cappy on 2007-06-21
Because he had started another thread and he said he had a "Vanta/Vanta LT" which is a legacy only card.

---

### Post by phizikal on 2007-06-21
```

0000:01:00.0 VGA compatible controller: nVidia Corporation NV6 [Vanta/Vanta LT] (rev 15) (prog-if 00 [VGA])
        Subsystem: ASUSTeK Computer Inc.: Unknown device fffe
        Flags: bus master, 66MHz, medium devsel, latency 40, IRQ 11
        Memory at f6000000 (32-bit, non-prefetchable) [size=16M]
        Memory at fc000000 (32-bit, prefetchable) [size=32M]
        Expansion ROM at f7000000 [disabled] [size=64K]
        Capabilities: [60] Power Management version 1
        Capabilities: [44] AGP version 2.0

```

Yeah, I retried all that cappy and still no no. BTW, alien arena won't even start up. =/

---

### Post by Cappy on 2007-06-21
Sorry, I didn't realize you are running Dapper so you don't have a "restricted driver manager".

Here is what you need to try:
```

gksudo gedit /etc/default/linux-restricted-modules-common

```
You see DISABLED_MODULES=""
change that to 
```
DISABLED_MODULES="nv"
```

Next, let's make sure xorg knows to use the nvidia driver:
```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.backupdriverinstall
sudo dpkg-reconfigure xserver-xorg
```
If "nvidia" is highlighted already, you are done - you can close the window and reboot.
If "nv" is highlighted you should select "nvidia" with the arrow keys and hit enter. You can continue hitting enter until all the options are done. Reboot.

---

### Post by phizikal on 2007-06-21
Ok, I did this. 100% exactly how you told me too. And when I went to reboot, it wouldn't even dare to try to start back up. I try putting in a cd to make it boot from HD, so I just reinstalled everything. I didn't loose nothing really.

---

### Post by Cappy on 2007-06-23
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia#head-f8ea537454e53c8ecf3af0d8946a8162ac1c008d](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia#head-f8ea537454e53c8ecf3af0d8946a8162ac1c008d)

I hope that helps. You may be missing step #2 and step #10. You may want to also consider using Ubuntu Feisty instead. Sorry, I guess my script doesn't work for either Dapper or Dapper nvidia-glx-legacy.

Envy says it will work on Dapper:
[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

### Post by UK-Wobbie on 2007-06-23
> **phizikal said:**
> Alien Arena is running very slow, but I looked at my system performance logs and noticed processor wasn't getting pass 60%.

Please help! I really want to play a game.


I installed Alien Arena 2007 for ubuntu and it did not open!
So i unstalled it and installed the windows one on wine! 
And it worked ok :p

---

### Post by hikaricore on 2007-06-23
> **UK-Wobbie said:**
> I installed Alien Arena 2007 for ubuntu and it did not open!
So i unstalled it and installed the windows one on wine! 
And it worked ok :p

Did you attempt to run it from a terminal to see if there was any error output?

You may want to try uninstalling it (the linux version) and using the packages built by [getdeb.net]("http://www.getdeb.net/app.php?name=Alien+Arena+2007") to see if they work for ya.

---

### Post by UK-Wobbie on 2007-06-23
[QUOTE=hikaricore;2898882]Did you attempt to run it from a terminal to see if there was any error output?

You may want to try uninstalling it (the linux version) and using the packages built by [getdeb.net]("http://www.getdeb.net/app.php?name=Alien+Arena+2007") to see if they work for ya.[/QUOTE

I did have a look in terminal,
And i did not see any error signs or what!

But the game will not open when i click on the start up icon lol And i got the game files from [http://www.getdeb.net/](http://www.getdeb.net/)

I got the windows game file of the game from the Alien Arena 2007 website! And it worked in wine ok :D

---

### Post by phizikal on 2007-06-29
Ok, I had it installed for weeks now. How can I uninstall it, urban terror is flippin nice.

---

