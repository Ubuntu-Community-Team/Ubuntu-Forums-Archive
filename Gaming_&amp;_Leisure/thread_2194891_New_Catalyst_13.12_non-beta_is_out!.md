---
title: "New Catalyst 13.12 non-beta is out!"
date: 2013-12-21
forum: Gaming &amp; Leisure
---

### Post by DanglingPointer on 2013-12-21
I ran Unigine Valley with the new driver with a R9-290X and looks like I gained 2-3 FPS.  I suppose something is better than nothing. LoL

---

### Post by oldrocker99 on 2013-12-21
Well, keep a good thought...

---

### Post by dannyboy79 on 2013-12-21
will try out the new AMD BETA driver AFTER I use clonezilla to backup my / partition. Thanks for letting me know!

UPDATE: Gained 8 FPS (from 18.4 to 26.6) in Valley, 5 FPS (from 20.1 to 25.2) in Heaven and a WHOOPING 41 FPS GAINED in the Team Fortress 2 test ran by Phoronix Test Suite (from 54.4 to 95.4). Now that's a SOLID AMD Driver update right there! All I had to do was log out, log into tty1, stop lightdm, run the 13.11v9.4 run file with the --uninstall option as root. Restart the machine. Log into tty1, stop lightdm, install the 13.12 AMD driver using the run file with sudo and restart my machine again and all is well. AWESOME!

---

### Post by DanglingPointer on 2013-12-23
That's awesome!  Perhaps most of the fixes were for the mature cards.  I got the immature R9-290X.  Hopefully I'll get more FGLRX-loving from the new drivers coming in Jan.

On another note, I finally got leave from work and was able to spend the last couple of days watercooling the R9; it is now running at a constant 1GHz.  I think I'll play Metro LL all over again knowing I'm now getting a constant 1GHz!

---

### Post by sjackling on 2013-12-27
I had no such luck with the new driver... black screen after i login... i noticed that your running 12.04 though do you know of any issues with fglrx and 13.10? (and if you do give me some links please) Thanks

---

### Post by R33D3M33R on 2013-12-28
You should completely uninstall the old driver, remove /etc/X11/xorg.conf and reboot (make sure you have generic ati driver installed: [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)). Then download the driver from here [http://archive.ubuntu.com/ubuntu/pool/restricted/f/fglrx-installer-updates/](http://archive.ubuntu.com/ubuntu/pool/restricted/f/fglrx-installer-updates/) . The version number is 13.125. Download all packages with the number (for your architecture offcourse), install as sudo ```
dpkg -i *deb
```
 If there are dependency problems, run ```
sudo apt-get install -f
``` 
After installation run ```
sudo amdconfig --initial
``` and reboot. If your hardware is supported, this should always work.

The performance improvement from 13.11 v9.4 for me is minor (+/- 3% - probably experimental error), xonotic performance dropped 3%. So no actual gains for me (HD 7750).

---

### Post by dannyboy79 on 2013-12-29
WOW, i'm shocked I saw an 8 FPS increase with my HD7770 but you didn't see any gain with your HD7750.

---

### Post by R33D3M33R on 2013-12-30
I think this is something you can expect from my version of HD7750. It's already heavily factory overclocked and it's running near the power limits of the PCI-E slot (remember, my card has no power connector). This means the power management tweaks your card might receive, won't have big effects on my card, since there is no juice to improve performance. Also, various sotware combinations might have different impacts on performance. I use heavy DE (KDE), you use lightweight XFCE (probably). I would say that my card is already running at it's best since the 12.4 drivers came out, there is hardly anything to fix, maybe some tweak here and there. The only thing I'm missing is ZeroCore Power support.

---

### Post by sjackling on 2013-12-30
Well after reading the post by R33D3M33R and going through the help link and another link on that page i tweaked a few things and am going to try the 13.12 driver again. If that doesn't work ill grab the 13.11 he reccomended and try that. If that doesn't work, ill take the video card out and get a hammer, then go buy the gtx 770 ive been looking at :p Thanks for all the help!!

Update: i made a post of the error i recieved installing 13.12 in the thread i started Driver questions including the make.log file that shows the error... if any of you could tell me what it means in english that would help a lot :P thanks

---

### Post by Daliz on 2013-12-30
As I play a lot in Ubuntu and have a HD6870, I would love to try these drivers out. I'm on 12.04 so the ones installed via the "Additional drivers" are pretty old, I think.

Always when I install a driver manually, the fglrx module cannot be loaded and when I try to do "amdconfig --initial" I get an error that libgl.so.1 cannot be found. This happened with this latest version also. The installer itself gives no error.

Anyone have any idea why? Is there a package I'm missing or something?

(Maybe I should post a new topic with more details..)

---

### Post by R33D3M33R on 2013-12-30
Mixing .deb and manual installer is **very very very very** bad! Before you install the manual package, you should purge the Additional driver version with: ```
sudo apt-get purge fglrx*
```
Please pay attention to what the package manager will be removing! Then do the [buildpkg]("http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide") and after that amdconfig initial. If you have any problems, delete /etc/X11/xorg.conf and rerun amdconfig initial.

---

### Post by Daliz on 2013-12-31
Thanks R33D3M33R, that does it.

Of course I had "disabled" the driver earlier using the "Additional drivers"-thingy, but I didn't think there was a need to purge anything. I thought it would be uninstalled that way..

I had a another problem: there was a /etc/modprobe.d/blacklist_local.conf in which fglrx was blacklisted. I have no idea where this file came from and what had generated it, but needless to say it didn't really help to get this working. :)

---

