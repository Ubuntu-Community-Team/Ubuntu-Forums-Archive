---
title: "Remove &quot;AMD testing use only&quot; script"
date: 2012-10-25
forum: Gaming &amp; Leisure
---

### Post by homerhomer on 2012-10-25
How I really "PAY" for my AMD video card on Linux. 

If you are using the latest beta then you'll notice a "AMD test use only" watermark. 

This little bash script should fix that  :D

Run as root and you should be good

As always, use at your own risk

---

### Post by donovanz on 2012-10-26
i love u so much!!!!!!!!!!!! kkkkkkkkkk ty dude

---

### Post by rockinkaj on 2012-10-26
works greak thanx

---

### Post by AARyuzakiKK on 2012-10-28
Thanks!!
It worked fine with Ubuntu 12.10 and driver AMD 12.11 beta:popcorn:

---

### Post by hexag on 2012-10-29
careful guys, probably my fault which did it, but this script totalled my install. all good now though :) got stuck on boot & rummaging round xorg, etc, resulted in nowt.

**USE AT OWN RISK!***

---

### Post by revnoah on 2012-11-01
Worked perfectly for me. Thanks!

---

### Post by aleshashvaika on 2012-11-04
Worked fine on Ubuntu 12.10 x64 with 12.11 beta drivers. Thanks a lot!

---

### Post by lukebolger on 2012-11-04
Hi guys, I have switched from windows 8 (the HORROR!) to Ubuntu 12.10 today, I must say it rocks, but I am a total noob now, so Please explain how I can run this as root? I selected run as exe in properties but there is no option to run as root????

---

### Post by MG&amp;TL on 2012-11-04
> **lukebolger said:**
> Hi guys, I have switched from windows 8 (the HORROR!) to Ubuntu 12.10 today, I must say it rocks, but I am a total noob now, so Please explain how I can run this as root? I selected run as exe in properties but there is no option to run as root????

Welcome! Great community here, I'm sure you'll love it. Here we're going to need a little shell (command-line) use, as this is a non-standard use case.

First backup stuff. System-changing scripts can and do break. While linux breaks really nicely and informatively, it still breaks. :)

Remember where you've downloaded the script to. I.e if it's in Downloads/remove_amd_message.sh, remember that.

Open a terminal (Ctrl-Alt-T), it's a little purple box. Then type:

```
sudo Downloads/remove_amd_message.sh
```

replacing the path with what you remembered. 

Enter your password when prompted (you can't see it, just type and press return), then you should be okay to go. :)

For more information, check here: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by lukebolger on 2012-11-04
Thanks for your reply man!

I tried what you said, when it asks for the password, it doesn't let me type it! The keyboard works fine when typing in the command, but when the password is requested I cant type it!

---

### Post by MG&amp;TL on 2012-11-04
> **lukebolger said:**
> Thanks for your reply man!

I tried what you said, when it asks for the password, it doesn't let me type it! The keyboard works fine when typing in the command, but when the password is requested I cant type it!

That's what I meant by "You can't see it." Just type and press return and it will work. Confusing, right? :)

---

### Post by lukebolger on 2012-11-04
Sorted it now THANKS!

---

### Post by coed on 2012-11-15
Top Man!

Just wanted to say thanks for this, worked a treat! :)

Used it on a new system I was building, using Mint 14 and the pre-beta version was having issues so decided to try the Beta version which worked a treat, *except* the little logo down in the bottom - ran the script and booyar!

:guitar:

---

### Post by midfingr on 2012-11-22
Excellent! Thank you very much. :)

---

### Post by mentorious on 2012-11-23
There's simpler method. You only need to "sign" your drivers:

```
sudo gedit /etc/ati/signature
```

(or other editor, e.g. kate in kubuntu)

Delete "UNSIGNED" and paste this code:

```
9777c589791007f4aeef06c922ad54a2:ae59f5b9572136d99fdd36f0109d358fa643f2bd4a2644d9efbb4fe91a9f6590a145:f612f0b01f2565cd9bd834f8119b309bae11a1ed4a2661c49fdf3fad11986cc4f641f1ba1f2265909a8e34ff1699309bf211a7eb4d7662cd9f8e3faf14986d92f646f1bc

```

Reboot and everything works :)

---

### Post by sk1887 on 2012-11-25
> **mentorious said:**
> There's simpler method. You only need to "sign" your drivers:

