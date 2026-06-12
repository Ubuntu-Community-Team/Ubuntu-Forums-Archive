---
title: "Installed 9.10's recommendednVidia driver.Got black screen upon required reboot."
date: 2010-04-04
forum: Florida Team - US
---

### Post by rlynwood on 2010-04-04
Hello,

Trying to get the best video out of a newly refurbished Dell Latitude c840 for a friend, I installed 9.10's recommended proprietary driver.  When it finished downloading and installing, it said to reboot.  I did.  Coming back up, 9.10 displayed its splash screen logo until it got to just before the login screen.  Then the screen went black.  I still can hear the drums, announcing the login screen's display.  I even could type in the username and password, knowing how to do that with the keyboard, despite the screen's being completely black.  Again, 9.10's music announced that it logged in, presumably going to the desktop.  But I saw only black.  Now what?

The Dell Latitude c840 (circa 2002), Service Tag no. 4VC6CZ11, has the nVidia GeForce4Go video card.  I believe that 9.10 recommended the nVidia version 96 driver, but I'm not sure.

Ray

---

### Post by dantrevino on 2010-04-06
Are you using the default theme?

Try Ctrl-Alt-F1 to get to a console.  If you see a login prompt, log in, then 
1. see if you had any errors
```

cat /var/log/Xorg.0.log | grep EE > xorg-errors.txt

```

2. change your driver to the new nouveau driver (2D accel, but no 3d) by editing the X config file.  Type:
```
sudo nano /etc/X11/xorg.conf
```
In that file, look for 
```
Driver "nvidia"
```
and change it to 
```
Driver "nouveau"
```
Save the file (CTRL-X).

3. restart your xserver
```
sudo restart gdm
```

4. paste the contents of xorg-errors.txt here

---

### Post by rlynwood on 2010-04-13
Yes, I am using the default theme.  But this problem was solved by a new fellow at our monthly Linux meeting last Tuesday evening--with considerable effort and looking things up on the 'net.  It took a couple of hours.

Thanks for your help anyway.  I have three other problems on another computer, my main computer.  But I'll try to get help for those on the IRC meeting this Thursday evening.

---

