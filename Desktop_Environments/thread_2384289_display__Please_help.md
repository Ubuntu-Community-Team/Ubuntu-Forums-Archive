---
title: "display  Please help"
date: 2018-02-05
forum: Desktop Environments
---

### Post by saeeddeeas on 2018-02-05
Hello 
I  istalled ubuntu 17.10
now my resolition is 1024 * 760
i want changed it but error 

```
    ram : 4
    cpu : AMD® Phenom(tm) ii x4 b97 processor × 4 
    VGA : AMD® Rs880
    64-bit
```

> saeeddeeas@saeeddeeas-HP-Compaq-6005-Pro-SFF-PC:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 17.10
Release:    17.10
Codename:    artful



Please see

  

```
       cvt 1280 1024
    # 1280x1024 59.89 Hz (CVT 1.31M4) hsync: 63.67 kHz; pclk: 109.00 MHz
    Modeline "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
    saeeddeeas@saeeddeeas-HP-Compaq-6005-Pro-SFF-PC:~$ xrandr --newmode "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
    saeeddeeas@saeeddeeas-HP-Compaq-6005-Pro-SFF-PC:~$ xrandr --addmode VGA-0 1280x1024_60.00
    xrandr: cannot find output "VGA-0"

```

Please help me for set diplau 1280*1024

---

### Post by cruzer001 on 2018-02-05
Hello

```
xrandr: cannot find output "VGA-0"
```

What does xrandr show as connected?

Maybe VGA1 or ?

Are you on xorg?

---

### Post by saeeddeeas on 2018-02-05
> **cruzer001 said:**
> Hello

```
xrandr: cannot find output "VGA-0"
```

What does xrandr show as connected?

Maybe VGA1 or ?

Are you on xorg?

I new user in linux :(
```

sudo lshw -c video
[sudo] password for saeeddeeas: 
  *-display                 
       description: VGA compatible controller
       product: RS880 [Radeon HD 4200]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 5
       bus info: pci@0000:01:05.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:18 memory:e0000000-efffffff ioport:1100(size=256) memory:f0100000-f010ffff memory:f0000000-f00fffff memory:c0000-dffff


```

> saeeddeeas@saeeddeeas-HP-Compaq-6005-Pro-SFF-PC:~$ xrandr --addmode VGA-1 1280x1024_60.00
xrandr: cannot find output "VGA-1"
saeeddeeas@saeeddeeas-HP-Compaq-6005-Pro-SFF-PC:~$ 



---

### Post by coffeecat on 2018-02-05
@saeeddeeas, welcome to the forum.

Where did you find those xrandr commands? We need to see whether you are logged in with Wayland or with xorg, and how your display device is recognised by xrandr. Please run this command, and post the output:

```
xrandr
```

---

### Post by cruzer001 on 2018-02-05
> We need to see whether you are logged in with Wayland or with xorg
```

echo $XDG_SESSION_TYPE
```

---

### Post by coffeecat on 2018-02-05
@cruzer001, the output of xrandr will tell you if you are running Wayland. Or at least it does in the laptop I'm using. I'll check with my desktop machine. 

Also, the command you posted has a typo in it. You might want to edit out the final "_" from it! :)

---

### Post by cruzer001 on 2018-02-05
> **coffeecat said:**
> @cruzer001, the output of xrandr will tell you if you are running Wayland. If it doesn't, you can assume xorg.

Also, the command you posted has a typo in it. You might want to edit out the final "_" from it! :)

Oops and did not know xrandr could recognize wayland.  Thanks

---

### Post by saeeddeeas on 2018-02-05
> **coffeecat said:**
> @saeeddeeas, welcome to the forum.

Where did you find those xrandr commands? We need to see whether you are logged in with Wayland or with xorg, and how your display device is recognised by xrandr. Please run this command, and post the output:

```
xrandr
```

 xrandr
```
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 8192 x 8192
XWAYLAND0 connected 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768      59.92*+
  1280x1024_60.00 (0x27e) 109.000MHz -HSync +VSync
        h: width  1280 start 1368 end 1496 total 1712 skew    0 clock  63.67KHz
        v: height 1024 start 1027 end 1034 total 1063           clock  59.89Hz
```

---

### Post by saeeddeeas on 2018-02-05
> **cruzer001 said:**
> ```

echo $XDG_SESSION_TYPE
```
 			 				[INDENT]saeeddeeas@saeeddeeas-HP-Compaq-6005-Pro-SFF-PC:~$ echo $XDG_SESSION_TYPE
wayland
saeeddeeas@saeeddeeas-HP-Compaq-6005-Pro-SFF-PC:~$ 

[/INDENT]

---

### Post by coffeecat on 2018-02-05
> **cruzer001 said:**
> Oops and did not know xrandr could recognize wayland.  Thanks

Oops from me too! My bad. It identifies wayland by implication in my laptop, showing my display device the same as the OP's: XWAYLAND0 . But with my desktop, I get the same output as for xorg, with the conventional VGA, HDMI and DVI connections shown.

