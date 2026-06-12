---
title: "1420n Heat Problems"
date: 2008-08-01
forum: Dell Ubuntu Support (CLOSED)
---

### Post by phynix on 2008-08-01
When watching videos on site like youtube temp gauge can sometimes spike to 70c. Is this normal? and if not how can I engage the fans.

---

### Post by vandorjw on 2008-08-03
70 Degrees Celsius is NOT normal.

I have an Inspiron 1520 and had the same problem as you did. Whenever I played a game, or did something CPU intensive, my temperature would go up to 75 Celsius.

Some people said it was because my HeatSink was dirty and I needed to clean the inside of my laptop, however, I was pretty sure that my fan wasn't working as it should.

So, I did some looking around, and found "Dellfand"
> 
[http://dellfand.dinglisch.net/](http://dellfand.dinglisch.net/)


On this page, there is a download link, download the file, (its only about 13 Kb), and extract the contents. (right click and extract)

Now, open up the terminal, (applications --> accessories --> terminal)
and navigate to the the dellfand folder. 

If you downloaded it to your "home" folder, use this.

> 
cd /home/**INSERT YOUR USERNAME HERE**/dellfand-0.9


the type > make
(this will now build the program for you.)

Now, copy some files to new locations
> 
sudo cp dellfand /usr/sbin

enter your password...
> 
sudo cp etc.init.d.dellfand /etc/init.d/dellfand

and finally
> 
sudo cp etc.default.dellfand /etc/default/dellfand


To start the Deamon/program, type
> 
sudo /etc/init.d/dellfand start


Now, instead of typing that line, ever time you start your laptop, type this into the terminal. It will add Dellfand to your start-up programs.
> 
sudo update-rc.d dellfand multiuser


Configure Dellfand.
If you type "sudo dellfand"
the deamon will tell you your computer temperature, the fan being controlled, program version, program status, and fan speed.

**example** v0.9: Fan 0 Status 1 Speed 76440 CPU Temp 40C

"sudo dellfand 1 5 28 36 43"
---> the above command tells dellfand the following.

1 = Work in the background (if you set this to "0" it will continually update you about fan speed and CPU temp)
5 = Check CPU temperature every 5 seconds
28 = Turn the fan OFF when below 28 Degrees Celsius.
36 = Turn the fan to LOW when temp reaches 36 Celsius
43 = Turn the fan to HIGH when temperature is over 43 Celsius

Feel Free to change those numbers to something different.

(Keep numbers below 60 or it will give you errors)
~~ something in the source code that prevents you from destroying your PC :KS~~

Also, to turn OFF dellfand use
> 
sudo /etc/init.d/dellfand stop


IF you don't do this, your BIOS may report that you have incorrect power intake and that there is something wrong with your fans.
It doesn't matter if you forget, its just annoying and scared the crap out of me the first time I saw that.

(I'll try to find out how to add that line to the shutdown list so you don't have to enter it every time you shut-down)

Cheers - cc7

---

### Post by anjilslaire on 2008-08-03
I'll be sure to check dellfand too, as I have a 1420 myself.

For some insight into this, it seems like it may be a GPU issue. Check this article on /. :
[http://mobile.slashdot.org/article.pl?sid=08/08/01/0142219](http://mobile.slashdot.org/article.pl?sid=08/08/01/0142219)

also:
[http://direct2dell.com/one2one/archive/2008/07/25/nvidia-gpu-update-for-dell-laptop-owners.aspx](http://direct2dell.com/one2one/archive/2008/07/25/nvidia-gpu-update-for-dell-laptop-owners.aspx)

I'm hoping it doesn't get ugly, as I've also purchased a 1420n for an out of state relative, which would be a pain if it breaks down as well.

Maybe someone should request Getdeb.net to package it for easy use?

---

### Post by phynix on 2008-08-03
Thanks for the links and the very detailed tutorial. Love it. I looked at those articles and don't know if they apply to me since mine is intel based, but I have seen some bits and pieces about nvidia problems. I figured I wasn't alone though.

---

### Post by phynix on 2008-08-03
Sweet so far watching a video that used to get it above 65 not its at 44. Thanks for the tip.

---

### Post by indigoshift on 2008-08-04
Very cool.  Thanks!

My Latitude D610 would get over 50C running Amarok, and would get up to 70C watching videos in Firefox, then freeze completely.

Now I'm doing both, and not getting over 43C.

---

### Post by phynix on 2008-08-04
The only problem I have with the program is that it revs. When it reaches a high it will go for a few secs then stop then start again.

---

### Post by indigoshift on 2008-08-04
The only problem I had was with this bit:

> sudo update-rc.d dellfand multiuser

My shell doesn't like that syntax, and I'm not well-versed enough to know how update-rc.d likes its arguments.  So, I did this instead:

I added two lines to .bashrc:

```

alias fan="sudo /usr/sbin/dellfand 1 2 30 35 42"
alias stopfan="sudo /etc/init.d/dellfand stop"

```

Which allows me to start and stop the fan from the command line.  It's handy for when I'm on battery power only.

The downside is that it doesn't start up when I boot up--I always have to start it manually.  But that's not really a problem.  I have tilda, so my command line is just an F1 key away.

---

### Post by Crowchild on 2008-08-04
When I try the command 'make' I get:> g++ -Wall -O2 dellfand.cc -o dellfand
make: g++: Command not found
make: *** [dellfand] Error 127


Any idea what this means?

---

### Post by indigoshift on 2008-08-04
I may be wrong, but it looks like you don't have g++ installed, perhaps?

I've found that build-essential is what you need anytime you're using the make command.  [This page]("http://www.ubuntux.org/how-to-install-basic-compilers-build-essential") shows you how to get it.

---

### Post by trooperchix on 2008-08-04
"Configure Dellfand"

Um, what?  I've gotten this far, but what do you mean by "configure Dellfand"?

---

### Post by mrynit on 2008-08-05
What version of ubuntu does this happen on? I have similar problem on my 1420n with 8.04. the problem started when i upgraded to 8.04.

I was thinking about flashing the BIOS to see if it helps.
[http://support.dell.com/support/downloads/download.aspx?c=us&l=en&s=gen&releaseid=R192444&SystemID=INS_PNT_PM_1420&servicetag=&os=WLH&osl=en&deviceid=12914&devlib=0&typecnt=0&vercnt=6&catid=-1&impid=-1&formatcnt=1&libid=1&fileid=264350#3DOS](http://support.dell.com/support/downloads/download.aspx?c=us&l=en&s=gen&releaseid=R192444&SystemID=INS_PNT_PM_1420&servicetag=&os=WLH&osl=en&deviceid=12914&devlib=0&typecnt=0&vercnt=6&catid=-1&impid=-1&formatcnt=1&libid=1&fileid=264350#3DOS)

[edit]
I read the link anjilslaire posted, im not sure if the flash will fix this issue.

The version says it has "Added enhancement for thermal control." so maybe that would hlep.

@cc7gir
IMO that is a work around the problem. What is actualy cause this issue? That should be fixed so we dont have to use "third party software".

---

### Post by trooperchix on 2008-08-05
> **mrynit said:**
> What version of ubuntu does this happen on? I have similar problem on my 1420n with 8.04. the problem started when i upgraded to 8.04.

I was thinking about flashing the BIOS to see if it helps.
[http://support.dell.com/support/downloads/download.aspx?c=us&l=en&s=gen&releaseid=R192444&SystemID=INS_PNT_PM_1420&servicetag=&os=WLH&osl=en&deviceid=12914&devlib=0&typecnt=0&vercnt=6&catid=-1&impid=-1&formatcnt=1&libid=1&fileid=264350#3DOS](http://support.dell.com/support/downloads/download.aspx?c=us&l=en&s=gen&releaseid=R192444&SystemID=INS_PNT_PM_1420&servicetag=&os=WLH&osl=en&deviceid=12914&devlib=0&typecnt=0&vercnt=6&catid=-1&impid=-1&formatcnt=1&libid=1&fileid=264350#3DOS)


So, I checked the above link, and I'm not seeing an option for a Linux fix.  I see only a downloadable .exe file.  Any ideas?  I keep getting an error that states the system is unable to detect the correct voltage through my dell plug for my 1420n.  When I try to run anything with any application in OpenOffice, I get flickering and blocks of black and eventually it freezes the system.  It also runs extremely hot.  I've had this sucker for under a year, and don't want to burn it up.

Also, upon logging in, the system pops a grey window that I can't read until later in booting that states >  There was an error starting the Gnome Settings Daemon. 

---

### Post by anjilslaire on 2008-08-06
It appears that users in the comments section of [http://direct2dell.com/one2one/archive/2008/07/25/nvidia-gpu-update-for-dell-laptop-owners.aspx]("http://direct2dell.com/one2one/archive/2008/07/25/nvidia-gpu-update-for-dell-laptop-owners.aspx") have a linux method of updating the BIOS:

Do a search on the page for linux. I believe the 3rd reference has a post:
> 
heinzoel said:

Bios-Update on Ubuntu without boot-disk:

- install libsmsbios-bin

- 'sudo getSystemId' , notice ID (for example 0x01BD)

- download bios.hdr from the matching folder under ' [http://linux.dell.com/repo/software/bios-hdrs/](http://linux.dell.com/repo/software/bios-hdrs/)'

- sudo modprobe dell_rbu

- sudo dellBiosUpdate -u -f ./bios.hdr

- reboot


---

### Post by mrynit on 2008-08-06
> **trooperchix said:**
> I keep getting an error that states the system is unable to detect the correct voltage through my dell plug for my 1420n.

where does the error come from? is it a pop up box in the top panne or a pop up window? It could be a bad power brick.

> **trooperchix said:**
> 
When I try to run anything with any application in OpenOffice, I get flickering and blocks of black and eventually it freezes the system.  It also runs extremely hot.  I've had this sucker for under a year, and don't want to burn it up.

that does sound like a graphics card issue discribed in the direct2dell post.

> **trooperchix said:**
> 
Also, upon logging in, the system pops a grey window that I can't read until later in booting that states

I dont know what that is related to the thermal issues


I have no graphics problems but my fan is not turning on and off when it should. I am going to do the above bios flash and see if it works.

[edit]
I did the above steps and upgrade from A04 to A09 and the fan still does not work the way it should :( It will tramp up and down but takes longer than it should. Also seems like the fan only has 4 speeds, off, low, med, hi. It is better than having the fan blasting all the time. :-|

```
mrynit@dell-desktop:~$ sudo apt-get install libsmbios-bin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libsmbiosxml1
Suggested packages:
  libsmbios-doc
The following NEW packages will be installed:
  libsmbios-bin libsmbiosxml1
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 158kB of archives.
After this operation, 659kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com hardy-updates/main libsmbiosxml1 0.13.10-1ubuntu1.1 [55.5kB]
Get:2 http://us.archive.ubuntu.com hardy-updates/universe libsmbios-bin 0.13.10-1ubuntu1.1 [103kB]
Fetched 158kB in 1s (112kB/s)      
Selecting previously deselected package libsmbiosxml1.
(Reading database ... 224164 files and directories currently installed.)
Unpacking libsmbiosxml1 (from .../libsmbiosxml1_0.13.10-1ubuntu1.1_i386.deb) ...
Selecting previously deselected package libsmbios-bin.
Unpacking libsmbios-bin (from .../libsmbios-bin_0.13.10-1ubuntu1.1_i386.deb) ...
Setting up libsmbiosxml1 (0.13.10-1ubuntu1.1) ...

Setting up libsmbios-bin (0.13.10-1ubuntu1.1) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
mrynit@dell-desktop:~$ sudo getSystemId
Libsmbios:    0.13.10
System ID:    0x01F3
Service Tag:  HS12GF1
Express Service Code: 38700146845
Product Name: Inspiron 1420
BIOS Version: A04
Vendor:       Dell Inc.
Is Dell:      1
mrynit@dell-desktop:~/Downloads$ sudo dellBiosUpdate -u -f ./bios.hdr
Supported RBU type for this system: (MONOLITHIC, PACKET)
Using RBU v2 driver. Initializing Driver. 
Setting RBU type in v2 driver to: PACKET
writing (4096) to file: /sys/devices/platform/dell_rbu/packet_size
Writing RBU data (4096bytes/dot): ............................................................................................................................................................................................................................................................................................
Done writing packet data.
Activate CMOS bit to notify BIOS that update is ready on next boot.
Update staged sucessfully. BIOS update will occur on next reboot.

```

when rebooting i got a white back ground with grey box that had in black dell bios updating, or something like that.

and yes still no difference from befor the update.

---

### Post by qwill on 2008-08-06
Here you will find a solution for keeping your GPU at a lower frequency without any noticeable performance downgrade.
It reduced GPU temp from 10 to 20 C in my case.

see : [http://ubuntuforums.org/showthread.php?p=5534254#post5534254](http://ubuntuforums.org/showthread.php?p=5534254#post5534254)
Qwill

---

### Post by vandorjw on 2008-08-06
> **trooperchix said:**
> "Configure Dellfand"

Um, what?  I've gotten this far, but what do you mean by "configure Dellfand"?

By "Configure Dellfand, what it wants is,

Sudo Dellfand "1 or 0" "Time" "Temp 1" Temp 2" "Temp 3"

What I mean by 1 or 0 is: 0, Dellfand will keep you updated on the temperature and Fan Speed, while choosing 1 will have Dellfand running in the background.

Time = How often Dellfand checks the CPU Temp. (in seconds)

Temp1 = Temperature that the Fan will shut OFF.
Temp2 = " " " " will be ON (but low)
Temp3 = " " " " will be ON (but High) 
 


> **mrynit said:**
> where does the error come from? is it a pop up box in the top panne or a pop up window? It could be a bad power brick.


This Error is a BIOS error.

Do not worry, there is nothing wrong with your brick, you just need to stop Dellfand before you turn off your computer. That way you give the controll of the Fan back to the BIOS when it turns off.

/etc/init.d/dellfand stop

---

### Post by vandorjw on 2008-08-06
> **phynix said:**
> The only problem I have with the program is that it revs. When it reaches a high it will go for a few secs then stop then start again.

My Fan did that to. 
I noticed that when I run on Battery, my fan works much better...

I do not know how to fix the "on, off, on off..."

---

### Post by Crowchild on 2008-08-07
> **cc7gir said:**
> My Fan did that to. 
I noticed that when I run on Battery, my fan works much better...

I do not know how to fix the "on, off, on off..."

This drove me crazy. I do a lot of transcribing and found the fan coming on and off. I've removed dellfand for now but a fix would be great.

---

### Post by anjilslaire on 2008-08-08
> **qwill said:**
> Here you will find a solution for keeping your GPU at a lower frequency without any noticeable performance downgrade.
It reduced GPU temp from 10 to 20 C in my case.

see : [http://ubuntuforums.org/showthread.php?p=5534254#post5534254](http://ubuntuforums.org/showthread.php?p=5534254#post5534254)
Qwill


Has anyone else tried this yet? Thoughts?

---

### Post by mrynit on 2008-08-09
in the past 3 days the fan has not changed its bad behavior. Odly enough this day it has been working perfectly fine.

I installed these packages after the BIOS flash.
sensors-applet	top panel display of gpu cpu temps
i8kutils	see below
gkrellm-i8k	gui monitor of system stat, includes fans. swtich fans auto and manual mode. click on the fan to change the speed. its like i8kmon

i8kutils contains
=================
sensors-applet	top panel display of gpu cpu temps
i8kutils	see below
gkrellm-i8k	gui monitor of system stat, includes fans. swtich fans auto and manual mode. click on the fan to change the speed. its like i8kmon

I did this [http://ubuntuforums.org/showpost.php?p=4829612&postcount=2](http://ubuntuforums.org/showpost.php?p=4829612&postcount=2) maybe that is why the fan is acting like it is some what working. I think i should remove it and see how the fan behavies.

---

### Post by xcesarfrancox on 2008-08-09
My CPU's temp is above 45°C and my GPU's over 60°C is it bad?

How can I correct this?

---

### Post by dfrandin on 2008-08-10
I have a Vostro 1400, originally with Vista Business, now running Ubuntu 8.04.. I'm of the impression that the Vostro 1400 is identical to the Inspiron 1420.. I have Nvidia 8400M video, so I'm VERY concerned about cpu/gpu temps, so I wonder if the dellfand mentioned earlier will work for me...

Dave

The Nvidia server settings temp display sez my gpu is at 73C.. I've applied the recommended A09 bios update..

---

### Post by anjilslaire on 2008-08-10
Ok, maybe I'm missing something in this therad, but what's the standard, accepted method to find out your GPU temp?

---

### Post by xcesarfrancox on 2008-08-11
> **anjilslaire said:**
> Ok, maybe I'm missing something in this therad, but what's the standard, accepted method to find out your GPU temp?

if you have nvidia-settings you can go there and under PowerMizer there's a Thermal Monitor, it displays your GPU Core's temp, also you can

```
sudo aptitude install sensors-applet
```

and then add the applet to your panel, it will show the same temp, but on your panel, it will also display your CPU's temp

---

### Post by anjilslaire on 2008-08-11
Hmm,

see attached, no thermal details at all. Weird.

---

### Post by aidave on 2008-08-12
I haven't had the heat problems others here have, but my laptop does get very hot when running 3D games.

I find one solution is a USB laptop cooler.

I have "Lapcool3" and it works well to keep the laptop from overheating in standard daily usage.

---

### Post by xcesarfrancox on 2008-08-12
> **anjilslaire said:**
> Hmm,

see attached, no thermal details at all. Weird.

Try installing sensors-applet and then adding the applet to the panel, you'll see the GPU and CPU temperatures in it

---

### Post by mrynit on 2008-08-13
@anjilslaire
[[img]http://arch.kimag.es/thumbs/23127836.png[/img]](http://arch.kimag.es/share/23127836.png)

i just installed the applet and i could see the gpu them. to beable to see cpu temps and fan speed you will need i8k

---

### Post by davidbruington on 2008-10-25
Ok, I know this post is a little old... but maybe someone will see this cry for help. I have an inspiron 1501 w/ AMD turion 64 X2, based on a ATI Mobo (w/ integrated ATI Xpress 1150 graphics)... my fan throttles fine in M$, but under linux it only runs on low, which makes it get a bit hot... my problem is that NO PROGRAMS detect my fan. I've installed lm-sensors, dellfand, gkrellm, nothing can recognize that I even HAVE a fan. 

Am I missing something? I've tried reinstalling and reconfiguring lm-sensors several times, just to make sure... Any thoughts would be greatly appreciated.

---

### Post by indigoshift on 2008-10-25
From what I've read, Dell uses proprietary chips to monitor temperature, and lm-sensors is kind of hit and miss when trying to talk to those chips.

For what it's worth, once I upgraded to 8.04.1, Ubuntu managed my fans and temperature just fine.  Still can't find a good app to display the unit's temp, though.

---

