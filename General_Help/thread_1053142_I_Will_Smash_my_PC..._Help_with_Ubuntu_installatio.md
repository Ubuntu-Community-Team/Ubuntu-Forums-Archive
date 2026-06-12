---
title: "I Will Smash my PC... Help with Ubuntu installation on Alienware M17"
date: 2009-01-28
forum: General Help
---

### Post by MG101 on 2009-01-28
I am new to Ubuntu. Give me any idea how to fix this, I will follow everything to the dot, no questions asked.

I tried Wubi and it seemed like it installed fine. Reboot. Loader comes up  asking me to pick Vista or Ubuntu. Great. Happy. Pick Ubuntu. &@$%^#*!!!

At first the damn thing tried to load, meaning the Orange progress bar was fine, finished filling up, then it went black, nothing but a blinking cursor. Did some Googling. Learned about CTRL ALT F1/F2 and saw the following:

blah blah... [OK]
blah blah... [OK]
X Server blah blah [FAILED]
X Server failed to start after 60 seconds

I should mention that in this same screen, all the way down I see:

ubuntu@ubuntu:-$ <---Literally, like that. my user name is not there. It says "ubuntu@ubuntu"

Ok, so I went around other threads here. Tried dpkg-reconfigure xserver-xorg. It asked me some questions, did the best I could, or just picked default answers and on the 4th question about the keyboard it said on the bottom something like: Possible counter configuration, backup at (some address), and then it gave me that ubuntu@ubuntu: -$ thing.

You can tell this is the first time I am trying Ubuntu. Previously (a week ago) I tried using the live CD. Same thing happen all the way to the "ABOSOLUTELY NO WARRANTIES" screen but I figured once I install it would work. It didn't.

Please help guys. I have another laptop where I used wubi and it worked, but that laptop is almost garbage, so why can't this work on my new one?

If it makes a difference I have:
Alienware M17
HD 3870 ATI Raedon x2
4GB RAM
250 GB
Vista Home Premium

Wubi installed with 30GB

I will be refreshing this page until the apocalypse if necessary. Thank you for any help here.

Oh, I almost forgot. Playing around I also got to some screen where it said something about "screens found but none have usable configuration" and "Fatal Error: No Screens Found" I don't remember how I got to that screen.

---

### Post by bgerlich on 2009-01-28
Post the file /var/log/Xorg.0.log on the forum - this will give more info why the graphical environment is failing to start.

---

### Post by MG101 on 2009-01-28
Thank you!

Where would I find this file? meaning, how do I get it to post it here? via Windows or what? Yeah, sorry, it must be aggravating helping people totally new to ubuntu...

(by the way I have Vista 64, so I guess the Ubuntu 64 too.)

---

### Post by vandorjw on 2009-01-28
1.) Does you computer connect to the internet?
--> An easy way to test would be turn on your computer, do the ctrl + alt + F1, log-in, and type 
```

ping www.google.com

```

I hope you do, it will make this much easier.

2) When you installed Ubuntu, what version did you install?
64 bit or 32 Bit?

64 Bit, type these commands.
```

wget https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/64bit/ati-driver-installer-8-12-x86.x86_64.run

```
This downloads the driver you need for your graphics card.

Try to install it using this
```

sudo /etc/init.d/gdm stop

```
This is to make sure that "X" (graphicall output) is turned off.
then
```

sudo sh ./ati-driver-installer-8-12-x86.x86_64.run

```

Follow the instructions. I cannot tell you what to do from here, because I don't have that card, and don't know what to expect. Hopefully it is just as easy as installing Nvidia cards.

For 32-bit system, apparently you use the same driver.

Best Wishes,

Report back if you get stuck.

Cheers - CC7

PS: [https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_cat812-inst.pdf](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_cat812-inst.pdf)

Scim through that.

---

### Post by vandorjw on 2009-01-28
```
 cat /var/log/Xorg.0.log 
```

Input this command after you logged in to TTY1 (using alt+ctr + F1)
That will print out the contents of that file to your screen.

I am not sure how you would post that on the forum though, other than typing it out on your laptop.
Actually, posting via windows is not such a bad idea.

Do you have a USB drive?

```
 cp /var/log/Xorg.0.log /media/USB ***(USB is wrong
```
cp is the command to copy from location1 to location2.
in this case, copying "/var/log/Xorg.0.log" to your USB, as soon as I figure out how to display the path.

Once that file is on USB, you can post it using windows.


Cheers - CC7

