---
title: "[How-To] Install and run Ubuntu on a Dell XPS M1530"
date: 2008-09-06
forum: Dell Ubuntu Support (CLOSED)
---

### Post by BryanMarley on 2008-09-06
Hey Guys,

i thought it would be nice to help you guys out with installing ubuntu 8.04 on a XPS laptop.
When i first installed Ubuntu on my laptop i ran into some troubles. After doing some research on the big and scary web i found some topics that really helped me. So i thought why don't tell my fellow ubuntu/dell users how to do this.

2 major problems i ran into: Touch Pad, nVidia drivers.

Lets start with:

```
My Hardware 
```
Processor: **Intel Core2Duo 2.2 GHz**
Networking: **Marvel Yukon Mini Port (UTP) and Intel Pro/Set WiFi**
Graphics: **nVidia GeForce 8600M GTS 256 **
Memory: **4GB DDR2 667MHz**
HDD: **250GiB 5400 RPM (I thought it was Samsung:confused:)**

i think that sums it up.
```
Problem Number 1: Touch Pad
```
when i first installed ubuntu my touch pad was really doing some weird things, when i put my finger on it, it went crazy as h**l, it was uncontrollable. So i did some research and soon it was clear that it was a bug ever since bios version A08 came out.
I had A08 installed so thats obviously. The one and only solution is, is to change your GRUB bootloader.
U need to add one little line to the GRUB 'menu.lst' file:

Press ALT+F2 and type gnome-terminal.
The terminal shows up and u need to login as root.
so type 'sudo -s' and login as root. (i dont know if its really necessary but i did it anyways :))
when logged in type 'gedit /boot/grub/menu.lst'
then gedit opens and it shows u the menu.lst file.

find the part where the files sais:  

```
title		Ubuntu 8.04.1, kernel 2.6.24-21-generic
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=628413CB8413A099 loop=/ubuntu/disks/root.disk ro quiet splash
initrd		/boot/initrd.img-2.6.24-21-generic
```

u need to add 'i8042.nomux=1' to the kernel line.
so it'll say:

```
title		Ubuntu 8.04.1, kernel 2.6.24-21-generic
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=628413CB8413A099 loop=/ubuntu/disks/root.disk ro quiet splash i8042.nomux=1
initrd		/boot/initrd.img-2.6.24-21-generic
```

After this save the file and to make sure ur edit was saved, reopen the file by entering the same command as you did before.
If everything works, reboot and check in grub if the line was successfully edited, or you could always boot straight ahead and check the touch pad.
 
Let me know if this solution worked for you.

