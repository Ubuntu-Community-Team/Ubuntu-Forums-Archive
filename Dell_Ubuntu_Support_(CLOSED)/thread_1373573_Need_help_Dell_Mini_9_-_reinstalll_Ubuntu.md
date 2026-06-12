---
title: "Need help Dell Mini 9 - reinstalll Ubuntu???"
date: 2010-01-05
forum: Dell Ubuntu Support (CLOSED)
---

### Post by dragonfly5 on 2010-01-05
Greetings> Long story short. My wife's Dell Mini 9 has been running not too bad for the last 10 months or so - only real problem seemed to be an increasing difficulty in logging on to wireless networks. In the past month I have tried a software update and now we are having issues with passwords, administration, the USB port works intermittently and just general frustrations- although right now we have got the computer hooked up to the internet via a wired connection.. We want to like Ubuntu/Linux - but are more familiar with Windows. We are thinking a complete re-install of the latest software may work(right now running Hardy Heron - I think) - but have no idea of how best to go about it. We have the original disk - but no optical drive (and it seems the USB port is not working). I could download the latest version onto a thumbdrive and try that.
I am not familiar with a lot of the Ubuntu/Linex coding stuff - but did get my start with DOS - I guess I need to get some help here and am looking for the first steps/recommendations. I feel lilke a newbie - so be patient with me please.

Thanks in advance.

---

### Post by chrisamiller on 2010-01-05
Start here:
[http://www.ubuntumini.com/2009/11/installing-ubuntu-910-karmic-koala.html](http://www.ubuntumini.com/2009/11/installing-ubuntu-910-karmic-koala.html)

(follow the link in step 2 for instructions on creating an installer on a USB drive)

---

### Post by ahood on 2010-01-07
Hi dragonfly5,

Just for reference....

(a) I have successfully installed Ubuntu Netbook Remix 9.10 on Dell Mini 10v.

(b) I recommend downloading UNR 9.10 as described in Step 1 of the instructions provided in the link by chrisamiller above.

(c) For step 2, I successfully used the unetbootin utility. Unetbootin works in Ubuntu or Windows. In Ubuntu, unetbootin can be installed from the repository using Synaptic Package Manager or Add Remove.

(d) After installing unetbootin, use unetbootin to install the downloaded UNR 9.10 iso file onto the USB thumb drive.

(e) After successfully installing UNR 9.10 iso onto USB thumb drive, follow the remaining steps in the link above.

I recommend connecting the computer to the LAN using ethernet cable during installation.

After successfully installing UNR 9.10, I recommend installing the Broadcom STA wireless driver.

Cheers!

---

### Post by dragonfly5 on 2010-01-08
First off - thanks both for your replies. I've been busy with other things so have not been able to devote as much time to this as I would like.. 
Right now this is where I am and I have a couple of questions. I have downloaded onto a compatable USB drive the following files:
ubuntu-9.10 desktop-i386.iso.torrent   28 kb
ubuntu-9.10 netbook remix-i386.iso   697,156 kb
USB installer for ubuntu v0.2exe   629 kb

Now as I understand it I have to run the USB installer program to make the iso file into an img file so it can be read by the Dell mini on bootup. As the USB drive seems not to be working on the Mini while it is running (although I can plug in my wireless mouse and it works) - Can I run the exe file off the USB drive on my Windows system and have it convert the iso file into an img file?? This of course while not affecting my Windows laptop.
Alternately, I am trying to get an external optical drive so I can try reinstalling from the original Dell disk - which would likely re-install Hardy Heron. Here again, I am hoping that the USB port is recognized at the BIOS level as the computer first boots.
Is there a place to go just to get the img file direct?

Again, thanks for you help and patience. The good thing out of this is that I get more familiar with Ubuntu and Linux. My wife and I are really impressed by and appreciative of the philosophy and community surrounding Ubuntu.

---

### Post by snowpine on 2010-01-08
Hi Dragonfly, you can't simply copy the Ubuntu .iso file to a USB drive, you need to create a bootable device by following these instructions: [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

Ubuntu is no longer distributed as a .img, so any instructions you read referring to .img are outdated. :)

-(see also the helpful link back in post #2)-

---

### Post by dragonfly5 on 2010-01-11
Thanks all for the help!!
I finally mounted the img file and loaded the latest version of Ubuntu onto my wife's Mini9.
I even manually partitioned the drive (although detailed instructions on the option of creating a swap file would have been nice).

Only issue now is with additional driver for the wireless. I think it is downloaded and active but the auto detect does not seem to work. I think between my wife and myself we have to work on configuration and adding settings.

Thanks again to everyone here.

Michael

---

### Post by ahood on 2010-01-18
> **dragonfly5 said:**
> Thanks all for the help!!
Only issue now is with additional driver for the wireless. I think it is downloaded and active but the auto detect does not seem to work. I think between my wife and myself we have to work on configuration and adding settings.

Thanks again to everyone here.

Michael

Congratulations on installing the OS.

Yes, the wireless won't work automagically on the Dell Mini 9. The company that makes the wireless device on the machine does not release their drivers as opensource, which is unfortunate. Having drivers in the kernel is so much easier for end users IMHO. 

The easiest way to install the wireless driver is via

> System --> Administration --> Hardware drivers.

Before clicking and activating the Hardware drivers utility, be sure the Dell Mini 9 is connected to the Internet via ethernet cable.

I recommend installing the Broadcom STA wireless driver, at least, this worked for my Dell Mini 9.

If you don't have wireless after installing the driver, I recommend pressing the keys on the keyboard that toggles the wireless device. It could be that the wireless device is turned off initially.

I hope you had already found the solution. If not, I hope the above helps.

Regards,

---

### Post by dragonfly5 on 2010-01-18
Thanks agian for all the help.
After some false starts the wireless is now working.
Just a matter of a setting that we were not aware of at first.
Wireless works in the house now - next day or two we will visit our favorite coffee spot with wireless and see if it works on the road.

---