---

### Post by MG101 on 2009-01-28
Ok, I tried that but when I entered "ping www.google.com" it said:
ping: unknown host [www.google.com](www.google.com)

I went on and entered those commands but said

Resolving a248.e.akamai.net... failed: Name or service not known.
wget: unable to resolve host address 'a248.e.akamai.net'

Now what? I'm pumped! help me fix this, or tell me how to fix it. Whoever wins gets bragging rights.

---

### Post by vandorjw on 2009-01-28
> 

ubuntu@ubuntu:-$ <---Literally, like that. my user name is not there. It says "ubuntu@ubuntu"



what happends when you log-in and type 
```

users

```

---

### Post by MG101 on 2009-01-28
What command to check drives? I don't know any commands. If it helps I tried that log command and it gave me a brutal amount of info. I can't type all that even if I wanted to. The screen scrolls too fast. All I can see is something like:

(II) VESA(0): Configured Monitor Using Hsync value of 55.47 kHz
 similar stuff ending in         Using vrefresh value of 60.82 hz
Unable to estimate virtual size

(II) VESA(0): Not using built-in mode 1152x864 (hsync out of range)
"
"
"
all the way down to 320x200 (illegal horizontal timings)
VESA(0): No valid modes
UnloadModule "vesa"
UnloadModule "int10"

more stuff about unloading, and finally this:

(EE) Screen(s) found, but none have a usable configuration

Fatal server error:
no screens found
ubuntu@ubuntu: ~$

---

### Post by MG101 on 2009-01-28
> **cc7gir said:**
> what happends when you log-in and type 
```

users

```

Did it just now, it says:

ubuntu ubuntu ubuntu ubuntu ubuntu ubuntu

ubuntu@ubuntu: ~$

---

### Post by vandorjw on 2009-01-28
if typing in ping [www.google.com](www.google.com)
returned noting, then you are not connected to the internet with that machine.
which makes life slightly more difficult....
but, not impossible.
Do you have a USB key? Aka thumb-drive?
---------------------------------------------------------------------------------

if you do, download the driver I specified  [[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/64bit/ati-driver-installer-8-12-x86.x86_64.run]](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/64bit/ati-driver-installer-8-12-x86.x86_64.run]) and put it on the USB drive.

Do you have msn by any chance?
----------------------------------------------------------------------------------