```
Problem Number 2: nVidia Driver installation
```
So thats that, now lets move on to installing nVidia.
When you first startup ubuntu the background looks a bit crappy, its not smooth at all, you can see the color rings in it if you know what i mean.
So thats gotta change, doesn't it?
Lets open the terminal again, if you don't have it opened up yet.
Press ALT+F2 and type 'gnome-terminal'.
When in the terminal type 'sudo apt-get update'. Now open up the hardware drivers screen (System -> Management -> Hardware Drivers. (login with your root password if asked) 
Then tick the little box that says activated. When activated it will start the download and when rebooted the drivers will work.

Let me know if this solution worked for you.

```
F.A.Q
```
If anyone has any questions, ill add them to this list and answer them here.
So let the questions and reactions come
i hope this information has been useful to you.

Good luck using ubuntu on your Dell XPS m1530.

Bryan

---

### Post by walahala on 2008-09-06
I have an XPS 1530 as well.  However, I am using Wubi Ubuntu, so you might not be able to help me out.  There is something wrong with my sound, where I have to crank it up to 75% to get a normal volume, and 100% not being that loud.  Did you run into any of this?  I have the default sound card: Sigma Tel High Definition Audio.  I have already asked this in a sound thread, but I was wondering if you ran into this because you have the same as I do.

---

### Post by Gausian on 2008-09-07
Actually Im using BIOS version A10 on a M1530, and the touchpad works fine.  As for your sound issue walahala, i have the same problem but haven't found a solution either.

---

### Post by accesshater on 2008-09-07
I have a xps m1530 for almost 3 months, i dont have any problems except one: [https://bugs.launchpad.net/dell/+bug/59695](https://bugs.launchpad.net/dell/+bug/59695)

but there is a fix for that:

Also check this page: [http://jesperdj.pbwiki.com/Ubuntu-on-the-Dell-XPS-M1530](http://jesperdj.pbwiki.com/Ubuntu-on-the-Dell-XPS-M1530)

Good luck

---

### Post by walahala on 2008-09-07
Accesshater, for your problem about the HD, what is defined as a "click"? My hard drive makes random very small noises that last only a split second.  Does this pertain to that problem, or is this just normal?  I know its normal for a HD to make noises, but I'm just paranoid, don't want to ruin my computer =]

---

### Post by accesshater on 2008-09-07
I dont know if you have that problem, but you can check this topic: [http://ubuntuforums.org/showpost.php?p=5031046&postcount=3](http://ubuntuforums.org/showpost.php?p=5031046&postcount=3)

There is a command that gets the value of the current cycle.. and if that value increases fast you have the problem to.

GL

---

### Post by BryanMarley on 2008-09-08
> **walahala said:**
> I have an XPS 1530 as well.  However, I am using Wubi Ubuntu, so you might not be able to help me out.  There is something wrong with my sound, where I have to crank it up to 75% to get a normal volume, and 100% not being that loud.  Did you run into any of this?  I have the default sound card: Sigma Tel High Definition Audio.  I have already asked this in a sound thread, but I was wondering if you ran into this because you have the same as I do.


i had that problem too, but i installed some kind of drivers that instsalled automatically when i opened a MP3.
Try that, start a MP3 open up the sound of ubuntu and crank up the audio volume of the music problem where i cant remember the name of.

---

### Post by BryanMarley on 2008-09-08
the hd click is the hard drive resetting its path, whenever this happens a little scratch appears on the disc, this can happen a few thousands of times. Whenever the HD does this, the scratches become worse, and eventually will kill your HD.

So, if you got this problem use a solution that was posted somewhere around here. It helped me too.

---

### Post by walahala on 2008-09-08
Well, my HD obviously makes sounds every once in a while, but I installed that program and it said everything was healthy, so I dont have to worry about anything right?

---

### Post by accesshater on 2008-09-09
> **walahala said:**
> Well, my HD obviously makes sounds every once in a while, but I installed that program and it said everything was healthy, so I dont have to worry about anything right?

```
sudo smartctl -a /dev/sda | grep Load_Cycle_Count
```

Just check with this command if the cycle load is increasing or not.

---

### Post by BryanMarley on 2008-09-09
> **accesshater said:**
> ```
sudo smartctl -a /dev/sda | grep Load_Cycle_Count
```

Just check with this command if the cycle load is increasing or not.

but is should be increasing but only not too fast right?

---

### Post by accesshater on 2008-09-09
> Look up how many Load_Cycle_Counts your harddrive can handle (most harddrives can handle 600.000 Load_Cycles but be sure to look it up). Calculate the average difference in Load_Cycle_Count per day. Now calculate what your Load_Cycle_Count will be in three years of harddrive use to determine whether you need to apply the ugly fix.


This is what the dude said in his post of the ugly fix ;)

---

### Post by BryanMarley on 2008-09-09
Owyeah, hahaha.
So its a problem then. Cant really hear the clicking in my machine, but i did that a while ago and i guess it worked. Not that im afraid of losing data or something. Cheers ):P

---

### Post by tcbopper on 2008-09-09
Sound issue...very faint/no loudness to sound

I have same issue....and haven't solved it yet.  When I boot up, it sounds fine....but once running, sound is faint with hardware volumne at the very highest setting (speaker ssoft touch button on far right) and software at highest setting as well.

---

### Post by tcbopper on 2008-09-09
M1530 BIOS

Where didd you get A10?  It looks like A09 was just released July 25.....anyone have success/issues w/ A09?

---

### Post by jespdj on 2008-09-10
> **accesshater said:**
> Also check this page: [http://jesperdj.pbwiki.com/Ubuntu-on-the-Dell-XPS-M1530](http://jesperdj.pbwiki.com/Ubuntu-on-the-Dell-XPS-M1530)
Hey, nice to see my page being quoted ;)
> **tcbopper said:**
> M1530 BIOS

Where didd you get A10?  It looks like A09 was just released July 25.....anyone have success/issues w/ A09?
I have version A09, I don't notice any differences with A08. I don't see any BIOS version A10 on the Dutch Dell website at this moment, the newest is A09 for the M1530.

---

### Post by BryanMarley on 2008-09-10
> **jespdj said:**
> Hey, nice to see my page being quoted ;)

I have version A09, I don't notice any differences with A08. I don't see any BIOS version A10 on the Dutch Dell website at this moment, the newest is A09 for the M1530.

To be honest, this topic was based on the info you put on that page hahaha
And er, Jespdj ur dutch too? me too, and yeah A09 is the newest for us so far.

---

### Post by accesshater on 2008-09-11
> **BryanMarley said:**
> To be honest, this topic was based on the info you put on that page hahaha
And er, Jespdj ur dutch too? me too, and yeah A09 is the newest for us so far.

Idd i upgraded to the latest bios with the help of the dell help center in windows. And the version of that bios was A09

And i am also dutch =p

---

### Post by jespdj on 2008-09-11
Yes, I'm Dutch too. :)

---

### Post by tcbopper on 2008-09-11
> **jespdj said:**
> Hey, nice to see my page being quoted ;)