```
sudo gedit /etc/ati/signature
```(or other editor, e.g. kate in kubuntu)

Delete "UNSIGNED" and paste this code:

```
9777c589791007f4aeef06c922ad54a2:ae59f5b9572136d99fdd36f0109d358fa643f2bd4a2644d9efbb4fe91a9f6590a145:f612f0b01f2565cd9bd834f8119b309bae11a1ed4a2661c49fdf3fad11986cc4f641f1ba1f2265909a8e34ff1699309bf211a7eb4d7662cd9f8e3faf14986d92f646f1bc

```Reboot and everything works :)
lol it works
On mint 14 I have a huge notification bar on the bottom where the AMD watermark was :P

---

### Post by MeteorBlume on 2012-11-25
Used the script, now when Ubuntu boots, it stucks at the Ubuntu-Loading screen. I dont even get to the login anymore.........

---

### Post by timetopat on 2012-11-25
Thanks for this.  I had this problem and luckily I found your script.

---

### Post by MilesRdz on 2012-11-25
I used the method *mentorious* mentioned and it works. :)

---

### Post by Pozihead on 2012-11-29
Thanks works a treat

---

### Post by Ste_JDM on 2012-12-03
Ty!

---

### Post by Teraspes on 2012-12-10
Thanks!

For those of you who don't want to create an account and/or login to access the file, I made it available here: [http://paste.ubuntu.com/1424555/](http://paste.ubuntu.com/1424555/)

---

### Post by tjeremiah on 2012-12-14
> **mentorious said:**
> There's simpler method. You only need to "sign" your drivers:

```
sudo gedit /etc/ati/signature
```

(or other editor, e.g. kate in kubuntu)

Delete "UNSIGNED" and paste this code:

```
9777c589791007f4aeef06c922ad54a2:ae59f5b9572136d99fdd36f0109d358fa643f2bd4a2644d9efbb4fe91a9f6590a145:f612f0b01f2565cd9bd834f8119b309bae11a1ed4a2661c49fdf3fad11986cc4f641f1ba1f2265909a8e34ff1699309bf211a7eb4d7662cd9f8e3faf14986d92f646f1bc

```

Reboot and everything works :)

Thanks! AMD should have an option to remove it in their manager.

---

### Post by eloinischith on 2013-01-05
Thank you so much :) im new to Linux this just gave me all the reason to permanently  say good buy to  windows :)

---

### Post by starfyredragon on 2013-01-29
Any suggestions on how to remove the script? It was great and all, don't get me wrong, it was wonderful to remove that watermark. But now, as I'm looking up updating my drivers, while attempting the prerequisite uninstall of old drivers, the uninstaller says the driver has been altered. Any suggestions?

---

### Post by starfyredragon on 2013-01-29
Addendum: Forcing the uninstall of the catalyst drivers worked fine for me, no big issues other than a warning when I restarted that amounted to nothing.

---

### Post by psychok9 on 2013-02-10
Thanks a lot homerhomer!

Uninstall from /usr/share/ati? I've installed 13.2 beta 3 generating package .deb, can I encounter the same problem?
Maybe forcing a reinstall (sudo dpkg -i amd*.deb for me) and, after it, can we uninstall?

---

### Post by auxilium on 2013-02-11
Thanks homerhomer

that saves the day. the script works perfect!!!

---

### Post by Pozihead on 2013-03-03
Works great thanks:P

---

### Post by Ximaceo on 2013-03-03
> **mentorious said:**
> There's simpler method. You only need to "sign" your drivers:

```
sudo gedit /etc/ati/signature
```

(or other editor, e.g. kate in kubuntu)

Delete "UNSIGNED" and paste this code:

```
9777c589791007f4aeef06c922ad54a2:ae59f5b9572136d99fdd36f0109d358fa643f2bd4a2644d9efbb4fe91a9f6590a145:f612f0b01f2565cd9bd834f8119b309bae11a1ed4a2661c49fdf3fad11986cc4f641f1ba1f2265909a8e34ff1699309bf211a7eb4d7662cd9f8e3faf14986d92f646f1bc

```

Reboot and everything works :)

Easy, thank you :P

---

### Post by ubunet on 2013-03-03
> **mentorious said:**
> There's simpler method. You only need to "sign" your drivers:

```
sudo gedit /etc/ati/signature
```

(or other editor, e.g. kate in kubuntu)

Delete "UNSIGNED" and paste this code:

