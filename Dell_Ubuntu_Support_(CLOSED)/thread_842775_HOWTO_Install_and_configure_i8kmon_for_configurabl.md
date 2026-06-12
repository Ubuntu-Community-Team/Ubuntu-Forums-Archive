---
title: "HOWTO: Install and configure i8kmon for configurable automatic fan speed control"
date: 2008-06-27
forum: Dell Ubuntu Support (CLOSED)
---

### Post by motin on 2008-06-27
Here is how to install i8kmon and set it up with sane settings for a XPS M1330:

1. ```
sudo apt-get install i8kutils
```
2. Add "i8k" on a new line in /etc/modules:
```
sudo gedit /etc/modules
```
3. Add "options i8k force=1" on a new line in /etc/modprobe.d/options
```
sudo gedit /etc/modprobe.d/options
```
4. Here, either restart your computer or run:
```
sudo modprobe i8k force=1
```
5. Open up a new file called /etc/i8kmon:
```
sudo gedit /etc/i8mon
```
And save the following to it:
```
# Run as daemon, override with --daemon option
set config(daemon)      0

# Automatic fan control, override with --auto option
set config(auto)        1

# Report status on stdout, override with --verbose option
set config(verbose)	1

# Status check timeout (seconds), override with --timeout option
set config(timeout)	1

# Temperature thresholds: {fan_speeds low_ac high_ac low_batt high_batt}
set config(0)   {{-1 0}  -1  55  -1  55}
set config(1)   {{-1 1}  55  70  55  70}
set config(3)   {{-1 2}  70  128  70  128}

# For computer with 2 fans, use a variant of this instead:
# Temperature thresholds: {fan_speeds low_ac high_ac low_batt high_batt}
# set config(0)	{{-1 0}  -1  52  -1  65}
# set config(1)	{{-1 1}  41  66  55  75}
# set config(2)	{{-1 1}  55  80  65  85}
# set config(3)	{{-1 2}  70 128  75 128}

# end of file
```
(based on [http://www.cvjb.de/comp/linux/debian/i8kmon](http://www.cvjb.de/comp/linux/debian/i8kmon) but adapted for the one-fan-only XPS M1330)

Now you can run "i8kmon" from a terminal to see (and hear) how it adjusts your fan speed. Or you can add it to the gnome panel (for autostart upon login as well as easy monitoring) by the following instructions:
1. ```
sudo apt-get install gnome-swallow-applet
```
2. Add the swallow applet to the gnome panel by right-clicking on the latter and choosing Add to panel
3. Enter "i8kmon" for Program name and leave the second field blank

Alternatively, you can have i8kmon autostart without the applet part by adding "i8kmon --daemon" as an entry to your sessions autostart list (in System -> Settings -> Sessions)

Note: Even though i8kmon seems to do it's job very well, erratic fan behavior can be experienced due to the built-in fan control methods of Dell's laptops. I am trying to get more advice on how to solve that matter in a parallell thread: [http://ubuntuforums.org/showthread.php?p=5275392](http://ubuntuforums.org/showthread.php?p=5275392) Informative replies in that thread are very welcome!

---

### Post by sc00ter on 2008-06-29
Unfortunately this doesn't work on the M1530, here's the dmesg output:

```

dmesg | grep i8k

[   27.713816] i8k: not running on a supported Dell system.
[   27.713819] i8k: vendor=Dell Inc., model=XPS M1530                       , version=A08
[   27.714137] i8k: unable to get SMM BIOS version
```

The sensors applet will pickup i8k when configured as a daemon, and successfully report the CPU Temp and FAN speed.

---

### Post by motin on 2008-06-30
> **sc00ter said:**
> Unfortunately this doesn't work on the M1530, here's the dmesg output:

```

dmesg | grep i8k

[   27.713816] i8k: not running on a supported Dell system.
[   27.713819] i8k: vendor=Dell Inc., model=XPS M1530                       , version=A08
[   27.714137] i8k: unable to get SMM BIOS version
```

The sensors applet will pickup i8k when configured as a daemon, and successfully report the CPU Temp and FAN speed.

I get the same output - no worries!
And since sensors applet is picking up the scent everything seems ok.

---

### Post by mrynit on 2008-08-13
I followed all the steps but for some reason doing this does not work. The fan will not behave according /etc/i8kmon. I am using a dell inspiron 1420 with 8.04 2.6.24-20-generic.

in my /etc/i8kmon i defined these settings. the rest of the file is the same as the above.
```
set config(0)	{{-1 0}  -1  50  -1  65}
set config(1)	{{-1 1}  40  60  55  75}
set config(2)	{{-1 2}  50  70  65  85}
set config(3)	{{-1 2}  75 128  75 128}
```

I have two fans, one that is controllable and the other is on at a fix speed all the time (uncontrollable).
```
mrynit@dell-desktop:~$ i8kfan 
-1 0
mrynit@dell-desktop:~$ i8kfan - 2
-1 2
mrynit@dell-desktop:~$ cat /proc/i8k 
1.0 A09 HS12GF1 40 -22 2 27660 119940 -1 -22
mrynit@dell-desktop:~$ i8kctl 
1.0 (null) HS12GF1 40 -1 2 27660 119940 0 -1

```


sensors-applet 2.2.1
[[img]http://arch.kimag.es/share/25143876.png[/img]](http://kimag.es/)
i took the screen shot at a different time so that is why the temps are different from the terminal output.

From the above I know that the right fan is the controllable fan. I configured the temp settings to work with it. I got the info from here [http://people.debian.org/~dz/i8k/00-README](http://people.debian.org/~dz/i8k/00-README), also the man page for i8kmon has the same info.

---

### Post by Ryan_macy on 2008-08-13
how would I configure this to make my fan run at medium speed all the time?

---

### Post by mrynit on 2008-08-13
> **Ryan_macy said:**
> how would I configure this to make my fan run at medium speed all the time?

I would assume just setting the fan to 1 in config(0)

```
set config(0)	{{-1 1}  -1  50  -1  65}
```

---

### Post by motin on 2008-08-14
> **Ryan_macy said:**
> how would I configure this to make my fan run at medium speed all the time?

You do understand that this could cause overheating with possibly malfunctioning and broken hardware as a consequence?

---

### Post by Ryan_macy on 2008-08-14
> **motin said:**
> You do understand that this could cause overheating with possibly malfunctioning and broken hardware as a consequence?

I doubt it.

---

### Post by hotplainrice on 2008-09-15
Thanks for saving me hours of figuring out how to silence this machine. You should edit this post to include the 1000->200 timer hack if not the machine whizzes almost every 2-3 seconds

---

### Post by Clockswork on 2008-10-18
Hello! I'm running a xps 1530 and I did all the things u wrote and I think it had some effect on my computer. After I applied the settings it seems as the fans has a higher threshold than before. 

And I have some questions..
1. What does the two blank buttons do in "i8kmon"?
2.What happens if I dont run i8kmon, are the fan settings still applied or are they now  running "as Dell want them to"?
3. I would like to have a GPU threshold of 65 degress celsius, and a CPU threshold of 50 degrees how would I apply those settings?

Is there a way to remove these settings and get back to where I was to compare? 

Thanks you guys!

---

### Post by jmjohn on 2008-11-03
Using 18kmon may be no longer necessary, it's best to update the bios first and see if this fixes the problem.

Here's info on the bios update: [http://linux.dell.com/wiki/index.php/Tech/libsmbios_dellBiosUpdate](http://linux.dell.com/wiki/index.php/Tech/libsmbios_dellBiosUpdate)

On my Dell XPS M1330, fan speeds seem normal after a bios update and switching to the nvidia 173 driver on Intrepid, though the fan seems to run more than normal after wakeup from sleep (anyone else have this problem?).  It seems the fan can't shut down once revved up after wake up.

Does anybody have good information on whether or not this is necessary after upgrading to bios update a13 on an xps M1330?  I'd be interested to hear anyone's thoughts.

-glass.dimly

---

### Post by Clockswork on 2008-11-03
I did a BIOS upgrade for my Dell XPS m1530 and the fans do seem to run better and with better thresholds.
Guide on how to do this can be found here: [http://www.clockswork.org/?p=3](http://www.clockswork.org/?p=3)

---

### Post by Clockswork on 2008-11-03
I did a BIOS upgrade for my Dell XPS m1530 and the fans do seem to run better and with better thresholds.
Guide on how to do this can be found here: [http://www.clockswork.org/?p=3](http://www.clockswork.org/?p=3)

---

### Post by chadeldridge on 2008-12-15
The BIOS on the m1710 does not seem to do a good job at all .. everything is about 60+ right now and the Bios is barely running the fans. i8kmon seems to be my best option, but despite reading the man page i am still very confused about exactly what these levels mean. low_ac high_ac low_batt high_batt .  can someone explain in lamens please?

---

### Post by LudaChr1s7 on 2008-12-15
Hi guys,
I am a fairly new Linux user. I have tried many different fan control programs now including nclock, dellfand and now gkrollm. While gkrollm seems to work, when set on automatic the fan goes on high (which is expected because my laptop is hot and over the degree) but every like 5 seconds or 10 seconds it pulses going to a lower speed and then back up, its not going completely off though just lower and starting up again. I worry this is wearing out the fan. I would also like to know how stop all these programs and just go back to the default Ubuntu fan settings as if I had never tweaked them.
Any help is greatly appreciated.
Thanks

---

### Post by chadeldridge on 2008-12-19
> **chadeldridge said:**
> The BIOS on the m1710 does not seem to do a good job at all .. everything is about 60+ right now and the Bios is barely running the fans. i8kmon seems to be my best option, but despite reading the man page i am still very confused about exactly what these levels mean. low_ac high_ac low_batt high_batt .  can someone explain in lamens please?


OK .. maybe someone can just tell me how to do this then:

1.  I want both fans to kick on mode 1 at 40 and then both switch to mode 2 at 60... stay at 60 until at 40 and then back to 1.  If below 30 both off.

---

### Post by vwbeamer on 2009-01-09
Thanks, I used this to increase the colling on my Inspriron B130, the fan was not running fast enough and the CPU temps were getting up to 50 C.

Running the fan on "1" drop the temp to 30 C

---

### Post by b.karthi-k-yan on 2009-02-13
Hi, 
 im using dell 1420 & tried to installing "i8k"



finally i ended up with this kind of display  [[img]http://arch.kimag.es/share/27814452.jpg[/img]](http://kimag.es/) without fans speed specifications.just with a box containing two numbers

instead of this kind of [[img]http://arch.kimag.es/share/87578189.png[/img]](http://kimag.es/) display

can some body help me in displaying it in a right form:(:confused::(:confused:

---

### Post by mihai.ile on 2009-03-01
> **b.karthi-k-yan said:**
> Hi, 
 im using dell 1420 & tried to installing "i8k"



finally i ended up with this kind of display  [[img]http://arch.kimag.es/share/27814452.jpg[/img]](http://kimag.es/) without fans speed specifications.just with a box containing two numbers

instead of this kind of [[img]http://arch.kimag.es/share/87578189.png[/img]](http://kimag.es/) display

can some body help me in displaying it in a right form:(:confused::(:confused:

we are talking about different things here.
For monitoring only you just need to modprobe i8k with the force option, no need to add anything at start-up or to execute any application.
Then for the nice gui you are talking need to use the gnome sensors applet.

---

### Post by mihai.ile on 2009-03-02
P.S to all of you that use the fan's rpm sensor to display the data:
The fan's rpm may be wrong (as seen in post above, 119940 RPM is waaaayyy too much). You can adjust to the real values as explained in this bug report: [https://bugs.launchpad.net/ubuntu/+source/sensors-applet/+bug/200449](https://bugs.launchpad.net/ubuntu/+source/sensors-applet/+bug/200449)

---

### Post by Checkhovian on 2009-03-09
Hello,

Trying to install i8kmon and having some problems...

```
bethany@dell-laptop:~$ sudo apt-get install i8kutils
[sudo] password for bethany: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package i8kutils
bethany@dell-laptop:~$
```

Help please?

---

### Post by mihai.ile on 2009-03-10
What ubuntu are you using 32,64?
Could it be related to this: [https://bugs.launchpad.net/ubuntu/+source/i8kutils/+bug/309262](https://bugs.launchpad.net/ubuntu/+source/i8kutils/+bug/309262) ?

---

### Post by Checkhovian on 2009-03-10
Ah, using 64 bit Hardy, so I guess that could be the problem. It says it can be compiled, though...?

---

### Post by klein de usa on 2009-03-20
hi 
how can you tell what bit your using? 32bit or 64bit

---

### Post by michael37 on 2009-05-01
> **Checkhovian said:**
> Ah, using 64 bit Hardy, so I guess that could be the problem. It says it can be compiled, though...?

Go for 64-bit Jaunty, it's working very well there.

---

### Post by michael37 on 2009-05-01
Could someone please help me force loading i8k modules in Jaunty?  As far as I read the manual, sounds like Jaunty asks for /etc/modprobe.d/i8k.conf in the new format?

---

### Post by mihai.ile on 2009-05-08
using this configuration I had no problems in loading fan speed info into gnome sensors applet

```

mihai007@mihai007-dell:~$ cat /etc/modprobe.d/i8k.conf 
options i8k force=1
mihai007@mihai007-dell:~$ cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
rtc
i8k
mihai007@mihai007-dell:~$ 


```

My fan speed is around 3000rpm but now on my m1330 with nvidia found another fan at 913rpm but I think it doesn't really exist as the m1330 has one fan only...

---

### Post by l-x-l on 2009-05-13
> **motin said:**
> 
5. Open up a new file called /etc/i8kmon:
```
sudo gedit /etc/i8mon
```


Edit your post. Should be:

```
sudo gedit /etc/i8kmon
```

Not:
```
sudo gedit /etc/i8mon
```

Caused a noob like me a bit of trouble when trying to install.

---

### Post by Boondoklife on 2009-05-21
I think this may have changed:
> **l-x-l said:**
> Edit your post. Should be:

```
sudo gedit /etc/i8kmon
```Not:
```
sudo gedit /etc/i8mon
```Caused a noob like me a bit of trouble when trying to install.

Can anyone verify that the config file is now, /etc/i8kmon.conf. I looked inside /usr/bin/i8kmon and see this line.```
sysconfig   /etc/i8kmon.conf
```

---

### Post by l-x-l on 2009-05-25
> **maletek said:**
> I think this may have changed:


Can anyone verify that the config file is now, /etc/i8kmon.conf. I looked inside /usr/bin/i8kmon and see this line.```
sysconfig   /etc/i8kmon.conf
```


I think it was simply a typo by Motin. It should be "sudo gedit /etc/i8kmon".

---

### Post by gmorando on 2009-06-05
> **jmjohn said:**
> Using 18kmon may be no longer necessary, it's best to update the bios first and see if this fixes the problem.

Here's info on the bios update: [http://linux.dell.com/wiki/index.php/Tech/libsmbios_dellBiosUpdate](http://linux.dell.com/wiki/index.php/Tech/libsmbios_dellBiosUpdate)

On my Dell XPS M1330, fan speeds seem normal after a bios update and switching to the nvidia 173 driver on Intrepid, though the fan seems to run more than normal after wakeup from sleep (anyone else have this problem?).  It seems the fan can't shut down once revved up after wake up.
-glass.dimly

Hello everyone, I have an XPS M1330 too. My fans are very loudy. As suggested above, I tried to upgrade my Bios but it seems it is the last version (A15).

Any idea?

Thanks in advance,
Giovanni

---

### Post by stu002 on 2009-11-01
I am tryig to follow this guide for my C400 as I used the windows version of this app with great success.
 
In the howto that this thread starts with it says to add an addtional line to /etc/modprobe.d/options however on Ubunto 9.10 Koala the modprobe.d folder is not present so I can't find the options file to add a line.
 
Any guidance or update of this howto would be appreciated.

---

### Post by michael37 on 2009-11-01
> **stu002 said:**
> I am tryig to follow this guide for my C400 as I used the windows version of this app with great success.
 
In the howto that this thread starts with it says to add an addtional line to /etc/modprobe.d/options however on Ubunto 9.10 Koala the modprobe.d folder is not present so I can't find the options file to add a line.
 
Any guidance or update of this howto would be appreciated.
Skip this step; Karmic 9.10 doesn't need the force.

---

### Post by Pifilatakanemu on 2009-11-12
edit: ok, i achieved to configure i8k and now i got a problem:

one fan seems to be stucked. the left small button in i8kmon is red. which fan is it? i got an inspiron 6400 with a Dual Core.
sometimes there is quite a big difference between the temperature of the cores (about 5-6 °C) anything to worry about?

Just to check whether I understood i8mon: right now this is my configuration. As I don't have a battery, the last rows are not interesting for me.

# For computer with 2 fans, use a variant of this instead:
Temperature thresholds: {fan_speeds low_ac high_ac low_batt high_batt}
set config(0)    {{-1 0}  -1  52  -1  65}
set config(1)    {{-1 1}  45  66  55  75}
set config(2)    {{-1 1}  55  80  65  85}
set config(3)    {{-1 2}  70 128  75 128}

set config(1) is the fan speed. the first two numbers in the brackets are to identify the fans, are they? the following two are those of interest for me: the first is at what temperature to stop the mode and the 2nd at what temperatur to start. right?
right now the fan cools down till 41. which shouldn't be the case, right? any way to check whether i8mon really is active?

---

### Post by mohegan on 2009-12-29
With Karmic, it is i8kutils version 1.31. So, to configure i8kmon, the configuration file is : **/etc/i8kmon.conf**.

With the old file /etc/i8kmon, it doesn't work.

---

### Post by Pifilatakanemu on 2010-03-05
Thanks for the hint. I tried to make i8kmon work once again today and now it seems to work... theoretically!

In practice, the values in i8kmon.conf are mainly ignore. The fan just cools the CPU down to about 30° in "steps" (it cools for some seconds, than stops for a second, than continues etc.) which is really annoying!

This is my i8kmon.conf:

```
# Run as daemon, override with --daemon option
set config(daemon)      1

# Automatic fan control, override with --auto option
set config(auto)        1

# Report status on stdout, override with --verbose option
set config(verbose)    1

# Status check timeout (seconds), override with --timeout option
set config(timeout)    30

# Temperature threshold at which the temperature is displayed in red
set config(t_high)    75

# Temperature thresholds: {fan_speeds low_ac high_ac low_batt high_batt}
set config(0)     {{0 0} -1 60 -1 55}
set config(1)     {{0 1} 50 70 50 60}
set config(2)     {{0 2} 60 80 55 125}
set config(3)     {{0 2} 70 128 10 128}

#set config(0)   {{- 0}  -1  60  -1  55}
#set config(1)   {{- 1}  50  70  55  70}
#set config(3)   {{- 2}  75  128  70  128}


# end of file
```

Any suggestions about what to do?

---

### Post by rp88 on 2010-06-20
I am also having the same problem as Pifilatakanemu, i8kmon will set the fan speed and another program or the dell bios will change it back to whatever speed it wants. 

I think if we change the timeout from 1 second to 200 miliseconds it will fix this problem, since i8kmon will enforce the desired settings more often, almost immediately overriding the settings the dell bios sets.

I tried setting the timeout to .2 in /etc/i8kmon.conf and restarting i8kmon but i got the following error:
[COLOR="Blue"]
expected integer but got "200.0"
    while executing
"after [expr $config(timeout)*1000] {status_timer}"
    (procedure "status_timer" line 7)
    invoked from within
"status_timer"
    (procedure "main" line 6)
    invoked from within
[/COLOR]

Can anyone help me change the timeout please?

---

### Post by michael37 on 2010-06-20
> **rp88 said:**
> 
Can anyone help me change the timeout please?

No luck here, it seems to work only on 1 second timeouts for me.

---

### Post by palmboy5 on 2010-06-26
Post #9 states there is a hack workaround, anyone know what hes talking about?

EDIT: got it.
[http://ubuntuforums.org/showpost.php?p=5434295&postcount=3](http://ubuntuforums.org/showpost.php?p=5434295&postcount=3)
top of post

---

### Post by palmboy5 on 2010-06-28
It seems for any fan speed that isn't "0", even with a 50ms timeout period the fan still spins up every few seconds.

Also, by setting the script to be run as a startup application, a new instance of it will be run if you log out and log back in. This is pretty stupid, is there a way to autostart this program only once each boot, no matter what happens?

---

### Post by akernan on 2011-05-15
Looks like this thread has been dead for a while.  I have a Dell Inspiron 1564 that is about 1 year old.  Should I use i8kmon?

---

### Post by FerroPower on 2011-08-14
Sorry for sounding noob but I installed i8kmon as given here but I can't seem to get the details related to my current Cpu Fan RPM and what is the exact CPU temperature.
I am using Dell Inspiron 1545 laptop dual core. using Kubuntu 11.04 64 bit OS.

i8kmon shows some number like 52 50 and keeps changing...

I don't know what that number is. Please help.


**[COLOR=Blue][COLOR=Red](EDIT) [/COLOR]P.S.: I got it working I upgraded the Kernel to 3.0 and i8kmon is working !! I can see the Fan RPM in the plasma widget FANSpeed. the Fan works just normal. with CPU temp mostly in 39C- 47C.  [/COLOR]**

---

### Post by Jakin on 2012-01-01
Hello, i have been looking at this subject- all about the net, the Dell (e1505/6400) i am using just doesn't turn on the fan at all.. 
Using i8kmon; the CPU will heat up well past 50c even with the settings i copied exactly from the tutorial (first post). I can manually turn on the fan when i see it is  getting hot, sure, but much rather, how can i just set up the fan to be always on? Sound doesn't bother me. Level 1 keeps the CPU a max of 29c this is perfect. 

Can someone explain how to set this so i never have to bother with it again? ubuntu 10.10

---

### Post by michael37 on 2012-01-02
> **Jakin said:**
> <snip>
Can someone explain how to set this so i never have to bother with it again? ubuntu 10.10

My only useful advice is upgrade to 11.10.

---

### Post by kenju4u on 2012-05-24
Hello,

I have a Dell Vostro 1500 with Ubuntu 12.04. I have tired things from a few different forms without success. My temp range is between 47C - 60C. Mostly in the upper 50's. The fan speed is showing as right fan 0 but I can hear the fan running at times but just not at high. I believe I only have one fan. I had a few questions:

1) Does the issue with Dell's still exist in 12.04?

2) I was able to perform the steps on page 1 of this tread successfully, but the fan is not kicking into high. How can I can I set it to go on high through the config?

3) I have crellm installed for monitor. Is there something better I can use?

---

### Post by Kooothor on 2012-07-26
Hello and sorry for necroposting but for future googlers :

The stuff described in the first post **worked for me** :
Ubuntu Server 12.04, fans were at full speed after kernel update, pwmconfig detected nothing.

Do stuff described in post #1, and add this to /etc/rc.local to have the fan spin down after boot
```
(sleep 60; i8kfan 1 1) &
```

Here is my machine :
Libsmbios version:      2.2.28
Product Name:           PowerEdge SC440
Vendor:                 Dell Inc.
BIOS Version:           1.5.0
System ID:              0x01DF

And the error message for googlers :
/usr/sbin/pwmconfig: There are no pwm-capable sensor modules installed

---

### Post by kenju4u on 2012-08-12
Great thanks I installed everything as the post #1 and see a difference but what is this suppose to do again?

(sleep 60; i8kfan 1 1) &

Also I have a dell Vostro 1500 with only fan but that fan is showing as 0 RPM. I know physically the fan is running. What can I do to have the fan speed show up correctly?

Here are my system specs:
MEM: 2.0 GiB
processor: Intel® Core&#8482;2 Duo CPU T5270 @ 1.40GHz × 2
Graphics: GeForce 8400M GS/PCI/SSE2 using 
OS TYPE: 32-bit

---

### Post by michalt on 2012-09-08
Hello, I installe i8k on my Dell Vostro 3360 with Ubuntu Precise 12.04. It works as expected although when i start i8kmon it causes computer to microfreeze every time the deamon checks the temperature. This makes it quite unusable. It seems the freeze is caused whenever i8kctl or i8kfan is executed by the daemon. 

Even just running "cat /proc/i8k" causes system to freeze for a quarter of second.

Any hints?

---

### Post by kuknick on 2012-09-11
Hi, I have the same problem on 3360 with 12.04 and i8kmon. I don't know how to fix it, but advice you to update BIOS. As Dell support site states they have updated Fan/Thermal table in last version (which is A04).

---

### Post by michalt on 2012-09-11
> **kuknick said:**
> Hi, I have the same problem on 3360 with 12.04 and i8kmon. I don't know how to fix it, but advice you to update BIOS. As Dell support site states they have updated Fan/Thermal table in last version (which is A04).

I have A04 here so problem still persists. (Anyway flashing the Dell BIOS on Linux is problem of it's own and I'm bit distracted by the fact I totally bricked my HP 43320s while flashing two weeks ago).

---

### Post by michalt on 2012-09-13
One solution would be to write a script with similar functionality as i8kmon to monitor core temperature through the sensors. This would avoid microfreezes which only happens when accessing /proc/i8k . The i8kfan command seems to work properly. I found such script here in post #9 [https://bbs.archlinux.org/viewtopic.php?pid=780692](https://bbs.archlinux.org/viewtopic.php?pid=780692)

Though there are problems with this script - it uses ACPI temperatures which are generally lower on my system, the coretemp-isa-0000 bus readings would be better.

Also the script fails to separate temperature reading from the acpi command output - probably because on my system acpi -t output is two lines (for two cores) and original was one line (one core). Someone more fimiliar with sed command can help here.

---

### Post by michalt on 2012-09-13
Some followup in this selftalk: 

The script linked in previous post can be made working for two cores by updating line 15 this way:

temp=`acpi -t | grep "Thermal 0" | sed -e 's/\(\.[0-9]\+ \)\?degrees C$//' -e 's/^Thermal 0: ok, //'`

Anyway script is not of real help, because apparently i8kfan causes microfreezes too.

---

### Post by post-factum on 2013-01-15
Any progress on fixing the issue with i8k microfreezes?

---

### Post by ozp on 2013-02-16
I have a Inspiron-7520 ( 15r special edition with 3rd gen i7)

This tutorial worked for me (the first post)

> 

Open up a new file called /etc/i8kmon:



I also create /etc/i8kmon.conf (with same contend)


The FAN problem is gone.

But I noticed that the temperature was getting too hot (around and above 70°C)

Then I turned off the Discrete video card and the temperature now its around 60°C 


There are tons os questions at ask.ubuntu about FAN, the answer for many people is here at the first post (even being a very old post)

---

### Post by ohrus on 2013-02-16
Thank you so much for this.  Can't believe I've finally found a fix for my noisy fan problem.  

I have the same laptop as ozp above - thank you as well for showing up in a google search! :D

As an added step, in case others run into this, I was getting an error after initially following the instructions: can't find package Tk 8.5.  To solve this I removed and updated tk and tcl:

sudo apt-get remove tk8.4 tcl8.4
sudo apt-get install tk8.5 tcl8.5

Cheers.

---

### Post by vitorafsr on 2013-06-12
Hello all.

I'm updating this package, and the source code is here at 

[https://launchpad.net/i8kutils](https://launchpad.net/i8kutils)

and the *.deb are at my ppa

ppa:vitorafsr/ppa

I welcome any feedback. For now I'm fixing bugs. And a plan for future releases are at

[http://registrosdeengenharia.blogspot.com.br/2013/06/linux-i8kutils-package-for-dell-laptops.html](http://registrosdeengenharia.blogspot.com.br/2013/06/linux-i8kutils-package-for-dell-laptops.html)

Cheers.

---

### Post by PcCopat on 2013-06-13
Hello, I have an Inspiron 7520 SE laptop and I'm experiencing the fan problem. Although I installed i8kmon, I couldn't make it run automatically with the parameters -a and -d (automatic and without the user interface). apt-get couldn't find gnome-swallow-applet and I have no idea how to add this app to startup list. Also can anybody explain how to install i8kutils above? This is my very first hours with Linux and I'm trying to learn the basics, but fan sound is really annoying. :(

---

### Post by rrich1974 on 2013-06-14
read carefully the first post.

LE.
instead of "i8kmon" file, it should be named "i8kmon.conf"

---

### Post by ppierpaolo on 2013-06-15
The first message could maybe be updated:
> **motin said:**
> Here is how to install i8kmon and set it up with sane settings for a XPS M1330:
3. Add "options i8k force=1" on a new line in /etc/modprobe.d/options
```
sudo gedit /etc/modprobe.d/options
```


If I'm not wrong, on recent Ubuntu releases (at least for my 12.04 version) the "options" file has been replaced by files with the .conf extension. The filename doesn't matter, it just has to be something like filename.conf . :)

---

### Post by michalt on 2013-06-16
> **vitorafsr said:**
> Hello all.

I'm updating this package, and the source code is here at 

[https://launchpad.net/i8kutils](https://launchpad.net/i8kutils)

and the *.deb are at my ppa

ppa:vitorafsr/ppa

I welcome any feedback. For now I'm fixing bugs. And a plan for future releases are at

[http://registrosdeengenharia.blogspot.com.br/2013/06/linux-i8kutils-package-for-dell-laptops.html](http://registrosdeengenharia.blogspot.com.br/2013/06/linux-i8kutils-package-for-dell-laptops.html)

Cheers.

I tried the new version from the ppa. My system is Dell Vostro 3360. The problem with i8k is that it introduces microfreezes any time the system is polling for the temparature and fan or is setting fan speed. This makes the utility unusable. Same with the version provided by ubuntu and this one. Would be very nice if you can debug this.

---

### Post by fievelk on 2013-08-10
I wrote this guide on my blog:
[Keenformatics: How to solve dell laptops fan issues in Ubuntu]("http://keenformatics.blogspot.it/2013/06/how-to-solve-dell-laptops-fan-issues-in.html")

It's a mix of different guides I found on the internet, and I thank the author of this thread for his post.
But there's still a problem for me: sometimes i8kmon gets overwritten by (I think) the default fan behaviour. So, even if the temperature is lower than the one I set with i8kmon, the fans start running; to stop them I need to stop and restart i8kmon. 

Any help about this issue?

---

### Post by vitorafsr on 2013-10-16
> **michalt said:**
> I tried the new version from the ppa. My system is Dell Vostro 3360. The problem with i8k is that it introduces microfreezes any time the system is polling for the temparature and fan or is setting fan speed. This makes the utility unusable. Same with the version provided by ubuntu and this one. Would be very nice if you can debug this.

I'm working on this. If you are interested in the discussion, it is going [here]("https://bugs.launchpad.net/i8kutils/+bug/1179282").

---

### Post by carwe on 2014-01-01
The OP and others have used i8kutils to set the fan speed successfully, but experience that it is immeiately changed back/overridden. This is schedueled SMM BIOS sessions. A workaround is to disable the BIOS fan control, which can be done with a trick. I have described it here, along with complete instructions on how to install and use i8kutils, and some general notes on fan control on Dell laptops:[URL="http://askubuntu.com/questions/63588/how-do-i-get-fan-control-working/398635#398635"]

http://askubuntu.com/questions/63588/how-do-i-get-fan-control-working/398635#398635[/URL]

I have successfully used this method on my Dell Latitude E7440.

---

### Post by Robin_Murray on 2014-01-26
I just bought a dell inspiron 3521, which has only a right side fan. I've installed i8kctl and set up a conf file in /etc/i8kmon as follows:

# Run as daemon, override with --daemon option
set config(daemon)      0

# Automatic fan control, override with --auto option
set config(auto)        1

# Report status on stdout, override with --verbose option
set config(verbose)     1

# Status check timeout (seconds), override with --timeout option
set config(timeout)     1

# Temperature thresholds: {fan_speeds low_ac high_ac low_batt high_batt}
set config(0)   {{-1 0}  -1  50  -1  50
set config(1)   {{-1 1}  50  70  50  70}
set config(3)   {{-1 2}  70  128  70  128}

I am able to manually control the fan speed using the gui, or with i8kctl/i8kfan, however, i8kmon is not automatically controlling the fans.

I started it by: "i8kmon --auto --verbose --nouserconfig" and watched what it was doing while I played a small game to drive up the temperature. It seems like it's still trying to treat the system like it has two fans:

# exec /usr/bin/i8kfan 1 {}
1390754042 1.0 A12 6YRWVY1 66 -22 0 -22 0 0 -22
# exec /usr/bin/i8kfan 1 {}
1390754047 1.0 A12 6YRWVY1 67 -22 0 -22 0 0 -22
# exec /usr/bin/i8kfan 1 {}
1390754052 1.0 A12 6YRWVY1 69 -22 0 -22 0 0 -22
# exec /usr/bin/i8kfan 1 {}
1390754057 1.0 A12 6YRWVY1 70 -22 1 -22 0 0 -22
# exec /usr/bin/i8kfan 1 0
1390754062 1.0 A12 6YRWVY1 70 -22 0 -22 0 0 -22
# exec /usr/bin/i8kfan 1 {}
1390754067 1.0 A12 6YRWVY1 71 -22 0 -22 0 0 -22
# exec /usr/bin/i8kfan 1 {}
1390754072 1.0 A12 6YRWVY1 72 -22 0 -22 0 0 -22
# exec /usr/bin/i8kfan 1 {}
# exec /usr/bin/i8kfan {} 1
# exec /usr/bin/i8kfan {} 2

With only a right side fan, shouldn't all the i8kfan commands be operating on the right fan?

---

### Post by Robin_Murray on 2014-01-27
Please ignore earlier post, I had misnamed my i8kmon.conf file.

---

