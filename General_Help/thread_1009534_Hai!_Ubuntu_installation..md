---
title: "Hai! Ubuntu installation."
date: 2008-12-12
forum: General Help
---

### Post by Tribalnecktie on 2008-12-12
Hai. umm, i used the newest version of wubi to install Ubuntu style desktop on my pc. its windows xp 64 bit. i have plenty of space for it and plenty of ram. i started wubi and it seemed to 

install just fine. i rebooted, then i presed enter on the ubuntu 

installation. it had some code scroll on the screen, and then it 

went to a loading bar with UBUNTU written above it. after this. 

it asked to press esc to go to the menu. i didnt click nothin. 

then i let it run and it did some code stuff. and then it sorta 

stopped :|. like if i just click ubuntu, dont press anything. 

and wait for it to load. it gets to a black screen where it has 

maybe 2 lines of code at top. then it says loading please 

wait... then 2 lines under that it says.
 Type help for a list of something. i typed help. im new to 

linux so i had no idea what any of those things would do. and so i figured it would start on its own and was just loading. i 

waited for a while and still nothing happened. Basically when i reboot pc and click ubuntu. it gets to that point then seems to 

stop. i can still type things in the lines but nothing seems to get it to i guess Fully install. Basically i cant get to the ubuntu screen where you type in username and password. it gets "stuck". Help??

Thanks :)

(ps) srry for wierd spacing thought it was easier to read that way :)

---

### Post by Jammanuser on 2008-12-12
hmm...perhaps ur hardware is not supported? it would help a lot if u describe precisely the code u mentioned, just as u see it! ;)

Cheers! ):P

Jam Man

:guitar:

---

### Post by magmon on 2008-12-12
The wubi install is wierd. Uninstall, and start the installer again. Once it finishes, restart and boot into windows. Then, restart again and boot to ubuntu. Tell me if that works!

---

### Post by Tribalnecktie on 2008-12-12
umm when i uninstall should i back up any of those files or not??

asks me if i want to backup downloaded files (CD ISO)?? i did this time cuz i thought i wont have to download it agin.

---

### Post by Jammanuser on 2008-12-13
> **Tribalnecktie said:**
> umm when i uninstall should i back up any of those files or not??

asks me if i want to backup downloaded files (CD ISO)?? i did this time cuz i thought i wont have to download it agin.

yeah...u can back it up! just make sure to put the ISO in the same location as the wubi installer, though, and it will use that to install Ubuntu, instead of downloading another one! ;)

Cheers! ):P

Jam Man

:guitar:

---

### Post by Tribalnecktie on 2008-12-13
mk, i did that. didnt work. here is the cod shown .

[     0.004000] Aperture beyon 4GB. Ignoring.
Loading please wait...


Busybox v1.102 (ubuntu 1:1.10.2-ubuntu6)Built in shell (ash)
Enter help for a list of built-in commands

(initramfs)_ <-- the underscore is flashing and is where it types when i hit a key.

---

### Post by jmszr on 2008-12-13
Edit: Sorry,answer not applicable.

---

### Post by Tribalnecktie on 2008-12-13
?? wat?

---

### Post by Jammanuser on 2008-12-13
> **Tribalnecktie said:**
> mk, i did that. didnt work. here is the cod shown .

[     0.004000] Aperture beyon 4GB. Ignoring.
Loading please wait...


Busybox v1.102 (ubuntu 1:1.10.2-ubuntu6)Built in shell (ash)
Enter help for a list of built-in commands

(initramfs)_ <-- the underscore is flashing and is where it types when i hit a key.

yep...sounds like a hardware problem to me! something is most likely not supported...try disconnecting any external devices u may have currently connected, and try it again...and see if that works! ;)

Cheers! ):P

-jamman

:guitar:

---

### Post by Tribalnecktie on 2008-12-13
hmm, as far as i can  think of i dont have any external devices. i do however have a Razer Deathadder mouse wich is a Gaming mouse. That may be the thing not supported. i will unplug that and try it. i do have another mouse so im ok. Thank you :) ill let you know if it works!

---

### Post by CyberPrime on 2008-12-13
I would recommend stripping the computer down to its box components (meaning remove any added RAM, any cards, etc.). Please tell us if you see anything saying "FAILURE" or "ERROR" in that scrolling text, and if possible provide pictures of said occurances. I used to have hardware problems (stuff not being recognized), but that was a long time ago and linux drivers have come a long way since then.

Also, please provide us with all the specifications you can get on your computer so we can make sure everything is compatible, and if anything isn't compatible.

HAND

---

### Post by ago on 2008-12-14
Uninstall and reinstall, if you are dropped to a command prompt, type the following commands and post here the output (watch the white space):

cat /proc/cmdline
cat /proc/mounts
cat /proc/partitions
grep err /casper.log
grep mount /casper.log

note that raid arrays and encrypted disks are not supported, nor are some external disks.

---

### Post by Tribalnecktie on 2008-12-14
i tried removing external drives, no luck. ive had ubuntu work on this box before so i know its not the ram or any other inside components. its the same as when i boughgt it, and it used to work till i uninstalled. ill try thos commands. thank you :)

---

### Post by Tribalnecktie on 2008-12-14
ok. well, as i was going to type the code in that you gave me. ubuntu started up and was fine. but this leads me to my next problem. i have a wireless network card. but ubuntu doenst know it. i read the thhelp and it said i need ndis gtk so i can use the windows driver or .inf or something. so i looked in the package manager thing and for some reason it wasnt in there. so idk what to do. im not close enough to the modem to plug it in otherwise i would download it from the web.what should i do?? also. i can acces my c:\\ drive from ubuntu like i used to be able to with an older version. Thank you for all the help :)

---

### Post by ago on 2008-12-15
You might need to enable extra repositories in the software sources, also make sure you are connected to the lan.

---

### Post by vanitor on 2008-12-18
hi, i've installed ubuntu throu wubi on my pc, it all works fine until i reboot, then i try to use all the options (try ubuntu without effecting ur ppc etc.) then it just beeps for a sec and does nothing, screen doesnt freeze, just no response from that action, the only button i can use it boot from first disc, i select that there is a quick ubuntu splash screen and it dumps me on the busy box intramfs screen, ubuntu is installed on my d: wich is an NTFS drive, winxp is stored on my c: (also a NTFS drive), sum1 plz i help, i used ubuntu on a mates laptop and i rlly like it.

---

### Post by vanitor on 2008-12-18
btw is it normal not to be able to select install ubuntu on the bootup menu?

---

### Post by vanitor on 2008-12-18
i have the same problem, tried all codes etc. and continuously install/reinstall it but it just drops me to the busybox initramfs prompt screen, bbtw the only option i can do is bot from drive, install ubuntu, try ubuntu, check for defects and test memory don't work, is this normal, (wubi is installed on my c drive wich is a NTFS drive, sum1 help plz, oh also i i have 2 drives c and d, windows is on my c: so are my ubuntu files.)

---

### Post by ago on 2008-12-19
If you end up in busybox please post the output of the commands above
Also make sure you are not running on incompatible hardware: [https://wiki.ubuntu.com/WubiGuide#Unsupported%20set-ups](https://wiki.ubuntu.com/WubiGuide#Unsupported%20set-ups)

---

