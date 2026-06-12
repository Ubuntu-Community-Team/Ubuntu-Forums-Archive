---
title: "this may sound dumb"
date: 2008-12-22
forum: General Help
---

### Post by neogeo124 on 2008-12-22
Ok I'm a first time linux user and I like the idea and everything but I'm having some issues. I installed ubuntu 8.10 and I can't for the life of me find what I use to search for wireless networks, so therefore I have no idea if my network card and everything is working. also I'm a little new to the terminal and I don't know what that letter (or whatever you want to call it) that looks like 2 "L"s put together with one upside down and backwards is.


 sorry for what seem like stupid questions, thanks for the help

p.s. its an atheros 5007eg

---

### Post by inxygnuu on 2008-12-22
you need madwifi. It is a set of drivers for your card. and that is not a dumb question, I had that problem too. I will see what i can do, but my system is corrupted right now and I am answering ths on a live cd.

---

### Post by inxygnuu on 2008-12-22
ok, try these commands in this order.
```
wget -c http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz
```
that is getting the package.
```
tar xvf madwifi-ng-r2756+ar5007.tar.gz
```
untarring and downloading the package
```
cd madwifi-ng-r2756+ar5007
```
get inside the folder. (I would do this all in a specific folder, like your desktop for example)
```
sudo apt-get update && sudo aptitude install build-essential
```
you have to get this to compile the source code, you might not have to do this later, but it looks like your a beginner.
```
sudo make install
sudo modprobe ath_pci
sudo modprobe wlan_scan_sta
```
If they don't work all at once, try each line seperatly (or each 'make')

Hope it works,
3v4n

---

### Post by monkeyking on 2008-12-22
> **neogeo124 said:**
> ...that looks like 2 "L"s put together with one upside down and backwards is.
...

I have no idea what your talking about.

on the upper right side of the gnomebar,
theres a networking icon.

try clicking on it.


otherwise

post your
ifconfig
and your
/etc/network/interfaces

You can check for local wlan by using

iwlist scan

---

### Post by neogeo124 on 2008-12-22
where do I get madwifi? is it on the cd? and the letter I'm talking about looks sortof like a parenthesis with the top part pointing backward.

---

