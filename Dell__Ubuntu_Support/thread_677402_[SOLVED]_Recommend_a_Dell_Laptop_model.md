---
title: "[SOLVED] Recommend a Dell Laptop model?"
date: 2008-01-24
forum: Dell  Ubuntu Support
---

### Post by jmate24 on 2008-01-24
can anyone recommend a dell laptop in the $1,800-$2,800+ US range that is Most Compatible with Dual Booting Ubuntu/Kubuntu/Xubuntu?

---

### Post by Buffalo Soldier on 2008-01-24
i think your best bet would be Inspiron 1420n or XPS M1330n. If you're in the States, then you should probably get the one pre-loaded with Ubuntu 

- [http://linux.dell.com/wiki/index.php/Ubuntu_7.10](http://linux.dell.com/wiki/index.php/Ubuntu_7.10)

- [http://www.dell.com/ubuntu](http://www.dell.com/ubuntu)

---

### Post by Jeff311 on 2008-01-25
Sorry to hi-jack the thread but this is still on the front page and I don't see it warranting a new one.  Im in Canada and Dell doesn't offer laptops preloaded with Ubuntu.  I was thinking of getting a Vostro 1400 or 1500.  Would the regular [k]Ubuntu 7.10 have all the necessary drivers to work with the hardware?  If not, should I download the ISO of the Dell 7.10 instead?  Thanks.

Regards,
Jeff

EDIT: 1 more question.  Will upgrading to an nVidia 8400GS give better compatibility (with Compiz Fusion/KDE) over the Intel X3100

---

### Post by Roger E Critchlow Jr on 2008-01-25
I've been happy with a Latitude D630 running Gutsy 7.10 since last fall.

That said, you need the unfree new nvidia drivers, which are on the Ubuntu repos right next to the unfree nvidia drivers and the unfree legacy nvidia drivers, none of which are at all clear about exactly which cards they support.

And you may need to do the install in 'safe graphics' mode because the installer doesn't work well with the Nvidia card.

And you need to enable the backport repository to get the backported Alsa drivers that know how the snd-hda-intel works.


And I'm not sure if the bluetooth works or not.  I tried to pair with some headphones, but there was enough confusion in the instructions that I'm not sure why it didn't work.

And the suspend on lid close hasn't been working as well as it once was, there was an nvidia upgrade that made it work perfectly, but I think a subsequent kernel upgrade made it less a sure thing.

Anyway, all those qualifications aside, I like it enough that I doubled up my memory to 4G, tripled my disk size, and I'm now running the amd64 bit alpha release of Hardy Heron, 8.04 with alternate root partitions for Gutsy.  (I don't recommend the Hardy Heron alpha3 for the D630, I'm not sure how much is broken yet.)

I think the Nvidia has more horsepower for executing the fancy desktop graphics than the Intel integrated graphics.  

If you can get a Dell assembled ISO for the hardware you buy, it should be a painless experience.

-- rec --

---

### Post by jmate24 on 2008-01-26
this laptop is going to be for school, plus i don't want the college mainframe 'scanning' my laptop to see if i use windowz and to make sure that i am windowz 'compliant(loyal servant)'

---

### Post by Orion2000za on 2008-01-26
> **Jeff311 said:**
> Sorry to hi-jack the thread but this is still on the front page and I don't see it warranting a new one.  Im in Canada and Dell doesn't offer laptops preloaded with Ubuntu.  I was thinking of getting a Vostro 1400 or 1500.  Would the regular [k]Ubuntu 7.10 have all the necessary drivers to work with the hardware?  If not, should I download the ISO of the Dell 7.10 instead?  Thanks.

Regards,
Jeff

EDIT: 1 more question.  Will upgrading to an nVidia 8400GS give better compatibility (with Compiz Fusion/KDE) over the Intel X3100

Well I can not answer you extra query since I have the Vostro 1400 w "all-Intel" stuff. Here my thread on how I got all hardware including modem to work. Suspend/hibernate also works as good/bad as on other laptops:
[http://ubuntuforums.org/showthread.php?t=668235](http://ubuntuforums.org/showthread.php?t=668235)

Note that I run the "vanilla"-Kubuntu, not the Dell Ubuntu ISO. 

I find it a very nice laptop indeed!
Sinclair

---

### Post by aikiwolfie on 2008-01-26
I'd also recommend the M1330n.

---

### Post by irish8890 on 2008-01-26
I am running Gutsy on a Dell D630 for about a month.  I had to use the alternate install CD.  The only problems I have had are not being able to use wireless with WPA/WEP security & the sound is not very loud - even at the highest sound settings.

John

---

### Post by fragos on 2008-01-27
I love my Dell 1420n with the optional 9 cell battery.  It runs on battery for over 5 hours and I've had good luck with WiFi roaming.  It's a good choice for a college campus environment.

---

### Post by Vuddha on 2008-01-27
I've been using a second hand Dell Latitude D600. Ubuntu works perfectly with no hiccups whatsoever. Dual boot works fine, as well, if you're inclined. I bet you could get one cheap.

I use it for university, as well.

---

### Post by Twintop on 2008-01-28
I got a Dell XPS M1210 from Dell's refurb website back in September and have had NO problems at all with it with 7.10. It is tiny (12.1" screen, 1280x800) with a large hard drive and option Bluetooth that works out of the box with everything I've thrown at it (short of a Wiimote, because I haven't tried yet). It also has amazing battery life, pushing 6 hours if I dim the screen and tun at 1GHz (but lasts well over 4 hours with WiFi, Windows in a Virtual Machine, running at full speed, 1.83GHz, and no dimming of the screen).

After upgrading it to 4GB of RAM and adding the Bluetooth module, it cost me about $1600 (from the refurb site). It wasn't the most decked out machine in terms of processor speed, but it wouldn't be much more to upgrade it if it's in your price range.

---

### Post by nyqo on 2008-01-30
I just bought an Inspiron 1525 from Staples for $599 and it runs Gutsy beautifully. There were a few tweeks needed for wifi and the integrated mic, but everything else runs as well as I have ever seen (also running on a Toshiba lappy, two custom built desktops, and an iBook). I highly recommend checking this model out if you don't need the uber-power system.

---

### Post by jmate24 on 2008-02-02
well it has to be 64-bit because in 2009 my university will be switching from 32-bit to 64-bit.

---

### Post by fragos on 2008-02-02
> **jmate24 said:**
> well it has to be 64-bit because in 2009 my university will be switching from 32-bit to 64-bit.

Your university may be going to 64 bit on it's servers and PC's they own but that has no impact on whether your laptop is running a 32 or 64 bit OS.  Schools do sometimes have requirements for specific software and data formats but that still doesn't require you to run those applications on a 64bit OS.  It should be noted that running 64 bit can prevent you from easily running some application.  Flash browser plugin for one.  IMHO you are mis-interpeting what they said or their IT department is in very sad shape.

---

### Post by jmate24 on 2008-02-02
they emailed me that they were going with the switch because even though they use linux for their servers (which will be 64-bit too) they mostly run windows on their computers and that means that if i don't switch by 2009 i will be a sore loser. but i probably will keep my home 32-bit pc for a while.

---

### Post by fragos on 2008-02-02
When networking you don't need a 64 bit OS to network with a 64 bit OS.  That difference is transparent to both sides of the connection.  Therefore you don't have to switch to 64 bit to use the school network.  If they tell you that you must they are flat wrong and technically ignorant.

---

### Post by jmate24 on 2008-02-02
my main concern is that they will block all access from 32-bit computers/laptops on their student web and mail and their network. maybe i should call them? thanks anyways. Problem Solved!

---

### Post by Twintop on 2008-02-03
> **jmate24 said:**
> my main concern is that they will block all access from 32-bit computers/laptops on their student web and mail and their network. maybe i should call them? thanks anyways. Problem Solved!

They might be eliminating their own 32-bit computers so they don't have to maintain them, but I highly doubt that they will be blocking 32-bit systems outside of their control. If that's the case, this is the most uninformed and incompetent IT department I've ever heard of.

In short, you should have nothing to worry about.

---

### Post by shaggy999 on 2008-02-03
Speaking from a standpoint of a techie person that worked in technical support on many laptops, I highly recommend staying away from Dell's consumer notebooks and get a Latitude from their small business section (when checking out just use your exact full name as the business). The latitudes are far more reliable and sturdy. I'm typing right now on a Dell D810 + ATI x600 + Ubuntu 7.10 + compiz + encrypted hard drive.... everything works great. The only problem I've had is with the cpu frequency throttling. When I install w/ the live cd throttling works, if I install using the alternate cd (needed for encryption) it doesn't seem to work. I'm still poking around trying to fix that issue because I've gotten Ubuntu to get it to work before out of the box, so it seems to be a difference in detection of hardware on the live cd vs alternate cd.

Anyway, I should also mention that I'm able to boot off a usb key as well and even the volume buttons are supported out of the box. The only thing I don't know about are the internal network card (I use wireless, which works out of the box) because I've never plugged it into a lan and the modem. Ubuntu recognizes a software driver for it, but I've never bothered to install it.

---

### Post by jmate24 on 2008-02-04
thanks! looks like i may get a latitude. Problem Solved!:)

---

### Post by StefAndrew on 2008-02-05
If I might suggest as others have, the Vostro model is very good for dual booting.  I have nothing but good things to say about it.  I still have my pre-installed Windows Vista Business installed on it, but I have tried out several distros after shrinking down my Vista partition, and haven't had any problems whatsoever.  I'm finally back to Gutsy, and fully functional now too.  I got mine when the Intel processors were getting the better deal, but I maxxed everything out except the RAM(only 2gb) and the harddrive(160gb 5400rpm), and shipped it was only a couple dollars over $1500.  I'm very happy with my choice.

---