```
9777c589791007f4aeef06c922ad54a2:ae59f5b9572136d99fdd36f0109d358fa643f2bd4a2644d9efbb4fe91a9f6590a145:f612f0b01f2565cd9bd834f8119b309bae11a1ed4a2661c49fdf3fad11986cc4f641f1ba1f2265909a8e34ff1699309bf211a7eb4d7662cd9f8e3faf14986d92f646f1bc

```

Reboot and everything works :)

+1! Works for me.

Netbook Acer One 722/**Xubuntu 12.10 x32**/Radeon HD 6290/AMD Catalyst 13.1

---

### Post by AbtZ on 2013-03-05
> **mentorious said:**
> There's simpler method. You only need to "sign" your drivers:

```
sudo gedit /etc/ati/signature
```

(or other editor, e.g. kate in kubuntu)

Delete "UNSIGNED" and paste this code:

```
9777c589791007f4aeef06c922ad54a2:ae59f5b9572136d99fdd36f0109d358fa643f2bd4a2644d9efbb4fe91a9f6590a145:f612f0b01f2565cd9bd834f8119b309bae11a1ed4a2661c49fdf3fad11986cc4f641f1ba1f2265909a8e34ff1699309bf211a7eb4d7662cd9f8e3faf14986d92f646f1bc

```

Reboot and everything works :)


Here's how to do the safer signature replacer with a oneliner:
```
sed -i "s/^UNSIGNED/9777c589791007f4aeef06c922ad54a2:ae59f5b9572136d99fdd36f0109d358fa643f2bd4a2644d9efbb4fe91a9f6590a145:f612f0b01f2565cd9bd834f8119b309bae11a1ed4a2661c49fdf3fad11986cc4f641f1ba1f2265909a8e34ff1699309bf211a7eb4d7662cd9f8e3faf14986d92f646f1bc/g" /etc/ati/signature
```

I'll also attach a more advanced script that guides you through the process. It essentially does the same thing.

---

### Post by Looking4Llamas on 2013-03-16
Thanks So Much It WORKED!!! :KS

---

### Post by stevetsc on 2013-04-19
> **AbtZ said:**
> Here's how to do the safer signature replacer with a oneliner:
```
sed -i "s/^UNSIGNED/9777c589791007f4aeef06c922ad54a2:ae59f5b9572136d99fdd36f0109d358fa643f2bd4a2644d9efbb4fe91a9f6590a145:f612f0b01f2565cd9bd834f8119b309bae11a1ed4a2661c49fdf3fad11986cc4f641f1ba1f2265909a8e34ff1699309bf211a7eb4d7662cd9f8e3faf14986d92f646f1bc/g" /etc/ati/signature
```

I'll also attach a more advanced script that guides you through the process. It essentially does the same thing.

Thanks!  used this command with 13.04B2 (AMD64) and AMD13.3B3 and works great!  Anyone else wanting to use Raring and get decent frame rates this seems to be the best way to go.

---

### Post by josh11 on 2013-05-02
Does this work in 13.04? I tried to perform this, and got "Downloads/script.sh" is an unknown command.

---

### Post by mentorious on 2013-05-03
Are you sure that command was correct?

```
cd ~/Download
```

and then

```
chmod a+x script.sh && ./script.sh
```

---

### Post by techouse on 2014-03-26
This script worked perfectly for me.  All other methods I tried, including an alternative script from Kano [http://phoronix.com/forums/showthread.php?19875-Unsupported-Hardware-watermark]("http://phoronix.com/forums/showthread.php?19875-Unsupported-Hardware-watermark"), sinature signing ... etc failed.  The reason I really posted this however is because the script also fixed another really annoying problem for me.  Everytime I rebooted, my graphics card would revert to some default settings, including a ridiculously low refresh rate of 24 Hz!  My screen would actually flicker, which I'd never even seen before with an LCD.  This meant after every reboot, I'd have to go to the catalyst control center and change my settings.  Annoying.  This problem is now gone along with the watermark.  Thanks HomerHomer!

Ubuntu 13.10 64-bit
ATI FirePro V4800 (FireGL) Graphics Adapter
fglrx-updates 2:13.101-0ubuntu3 (Driver Packaging Version 13.101-130523a-157671E-ATI)
fglrx-amdcccle-updates 2:13.101-0ubuntu3 (Catalyst Control Center Version 2.18)
OpenGL Version 4.2.12337 Compatibility Profile Context FireGL 13.101

---

