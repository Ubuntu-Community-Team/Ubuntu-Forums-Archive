---
title: "Newbie Problems..."
date: 2006-05-26
forum: Desktop Environments
---

### Post by mad_willsy on 2006-05-26
Hi ive just installed linux on my computer and have fallen in love with it instantly, except for the following:

1. Music that sounds fine in w*****s XP souns naff in linux (and wma's dont even play!)
2. Drive partitioned, 1 for linux, 1 for w*****s, and some swap space. Linux reads its partition (e) but w*****s partition (c) isn't on desktop. W*****s cant see linux's partition.
3. Not the fogyest on how to uninstall/install anythinf w.s.e.
4. Screen resolution HUGE and not all suported modes are displayed in list (under system/preferences/screen resolution)
5. 2. doesnt matter if the answer to this question is yes. If i put a new 250GB HD in (1 in atm is only big enough for w** and linux anyway), will both OS's see it and write/read to it in harmony (i use w** for dreamweaver and fireworks and fash)

Sorry if I confused you!

Help apreciated!

p.s. W*****s has been reinstalled here so many times now that it has now become a swear word, hense the ***.

---

### Post by cskeide on 2006-05-26
1. [https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats) (w32codecs for wma)
2. [https://wiki.ubuntu.com/MountingWindowsPartitions](https://wiki.ubuntu.com/MountingWindowsPartitions)
Windows can't read linux filesystems. There might be ext2/ext3 drivers for windows?
3. [https://wiki.ubuntu.com/SoftwareManagement](https://wiki.ubuntu.com/SoftwareManagement)
4. You might have to reconfigure xserver```
sudo dpkg-reconfigure xserver-xorg
```
5. I suggest formatting the new drive using the fat32 filesystem. This way both win and linux can read/write.

Hope this helps.

---

### Post by aysiu on 2006-05-26
[QUOTE=mad_willsy]
2. Drive partitioned, 1 for linux, 1 for w*****s, and some swap space. Linux reads its partition (e) but w*****s partition (c) isn't on desktop. W*****s cant see linux's partition.[/quote] To have the Windows partition show up on the desktop, just middle-click-drag (Gnome) or drag (KDE) the folder to the desktop and select **link here**.

To have Windows read/write Linux:
[http://www.fs-driver.org](http://www.fs-driver.org)

> 
3. Not the fogyest on how to uninstall/install anythinf w.s.e. [http://www.monkeyblog.org/ubuntu/installing](http://www.monkeyblog.org/ubuntu/installing)
> 
4. Screen resolution HUGE and not all suported modes are displayed in list (under system/preferences/screen resolution) Check [this out](http://ubuntuforums.org/showpost.php?p=129379&postcount=21)
> 
5. 2. doesnt matter if the answer to this question is yes. If i put a new 250GB HD in (1 in atm is only big enough for w** and linux anyway), will both OS's see it and write/read to it in harmony (i use w** for dreamweaver and fireworks and fash) If it's FAT32 or if it's Ext3 and you use the FS-driver I linked to earlier.

---

### Post by badrinarayan on 2006-05-26
[LIST]
[*] See [this]("https://wiki.ubuntu.com/RestrictedFormats") to learn why you can't play mp3 and wma files out of the box in Ubuntu. It also tells you how you can get it to work. I don't understand what "naff" means, but if you cant hear sounds at all, [this]("https://wiki.ubuntu.com/DebuggingSoundProblems") may help
[*] In Linux, you need to [mount]("http://www.tuxfiles.org/linuxhelp/mounting.html") a filesystem before you use it. You need to [tell Ubuntu]("http://ubuntuguide.org/#windows") where your windows partitions are so you it can mount them automatically at bootup each time.
[*] If you don't have the foggiest idea about [how to install anything]("http://monkeyblog.org/ubuntu/installing.html") on Ubuntu, don't panic. 
[*] We need more information about your graphics adapter for this.
[*] Yes.
[/LIST]

---

### Post by jvictor on 2006-05-27
W*****s cant see linux's partition. 

Do you expect MS to do that ? :) I have doubts if they will even acknowledge that Linux exists ;) 


Btw u can  *BUY* tools like partition magic to use linux data when in windows

---

### Post by Lin-X on 2006-05-27
All of these issues and more are fully covered in the Ubuntu documentation: [http://help.ubuntu.com/starterguide/C/index.html](http://help.ubuntu.com/starterguide/C/index.html)
You will save yourself a ton of time and effort by looking there before you try anything else. The descriptions and how-to's are much more clearly written and easy to understand than some of the answers you might get from other users. Also, take a look at the forum, which is tabbed at the top of the home page. This is a great community and I'm sure you will find all the help you need. Welcome to Ubuntu!

---

### Post by aysiu on 2006-05-27
[QUOTE=jvictor]W*****s cant see linux's partition. 

Do you expect MS to do that ? :) I have doubts if they will even acknowledge that Linux exists ;) 


Btw u can  *BUY* tools like partition magic to use linux data when in windows[/QUOTE] You don't have to buy tools. Just use [http://www.fs-driver.org](http://www.fs-driver.org)

---

### Post by mad_willsy on 2006-05-27
Thanks all, just trying to get mp3/wmas to work. 

By naff, i mean its like im listening to a radio with a bad signal, not that it doesn't work at all.

---

### Post by the_witch_king on 2006-05-27
I too have been xperiencing this resoultion problem, but mine is more bizzare the resolution changes every reboot. Please check out my post [http://www.ubuntuforums.org/showthread.php?t=183132](http://www.ubuntuforums.org/showthread.php?t=183132)
and help me out if you can.

---

### Post by Lord Illidan on 2006-05-27
[quote=mad_willsy]Thanks all, just trying to get mp3/wmas to work. 

By naff, i mean its like im listening to a radio with a bad signal, not that it doesn't work at all.[/quote] 
I know what you mean.

Try running alsamixer in the terminal, and adjusting the PCM and WAV volumes down to 80% or less.

Master can be left at 100%

---

### Post by mad_willsy on 2006-05-29
and you do that how?

---

### Post by mad_willsy on 2006-05-29
[QUOTE=the_witch_king]I too have been xperiencing this resoultion problem, but mine is more bizzare the resolution changes every reboot. Please check out my post [http://www.ubuntuforums.org/showthread.php?t=183132](http://www.ubuntuforums.org/showthread.php?t=183132)
and help me out if you can.[/QUOTE]

That post solved my screen resoulution problem

---

### Post by steve.horsley on 2006-05-29
[QUOTE=mad_willsy]and you do that how?[/QUOTE]
You have a volume control on your panel? If so, right-click the speaker and choose **Open volume control.**
If not, run **gnome-volume-control** from the command line.

---

