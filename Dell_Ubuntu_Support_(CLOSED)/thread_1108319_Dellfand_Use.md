---
title: "Dellfand Use"
date: 2009-03-27
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Checkhovian on 2009-03-27
Hello everyone,

My laptop fan has not been kicking in at all and as a result my Dell 1525 laptop has been running HOT - over 80, until it overheats and dies on me. Running 64 bit Hardy and BIOS updated to Dell's newest.

I put dellfand on earlier today, and can use it to monitor my high temp, but even in daemon mode it isn't turning the fan on at all. 

```
bethany@dell-laptop:~$ sudo dellfand
[sudo] password for bethany: 
v0.9: Fan 0 Status -1 Speed -1 CPU Temp 68C
```

Please, help me control my fan! At this rate, the hardware damage is enough of a reason that I'm going to have to go back to Windows if I want my computer to keep working at all...

---

### Post by mtbsoft on 2009-03-30
Do a search on i8k tools and i8k utils - it has my Dell lappy cool and happy.

---

### Post by Checkhovian on 2009-03-30
Can't install the package on 64-bit Ubuntu, but if anyone can tell me how to work around this it would be very helpful :)

---

### Post by Mr_bleu on 2009-03-30
I have an e1505 and have been using this for 3 yrs. Hope it works for you.
[http://ubuntuforums.org/archive/index.php/t-450904.html](http://ubuntuforums.org/archive/index.php/t-450904.html)


Mr_bleu
June 3rd, 2007, 07:25 PM
Recap:
[http://dellfand.dinglisch.net/](http://dellfand.dinglisch.net/)
Save to Desktop.
system>administration>synaptic manager
Install g++ (I clicked the Search button and typed it in)
Untar the file (I'm a former windows user so I double click, then extract)
Open a terminal
$cd ~/Desktop/dellfand-0.7
$chmod a+x dellfand
$sudo cp dellfand /usr/bin
$sudo cp etc.default.dellfand /usr/bin
$sudo cp etc.init.d.dellfand
$sudo dellfand (This will display current fan status output and temp)
$sudo dellfand 1 10 25 35 43 (My personal settings for dellfan)
OR
$sudo dellfand 0 10 25 35 43 (This will output the status until the terminal is closed)
output from the above command:
Fan 0 Status 2->1 Speed 123960 CPU Temp 37C

Good luck everyone!!

---

### Post by Checkhovian on 2009-03-30
I'm running into trouble with the daemon mode. I'm installing 0.9, not 0.7, but everything seems to run smoothly up to there, then I hit a snag.

```
bethany@dell-laptop:~/Desktop/dellfand-0.9$ chmod a+x dellfand
bethany@dell-laptop:~/Desktop/dellfand-0.9$ sudo cp dellfand /usr/bin
bethany@dell-laptop:~/Desktop/dellfand-0.9$ sudo cp etc.default.dellfand /usr/bin
bethany@dell-laptop:~/Desktop/dellfand-0.9$ sudo cp etc.init.d.dellfand
cp: missing destination file operand after `etc.init.d.dellfand'
Try `cp --help' for more information.
```

Any help?

---

### Post by Checkhovian on 2009-03-30
If I try to skip the daemon step, this is what happens...

```
bethany@dell-laptop:~/Desktop/dellfand-0.9$ sudo dellfand 0 10 25 35 43
Fan 0 Status -1->2 Speed -1 CPU Temp 58C
dellfand: warning: set fan 0 status to 2 last cycle, it's now -1 (BIOS interference ?)
```

Any suggestions welcome!

---

### Post by Mr_bleu on 2009-04-11
You have to cp <copy> to the same directory. /usr/bin  The line you have a problem with had nowhere to cp to.

bethany@dell-laptop:~/Desktop/dellfand-0.9$ sudo cp dellfand /usr/bin
bethany@dell-laptop:~/Desktop/dellfand-0.9$ sudo cp etc.default.dellfand /usr/bin
bethany@dell-laptop:~/Desktop/dellfand-0.9$ sudo cp etc.init.d.dellfand
cp: missing destination file operand after `etc.init.d.dellfand


The destination should be the same as the line above, /usr/bin.

---

### Post by Checkhovian on 2009-04-11
Thanks for your reply. I feel rather dumb for having missed my destination.

So now this is what I have...

```
bethany@dell-laptop:~/Desktop/dellfand-0.9$ chmod a+x dellfand
bethany@dell-laptop:~/Desktop/dellfand-0.9$ sudo cp dellfand /usr/bin
[sudo] password for bethany: 
bethany@dell-laptop:~/Desktop/dellfand-0.9$ sudo cp etc.default.dellfand /usr/bin
bethany@dell-laptop:~/Desktop/dellfand-0.9$ sudo cp etc.init.d.dellfand /usr/bin
bethany@dell-laptop:~/Desktop/dellfand-0.9$ sudo dellfand
v0.9: Fan 0 Status -1 Speed -1 CPU Temp 59C
bethany@dell-laptop:~/Desktop/dellfand-0.9$ sudo dellfand 0 10 25 35 43
Fan 0 Status -1->2 Speed -1 CPU Temp 60C
dellfand: warning: set fan 0 status to 2 last cycle, it's now -1 (BIOS interference ?)
Fan 0 Status -1->2 Speed -1 CPU Temp 59C
```

So basically it's trying to turn on my fan and failing? Fan works with a Windows hard drive in the laptop, but still nothing here....

---

### Post by stargate2500 on 2009-04-12
You need to run  with option 1.

sudo dellfand 1 10 25 30 38

I use these settings and tweak when needed.  1 turns the fan ON.

---

### Post by samsaptak on 2009-04-26
Hi,
I have xps m1210. I am trying to install dellfand 9.0. the chmod a+x dellfand is not working
sumit@Illusion:~$ cd ~/Desktop/dellfand-0.9
sumit@Illusion:~/Desktop/dellfand-0.9$ chmod a+x dellfand 
chmod: cannot access `dellfand': No such file or directory
sumit@Illusion:~/Desktop/dellfand-0.9$ 

I would highly appreciate if someone could help me

---

### Post by david.paige on 2009-05-10
I would like some help with this, as well.  I downloaded dellfand, but it was only the source tarball.  Apparently a compiled version would crush the author's bandwidth.

It wanted to compile when I ran make, but I don't have a compiler, and no experience with installing one on my system.  Does anyone have a compiled version of dellfand anywhere?  If so, I would appreciate it if anyone could point me in the correct direction.

Thanks.

dellfand <at> paiged <dot> fea <dot> st

---

### Post by l-x-l on 2009-05-13
At first I installed dellfand on my laptop & it worked at keeping my CPU cool. But since I also have a NVidia graphics card, the right side of my keyboard was always really warm. The GPU temp easily rose to 70C at idle. From my understanding dellfand can't control the 2nd fan on a Linux OS, which is wierd because I use it in Vista on the same machine & can control both fans.

Anyway I deleted dellfand & tried i8kfan/i8kmon & can now control both fans on my Dell laptop. Keyboard is no longer warm to the touch. I recommend using it. Search this forum for instructions.

---

### Post by v1nsai on 2010-01-25
I was getting the error 'dellfand: warning: set fan 0 status to 0 last cycle, it's now 2 (BIOS interference ?)' using dellfand with verbose output, but running it as a daemon seems to work, hope that helps someone having the same problem as me, I'm using a Dell Studio 1555.

---

### Post by horsemanoffaith on 2010-09-24
To install dellfand on Ubuntu Linux 10.04
 

 Download the dellfand file from [http://www.dellfand.dinglisch.net]("http://www.dellfand.dinglisch.net/"). Ensure that you save the file instead of opening it from the site.
 

 Open a terminal- Applications>Accessories>Terminal
 

 In the terminal, navigate to the location into which you downloaded the file. In my case, the location is **/home/mike/Downloads**.  
 

 My terminal shows **[EMAIL="mike@laptop"]mike@laptop[/EMAIL]:~/Downloads$**
 

 untar the file by typing **tar xvf dellfand-0.9.tar.bz2**
 

 The terminal should output the follwing information:
 **tar: Record size = 8 blocks ** 
 **dellfand-0.9/ ** 
 **dellfand-0.9/dellfand.cc ** 
 **dellfand-0.9/fan.cc ** 
 **dellfand-0.9/gpl.txt ** 
 **dellfand-0.9/bofn.licence.txt ** 
 **dellfand-0.9/MANIFEST ** 
 **dellfand-0.9/etc.init.d.dellfand ** 
 **dellfand-0.9/etc.default.dellfand ** 
 **dellfand-0.9/README ** 
 **dellfand-0.9/DISCLAIMER ** 
 **dellfand-0.9/Makefile ** 
 **dellfand-0.9/CHANGES ** 
 

 Do not close the terminal window- just minimize it, you'll be using it later.
 

 Once this is done, you need to ensure that you have the g++ compiler installed on your system. To check this, click on **System>Administration>Synaptic Package Manager. **In the quick search box, type **g++ **and click search. If g++ is not installed, click on the checkbox and click apply. If the g++ compiler isn't installed, you will not be able to compile the program.
 

 Once this is done, go back to your terminal and type the following: **cd dellfand-0.9; make.** This will compile the program and set it up for use on your system.
 

 Once the program is compiled, I test the program by typing **sudo ./dellfand. **If the program has been properly installed, this command will output the version of the program and the status of your fan. My output shows the following: **v0.9: Fan 0 Status 0 Speed 0 CPU Temp 46C ** 
 

  You can set up dellfand to run at startup by editing the **/etc/rc.local** file by doing the following:
 

In your terminal, type **sudo gedit /etc/rc.local**. This will open the /etc/rc.local file with root priviledges. It will output the following: 

 **#!/bin/sh -e ** 
 **# ** 
 **# rc.local ** 
 **# ** 
 **# This script is executed at the end of each multiuser runlevel. ** 
 **# Make sure that the script will "exit 0" on success or any other ** 
 **# value on error. ** 
 **# ** 
 **# In order to enable or disable this script just change the execution ** 
 **# bits. ** 
 **# ** 
 **# By default this script does nothing. ** 
 

 **exit 0**
 

 Between the last line with a # and exit 0, type the executable file for dellfand as well as the values that you want dellfand to execute. The syntax is as follows:  
 **dellfand directory/dellfand  *mode sleep-seconds off low high*[COLOR=#000000][FONT=Times New Roman][/FONT][/COLOR]**

 [COLOR=#000000][FONT=Times New Roman]See [/FONT][/COLOR]**[http://dellfand.dinglisch.net]("http://dellfand.dinglisch.net/")**[COLOR=#000000][FONT=Times New Roman] for the explanation of the values for the program.[/FONT][/COLOR]
 

  For example, my dellfand command line is
 **/home/mike/Downloads/dellfand-0.9/dellfand 1 5 40 50 70**
 

  Here's the edited script:
  

 **#!/bin/sh -e ** 
 **# ** 
 **# rc.local ** 
 **# ** 
 **# This script is executed at the end of each multiuser runlevel. ** 
 **# Make sure that the script will "exit 0" on success or any other ** 
 **# value on error. ** 
 **# ** 
 **# In order to enable or disable this script just change the execution ** 
 **# bits. ** 
 **# ** 
 **# By default this script does nothing. ** 
 

 **/home/mike/Downloads/dellfand-0.9/dellfand 1 5 40 50 70**
 

 **exit 0**
 

  Click the save button and restart the computer. Your fans should now be controlled by the dellfand daemon!

---

### Post by kenju4u on 2012-05-23
This dellfand utility is not available any more. What are my other options?

---

### Post by kenju4u on 2012-05-31
I was able to find the utility and installed it on 12.04 LTS. I also followed the below steps and all seems to be fine while I am logged into Ubuntu, but when i login to XBMC instead the fan does not kick on. What can I do to make sure the same script executes while I am in XBMC? 

- Ken




> **horsemanoffaith said:**
> To install dellfand on Ubuntu Linux 10.04
 

 Download the dellfand file from [http://www.dellfand.dinglisch.net]("http://www.dellfand.dinglisch.net/"). Ensure that you save the file instead of opening it from the site.
 

 Open a terminal- Applications>Accessories>Terminal
 

 In the terminal, navigate to the location into which you downloaded the file. In my case, the location is **/home/mike/Downloads**.  
 

 My terminal shows **[EMAIL="mike@laptop"]mike@laptop[/EMAIL]:~/Downloads$**
 

 untar the file by typing **tar xvf dellfand-0.9.tar.bz2**
 

 The terminal should output the follwing information:
 **tar: Record size = 8 blocks ** 
 **dellfand-0.9/ ** 
 **dellfand-0.9/dellfand.cc ** 
 **dellfand-0.9/fan.cc ** 
 **dellfand-0.9/gpl.txt ** 
 **dellfand-0.9/bofn.licence.txt ** 
 **dellfand-0.9/MANIFEST ** 
 **dellfand-0.9/etc.init.d.dellfand ** 
 **dellfand-0.9/etc.default.dellfand ** 
 **dellfand-0.9/README ** 
 **dellfand-0.9/DISCLAIMER ** 
 **dellfand-0.9/Makefile ** 
 **dellfand-0.9/CHANGES ** 
 

 Do not close the terminal window- just minimize it, you'll be using it later.
 

 Once this is done, you need to ensure that you have the g++ compiler installed on your system. To check this, click on **System>Administration>Synaptic Package Manager. **In the quick search box, type **g++ **and click search. If g++ is not installed, click on the checkbox and click apply. If the g++ compiler isn't installed, you will not be able to compile the program.
 

 Once this is done, go back to your terminal and type the following: **cd dellfand-0.9; make.** This will compile the program and set it up for use on your system.
 

 Once the program is compiled, I test the program by typing **sudo ./dellfand. **If the program has been properly installed, this command will output the version of the program and the status of your fan. My output shows the following: **v0.9: Fan 0 Status 0 Speed 0 CPU Temp 46C ** 
 

  You can set up dellfand to run at startup by editing the **/etc/rc.local** file by doing the following:
 

In your terminal, type **sudo gedit /etc/rc.local**. This will open the /etc/rc.local file with root priviledges. It will output the following: 

 **#!/bin/sh -e ** 
 **# ** 
 **# rc.local ** 
 **# ** 
 **# This script is executed at the end of each multiuser runlevel. ** 
 **# Make sure that the script will "exit 0" on success or any other ** 
 **# value on error. ** 
 **# ** 
 **# In order to enable or disable this script just change the execution ** 
 **# bits. ** 
 **# ** 
 **# By default this script does nothing. ** 
 

 **exit 0**
 

 Between the last line with a # and exit 0, type the executable file for dellfand as well as the values that you want dellfand to execute. The syntax is as follows:  
 **dellfand directory/dellfand  *mode sleep-seconds off low high*[COLOR=#000000][FONT=Times New Roman][/FONT][/COLOR]**

 [COLOR=#000000][FONT=Times New Roman]See [/FONT][/COLOR]**[http://dellfand.dinglisch.net]("http://dellfand.dinglisch.net/")**[COLOR=#000000][FONT=Times New Roman] for the explanation of the values for the program.[/FONT][/COLOR]
 

  For example, my dellfand command line is
 **/home/mike/Downloads/dellfand-0.9/dellfand 1 5 40 50 70**
 

  Here's the edited script:
  

 **#!/bin/sh -e ** 
 **# ** 
 **# rc.local ** 
 **# ** 
 **# This script is executed at the end of each multiuser runlevel. ** 
 **# Make sure that the script will "exit 0" on success or any other ** 
 **# value on error. ** 
 **# ** 
 **# In order to enable or disable this script just change the execution ** 
 **# bits. ** 
 **# ** 
 **# By default this script does nothing. ** 
 

 **/home/mike/Downloads/dellfand-0.9/dellfand 1 5 40 50 70**
 

 **exit 0**
 

  Click the save button and restart the computer. Your fans should now be controlled by the dellfand daemon!

---

### Post by mikewhatever on 2012-06-05
Is XBMC installed on the same computer, and does it use the same home folder (user name)? Make sure the path, /home/mike/Downloads/dellf... is correct.

---

