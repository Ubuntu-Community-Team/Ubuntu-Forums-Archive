---
title: "Desktop to right side"
date: 2005-10-30
forum: Desktop Environments
---

### Post by jobee on 2005-10-30
Hi all I'm new here. I just downloaded and am checking out the live ubuntu, my question is this. I have a Windows installation on the same computer and I have my monitor adjusted to fit the desktop on it. Now I'm thinking about installing ubuntu on the other hard drive on it but when I boot live the screen shows off to the right just a little bit. Is there a program to adjust this like in other linux installations I've tried before? I don't want to use the buttons on my monitor because everytime I go back and forth betweeen Windows and Ubunta I will have to adjust it again.  Thank You 
By the way just from trying this just a little while I think I'm liking it a lot.:smile:

---

### Post by heimo on 2005-10-30
Hi!

I don't know if it's possible to make this permanent on Live CD, but this is how I'd do it on installed Ubuntu. To adjust position of your screen, open terminal (Applications->Accessories->Terminal), run xvidtune (type: "xvidtune"), adjust the screen and hit Show-button. You'll see a line with something like this on the terminal screen:
```
"1280x1024"   157.50   1280 1332 1492 1728   1024 1025 1028 1072 +hsync +vsync
```

Next you should:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
sudo gedit /etc/X11/xorg.conf

```
In Monitor section, add the above line with a prefix "Modeline", like this:
```
Modeline "1280x1024"   157.50   1280 1332 1492 1728   1024 1025 1028 1072 +hsync +vsync
```

That should do it. There should be no need to restart X if you did make the change (hit Apply in xvidtune), but you should test that this new change works. Hit ctrl+alt+backspace to restart X. If it doesn't work, you can copy back the old configuration file using:
```
sudo /etc/X11/xorg.conf_backup /etc/X11/xorg.conf
```
and restart X using:
```
sudo /etc/init.d/gdm start

```

---

### Post by jobee on 2005-10-30
Perfect works like a charm. Didn't need to do any code, I just opened the xvidtune program and pressed left a couple of times and it's perfect.
Thank you very much, I do beleive I'm going to have to install Ubunta on the hard drive.:D

---

### Post by heimo on 2005-10-30
[quote=jobee]Perfect works like a charm. Didn't need to do any code, I just opened the xvidtune program and pressed left a couple of times and it's perfect.
Thank you very much, I do beleive I'm going to have to install Ubunta on the hard drive.:D[/quote]

:) Great. And when you've installed Ubuntu on hard disk, the instructions above will help you to make the change permanent.

---

### Post by jobee on 2005-10-30
I don't understand this, I had it working perfectly last night using the live version. The resolution at 800 x 600 and the refresh at 75, now I install it to the hard drive and the only refresh rates I get as as option is 56 or 60 at 800 x 600 and 60 at 1024 x 768 or 640 x 480. What did I do wrong? Looking in the device manager it has my video card as a pci when it is actually an agp. Do I start over or ?:(

---

### Post by sam hassell on 2005-10-30
run "sudo dpkg-reconfigure xserver-xorg" and you can set the monitor settings in the last few pages. Most of the earlier settings you can accept as the default.

Let us know if you run into any other complications.

edit: youll have to restart gdm of do a "ctrl-alt-backspace" to see the changes.

---

### Post by heimo on 2005-10-30
Reconfiguring should work. Some additional tips'n'tricks:
[http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)

---

### Post by jobee on 2005-10-30
You guys are the greatest!!! I think I know how this happened. I have a kvm switch and when I was waiting for the ubuntu to install I was on the other computer via the kvm switch. Probably when it was trying to detect the monitor during install it couldn't because of it hit a dead end at the switch.  All looks good now because of your help. Thank You:D

---

### Post by pedja_portugalac on 2008-01-03
Please, can anybody help me to solve this problem? I have followed tutorial from heimo and it works fine until I restart computer but then it turns back like before. Opening xvidtune and pushing 2X left button I get right resolution. Then I push apply and show, after what it give me: > "1024x768"   78.80   1024  1048 and so on
Then I've opened sudo gedit and pasted that line in monitor section with Modeline before:> Modeline  "1024x768"   78.80   1024  1048 and so on
I saved that and exit gedit and xvidtune. After rebooting ctrl+alt+back it comes back with initial problem. I have tried to paste that line as first in monitor section, then as last but still no difference it comes back as initial resolution again and again. Where I was wrong? Please somebody help me if You can cause it's boring me to set the resolution with xvidtune in the beginning of every session. 
PS. I had some problem updating gedit from APTonCD and now I am reinstalling whole system. Then I'll try procedure ones again but without updates from APTonCD, may be something is wrong with that?

---

### Post by pedja_portugalac on 2008-01-03
So many tries and 4 times reinstalling OS. For tonight it's enough. :(

---