I have version A09, I don't notice any differences with A08. I don't see any BIOS version A10 on the Dutch Dell website at this moment, the newest is A09 for the M1530.

Thanks for the advice and the link.  Nice page BTW.

Another quick ?.....how do we completely disable power manageement?

My 1530 is set up to dual boot.....Vista - Ubuntu 8-04.  It seems that if a walk away from the PC with UBUNTU running for some period of time, it hibernates/sleeps/suspends....and I am unable to recover the "desktop" with out a "hard" reboot.

I've changed all the preferences/admin settings I can find to no screen saver/no hibernate/no power managemet etc.  But I haven't been able to solve this.

---

### Post by BryanMarley on 2008-09-18
Well i did some research about the problem with low sound output, you need to install the drivers for mpeg 3,4 etc playback. Then restart and go to the sound options, at the most right in the window there's your 'front ouput', put this to 100%, now your sound output will greatly increase.

i hope every m1530 user is now satisfied with his or hers laptop.

Greetings from a sunny holland!:confused: (yeah, for once in a year its sunny here :P)

EDIT****

About the drivers you should install, as far as i could see there are 2 or 3 GStreamer packages that needed to be installed for MP3 MPeG2 (etc) playback, which were obviously not included into the installation of ubuntu.

So, go to synaptic and install whatever you miss from GStreamer, and i hope your sound problems will be gone!

---

### Post by accesshater on 2008-09-22
I am very satisfied, the only problem i have is a windows problem =p

The driver support for windows xp for this laptop is too poor to be true. (I need this for work/school)

---

### Post by jespdj on 2008-09-22
> **accesshater said:**
> The driver support for windows xp for this laptop is too poor to be true. (I need this for work/school)
That's because the hardware is too new for Windows XP. Is there a reason why you really need XP? If you need to run Windows, then why don't you use Vista?

---

### Post by BryanMarley on 2008-09-22
Just one comment about the 'why dont you use vista instead' thingy, i rather not use vista, i have found a few links on the web that tells us XPS M1530 users on how to run and use xp with all drivers, because there are indeed not much drivers out there.
The most M1330 drivers for xp work on our laptop, but ill come back to this post with some links which give you some pages with the support.

---

### Post by melenor on 2008-09-22
Alright i have a Dell Wireless 1505 Wireless-N Mini-card and i can't get my wireless to work i have, Any help would be very nice.

---

### Post by melenor on 2008-09-23
My nvidia drivers are acting up odd, I have the 8600M, the driver is 
nvidia "new" Driver
When i boot up my log on screen is really messed up, i had to boot to recovery mode to fix it by using Xfix which looks like it basically just reset the driver, because it is no longer enabled.

Would downloading the offical linux driver from nvidia's site work?

---

### Post by melenor on 2008-09-23
Sorry Duplicate post (See Above)

---

### Post by BryanMarley on 2008-09-23
So, you mean you updated the driver using the built-in update system?


And about the Wireless N Card, i got it too, but my network works out of the box. What wireless acces point do you have?
Cus i found some problems trying to connect to a linksys system.

---

### Post by melenor on 2008-09-23
Yes.

I don't know all i know is that i finally got my wireless working.

---

### Post by melenor on 2008-09-25
I have not yet found any way to fix the nvidia display driver problem any help would very much appreciated.

---

### Post by walahala on 2008-10-05
Do you think that 8.1 update will fix the ugly problem?  I would definitely like to go back to Linux, I'm just not skilled enough with ubuntu to feel comfortable fixing the problem.

---

### Post by jespdj on 2008-10-05
Which ugly problem are you talking about, walahala? The [harddisk click problem](https://bugs.launchpad.net/dell/+bug/59695)? I don't think it's going to be fixed in Ubuntu 8.10. Note that it's not really a bug in Ubuntu. And there's no reason to not use Ubuntu because of it, because there's a [workaround](http://ubuntuforums.org/showpost.php?p=3675960&postcount=26) for it.

When I use Windows Vista on my M1530, the harddisk also clicks sometimes. So the problem is not limited to Ubuntu.

---

### Post by melenor on 2008-10-05
I'm an okay skilled level, but i still cannot fix the problem with the graphic card, and i have tried multiple ways, i actually think that it is because the drivers that 8.04 uses do not support the 8600M which is different then the 8xxx series in the fact that it is mobile. Since 8.10 should be using the newer nvidia drivers, i am hoping that problem will be fixed.

EDIT: That clicking is the Hard disk i thought that, that was the disc drive. I am actually going to look into that workaround, anyone know of a workaround for vista? I get the clicks in there too.

---

### Post by BryanMarley on 2008-10-05
dunno why the nvidia thing didnt work for you, i got the same gfx card and for me it worked.
Did u really do what my post said?

---

### Post by melenor on 2008-10-05
what is your BIOS, and what nvidia driver did it download for you by default?

---