### Post by clw3388 on 2008-12-22
}][{ those ones? |.. their by your p key :)they're called brackets... dont recall seeing em in terminal unless typed? hmm..

Oh and inxygnuu post is using webget.. to get the madwifi

---

### Post by neogeo124 on 2008-12-22
no no I mean when I go into help it tells me to type the command

  sudo (weird parenthisis)shw -c network

---

### Post by neogeo124 on 2008-12-22
I'm so confused... whats webget? does that mean I have to get it from the internet with a terminal command ? if so I'm using a windows pc right now for the internet as I can't get connected to anything on my ubuntu laptop

---

### Post by clw3388 on 2008-12-22
sudo lshw -short | grep network

---

### Post by kiisu on 2008-12-22
Yeah I have that same wifi chip - you do need madwifi unless something has changed recently.

The post by inxygnu tells you how. See all those code commands in quote boxes? Paste those one by one into the terminal, hitting return between each, and it should work (been awhile since I did this so can't be sure if that's all you need ... i do know that madwifi was wwaaaayyyyyyy easier than ndiswrapper, for me at least).

Good luck!

---

### Post by clw3388 on 2008-12-22
> **neogeo124 said:**
> I'm so confused... whats webget? does that mean I have to get it from the internet with a terminal command ? if so I'm using a windows pc right now for the internet as I can't get connected to anything on my ubuntu laptop

Assuming your wired connection works.. webget will pull the files down from terminal automagically.. 
Have you tried the hardwire?

---

### Post by neogeo124 on 2008-12-22
ok but what I'm asking is, do I need to be connected to the internet for that? because I'm on an xp computer right now and can't get internet on the linux laptop

---

### Post by clw3388 on 2008-12-22
yes, you'll need internet access to use webget

---

### Post by tarps87 on 2008-12-22
¬ ?
If it is top left on the keyboard, or at least on a UK keyboard.

The command should be
```

sudo lshw -c network

```

For the network you may already have it set up so try that command and then ```
ifconfig
```
Also
[code]sudo iwlist wlan0 scan[code]
This is assuming your wireless card is interface wlan0, it you post the output of the previous commands I can give you more detailed help

---

### Post by kiisu on 2008-12-22
have you tried ethernet?

---

### Post by neogeo124 on 2008-12-22
oh I see... is there any way to do it by transferring the fils from the internet to a windows pc then to my linux pc?

---

### Post by inxygnuu on 2008-12-22
(thank you kiisu & clw3388) yes, if you have Ethernet, you should be able to connect. then simply paste the commands into your terminal, and it should work on a reboot. do you have an hp laptop like me? if so, your ethernet should work.

---

### Post by inxygnuu on 2008-12-22
> **neogeo124 said:**
> oh I see... is there any way to do it by transferring the fils from the internet to a windows pc then to my linux pc?

not through terminal, why wont ethernet work? through windows, you would have to find all the download sources and do it manually. (I don't know how to do that though :( )

---

### Post by neogeo124 on 2008-12-22
I tried 
sudo lshw -c network

 but it comes up command not found

---

### Post by neogeo124 on 2008-12-22
my problem is, in my house all our internet is set up through wireless only

---

### Post by tarps87 on 2008-12-22
In the command```
sudo lshw -c network
```
l = lower case L

I strongly suggest trying this command first as by the information given in this thread there is no way that anyone can determine if you wireless is already working. You maybe over complicating things.

---

### Post by tarps87 on 2008-12-22
> **neogeo124 said:**
> I tried 
sudo lshw -c network

 but it comes up command not found

Is the an I or L?

also did ifconfig work?

---

### Post by neogeo124 on 2008-12-22
*-network               
       description: Ethernet interface
       product: NetLink BCM5906M Fast Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 02
       serial: 00:1b:38:77:fe:6b
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.94 duplex=full ip=192.168.1.103 latency=0 link=yes module=tg3 multicast=yes port=twisted pair speed=100MB/s
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: d2:c4:bc:d2:a3:e3
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

---

### Post by neogeo124 on 2008-12-22
I got it hardwired now.. sorry for my stupidity

---

### Post by neogeo124 on 2008-12-22
should I have done the commands because I started that, is that a problem?

---

### Post by tarps87 on 2008-12-22
It shouldn't be, what commands though?
Try
```
iwlist pan0 scan
```
or
```
sudo iwlist pan0 scan
```

---

### Post by neogeo124 on 2008-12-22
I mean the commands on the first page of this thread, for madwifi

---

### Post by neogeo124 on 2008-12-22
eric@trogdor:~$ sudo iwlist pan0 scan
pan0      Interface doesn't support scanning.

---

### Post by tarps87 on 2008-12-22
Did you run the lshw command after, if so you may be using a different driver but this should not matter. If you ran the lshw command before try running it again. The part your looking for is the second half it should contain the line:
product: AR242x 802.11abg Wireless PCI Express Adapter
Edit: I believe this card does the the drivers from madwifi
Edit: Can you also try running the ifconfig command

---

### Post by tarps87 on 2008-12-22
Sorry just reread the post by inxygnuu, the command sudo lshw -c network shows that you have a AR242x 802.11abg Wireless PCI Express Adapter which will need the drivers from madwifi. inxygnuu was correct about this but it is always a good idea to check first. You may want to check you modules 
```

sudo gedit /etc/modules

```
Add the line "ath_pci" to the end (without the quotes) reboot and then try it
sudo modprobe ath_pci should have activated it without rebooting.

---

### Post by neogeo124 on 2008-12-22
oops I was doing the madwifi thing and typed something wrong now it says

>

and I can't get it to do anything.. how do I make it go back to "eric@trogdor:~/" ?

---

### Post by inxygnuu on 2008-12-22
> **tarps87 said:**
> Sorry just reread the post by inxygnuu, the command sudo lshw -c network shows that you have a AR242x 802.11abg Wireless PCI Express Adapter which will need the drivers from madwifi. inxygnuu was correct about this but it is always a good idea to check first. You may want to check you modules 
```

sudo gedit /etc/modules

```
Add the line "ath_pci" to the end (without the quotes) reboot and then try it
sudo modprobe ath_pci should have activated it without rebooting.

wait, if he has that, I know the exact commands. I have the same card.

---

### Post by inxygnuu on 2008-12-22
> **neogeo124 said:**
> oops I was doing the madwifi thing and typed something wrong now it says

>

and I can't get it to do anything.. how do I make it go back to "eric@trogdor:~?/" ?

just restart. if not, go where you left off. close the terminal and resume.

---

### Post by tarps87 on 2008-12-22
> **neogeo124 said:**
> oops I was doing the madwifi thing and typed something wrong now it says

>

and I can't get it to do anything.. how do I make it go back to "eric@trogdor:~?/" ?

Press Ctrl + c

> **inxygnuu said:**
> wait, if he has that, I know the exact commands. I have the same card.

You'd be better to help than me then.

---

### Post by neogeo124 on 2008-12-22
I got stuck at the sudo make install part

eric@trogdor:~/madwifi-ng-r2756+ar5007$ sudo make install
[sudo] password for eric: 
make: *** No rule to make target `install'.  Stop.
eric@trogdor:~/madwifi-ng-r2756+ar5007$

---

### Post by inxygnuu on 2008-12-22
> You'd be better to help than me then.

what do you mean? I can help both of you if needed.

---

### Post by inxygnuu on 2008-12-22
> **neogeo124 said:**
> I got stuck at the sudo make install part

eric@trogdor:~/madwifi-ng-r2756+ar5007$ sudo make install
[sudo] password for eric: 
make: *** No rule to make target `install'.  Stop.
eric@trogdor:~/madwifi-ng-r2756+ar5007$

try skipping that part. I am not really an expert, i am simply between beginner and intermediate. I have to try something right now. (I am on a live cd, GRUB error 21)

Good luck, and be back soon,
3v4n

---

### Post by tarps87 on 2008-12-22
> **inxygnuu said:**
> what do you mean? I can help both of you if needed.

If you have set this card up before you know what needs doing. I didn't mean any offence or anything.

> **neogeo124 said:**
> I got stuck at the sudo make install part

eric@trogdor:~/madwifi-ng-r2756+ar5007$ sudo make install
[sudo] password for eric: 
make: *** No rule to make target `install'.  Stop.
eric@trogdor:~/madwifi-ng-r2756+ar5007$

Try ```
sudo make
```
and then
```

sudo make install
```

---

### Post by neogeo124 on 2008-12-22
eric@trogdor:~/madwifi-ng-r2756+ar5007$ sudo make
[sudo] password for eric: 
make: *** No targets specified and no makefile found.  Stop.
eric@trogdor:~/madwifi-ng-r2756+ar5007$ sudo make install
make: *** No rule to make target `install'.  Stop.
eric@trogdor:~/madwifi-ng-r2756+ar5007$

---

### Post by neogeo124 on 2008-12-22
Setting up build-essential (11.4) ...
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information        
Initializing package states... Done
Writing extended state information... Done

eric@trogdor:~/madwifi-ng-r2756+ar5007$ eric@trogdor:~$ sudo iwlist pan0 scan
bash: eric@trogdor:~$: command not found
eric@trogdor:~/madwifi-ng-r2756+ar5007$ pan0      Interface doesn't support scanning.
> sudo make install
> sudo modprobe ath_pci
> sudo modprobe wlan_scan_sta
> sudo
> 
> o[\
> eric@trogdor:~/
> 
eric@trogdor:~/madwifi-ng-r2756+ar5007$ sudo make install
[sudo] password for eric: 
make: *** No rule to make target `install'.  Stop.
eric@trogdor:~/madwifi-ng-r2756+ar5007$ sudo make
[sudo] password for eric: 
make: *** No targets specified and no makefile found.  Stop.
eric@trogdor:~/madwifi-ng-r2756+ar5007$ sudo make install
make: *** No rule to make target `install'.  Stop.
eric@trogdor:~/madwifi-ng-r2756+ar5007$ 

 thats how it happened.. I accidently pasted the wrong thing not it doesn't want to work

---

### Post by tarps87 on 2008-12-22
It sounds like it can't find the make file.
Change of plan, it sounds like it is in the repository, connect to the internet again and try
```
sudo apt-get install madwifi-tools
```

---

### Post by neogeo124 on 2008-12-22
eric@trogdor:~$ sudo apt-get install madwifi-tools
[sudo] password for eric: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  madwifi-tools
0 upgraded, 1 newly installed, 0 to remove and 199 not upgraded.
Need to get 50.9kB of archives.
After this operation, 266kB of additional disk space will be used.
Get:1 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid/universe madwifi-tools 1:0.9.4~rc2+dfsg-1 [50.9kB]
Fetched 50.9kB in 1s (47.2kB/s)       
Selecting previously deselected package madwifi-tools.
(Reading database ... 100719 files and directories currently installed.)
Unpacking madwifi-tools (from .../madwifi-tools_1%3a0.9.4~rc2+dfsg-1_i386.deb) ...
Processing triggers for man-db ...
Setting up madwifi-tools (1:0.9.4~rc2+dfsg-1) ...

eric@trogdor:~$ 


does that mean it should work now after a reboot?

---

### Post by tarps87 on 2008-12-22
You will need to add the line ath_pci to your modules file
```
sudo gedit /etc/modules
```
Add the line "ath_pci" to the end (without the quotes) reboot and then try it
You can use this to activate it without rebooting
```
sudo modprobe ath_pci
```

The swine's added it to the repository to save all the hassle of compiling it :)

---

### Post by neogeo124 on 2008-12-22
you mean just write ath_pci at the bottom of the text file that opens?

I did that and rebooted and everything still seems the same as it was and I still haven't figured out where I go to make it search for a wireless network

---

### Post by inxygnuu on 2008-12-22
> **neogeo124 said:**
> you mean just write ath_pci at the bottom of the text file that opens?

I did that and rebooted and everything still seems the same as it was and I still haven't figured out where I go to make it search for a wireless network

just look at the network icon. you will see when it happens

---

### Post by kiisu on 2008-12-22
Have you tried this?
[http://ubuntuforums.org/showthread.php?t=662877&highlight=ar5007+madwifi](http://ubuntuforums.org/showthread.php?t=662877&highlight=ar5007+madwifi)
I'm pretty sure these are the instructions I followed to get mine working ..

---

### Post by inxygnuu on 2008-12-22
> **kiisu said:**
> Have you tried this?
[http://ubuntuforums.org/showthread.php?t=662877&highlight=ar5007+madwifi](http://ubuntuforums.org/showthread.php?t=662877&highlight=ar5007+madwifi)
I'm pretty sure these are the instructions I followed to get mine working ..

just make sure it is updated. when i followed a certain post, it worked until restart. Then i did the same thing with an updated package, worked great.

---

### Post by tarps87 on 2008-12-22
> **neogeo124 said:**
> you mean just write ath_pci at the bottom of the text file that opens?

I did that and rebooted and everything still seems the same as it was and I still haven't figured out where I go to make it search for a wireless network

Try this again
```
iwlist interface scan
```

you can use the lshw to find out the interface name like before. There should be a network icon next to the sound icon in the notification area in the to right

---

### Post by neogeo124 on 2008-12-22
eric@trogdor:~$ iwlist interface scan
interface  Interface doesn't support scanning.

---

### Post by neogeo124 on 2008-12-22
and the network bit at the top right only says wired network

---

### Post by neogeo124 on 2008-12-23
bump

---

### Post by magmon on 2008-12-23
> **neogeo124 said:**
> no no I mean when I go into help it tells me to type the command

  sudo (weird parenthisis)shw -c network

That is simply the thing that shows where you're typing. You know, the one that usually just a | looking thing.

---

### Post by monkeyking on 2008-12-23
> **magmon said:**
> That is simply the thing that shows where you're typing. You know, the one that usually just a | looking thing.

I still have no idea...

---

### Post by tarps87 on 2008-12-23
Lets try starting from the start, first check restircted hardware, it's under system -> admin -> hardware
If there is a wireless driver there click enable and restart.
If not try, ```
uname -r
sudo apt-get install linux-restricted-modules-*output from uname -r*
```
restart and check the restriced drivers again, if there's still nothing make sure ath_pci is added to the end of /etc/modules
Also which version of Ubuntu are you using, it should already be in 8.10

---

### Post by tarps87 on 2008-12-23
The above may not work a I have just discovered it is the same wireless can as in my laptop and I could not get it to work using this driver.
I am using the 'latest' drivers from madwifi, they are in the backports repository. To use this driver:
Remove the old driver
```

sudo rmmod ath_pci

```
install the modules
```

sudo apt-get install linux-backports-modules-intrepid-generic

```
enable the new driver
```

sudo modprobe ath5k

```
```

sudo gedit /etc/modules

```
add the line
ath5k
(You may need to restart and enable the driver in hardware drivers under system -> admin)

This driver is set to replace the original madwifi drivers. Sorry for not realising it was the same card earlier, hope this works.

---

### Post by neogeo124 on 2008-12-23
eric@trogdor:~$ sudo rmmod ath_pci
[sudo] password for eric: 
eric@trogdor:~$ sudo apt-get install linux-modules-intrepid-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-modules-intrepid-generic
eric@trogdor:~$

---

### Post by neogeo124 on 2008-12-23
oops typed the wrong thing

---

### Post by neogeo124 on 2008-12-23
ok so you mean add ath5k to the the text file that opens?

---

### Post by neogeo124 on 2008-12-23
ok did all that but I'm still lost

---

### Post by neogeo124 on 2008-12-23
is there something I can go to to search available wireless networks?

---

### Post by neogeo124 on 2008-12-23
oh sorry if I've frustrated some of you, I'm just very new to linux and would like to learn

---

### Post by neogeo124 on 2008-12-23
this is what it shows right now... what does it all mean?


eric@trogdor:~$ sudo lshw -c network
[sudo] password for eric: 
  *-network               
       description: Ethernet interface
       product: NetLink BCM5906M Fast Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 02
       serial: 00:1b:38:77:fe:6b
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.94 duplex=full ip=192.168.1.103 latency=0 link=yes module=tg3 multicast=yes port=twisted pair speed=100MB/s
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 2a:df:ee:6a:05:04
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
eric@trogdor:~$

---

### Post by Jammanuser on 2008-12-23
> **inxygnuu said:**
> you need madwifi. It is a set of drivers for your card. and that is not a dumb question, I had that problem too. I will see what i can do, but my system is corrupted right now and [COLOR="Red"]I am answering ths on a live cd.[/COLOR]

Really? :o I was of the understanding that Internet didn't work on the LiveCD...because every single time I've ever been in a Live session, I was unable to access the Internet, even though my wireless connection works fine on a normal boot! ;)

I would certainly like to hear how you managed to do that! :)

Cheers! :lolflag:

-Jam man

:guitar:

---

### Post by neogeo124 on 2008-12-23
is there anyone with answers?... when you guys connect to a wireless network.. where do you go to search for wireless networks? how do I get this to work? how come any time I do "sudo make" on anything it won't do anything

---

### Post by Jammanuser on 2008-12-23
> **neogeo124 said:**
> is there anyone with answers?... when you guys connect to a wireless network.. where do you go to search for wireless networks? how do I get this to work? how come any time I do "sudo make" on anything it won't do anything

On mine, it finds the wireless networks automatically at boot, and I only had to choose the correct network once, after which it connects to that network each time! :) If you look at the top of your desktop, on the right, in Ubuntu, you'll see something called "Wireless networks", or something to that effect. Simply left click on it, which should open up a list of the available wireless networks...and then simply choose the network that you signed up for in order to connect to it! :popcorn:

Hope I helped! :lolflag:

Cheers! :)

-Jam man

:guitar:

EDIT: I haven't taken the time yet to look through this whole thread...so i'm not sure which Linux distro you use! I use Ubuntu 8.10...no doubt the proceedure might be different in a different distro of Linux! Cheers! :D

---

### Post by neogeo124 on 2008-12-23
it doesn't come up with anything on the wireless part

---

### Post by Jammanuser on 2008-12-24
> **neogeo124 said:**
> it doesn't come up with anything on the wireless part

hmm...its very odd! :-k Now that I think about it...I may have got the wrong name for the wireless networks at the top of the screen! :lolflag:

Let me go check on Ubuntu (as I'm in Vista, right now)...and try to get the exact name! :guitar:

Cheers! :popcorn:

-Jam man

:guitar:

---

### Post by Jammanuser on 2008-12-24
Ahh...I see where I made the mistake! :) I was thinking, I guess, that it actually gave the name! I apologize...:redface: What I actually was talking about was the stairs-looking icon on the taskbar at the top right of the Ubuntu screen! :) Simply left click on that, and it will bring up a list of the available networks, after which you simply pick the network to connect to! :guitar:

