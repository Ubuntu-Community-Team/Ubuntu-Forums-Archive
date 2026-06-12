---
title: "No GUI load at boot"
date: 2011-12-03
forum: Desktop Environments
---

### Post by bobo123333 on 2011-12-03
[LEFT][FONT=Times New Roman, serif]**hi, i upgrade from 11.04 to 11.10.**[/FONT]
[FONT=Times New Roman, serif]It was not so clean install.[/FONT]
[FONT=Times New Roman, serif]Any way it works and i was able to logon and word.[/FONT]
[FONT=Times New Roman, serif]BUT, i done restart now and after bios all I see is black screen.[/FONT]

[FONT=Times New Roman, serif]i try to boot and click on the keypad (arrows, shift and enter keys)[/FONT]
[FONT=Times New Roman, serif]This way i finally saw something - part of the boot process of Ubuntu (like: starting cpus printing spooler [ok], and wait to network configuration).[/FONT]
[FONT=Times New Roman, serif]Any why it is not booting to the logon screen.[/FONT]

[FONT=Times New Roman, serif]What can I do?[/FONT]

[FONT=Times New Roman, serif]Again. it works in the past after the upgrade only once (just after the upgrade).[/FONT]

[FONT=Times New Roman]I tried the command:[/FONT]
[FONT=Times New Roman]"startx"[/FONT]
[FONT=Times New Roman]the error whas "giving up" and there was one fatal error about module "nvidia_173 not found"[/FONT][/LEFT]
Tries re install
[[COLOR=#444444]http://askubuntu.com/questions/66124...-173-not-found[/COLOR]]("http://askubuntu.com/questions/66124/module-nvidia-173-not-found")
Then it is worked but after boot all over gain including the reinstall is needed to be done again....

---

### Post by Azyx on 2011-12-03
I have no idea why it happens for you. But do you use propretarian drivers before you upgraded? Could it be that nvidia no longer support your gfx-card with propretarian drivers? If you know the model on the gfx-card and search you may find an awnser?

/Cheers

---

### Post by bobo123333 on 2011-12-04
ths issue is htat after i reinstall the driver, i call xstart and all is ok.
But after the reboot i should do all again...

---

### Post by Dubslow on 2011-12-04
I have something similar.
> Originally posted by: Dubslow
Hey guys, 
A couple of months ago, I tried booting Ubuntu (11.04) and got to the screen where it lists various applications on the left and (usually) [OK] on the right; I can't really give any more description than that. After getting to the screen, it stays there, and nothing happens. The boot just seems to freeze there. However, I know that the computer itself is working fine, because Ctrl+Alt+[F1-F6] bring up perfectly usable CLI's, and Ctrl+Alt+F7 just brings me back to the boot screen. 

As I recall, the trouble started when I was trying to update my nVidia drivers for the GTX 460 I have. Around 3 weeks ago I tried updating again, and initially it didn't seem to work, but then I (thought I) got it to work, and tried again, and got the same result. 

I have no clue how to fix this, and have been using Windows since. I can post the contents of any text file necessary (as I said the CLI's work fine and I have a flash drive).

Thanks
Dubslow


Intel i7-2600k
Intel DZ68DB Mobo
12 GB Memory
GTX 460
1 TB 7200 RPM Boot HDD
2 TB 5400 RPM Storage HDD
600W PSU

(Also for whatever reason I can't access my own Control Panel on the forum here, says I don't have access.)
I am certain that nVidia supports my card, and I've already tried re-updating the drivers.

Edit: I will try the solution in the other thread, thanks OP. Could you clarify what you said about trying the other solution, that solution working, and then somehow it breaking again?

Edit2: WOOOOOOOOOOOOOOOOOO!!!! Finally, after 2 months! OP, did you try running ```
apt-get install --reinstall nvidia-current
``` as opposed to ```
apt-get install --reinstall nvidia-173
```? The second didn't work for me, but then I tried the first, and BAM! GOT MAH LINUX BACK

---

### Post by bobo123333 on 2011-12-04
Both option not working for me.
startx luch the gui but ther is no auto load og the pc agter boot to the gui
 
When i boot and choose from grab the last version i see all [ok] and thw rwo lines :
starting load fallback graphics decives [ok]
starting load fallback graphics decives [fail]
 
after that i see:
starting bluetoth and nothing else ... it is stack here
 
BTE, there is no BT on ths PC

---

