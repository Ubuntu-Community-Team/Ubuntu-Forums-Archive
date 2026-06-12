---
title: "Breezy Badger running SLOW"
date: 2006-03-01
forum: Desktop Environments
---

### Post by Joelist on 2006-03-01
Hi,

I am new to Linux, and have just installed Ubuntu Breezy Badger on my laptop. Before (on XP), this was a snappy and fast machine, now I am getting REALLY slow performance such as:

a) Boot up times in the 5 minute range

b) applications taking 30 sec or more to open

c) machine hangs up if more than one application attempted to open

d) even mouse clicks have about a 2 sec delay

I checked the Device Manager, and it does not appear to show my CPU as a Pentium M, my RAM, etc. 

Is there some type of tuning I need to do? My hardware specs are:

Pentium M 2.0 Ghz (Dothan)
2 GB RAM
60GB 7200rpm HDD
DVD Writer

Thank you in advance for any help you can give.

JT

---

### Post by zxee on 2006-03-01
What does 'uname -a' output when typed in a terminal? Also did you always have this problem or did it start after installing more software e.g. with apt-get?
Something doesn't seem right with the ram you have installed your laptop should be pretty fast. Last question 4 now-is the laptop overheating-does the fan come on?

---

### Post by Joelist on 2006-03-01
Terminal shows the following:

i686 GNU/Linux

This is very odd as I did download the correct package.

How do I get it reconfigured properly?

---

### Post by Joelist on 2006-03-01
bump.

---

### Post by Joelist on 2006-03-01
Actually x686 does make sense for a Pentium M

---

### Post by Joelist on 2006-03-02
Does anyone have any ideas? 

This is a modern laptop that I put Ubuntu on as a comparison against Windows XP. Based on what I have seen thus far Linux would have to be considered a sick joke. However, I would like to think that the real cause is a tuning issue or some sort of install problem.

---

### Post by Didjit on 2006-03-02
Did you try bringing up the system monitor and see if a process is sucking up your resouces? Applications->System Tools->System Monitor. Or if in a console session, just issue the command TOP.

With your hardware specs are about 4 time faster then mine and Ubuntu runs fine even w/all the extra GUI eye candy.

HTH

Didjit

---

### Post by Joelist on 2006-03-02
System monitor did not show anything especially weird, except CPU usage of 42% with no applications running. 

Could the syrup like performance be connected to the LONG boot time (over 5 minutes)?

---

### Post by Bokonon on 2006-03-02
My system seems a bit bogged down too.  I just seemed snappier when I first installed.  It isn't bad, but slightly noticeable.  Way better than a windows system after a similar period of time.

I will try some of the suggestions above, but I am pretty strict about installing software and try to keep things to a minimum.  I have been monitoring the system, uninstalling what I can get rid of safely and I even ran clamscan to check if something got through.  Nothing yet, but I will keep working at it.

FYI, AMD64 3500, 2G RAM, 6800GT, so I am pretty certain it isn't the hardware.

---

### Post by Joelist on 2006-03-03
I wish I could agree with you about Ubuntu outperforming an XP box, but my experience is showing the opposite.

My XP build on this laptop (that I am putting Linux on) was there for well over a year, and never reimaged. It always booted all the way up (including NIS) in 20-30 seconds and nothing I ran had even a slight lag. Linux (Ubuntu) is taking over 5 minutes to boot, and everything I do is so laggy that it feels like the computer is immersed in tar. 

I was going to recommend Ubuntu to a friend who has a low powered PC, but after this experience I would be afraid of a disaster. Unless of course we can solve the performance bugs.

---

### Post by RAOF on 2006-03-03
There really must be some solution to your performance problem.  Some part of your setup is seriously wrong.

What was using CPU when nothing (else) was running?  You can get that sort of detail from the system monitor.

Are there any kernel messages?  You can get them from the System Log viewer, or by typing "dmesg" in a terminal.

Aside from the boot (Breezy does boot, in general, slower than windows.  But not 5-minutes slower!) I've found Breezy (and now Dapper) to be substantially faster than windows.  There should be something simple to fix with your laptop.

---