When you log in and type pwd [pwd stands for present working directory], it should display something like, /home/** your-user-name**

I guess that it will return /home/ubuntu
(This will be important later)

---

### Post by MG101 on 2009-01-28
yeah, i just plugged it in. said something about write disk or something, like it detected it. Now what?

---

### Post by MG101 on 2009-01-28
> **cc7gir said:**
> if typing in ping [www.google.com](www.google.com)
returned noting, then you are not connected to the internet with that machine.
which makes life slightly more difficult....
but, not impossible.
Do you have a USB key? Aka thumb-drive?
---------------------------------------------------------------------------------

if you do, download the driver I specified  [[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/64bit/ati-driver-installer-8-12-x86.x86_64.run]](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/64bit/ati-driver-installer-8-12-x86.x86_64.run]) and put it on the USB drive.

Do you have msn by any chance?
----------------------------------------------------------------------------------

When you log in and type pwd [pwd stands for present working directory], it should display something like, /home/** your-user-name**

I guess that it will return /home/ubuntu
(This will be important later)

I put the file on my usb drive. it was like 77 MB. 

I also did the pwd thing. It did return "/home/ubuntu"

I also sent you a PM with my msn. (using pidgin from ubuntu)

---

### Post by vandorjw on 2009-01-28
OK this will now depend on you having a USB-KEY

1. Download the driver to it.
2. plug it in to your alien-ware computer.
3. log in and type
```
 cd /media 
```
then
```
 dir 
```
Copy down the exact name of your USB. [NAME-OF-USB]

```

cd /home
dir

```
write down the name of that shows up. [NAME-OF-HOME]

4. type
```
 
cd ~
cp /media/NAME-OF-USB/ati-driver-installer-8-12-x86.x86_64.run /home/NAME-OF-HOME

```

5.
```

cd /home/NAME-OF-HOME

```

6.
```

sudo /etc/init.d/gdm stop

```

```

sudo sh ./ati-driver-installer-8-12-x86.x86_64.run

```

7. Follow the instructions and let me know how it went.

Success - CC7

---

### Post by r+9 on 2009-01-28
Perhaps I'm late to the game, but the LiveCD won't get to the desktop environment right?

If that's the case wouldn't a little tweak to the boot line help?

---

### Post by MG101 on 2009-01-28
> **r+9 said:**
> Perhaps I'm late to the game, but the LiveCD won't get to the desktop environment right?

If that's the case wouldn't a little tweak to the boot line help?

by desktop environment do you mean, *see* the desktop, or at least get to it? then you are right, i just see a black screen.

And apparently the "dir" shows up nothing.

---

### Post by vandorjw on 2009-01-28
List of problems:
1)
[ 3418.375642] sd 8:0:0:0 [sdb] Assuming drive cacche: write through
--> USB doesn't automount and is not seen in /media or cat /etc/fstab
--> "mount" doesn't show the USB key either
--> no CDRom present in /media

2) Cannot connect to the internet. (Wireless)

3) No Graphical display.

4) No user has been created.

--------------------------------------------------------------
To get the graphical display up, my best bet is to install the proper drivers.

-- the driver can be downloaded using windows.
-- what is the correct procedure for mounting the windows partition?

As soon as a graphical display is running, things should get easier.

---

### Post by MG101 on 2009-01-28
OK, I went out and bought a ethernet cable. The Ping works now!!! I pinged google and got packets and time back, then I stopped with CTRL + C. Now I will try to install the driver via internet. Will post soon.

---

### Post by MG101 on 2009-01-28
I installed the driver you gave me. It just asked me to accept the license, whether I wanted a expert installation or the recommended one, I picked recommended. Then It asked Normal, or something else and in the end it just said "Installation Successful."

Restarted the PC and now I am at the same black screen with the "ABSOLUTELY NO WARRANTIES" and on the bottom "ubuntu@ubuntu: ~$

What else should I do?

Thank you.

*refresh, refresh, refresh,...*

By the way, I ran that command log.0. that shows you stuff about the Xorg. It still gave me that Screen(s) found, but none have a usable configuration

---

### Post by MG101 on 2009-01-28
By the way, the error is still the same I think:

ret = dm.run(*sys.argv[3:])
File "usr/bin/ubiquity-dm", line 113, in run
  raise XStartupError, "X server failed to start after 60 seconds"
_ _main_ _.XStartupError: X server failed to start after 60 seconds  [fail]

---

### Post by MG101 on 2009-01-29
Uninstalling Wubi...

(Refused to be unistalled. Had to system restore...)

...

Thanks for the help so far cc7gir.

---

### Post by CowzRule on 2009-01-29
Try this:

After selecting Ubuntu from the Vista loader, look at the top left of your screen and you'll see something like "Press Esc to show menu" with a timer. Do that, it will bring up the Grub menu. From that menu select the "Recovery" option. After it loads you'll get a menu with 4 choices. Select the one titled "Root". You'll get a prompt at the bottom of the screen. Do Not hit Ctrl D, just type your password and hit enter. That will give you a root shell. Now type "apt-get install envyng-core envyng-gtk". When it finishes type "envyng -t" and follow the instructions.
Envyng is a program that will automatically install the ATI drivers for you. I have an ATI card and that's what I had to do to get Ubuntu 8.10 to boot correctly.

---

### Post by MG101 on 2009-01-29
Thanks for the reply. Yesterday was a day full of disappointments. Made especially worse by Wubi not uninstalling itself. Anyway, now that my PC is working at full speed again I am ready to try again. I told cc7gir I will die before I give up on this damn thing. 

But first a couple of questions:

1. I don't want to use Wubi. My laptop has room for 2 hard drives and I have a new one, still wrapped. Would it be safer for my Windows side if we just attempt to make Ubuntu work in this new drive, like making it an Ubuntu only drive? I don't like partitions. If I am gonna kill the computer, at least I want to have my Windows 100% safe.

2. I should have more changes of having Ubuntu work if it has its own hard drive no?

3. If at the end it doesn't work, can I still use the hard drive and reformat it to its original state? Meaning, can I still use it on my Windows and still get my 100GB space from it?

4. I like the dual boot option Wubi gives. Can we have the same booting thing if we install Ubuntu on its own hard drive?

All this without touching my Windows hard drive?

One more thing. I am pretty sure cc7gir and I tried that envyng thing and it didn't work. We ran into huge problems trying to install it as it wasn't being recognized or found. Anyway, I haven't tried that ESC menu yet. Remember that I don't have Wubi anymore, so Ubuntu is gone, I would first need to install on my second hard drive to try again so please answer questions above.

Help me make this damn thing work.

---

### Post by tomeriker on 2009-01-29
Please don't smash your PC...

OK, the fix to your dilema is as simple as: ( drum roll please )
Install Ubuntu 8.04LTS. It will load and install the Proper ATI drivers just fine. Once you have it installed a window will pop up telling you that new restricted drivers are available. Just click the apply button and you will have it. 

I assume by what I read your trying to install 8.10. there is a problem with 8.10 and our computers. I don't know what or why but it absolutely will not install.

The only problem I had was getting my wireless to work and I posted a thread on that I think. If not e-mail me and I will walk you through it.

Actually I think the first kernel update should fix the wireless but I didn't have that option.

I hope this helps. 

Tom

---

### Post by MG101 on 2009-01-29
Tomeriker, 

Did you find this thread by reading the email I sent you to your yahoo or just surfing this forum? You are the only person I know that has a ATI HD 3870 x2 and Ubuntu running.

I will try what you tell me. However I want to install on a new hard drive (my second one) so I will need help with that too. But the questions on my previous post still stand before proceeding.

Also, can you tell me what is the difference between Ubuntu 8.10 and 8.04LTS? I have only used Ubuntu 8.10 and love it. I hope the differences are behind the scenes.

In any case, I have a 64-bit machine. Does the 8.04LTS come in 64-bit flavor? I hope it does. 

Any more information will be appreciated. Can't wait to try this option! (but for now, I am late for class, be back in a few hours)

*crossing fingers*

---

### Post by tomeriker on 2009-01-29
Yes I am responding from the e-mail you sent.

To help you better understand ubuntu I will try to explain how it works.

To the normal user there are very few differences between 8.04 and 8.10. 8.04LTS Stands for 8.04 Long Term Support. What that means is that it is very stable. 8.10 is still a work in progress. Thus the problem you are having. Perhaps 9.04 will work for us but 8.10 never will because we can't even install it.

You will be very happy with 8.04. 

I use the 32 bit version because there is no reason for me to use the 64 bit. Plus I believe there are more apps for 32. ( I may be wrong) The only thing 64 bit helps with is if you run many apps at the same time, but we have multi core processors to handle that.

The one thing you will notice about almost any linux version is the ease in which you can install. If you want to install ubuntu on its own drive, during the install just select the drive in the list. ( ubuntu will detect all drives, even usb drives )

another thing I have noticed is that ubuntu (linux) can see and manipulate windows but windows can"t even see the linux thats installed.

recently I had a windows xp machine that I was suppose to fix for a friend, but for the life of me I couldn't get the virus off the machine. ( I tried many ways and programs )I finally gave up and decided it wasn't fixable and I would format and reload windows. Then I thought, duh, I just put the 8.04 cd in and booted to the live cd and went to the file and deleted it. BAM , I waisted alot of time because I forgot I could do that.

Well this is getting long so good luck and you have my e-mail if you need anything else..

P.S. that M17 with compiz is really sweet!

---

### Post by MG101 on 2009-01-29
Bro, are you serious? Guess where I am typing this from? My M17 Alienware with Ubuntu (and 64-bit). What!?

Of course, I am running it from the Live CD, but with Ubuntu 8.10 the Live CD gave me the same errors! You have no idea how amazing this is!

The graphics are not the sharpest but I know it's because of the drivers that are not updated. Now I just need to install my second hd and install Ubuntu only. So, any volunteers out there? I just want a dedicated hd for Ubuntu only, and leave my Windows hd alone.

Thanks to everyone who gave me a hand and gave input. Especially cc7gir. This dude helped until passed 1:00 am. I leaned a lot along the way with him; stuff I would have learned in about 6 months on my own.

In any case, I am awaiting some instructions. I have an idea but I really don't want to mess this up; too good to be true.

Thanks for the solution tomeriker!

---

### Post by tomeriker on 2009-01-30
I will look at mine tonight after work and tell you how to do the additional HD. I too am going to use 2 drives but use the 2nd for dedicated storage.

talk to you later

---

### Post by tomeriker on 2009-01-31
Me again:

To install a second hard drive in the M17 is easy as taking out one screw and removing the access panel. If you look at the bottom of your M17, you will see two small panels on one side labeled 1 and 2. It is on the same side as the SD card slot and the Air Card slot. All you need to do is remove the retaining screew, remove the access panel and slide your new drive into the slot. Replace the panel and screw and boot the M17 so the bios can detect your new drive. once it is booted you can start the Ubuntu install.

If your wireless doesn't work it will be because you have the Intel 5300AGN wireless card. I will walk you through setting that up if need be.

Tom

---

### Post by husky55 on 2009-01-31
Please let me know how you guys are doing with the 2nd hd install.

I want to do the same thing to my laptop. Somehow 8.10 would hang on my gateway after install and reboot.

---

### Post by tomeriker on 2009-02-01
Husky;

If you already have 2 drives, it is as simple as clearing all data from the second drive (if you want to use the entire drive)and loading ubuntu on it. Again I recommend 8.04 because its stable. if you need to reorganize what is on the second drive and repartition it I highly recommend using Hirens Boot CD and using one of the partitioners in it. I prefer Acronis partition manager that is in the CD. It always works when others wont.

here is a link to get hirens...

[http://www.9down.com/Hiren-s-BootCD-9-5-23765/](http://www.9down.com/Hiren-s-BootCD-9-5-23765/)

---

### Post by husky55 on 2009-02-01
Thanks. I do have 2 hds. There is something wrong with my laptop because I can install ubuntu 8.10 but upon reboot it hangs after the moving ball and the screen went blank.

---

### Post by tomeriker on 2009-02-03
I don't know about your specific hardware, but I would try Ubuntu 8.04 and see what happens. I personally wouldn't want to start off with a buggie system if I can help it. 8.04 is a long term support version.

---

### Post by 2scott on 2009-02-05
Hello tomeriker,
I apologize for butting in to this thread, but I have a similar problem installing Ubuntu that I desperately hope that you can help me with.

I have a desktop with an AMD Sempron 3100+ chip (32 bit)

I have tried to install 8.10 unsuccessfully and none of the wubi or installation threads have helped.

I agree with your recommendation to try 8.04LTS so I downloaded it and used unetlogin to install it in the C drive.  After rebooting to Unetlogin, the Ubuntu "bouncing bar" appears but then a black screen appears with "busy box" and type 'help' for commands.  I transferred the iso image to the root directory with the other Ubuntu files and tried rebooting to Unetlogin - but the same thing happens.  Cntrl,Alt,F1 gives this message: 

cp:unable to openn 'root/var/log' no such file or directory
Target file system doesn't have /sbin/init

Any recommendations you may have would be most appreciated.  I really want to try this system!!

What I REALLY want to do is to load it onto my second hard drive and keep the OS separate.  bUT I will settle for getting it to run......

Thanks

---

### Post by MG101 on 2009-02-05
Hello all.

My Alienware is fully functioning. Thanks for all the help. Tomeriker, can you help me set up my wireless? I can only connect via wired connection via ethernet cable.

I am using EasyBCD to dual boot and my Vista MBR is completely safe and not overwritten by Grub. My sig tells the whole story. My system is pure awesomeness now.

Tomeriker, email me or help me through this forum if it is not too much trouble. Thank you all for all the help.

---

### Post by MG101 on 2009-02-05
Thank you

---

### Post by tomeriker on 2009-02-06
Hello,

First I need to know if you have the intel 5300AGN wireless card?

If so, I need you to go to "places/ computer/ filesystem/ lib/ firmware"

inside the firmware folder you should have a folder called "2.6.24-16-generic" and "2.6.24-23-generic". I need you to look in both folders and see if there is a file called "iwlwifi-5000-1.ucode". Plus, if there isn't are there any that start of with "iwlwifi"?

The 5000-1.ucode shouldn't be there yet, but I want to make sure.

Tom

---

### Post by MG101 on 2009-02-06
How do I find what wireless card I have?

---

### Post by tomeriker on 2009-02-06
When you ordered your M17 you should have seen an option to upgrade your wireless to the Intel 5300AGN. If you didn't upgrade then you have the default intel. All I need to know is did you upgrade?

Please let me know about what is in those folders also..

Tom

---

### Post by MG101 on 2009-02-06
Hi. I did not upgrade. No point in doing it I thought if you had a low-grade router and have no plans to upgrade it. I think the default M17 card is the "Internal Realtek Wireless LAN b/g Mini Card." I searched Google for it and that's what it said the default M17 comes with. 

Anyway, I only have the second folder (2.6.24-23-generic):

iwlwifi-3945.ucode
iwlwifi-3945-1.ucode
iwlwifi-4965.ucode
iwlwifi-4965-1.ucode
iwlwifi-5000-1.ucode

---

### Post by tomeriker on 2009-02-06
Ok, I was hoping you had the intel 5300AGN because that is what I have. I have never setup the realtek so I did some searching and found this: [http://forums.msiwind.net/debian/rtl8187se-drivers-for-ubuntu-and-deb-packages-t4954.html](http://forums.msiwind.net/debian/rtl8187se-drivers-for-ubuntu-and-deb-packages-t4954.html)


read the whole thing before you start and download the newest for your kernel. About halfway down the page is the last download for 8.04, that is the one you want. " update: 08.12.2008"

Ooops. here is his newest drivers: [http://boskastrona.ovh.org/index_en.html](http://boskastrona.ovh.org/index_en.html)

since its a deb package it should install right from your desktop by double clicking.. "I think"

If not he has the instructions on his webpage.

Good luck and tell me how it goes.

Tom

---

### Post by MG101 on 2009-02-06
No dude. Those are for MSI Wind or something. I tried anyway but even the architecture is wrong as it gives me an i836 error wrong architecture or something. Any other ideas? Thanks

---

### Post by MG101 on 2009-02-07
OK, apparently those drivers will work (my card is realtek RTL8187SE) but those drivers are NOT for AMD64 architecture. It gives me that error. I searched around but no one seems to have them for 64-bit.

I opened the .deb file that goes with my version of Ubuntu and saw its components. In a file called control it says the architecture. Would it be harmless for me to just change this to AMD64 so Ubuntu thinks it is for 64bit instead of 32?

---

### Post by tomeriker on 2009-02-07
You can try to change the switch to 64 but I really doubt it will work. I have been looking also for a 64 bit version but haven't seen any.

You may have to install the 32 bit version of Ubuntu to get your wireless to work.

Option 2 would be to buy a usb wireless device. until I got my wireless to work I used a Belkin usb wireless device.

I know your processor is 64 bit but it will run all 32 bit software and hardware perfectly; For normal home pc users there is no advantage to using the 64 bit Ubuntu and there are advantages for using the 32. One advantage in using 32 bit is just this problem. All software comes out in 32 before 64, and some software never gets a 64 bit version.

I know its a pain in the butt, but I would recommend you reinstall using the 32 bit Ubuntu.

Before you reinstall give me a day to talk to the guys over at Linux forums and get some good tech support from them. there may be a work around that I don't know of..

Tom

---

### Post by MG101 on 2009-02-07
Hi, thanks for the reply.

I don't know about re-installing, and a 32 bit version tom.. I rather buy a usb card, but would much rather have this running.. he he.

Anyway, I tried to force install the 32 bit version. It gave me plenty of warnings and in the end it didn't work. Anyway to uninstall this? I wouldn't know where to look for it to remove it. I don't want to have this driver force-installed and not even have it work. Any ideas how to remove it or check that it isn't installed?

I am also sending out emails, especially this one guy that compiled the drivers for the Realtek RTL8187SE and updates them with every kernel. This guy's drivers however are only 32-bit.

Can someone perhaps recompile them to 64 bit? (I know, it's along shot)

---

### Post by tomeriker on 2009-02-07
I posted over at linux forums asking them if there was a way to convert the 32 to 64 and I am waiting on a reply. Cross your fingers.

To check to see if the driver module is loaded just open a terminal and type " lsmod " without the quotes. that will list all modules loaded.

If it didn't work it shouldn't be loaded, but if it is let me know and I will lookup the code to kill it.

Is there a reason you need 64 bit Ubuntu? Just curious.:D

---

### Post by MG101 on 2009-02-07
No reason at all, other than stubbornness and trying to keep things homogeneous as much as I can... yea.. pretty lame.

I don't see anything important on that list. But maybe because I went and deleted the files that other driver I tried to "force install" installed...

I hope I find a solution. Perhaps someone can recompile the .deb I need for 64 bit?

---

### Post by tomeriker on 2009-02-07
ok, good news..

After searching and reading way too many articles I found that the realtek driver can be loaded using " ndiswrapper ". you need to install it and the graphical frontend. download the rtl8187se driver from alienware (use the vista 64 bit). Once ndiswrapper and frontend are installed just run it and use the vista 64 driver. I believe its an .inf file you need.

go here to read.  
 [http://blog.alexrybicki.com/2008/04/ubuntu-804-hardy-heron-is-here.html](http://blog.alexrybicki.com/2008/04/ubuntu-804-hardy-heron-is-here.html)

scroll down to "getting the wifi to work"

I hope this does the trick. I know how you feel wanting everthing to work.
I still can't get the internal mic to work on mine.

---

### Post by MG101 on 2009-02-07
Thanks dude. HOWEVER, I can download an .exe file only for the driver.. I need the .inf. Where is that?

---

### Post by tomeriker on 2009-02-07
I'm sorry,

I used wine to install the .exe file into the wine directory and found the file. I had to send it to your E-mail account. I sent the whole driver to you . Just put it in a folder called " Driver". That is what the folder was called.

The .inf is in there for ndiswrapper but I don't know if it needs the others.

Good luck and tell me how it goes..

---

### Post by MG101 on 2009-02-07
OK. When I use that .inf file it seems to be OK. It says hardware present: yes, and all. but it doesn't connect. anything I could try? look at the screen shot attached.

---

### Post by MG101 on 2009-02-07
OK, here is my dilemma so far:

Option using windows drivers: Used that program for windows drivers. Hardware is detected but no connection yet.

Option using deb driver for my ubuntu: Should work except drivers available are for 32-bit architecture and I have 64-bit architecture. Would need drivers recompiled for 64-bit

Option installing Ubuntu 32-bit instead: Erase all my settings in current ubuntu installation and No guarantees that the deb drivers for my card will work. Assuming they did, what is the main differences between Ubuntu 64 bit and 32 bit.

I guess I wouldn't mind installing Ubuntu 32 bit if there are really no differences in speed, etc., but what if it doesn't work anyway?? Also, how would I install the new Ubuntu? Keep in mind my Ubuntu now is on a second hard drive, and I use EasyBCD to dual boot... The easiest way might still be option 1 or option 2.

Help please!!!

---

### Post by tomeriker on 2009-02-07
I couldn't see the screen shot clearly. I would try shutting your security off in the router to test and see if you can connect. Also in the wireless properties you should select roaming and make sure DHCP is enabled. I am at work now so it will be later tonight before I can get to my computer to walk you through this.  Great sign that it is working this much.. I am positive we can get it working now.\\:D/

---

### Post by MG101 on 2009-02-07
I think you can just click twice on the picture and it pops out in another window full size.

The thing I notice is that it doesn't detect any wireless signals. I am losing my mind here,,,,,,,

---

### Post by MG101 on 2009-02-07
I uninstalled Ubuntu 64 bit and tried 32 bit. It doesn't work... sh!t...

Now I can't even see the wireless option wtf..

I also tried that option BS with windows drivers and it didn't work.

---

### Post by tomeriker on 2009-02-08
I sent you the new files to your e-mail. Sorry to hear you went to all the trouble to install 32 bit and it didn't work. Your setup is alien to me. no pun intended.

in your correspondence you said you are not using GRUB boot loader?
is that correct?

I think I know the problem now. All the drivers are for the rtl8187. The rtl8187se is completely different. Also the ndis wrapper uses windows xp drivers and the drivers from alienware are vista. SO, Here is a link where you can get the winxp driver to use in mdiswrapper.

[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=40&PFid=40&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8187SE](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=40&PFid=40&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8187SE)

This also has a 64 bit driver in it too. I am now at the end of my knowhow.

If I come accross anything I will post here. Sorry I couldn't be more help. I know how it feels to be so close yet so far.

Good luck and keep me posted.

---

### Post by tomeriker on 2009-02-08
I have more info that will help. please read this and you will figure it out... I feel so stupid right now.. but keep the 32 bit ubuntu.

[https://answers.launchpad.net/ubuntu/+question/57204](https://answers.launchpad.net/ubuntu/+question/57204)

---

### Post by MG101 on 2009-02-08
Hello,

Bro, thanks for all the help. 

Well, I actually tried both posts of yours above. No luck. After fighting with my 32-bit Ubuntu I managed to kill all connections, including the Wired one... Anyway, the list of changes I made was far too long so I erased it again and installed Ubuntu 64-bit, again.

At least that one connects via ethernet. It's so weird that even the solution for the 32-bit and the deb packages didn't work. The thing is that during the whole process my Ubuntu never tells me I have a RTL8187SE. I found that from Windows device manager. The problem is that the main solution everyone follows assumes that Ubuntu does recognize it.

One last thing I am willing to try is using the network driver that Alienware itself provides with ndiswrapper. Perhaps its something special. Before I was using a driver directly from Realtek. Do you want to give it this final try? I would need the .inf file from you since Alienware gives you an .exe to download. Can you download the .exe I uploaded to this site below and send me the .inf please?

[Quote=Alienware]
For Models:	 Realtek RTL8187SE 802.11g (M17)
M17 Realtek Wireless driver for Windows Vista 32 and 64. 
File Size:	9.83 MB
File Date:	N/A
Platform(s):	Windows Vista, Windows Vista x64
[/quote]

**[http://www.2shared.com/file/4829479/5a8030c/M17_WLAN_Realtek_Vista_x86_x64_690708182008.html](http://www.2shared.com/file/4829479/5a8030c/M17_WLAN_Realtek_Vista_x86_x64_690708182008.html)**
Way towards the end, at the right it says "Save file to PC: click here" in a tiny font.

Here you go buddy, last shot at getting this to work!

By the way, I didn't get any new email from you. I think the email services are blocking those files or something. Maybe you can upload them like I uploaded this file to a sharing site compressed and post the link here? Thank you!

If this final attempt doesn't work I am gonna go out and get a USB wireless card.  Perhaps you can help me find a list or give me an idea of a card I can plug into my USB and will work out of the Box with Ubuntu 8.04 and 64-bits?

---

### Post by MG101 on 2009-02-08
I just read wikipedia info on ndiswrapper. Maybe during yesterday's confusion and aggravation I didn't install the windows xp drivers for the card and instead only used vista. 

I will try again with ndiswrapper and the Windows XP drivers. I should use the 64-bit though right? Does it require a restart afterwards?

---

### Post by MG101 on 2009-02-09
No luck. It definitely doesn't work. Anyone know a usb wireless card that will work out of the box with Ubuntu 8.04 and 64-bit architecture?

Thank you!

PS. Ubuntu still rocks without wireless anyway... can't get enough of it!

---

### Post by MG101 on 2009-02-14
**Guys I fixed my wireless!!!**

Now I need 1 tiny thing. Help me do this (so that I won't have to manipulate the thing each time at startup):

These are the instructions I found:

We'll have to copy the driver files in the Linux kernel so that the driver works at startup without manipulation:
```

cd ieee80211

```
(When I try this in terminal it says bash: cd: ieee80211: no such file or directory)

Copy the .ko directory in the kernel
```

sudo cp *. ko / lib / modules / `uname-r` / kernel / drivers / net / wireless

cd..

cd rtl8185

```

Copy the .ko directory in the kernel:
```

sudo cp *. ko / lib / modules / `uname-r` / kernel / drivers / net / wireless

```

Add the drivers in the kernel:
```

cd / lib / modules / `uname-r` / kernel / drivers / net / wireless

sudo depmod -a sudo depmod-a 

sudo modprobe r8180

```

So how do I do this? I don't see anything with 'uname-r' I am including the original website where I got the fix from. (it is in French, I used Google translator)

[http://translate.google.com/translate?u=http://julienpecqueur.com/tutoriaux/install_driverwifi.html&sl=fr&tl=en&hl=EN&ie=UTF-8](http://translate.google.com/translate?u=http://julienpecqueur.com/tutoriaux/install_driverwifi.html&sl=fr&tl=en&hl=EN&ie=UTF-8)

The part where I am stuck is "Adding driver in kernel"

Thanks guys! Almost there!

---

### Post by chielectric on 2009-04-27
So were you successful in the Ubuntu installation on the M17? Any more news on this? I have an M17 myself and was considering getting rid of vista entirely in favor of Ubuntu.

---

### Post by sxe4ever on 2009-06-09
I have Ubuntu successfully installed on my M17 on the second hard drive, I'm just having a problem getting a video driver to work.  To save everyone a lot of headaches, please make sure and backup your xorg.conf before making any changes!!!!  Anyways, can anyone help out with this??? I tried to install the driver that was listed on the first page however it said that it wasn't supported with my version, here's the exact message it gave > Error: ./default_policy.sh does not support version
default:v2:i686:lib::none:2.6.28-11-generic.  

I also tried installing the drivers using envyng.  It said that it was downloaded successfully, but when I rebooted it just gave me the terminal.  Any ideas????

---

### Post by Yellow Pasque on 2009-06-09
[http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide)

---

### Post by sxe4ever on 2009-06-12
> **Temüjin said:**
> [http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide)

Thanks for the assistance, however this caused the screen to just completely black out once I got it installed.  Luckily I just got it back to a working state however :)

---