I was making a wrong assumption. I've learnt something today!

---

### Post by coffeecat on 2018-02-05
> **saeeddeeas said:**
> xrandr
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 8192 x 8192
XWAYLAND0 connected 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768      59.92*+
  1280x1024_60.00 (0x27e) 109.000MHz -HSync +VSync
        h: width  1280 start 1368 end 1496 total 1712 skew    0 clock  63.67KHz
        v: height 1024 start 1027 end 1034 total 1063           clock  59.89Hz

@saeeddeeas, you didn't say where you found your xrandr commands. I wonder if you copied them from an online tutorial, but VGA-0 and VGA-1 won't work for you. Your display device is being recognised as XWAYLAND0. I would guess you need to substitute that for VGA-0.

---

### Post by cruzer001 on 2018-02-05
I wonder if changing  to xorg will also change xrandr output.  His xrandr looks totally hosed to me.

---

### Post by coffeecat on 2018-02-05
> **cruzer001 said:**
> I wonder if changing  to xorg will also change xrandr output.  His xrandr looks totally hosed to me.

It didn't help that there were no code tags around it, thus losing formatting. I've added them now.

For comparison, here's the output of xrandr from the laptop I'm posting from:

```
*******@Vaio-Artful:~$ xrandr
Screen 0: minimum 320 x 200, current 1600 x 900, maximum 8192 x 8192
XWAYLAND0 connected 1600x900+0+0 (normal left inverted right x axis y axis) 380mm x 210mm
   1600x900      59.95*+
```

I don't get the comparable last three lines, even if I change the display setting to something other than the maximum resolution, but the rest is similar, allowing for differences in hardware.

@saeeddeeas, do you know where those three lines came from? Did you get all that you posted just from the command xrandr?

---

### Post by coffeecat on 2018-02-05
> **cruzer001 said:**
> I wonder if changing  to xorg will also change xrandr output. 

Sorry, cruzer001, I didn't address this point. It's a good one.

I've logged out and back into xorg, and here's my xrandr now - compare with my previous post:

```
*******@Vaio-Artful:~$ xrandr
Screen 0: minimum 320 x 200, current 1600 x 900, maximum 16384 x 16384
LVDS-1 connected primary 1600x900+0+0 (normal left inverted right x axis y axis) 382mm x 215mm
   1600x900      60.00*+
   1152x864      59.97  
   1024x768      59.95  
   800x600       59.96  
   640x480       59.94  
   720x400       59.97  
   640x400       59.96  
   640x350       59.84  
VGA-1 disconnected (normal left inverted right x axis y axis)
HDMI-1 disconnected (normal left inverted right x axis y axis)

```


@saeeddeeas, log out, at the login screen, where you can see your name, click on the cogwheel and choose "Ubuntu with Xorg", and then log in. And then post the output of the command "xrandr" again.

Also, while still in Xorg, click on "Activities" at top left, and then search for "display". Choose Displays under Settings and see if you can adjust your screen resolution that way.

---

### Post by saeeddeeas on 2018-02-05
> **coffeecat said:**
> @saeeddeeas, you didn't say where you found your xrandr commands. I wonder if you copied them from an online tutorial, but VGA-0 and VGA-1 won't work for you. Your display device is being recognised as XWAYLAND0. I would guess you need to substitute that for VGA-0.

I find it a site online :D

---

### Post by saeeddeeas on 2018-02-05
> **coffeecat said:**
> Sorry, cruzer001, I didn't address this point. It's a good one.

I've logged out and back into xorg, and here's my xrandr now - compare with my previous post:

```
*******@Vaio-Artful:~$ xrandr
Screen 0: minimum 320 x 200, current 1600 x 900, maximum 16384 x 16384
LVDS-1 connected primary 1600x900+0+0 (normal left inverted right x axis y axis) 382mm x 215mm
   1600x900      60.00*+
   1152x864      59.97  
   1024x768      59.95  
   800x600       59.96  
   640x480       59.94  
   720x400       59.97  
   640x400       59.96  
   640x350       59.84  
VGA-1 disconnected (normal left inverted right x axis y axis)
HDMI-1 disconnected (normal left inverted right x axis y axis)

```


@saeeddeeas, log out, at the login screen, where you can see your name, click on the cogwheel and choose "Ubuntu with Xorg", and then log in. And then post the output of the command "xrandr" again.

Also, while still in Xorg, click on "Activities" at top left, and then search for "display". Choose Displays under Settings and see if you can adjust your screen resolution that way.
now i login Xorg 
```
xrandr
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 8192 x 8192
VGA-0 connected primary 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768      60.00* 
   800x600       60.32    56.25  
   848x480       60.00  
   640x480       59.94  
DisplayPort-0 disconnected (normal left inverted right x axis y axis)


```

---