### Post by Joelist on 2006-03-03
That's what I am hoping. This lappy has very good hardware, and I let Ubuntu control the install. I guess the next step is to use WipeDrive to blow everything away and try Ubuntu again so I know I am working with a "pure" install. If it is still like tar I will have to do more investigating or move to another distro.

---

### Post by RAOF on 2006-03-03
[QUOTE=Joelist]That's what I am hoping. This lappy has very good hardware, and I let Ubuntu control the install. I guess the next step is to use WipeDrive to blow everything away and try Ubuntu again so I know I am working with a "pure" install. If it is still like tar I will have to do more investigating or move to another distro.[/QUOTE]
Maybe.  As a first guess, what graphics driver is being used?  You can check that out in /etc/X11/xorg.conf.

---

### Post by akiro.yamamoto on 2006-03-03
[QUOTE=Joelist]System monitor did not show anything especially weird, except CPU usage of 42% with no applications running. 

Could the syrup like performance be connected to the LONG boot time (over 5 minutes)?[/QUOTE]
Something is definately wrong there. The system is not supposed to be at 42% CPU
utilisation with NO APPS running.
Right now I have Nautilus, Firefox and Document Reader (PDF Viewer) and my
system is fluctuating between 16%-26% and I have a Celeron D 326 (2.53 Mhz) CPU. As well as using 192 MB Ram.
Check your System monitor and see what app or service is draning your system like that.

---

### Post by incubus on 2006-03-03
Strange. I have the same laptop configuration and everything is working fine. I'm using the 686-compiled kernel as well.

What I would do:
1. As RAOF said, see if you need a specific driver for your graphics card. X might be software-emulating everything instead of taking advantage of a graphics processor that you may have.
2. Install either fluxbox or xfce4 to see if the problem is only in Gnome or KDE.
3. Double check the BIOS setup.
4. run "cat /proc/cpuinfo" and also see if the memory stick is being recognized correctly.
5. Install cpufrequtils and see if the cpu scaling is working properly.
6. Burn and boot a live distro, such as Knoppix or Mepis, to rule out some Ubuntu weirdness.

Just curious. Is that a Dell?
Plus, is there a part in the boot that takes particularly long? In my case, since I'm usually at different places sometimes the network probing takes so long that I just CTRL+C it.

incubus

---

### Post by Didjit on 2006-03-03
Start digging through your logs and see if anything fishy is there. Logs are located /var/logs. Applications-> System Tools -> System Log is a nice GUI way to view them. I can't tell you exactly what to look for other then excessive entires within a short period of time.

Excessive logging can slow down performance. I once had a [LEFT][COLOR=red][FONT=serif]**_distro_**[/FONT][/COLOR][/LEFT]
 dogging my [LEFT][COLOR=red][FONT=serif]**_pc_**[/FONT][/COLOR][/LEFT]
 for a few days until I found excessive PSAD logging was the culprit.

HTH

Didijit

---

### Post by riker1968 on 2006-03-03
do a sudo ps -aux
this will let you know what processes are active on your system and what percentage of memory and cpu are using.

post the result for more info

---

### Post by Joelist on 2006-03-03
error

---

### Post by Joelist on 2006-03-03
My lappy is an Alienware Sentia, fully loaded, so this makes no sense.

In an update, I loaded SuSe Linux 10 to see if the same behavior occurs. Thus far:

The setup takes about as long (6+ hours)
The bootup also is in the 5+ minute range
will speak to desktop performance once I get to the desktop

If the desktop behavior occurs again, then this is a Linux issue rather than an Ubuntu issue specifically. At that point I will likely try updating the kernel and pulling in the Intel 855GM chipset drivers from Intel.com.

---

### Post by patrickfromspain on 2006-03-03
I installed ubuntu on a laptop from a friend.. the specs were: pentim M 1,73Ghz, 2gigs ram, 80gigs HDD and X600 graphics card... ubuntu flied on it!

---

### Post by Simimi on 2006-03-03
I am having a simliar problem. About 3 weeks ago, I got some updates and my Gui started running REALLY nice. I am running Ubuntu on a AMD-K6 233mhz comp from 94/95 and the Gui was so bad it made doing anything on it a pain. Then it got nice and speedy and I started doing everything on it. But now, firefox is so laggy even with my nice broadband connection that checking my email is just not worth it anymore...
 Any Ideas?
 Love-mimi

---