Of course, in order to access the Internet from the wireless network you choose, you will have to obtain the neccessary information from whoever owns the network...i.e. the security key or passphrase, or the IP address of the server. :popcorn:

Hope this helps! 

-Jam man

:guitar:

---

### Post by neogeo124 on 2008-12-24
no I meant when you go to the wireless "list" it doesn't say anything and the network is my own

---

### Post by Jammanuser on 2008-12-24
> **neogeo124 said:**
> no I meant when you go to the wireless "list" it doesn't say anything and the network is my own

Ahh...I see now what you mean! :) Then, in that case, a simple logical guess on my part would be...that you're not close enough to a wireless network to access it! :lolflag: Make sure first that you're in range...and then we can work from there if you are, and its simply a different problem! ;)

Cheers! :popcorn:

-Jam man

:guitar:

---

### Post by Jammanuser on 2008-12-24
Ok...I just did a bit of reading, and read all the previous posts on your thread! :) It seems that your problem is **way** bigger than I had first thought...from what I gathered, you're lacking the neccessary drivers for your wireless card! :lolflag:

Cheers! :popcorn:

-Jam man

:guitar:

---

### Post by Jammanuser on 2008-12-24
> **kiisu said:**
> Have you tried this?
[http://ubuntuforums.org/showthread.php?t=662877&highlight=ar5007+madwifi](http://ubuntuforums.org/showthread.php?t=662877&highlight=ar5007+madwifi)
I'm pretty sure these are the instructions I followed to get mine working ..

Have you tried yet what kiisu suggested? if you have not, then I would suggest trying it, as it very well may fix your problem! ;)

