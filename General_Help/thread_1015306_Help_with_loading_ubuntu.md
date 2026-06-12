---
title: "Help with loading ubuntu"
date: 2008-12-18
forum: General Help
---

### Post by ozweego5 on 2008-12-18
Ok, My girlfriend computer crashed with windows on it so I recommended ubuntu, She brought me her PC tower and I installed 8.10 on her hp pavilion f1703 on my monitor and when i brought it back and set it up on her monitor, right before the GDM screen loads the monitor kicks off and tells me to change the resolution, I tried to get help with changing the resolution [http://ubuntuforums.org/showthread.php?t=996047](http://ubuntuforums.org/showthread.php?t=996047)

that was my last thread 

so I just figured that if I re-installed ubuntu clean on her monitor then that might help me...... nope, I put in the Live 8.10 CD and it brings me to the screen that ask what I want to do (Install, Try ubuntu, ext......) then the ubuntu splash screen comes up and then after that loads, i get the same thing happens and the monitor kicks off and it tells me to change the resolution.. ANY help would be GREAT

Happy Holidays Ubuntu Geeks

---

### Post by ozweego5 on 2008-12-18
anyone else have this problem??

---

### Post by abn91c on 2008-12-18
did you try using a recovery mode and does her monitor have a reset menu you can try?

---

### Post by ozweego5 on 2008-12-19
yeah I have tried to enter repair mode and entered dpkg-reconfigure -phigh xserver-xorg
shutdown -r now

and that did not work, there is not a reset button on her monitor or anything of that matter in her monitor menu settings....
I am just completely stumpd??

---

### Post by redilyn on 2008-12-19
Can you post your xorg.conf so we can have a look?

Boot to recovery mode. Then drop to root terminal or terminal ( I don't remeber what it says off the top of my head.

Then

```
sudo nano /etc/X11/xorg.conf

```

I don't know how to help you get that posted to the forums though. I expect you have two computers??

Maybe you can do this

```
sudo cat /etc/X11/xorg.conf > /home/*username*/temp.txt
w3m ubuntuforums.org
```

Then you might be able to attach that file to a forum post.

If you can not use w3m, maybe install ssh on your gf's computer and copy the file to your computer that way and then post.

If you happened to have enable auto login on that computer you could use a very simple fix (won't work from the login prompt)

Even though you cant see the screen do the following

```
Press alt+F2
type xrandr -s 1280x1024
press enter

or

Press alt+F2
type xrandr -s 1024x768
press enter
```

---

### Post by clw3388 on 2008-12-19
Yea.. most likley the monitor of your GF's dont support the resolution that your xorg.conf is attempting to use on X.. If you post or just edit the xorg file to a "supported" resolution of the monitor and restart all should be well..

---

### Post by ozweego5 on 2008-12-19
ok cool guys, Thanks for your replies. I am going to have to try to have my girlfriend get the X11 information you guys want to look at, since I am an hour away from her pc right now..but I will get back to you in a bit after I "Tech Support" threw it.

---

### Post by braddcadd on 2009-07-04
I have a f1703 monitor with the same out of range problem.  It recommends 1280x1024@60hz.  I have tried changing the boot options in grub but that did not help.  Here is my xorg.conf file.  Thanks for any help.

```

Section "Device"
	Identifier	"Configured Video Device"
        Option          "UseFBDev" "true"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection



```

---

### Post by braddcadd on 2009-07-04
For those of you looking for an answer, here is my fix.  I added a subsection under the screen section.  Three lines added to the xorg.conf file and now it works even after a reboot.
```

Section "Screen"
...
     SubSection "Display"
          Virtual 1824 768
     EndSubSection
End Section

```

---

