---
title: "Wine doesn't play nice with PS7"
date: 2005-12-26
forum: General Help
---

### Post by Tmyers on 2005-12-26
In an effort to compare PS and the Gimp (I know, I know, one is free and on is not) I decided to download the PS7 trial version to test it out. (As far as I know wine does not support cs2, so I grabbed an older version). Everything goes fines through the installation and I virtually restart windows. To launch the program I did
[CENTER][b]
cd "/home/USER/.wine/drive_c/Program Files/Adobe/Photoshop 7.0"
         & Then
wine Photoshop.exe[/CENTER][/b]

As soon as the virtual desktop appears I get an error stating

**[CENTER]Failed to initialize Vbox!(0002-0073-0066)[/CENTER]**

Any ideas at why this is happening? Possible Solutions?

---

### Post by Tmyers on 2005-12-27
It's been around a day, so Im guessing it's alright to bump this topic

---

### Post by mztriz on 2005-12-27
hmm, that's odd. PS7 is working fine here-- except the pen tool is messed up which is a shame. 
I have never tried the command to open photoshop though, i just clicked the photoshop.exe and wine did the rest.

---

### Post by Tmyers on 2005-12-28
Thats odd then. I tried just click photoshop.exe and I get the same error. The program is completely installed, I just can't access it. Does anyone have any ideas?

---

### Post by detyabozhye on 2005-12-28
Um, what version of WINE are you using? The latest (0.9.3) breaks PS7 and CS for some reason although ImageReady still works on 0.9.3. I downgraded to 0.9.2 for now.

---

### Post by Tmyers on 2005-12-28
Im using the latest. So I need to downgrade? How do I go about downgrading? On the winehq.org download page, all I see are the latest versions.

*edit* & CS will work after the downgrade?

---

### Post by thekid on 2005-12-28
i would love to know the answer too.. i can't load Photoshop CS either.

---

### Post by detyabozhye on 2005-12-28
In my experience, CS wouldn't install properly on my system, but I just killed the install when it gave me the error, so that it wouldn't start deleting any files, then it works, but it worked kind of bad, especially with keyboard shortcuts. So I just use 7 and uninstalled CS, since CS did something to 7's save file dialogs.

Anyways, I couldn't find 0.9.2 anywhere either, so I looked in my install cache or whatever you call it, and found the debs there.

I'll put the debs on my site temporarely. I don't know if libwine is still needed or not, but I have it there anyways.

[http://detyabozhye.com/other/](http://detyabozhye.com/other/)

Install using:

sudo dpkg -i <package name>

I might get flamed for telling people how to downgrade WINE, but hey, some of us still need to use Photoshop, so it is necessary.

---

### Post by Tmyers on 2005-12-29
much appreciated man! Downloading now :D

---

### Post by Tmyers on 2005-12-29
I totally uninstalled wine 0.9.3 and installed wine 0.9.2 in it's place. However, after installing the program once again, I try and launch and get the same error.

---

### Post by detyabozhye on 2005-12-29
Try reconfiguring WINE. Backup you current WINE folder, then install PS again. The WINE configuration stays if you try removing WINE itself. It's in ~/.wine Just open your home folder and press Ctrl+H, then you will see all the hidden folders, one of them is .wine

---

### Post by Tmyers on 2005-12-29
I don't exactly understand what your saying. When I re-installed wine the first time, I removed it via synaptic and deleted the .wine & .winetools folder in my home directory. When I installed 0.9.2 the directory was created again. Do you want me to do this again?

---

### Post by detyabozhye on 2005-12-29
I just thought you may have skipped that step, many ppl do. What do you get when you run Photoshop in the terminal?

---

### Post by detyabozhye on 2005-12-29
Another thing you can try is installing PS into an unconfigured WINE, that might let us see whether it's your configuration or not.

---

### Post by Tmyers on 2005-12-29
I did install it into an unconfigured wine folder. The installation of photoshop forced wine into making the folder (because I deleted it before). 

When I launch the program through terminal, I cd to the directory, and do a "wine photoshop.exe" and I don't get any errors in the consol. The error pops up in a small window, not in the terminal itself

---

### Post by detyabozhye on 2005-12-29
I don't know then man, I never ran into this problem, somebody else will have to take over now, sorry. But, I know for sure that people had problems with 0.9.3 and PS, but I don't know what to do any further.

---

### Post by Tmyers on 2005-12-29
Alright, Thanks for your help. It was much appreciated. I guess Ill mess around with it and hopefully eventually get it working.

---

### Post by lovelykag on 2007-06-16
I've tried installing ps7 with both standalone wine and crossover office in feisty and both have the same problem. 5 minutes (approx.) after opening up photoshop, it stops recognizing the key board shortcuts and keyboard. 

does anyone have the same problem?

Thanks.

---