### Post by saeeddeeas on 2018-02-05
I can not changhe dispale agayn :(
[IMG]https://www.photobox.co.uk/my/photo?album_id=5247529242&photo_id=500558805514[/IMG]
[https://www.photobox.co.uk/my/photo?album_id=5247529242&photo_id=500558805514](https://www.photobox.co.uk/my/photo?album_id=5247529242&photo_id=500558805514)

---

### Post by coffeecat on 2018-02-05
> **saeeddeeas said:**
> I find it a site online :D

Is the link to the site a state secret? We are not mind readers.

Try your xrandr command with VGA-0, but while logged in with Xorg. Your display device is being recognised as XWAYLAND0 in Wayland, and I suspect that you ran the command while in Wayland, which is the default when logging in.

Oh, and...

> **saeeddeeas said:**
> [IMG]https://www.photobox.co.uk/my/photo?album_id=5247529242&photo_id=500558805514[/IMG]
[https://www.photobox.co.uk/my/photo?album_id=5247529242&photo_id=500558805514](https://www.photobox.co.uk/my/photo?album_id=5247529242&photo_id=500558805514)

I get "You cannot access this album"

Please use the attachment facility to upload any images to the forum - the paperclip icon.

Please help us to help you. Posts without adequate information, references to off-site resources without links, and non-viewable images do not encourage forum members to help.

---

### Post by saeeddeeas on 2018-02-05
Tankyou 
i login to Xorg 
after run this commend 
>     cvt 1280 1024
# 1280x1024 59.89 Hz (CVT 1.31M4) hsync: 63.67 kHz; pclk: 109.00 MHz
Modeline "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
saeeddeeas@saeeddeeas-HP-Compaq-6005-Pro-SFF-PC:~$ xrandr --newmode "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
saeeddeeas@saeeddeeas-HP-Compaq-6005-Pro-SFF-PC:~$  xrandr --addmode VGA-0 1280x1024_60.00
saeeddeeas@saeeddeeas-HP-Compaq-6005-Pro-SFF-PC:~$     xrandr: cannot find output "VGA-0"



I can set display 1280 *1024
But after reboot it reset to 1024*780
Please help how set it allways

---

### Post by cruzer001 on 2018-02-05
You need to do one more step

[https://askubuntu.com/questions/754231/how-do-i-save-my-new-resolution-setting-with-xrandr](https://askubuntu.com/questions/754231/how-do-i-save-my-new-resolution-setting-with-xrandr)

---

### Post by saeeddeeas on 2018-02-05
> **cruzer001 said:**
> You need to do one more step

[https://askubuntu.com/questions/754231/how-do-i-save-my-new-resolution-setting-with-xrandr](https://askubuntu.com/questions/754231/how-do-i-save-my-new-resolution-setting-with-xrandr)

I am newcomer to linux please help more
I created the file 
.xprofile

```
touch $HOME/.xprofile
```
after edit
```
cd /hme 
nano /.xprofile
```
I put 

```
cvt 1280 1024
xrandr --newmode "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034$
xrandr --addmode VGA-0 1280x1024_60.00
```
and save 
after 
```
chmod +x $HOME/.xprofile
```
but after reboot display reset :(

---

### Post by deadflowr on 2018-02-05
It's unclear if you have ever tried setting it in Displays.
If so, try again this time after setting up the xrandr newmode and addmode commands, like
1)Run the xrandr commands
2)Open Displays
3)Select the new res you created in the resolution dropdown
4)Select Apply
5)Select keep in the keep do not keep popup window that will show.
then try a reboot and see if the resolution stays as you wanted or not.

---

### Post by saeeddeeas on 2018-02-05
> **deadflowr said:**
> It's unclear if you have ever tried setting it in Displays.
If so, try again this time after setting up the xrandr newmode and addmode commands, like
1)Run the xrandr commands
2)Open Displays
3)Select the new res you created in the resolution dropdown
4)Select Apply
5)Select keep in the keep do not keep popup window that will show.
then try a reboot and see if the resolution stays as you wanted or not.

no after reboot i shuld run againe commend xradr :(

---

### Post by coffeecat on 2018-02-05
@saeeddeeas, please listen to what people are saying to you. Deadflowr is suggesting you try setting display resolution in the GUI. I've already told you how to do this in post #14.

---

### Post by saeeddeeas on 2018-02-05
@coffecat , yes i can set display on Activitis>setting>display>1280X1024 it work but after reboot display reset to 1024X789 so i shoul run comments

---

### Post by cruzer001 on 2018-02-05
This is what the others are trying to tell you.

First set your display to 1280x1024 using xrandr just like you did before.  Do not reboot.

Then go to your display GUI and look for the proper setting (1280x1024) and change it using the GUI.

Follow this guide for the "Displays GUI"

[https://help.ubuntu.com/stable/ubuntu-help/look-resolution.html](https://help.ubuntu.com/stable/ubuntu-help/look-resolution.html)

Be sure to click on "Keep Changes"

---