Cheers! :popcorn:

-Jam man

:guitar:

---

### Post by hyper_ch on 2008-12-24
It is advised to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;)

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

Also, when you are asked to post output from (config) files or from a command, use [noparse]```

```[/noparse] brackets around (each) output. That makes it also easier to read.

---

### Post by chemicalfan on 2008-12-24
I've got the same problem with my Acer Aspire One (wireless is a known issue with this laptop & distro though). Mine is a question not of drivers, but getting a list of available wireless networks (just like in XP), and then selecting the one you connect to.

I admit, without working drivers, I won't find anything (which is what is happening now!), but I can't even see an area for bringing up the list Unless it is a terminal command, of course! On a side note, is there is noobs list/reference of terminal commands anywhere?

---

### Post by monkeyking on 2008-12-24
> **chemicalfan said:**
> I've got the same problem with my Acer Aspire One (wireless is a known issue with this laptop & distro though). Mine is a question not of drivers, but getting a list of available wireless networks (just like in XP), and then selecting the one you connect to.

I admit, without working drivers, I won't find anything (which is what is happening now!), but I can't even see an area for bringing up the list Unless it is a terminal command, of course! On a side note, is there is noobs list/reference of terminal commands anywhere?

I thought the aspire one was working perfectly. Good thing I didn't buy one.


tjeck 

```

man iwconfig
man iwlist

```

also check the apropos command

```

apropos wireless
apropos wireless
iwconfig (8)         - configure a wireless network interface
iwevent (8)          - Display Wireless Events generated by drivers and setti...
iwgetid (8)          - Report ESSID, NWID or AP/Cell Address of wireless network
iwlist (8)           - Get more detailed wireless information from a wireless...
iwpriv (8)           - configure optionals (private) parameters of a wireless...
iwspy (8)            - Get wireless statistics from specific nodes
wireless (7)         - Wireless Tools and Wireless Extensions



```

---

### Post by Jammanuser on 2008-12-24
> **chemicalfan said:**
> I've got the same problem with my Acer Aspire One (wireless is a known issue with this laptop & distro though). Mine is a question not of drivers, but getting a list of available wireless networks (just like in XP), and then selecting the one you connect to.

I admit, without working drivers, I won't find anything (which is what is happening now!), but I can't even see an area for bringing up the list Unless it is a terminal command, of course! On a side note, is there is noobs list/reference of terminal commands anywhere?

Have you tried left-clicking on the stairs-looking icon on the Gnome taskbar at the top of the screen yet? This should bring up a list of the wireless networks available...:guitar:

Cheers! :popcorn:

-Jam man

:guitar:

---

### Post by chemicalfan on 2008-12-24
I'm running Xfce, so no stairs icon for me :(

I can confirm that the driver being used is correct, as when I run lshw, it returns all correct data about my wireless adaptor. It also shows 'Wireless Networks' when I right-click on the network icon on the taskbar. It just won't connect!!
I've got the router to set to MAC filter (as I couldn't get encryption to work with the other laptop in this house), but I've added my wireless adaptor's MAC onto the allowed list, so this shouldn't be a problem. That said, my brother's Nintendo Wii doesn't like it much, maybe it is an issue?

I think that's a red herring though, as ```
sudo iwscan wmaster0 scanning
``` states that the interface doesn't support scanning. Ugh, drivers - why are they such a pain?

---

### Post by leva on 2008-12-24
Have you tried adding in your wireless connection manually? Putting in your SSID could help.

---

### Post by chemicalfan on 2008-12-24
Do you mean if I right click on the network icon in taskbar, and then select 'Create New Wireless connection'? I've tried that, and it just spins the icon for a minute or 2, and then says disconnected.
Annoying!

---

### Post by leva on 2008-12-24
To get my wireless working I had to go into Edit Connections. Then under the Wireless tab I Added my wireless connection.
I don't know if you have that same menu layout, you having mentioned earlier that you were using a different GUI.

---

### Post by leva on 2008-12-24
To get my wireless working I had to go into Edit Connections. Then under the Wireless tab I Added my wireless connection.
I don't know if you have that same menu layout, you having mentioned earlier that you were using a different GUI.

---

### Post by chemicalfan on 2008-12-24
Ah yes, I know where you mean - that doesn't work either though :(
At the moment, I'm blaming the drivers. I'm gonna have another go at those (probably tomorrow now!)

---

### Post by chemicalfan on 2008-12-25
Update: I'm still at a loss here - I've even tried removing the driver using sudo rmmod, and then adding back in the default one (ath_pci) with modprobe, but after a reboot it has reset it back to atk5k!!
I've no idea how to proceed on this one - should I hunt for a new kernel/distr, or is there a bit less "sledgehammer" approach I could try?

---

### Post by kiisu on 2008-12-25
As I said before I have the same wifi chip and madwifi worked for me.
Did you guys try following the guide I linked to?

[http://ubuntuforums.org/showthread.p...ar5007+madwifi](http://ubuntuforums.org/showthread.p...ar5007+madwifi)


And one other thing ... I always had problems with the built-in ubuntu network manager.
I replaced it with Wicd and I've had no wireless problems since.

[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

> If you are using Ubuntu Jaunty (not currently released), Wicd is in the universe repository.

Installing Wicd in Ubuntu is very simple. You just have to add the Wicd repository to the Ubuntu package manager. To open the package manager in Gnome, go to Administration > Synaptic Package Manager. When it appears, go to Settings > Repositories > Third Party Software > Add..., and enter the following line:

    deb [http://apt.wicd.net](http://apt.wicd.net) hardy extras 

where gutsy is your version of Ubuntu in lowercase (dapper, edgy, feisty, gutsy, hardy, intrepid). You'll also need to add the key used for signing Wicd by running the following command in a terminal:

    wget -q [http://apt.wicd.net/wicd.gpg](http://apt.wicd.net/wicd.gpg) -O- | sudo apt-key add - 

Now, click Reload, and wait while the package lists are downloaded. Now, search for "Wicd", and right click on it. Select Install, then press Apply, and Wicd will automatically be downloaded and installed for you. This will also keep you automatically up to date with the latest and greatest version of Wicd. Please note that this will remove network-manager, which is the default GNOME network manager and may cause loss of network connection temporarily. 

It will remove the original network-manager as it installs. Then run  'wicd-client' in terminal and it should appear in the system tray in the taskbar. Click on that and you'll see your list of wireless networks. Of course, if its empty, something still isn't right with your wireless setup. (In wicd preferences, I changed the WPA Supplicant Driver to 'WEXT').

hope it helps!

---

### Post by Jammanuser on 2008-12-25
> **kiisu said:**
> As I said before I have the same wifi chip and madwifi worked for me.
Did you guys try following the guide I linked to?

[http://ubuntuforums.org/showthread.p...ar5007+madwifi](http://ubuntuforums.org/showthread.p...ar5007+madwifi)


And one other thing ... I always had problems with the built-in ubuntu network manager.
I replaced it with Wicd and I've had no wireless problems since.

[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)



It will remove the original network-manager as it installs. Then run  'wicd-client' in terminal and it should appear in the system tray in the taskbar. Click on that and you'll see your list of wireless networks. Of course, if its empty, something still isn't right with your wireless setup. (In wicd preferences, I changed the WPA Supplicant Driver to 'WEXT').

hope it helps!

Thanks! :) I too have had problems with Ubuntu's standard network-manager...I will try Wicd instead, and hopefully it will work much better! :guitar: 
I have Intrepid.

Cheers! :popcorn:

-Jam man

:guitar:

---

### Post by kiisu on 2008-12-25
No problem. 

Also I realised the first link I posted got cut-off.

[http://ubuntuforums.org/showthread.php?t=662877&highlight=ar5007+madwifi](http://ubuntuforums.org/showthread.php?t=662877&highlight=ar5007+madwifi)

---

### Post by Maxxtsch on 2008-12-25
Did you enable wireless?

---

### Post by chemicalfan on 2008-12-26
Just another update - I've installed Wicd as suggested, with no immediate success (but at least it is a bit more intuitive for me!)
Next up, I grabbed the latest ath_pci module/package from Madwifi, and after a bit of wrestling, got it installed and loaded. Now, it will allow scanning, but doesn't produce any results (Wicd confirms this stating there are no wireless networks found). This may be down to the MAC filtering on the route; I sincerly hope it isn't though, as it's the only form of security that works with the other laptop in the house. 

One thing I have noticed - under sudo lshw, my wireless adaptor is under the heading "network DISABLED", where as my wired connection is simply under "network". Is this a real problem, or just an error with the report?

---

### Post by abn91c on 2008-12-26
> **neogeo124 said:**
> I tried 
sudo lshw -c network

 but it comes up command not found
it needs to be a capital C
sudo lshw -[COLOR="Red"]C [/COLOR]network
Also in the set up if you see a check box or line about"allow roaming" check it off, that will get you a connection

---

### Post by chemicalfan on 2008-12-26
Final update: GOT IT WORKING!!!
I now strongly suspect the router's MAC filtering (although I did change a couple of things before success), as I can connect to a completely unsecured network. Not good long term, but at least I know things are working! Now to find a happy security medium....

---

### Post by Jammanuser on 2009-01-02
> **kiisu said:**
> 
If you are using Ubuntu Jaunty (not currently released), Wicd is in the universe repository.

Installing Wicd in Ubuntu is very simple. You just have to add the Wicd repository to the Ubuntu package manager. To open the package manager in Gnome, go to Administration > Synaptic Package Manager. When it appears, go to Settings > Repositories > Third Party Software > Add..., and enter the following line:

    deb [http://apt.wicd.net](http://apt.wicd.net) hardy extras 

where gutsy is your version of Ubuntu in lowercase (dapper, edgy, feisty, gutsy, hardy, intrepid). You'll also need to add the key used for signing Wicd by running the following command in a terminal:

    wget -q [http://apt.wicd.net/wicd.gpg](http://apt.wicd.net/wicd.gpg) -O- | sudo apt-key add - 

Now, click Reload, and wait while the package lists are downloaded. Now, search for "Wicd", and right click on it. Select Install, then press Apply, and Wicd will automatically be downloaded and installed for you. This will also keep you automatically up to date with the latest and greatest version of Wicd. Please note that this will remove network-manager, which is the default GNOME network manager and may cause loss of network connection temporarily. 

I did all that, but was unable to find "Wicd" when I searched for it in synaptic...:confused: How could this be?

Looking forward to your reply...:popcorn:

-Jam man

:guitar:

---

### Post by kiisu on 2009-01-02
J.Man,

that's strange. Been awhile since I added it but I just checked and it shows up in synaptic.
Are you using intrepid, hardy, ... ? I assume you caught the line about changing the source name to your version?

Also, did you try just  'sudo apt-get install wicd' in terminal after adding the repository?

---

### Post by Jammanuser on 2009-01-02
> **kiisu said:**
> J.Man,

that's strange. Been awhile since I added it but I just checked and it shows up in synaptic.
Are you using intrepid, hardy, ... ? I assume you caught the line about changing the source name to your version?

Also, did you try just  'sudo apt-get install wicd' in terminal after adding the repository?

I'm using Intrepid, and i made sure to put "intrepid" instead of "hardy" when adding the source line. :-k

Thanks for the reply! :)

-Jam man

:guitar:

---

### Post by kiisu on 2009-01-02
and still no luck?

---

### Post by Jammanuser on 2009-01-02
> **kiisu said:**
> 
Also, did you try just  'sudo apt-get install wicd' in terminal after adding the repository?

Ahh...that worked! :D Thanks a lot man! Strange though that it didn't work with synaptic...:-k

-Jam man

:guitar:

---

### Post by Jammanuser on 2009-01-02
> **kiisu said:**
> and still no luck?

Actually i just tried apt-get, and it worked! :D

Thanks! :P

-Jam man

:guitar:

---

### Post by Jammanuser on 2009-01-02
> **kiisu said:**
> 
I changed the WPA Supplicant Driver to 'WEXT').


It seems to have done it automatically with mine...:-k

-Jam man

:guitar:

---

### Post by Jammanuser on 2009-01-02
Now i have a new problem...when I type "wicd-client" in the terminal, it shows the icon on the Gnome taskbar. But when i close the terminal, the Wicd manager icon disappears from the taskbar! :confused: :confused: :confused: How do I get it to stay on the taskbar?

Looking forward to your reply...

-Jam man

:guitar:

---

### Post by kiisu on 2009-01-02
Add 'wicd-client' as a script on startup ( think it's in settings -> sessions ) then logout and back in, that way it will just run.

By doing it in the terminal it only runs as long as you keep that terminal window open. Not sure why, someone with more linux expertise would know.

---

### Post by Jammanuser on 2009-01-02
> **kiisu said:**
> Add 'wicd-client' as a script on startup ( think it's in settings -> sessions ) then logout and back in, that way it will just run.

By doing it in the terminal it only runs as long as you keep that terminal window open. Not sure why, someone with more linux expertise would know.

Thanks, but i just checked System>Preferences>Sessions (not settings>sessions), and it already exists in the startup programs! :o maybe it will show up when i reboot...:-k

Cheers! :popcorn:

-jam man

:guitar:

---

### Post by Jammanuser on 2009-01-06
Yep. :) When i rebooted, it showed the icon on my Gnome taskbar, and now every time when i boot into Ubuntu! :D Sorry to have not mentioned it before.

Cheers! :popcorn:

-Jam man

:guitar:

---

