---
title: "ubuntu 10.10 - blank screen on sleep and overflowing box on dell mini 1012"
date: 2010-10-13
forum: Dell Ubuntu Support (CLOSED)
---

### Post by tikusjamban on 2010-10-13
i have a dell mini 1012..iv installed the ubuntu 10.10...there is some problems that iv neverdah on 10.04..
 
blank screen when i close the lit off...then when i opend the lid..its stays blank..i did everything to make the screen came on..but i cant except pust the power button for couple of second and turn it on again...
 
box overflowing on my dell..on my 10.04 this situation is kinda imposibe....
 
can some one or anyone help me in this...

---

### Post by olivierroy on 2010-10-14
Same problem occurs on my HP Elitebook 2530p.

---

### Post by Mark Uhde on 2010-10-15
Same problem, make sure you note what you can on this bug report I opened:

[https://bugs.launchpad.net/ubuntu/+bug/632538](https://bugs.launchpad.net/ubuntu/+bug/632538)

I'm amazed such a major bug on such a common laptop hasn't been more widely noted.

Now, about the "overflowing box" - I'm not totally sure what you're referring to there?

---

### Post by pheonixcoder on 2010-10-16
I have the same situation with my Dell XPS Studio 16 laptop. I have a 64 bit intel processor with ATI 1GB RAM dual boot with Win 7. I have ubuntu 64 bit 10.04 installed. In my prower settings have the option set for blank screen when i close the lid. when i open i cant get the ubuntu screen, the screen goes absolutely blank. I have to restart every time. I still new with ubuntu, so any pointers would be appreciated. Please let me know where to look for the logs may be posting would help debug the issue.:confused:

---

### Post by Mark Uhde on 2010-10-16
This seems to be affecting a lot of Dell models. Is there anyone who knows what could be different about Dells?

---

### Post by gibbylinks on 2010-10-16
Same on Inspiron 1501

---

### Post by yeahitsmeagain on 2010-10-16
I have a Mini 12, when I open the lid, the screen is black as well.  I slide my finger back and forth on the mouse pad and the log in screen comes back. It takes a few seconds but works fine an no reboot is required.

---

### Post by fdmille on 2010-10-17
My Gateway NV7919u laptop (Ubuntu 10.10, i5 Intel CPU, with i915 on board Intel Video) has kind of the same issue, except it seems to be reversed.

I get the Grub menu ok.  The problem is the screen turns black during the operating system load. I can login (in the blind) and can hear the gnone desktop come up, but the screen stays black.  I've discovered that if I close the lid and reopen it, the screen comes up.  This only started happening after I upgraded from Ubuntu 10.4 to 10.10.  And if I load an earlier version of the kernel, which I was using with 10.04, I don't have this problem.  Therefore, this seems to be some sort of power management issue, maybe.

---

### Post by tikusjamban on 2010-10-18
> **Mark Uhde said:**
> Same problem, make sure you note what you can on this bug report I opened:

[https://bugs.launchpad.net/ubuntu/+bug/632538](https://bugs.launchpad.net/ubuntu/+bug/632538)

I'm amazed such a major bug on such a common laptop hasn't been more widely noted.

Now, about the "overflowing box" - I'm not totally sure what you're referring to there?

the overflowing box are...if ur open the application..than click on file...and then select folder...the box is oversize than the screen...the 'ok' and 'cancel' button are hidden far under the screen....this situation happen is almost all the applications...

---

### Post by olivierroy on 2010-10-18
Just installed the latest recommended updates and the black screen problem seems to be resolved on my Elitebook 2530p.

UPDATE: The problem reappears when the computer is running on battery, i.e. when the power adapter is **not** plugged.

---

### Post by pheonixcoder on 2010-10-18
I have an update the same thing happened with me while i was working on my system. which was very strange but i couldnt find any logs regarding this. Does anyone know under which category these logs would be there so that may be someone can debug. Any pointers would be appreciated.

---

### Post by 87linux on 2010-10-18
Out of curiosity, does anyone have dedicated swap space on their boot record? I'm thinking this might be a source of the problem, as I deleted it when I upgraded to 10.10 when the problems arose.

---

### Post by Mark Uhde on 2010-10-19
It's became clear from the bug report I filed that this is not a 1012-only or even a Dell-only bug. Now we need to start figuring out what all the systems it's happening to have in common, right?

---

### Post by olivierroy on 2010-10-19
I've updated my earlier reply stating that the problem was solved after installing updates on my Elitebook 2530p. The problem reappeared when the computer was running on battery, but only then. On AC power the problem did not occur.

Searching around for posts on "suspend" and "battery" or "power" together, I found this: 

[http://ubuntuforums.org/showthread.php?t=471855&page=21](http://ubuntuforums.org/showthread.php?t=471855&page=21)

Up to now, following the instruction in the last post seem to have solved the problem for me.

---

### Post by DrWig on 2010-10-21
My laptop (an old Acer 4604) is having many problems with 10.10.  If I start up the laptop on battery, quite often the ubuntu boots to a blank screen where I have to hard reset.  On AC power it happens less, but still sometimes occurs.  I've never been able to hibernate or sleep properly, but never had problems with general booting like this before 10.10

cheers

DrWig

---

### Post by Aitaix on 2010-10-22
happens on my e6510.

---

### Post by pheonixcoder on 2010-10-24
Has anyone tried this script [https://help.ubuntu.com/9.10/hardware/C/pm-suspending.html](https://help.ubuntu.com/9.10/hardware/C/pm-suspending.html) I will give this script a shot once i get back to my notebook. With this issue i simply cant work on my laptop.:)

---

### Post by pheonixcoder on 2010-10-25
you can also have a look at this bug [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/578673](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/578673) may be it will help someone. In this it has been claimed that latest kernel 2.6.36 has solved the issue.:)

---

### Post by giannib on 2010-10-31
same to me, only with >Unity:

after display sleep

dell xps m1530

---

### Post by kooldino on 2010-12-15
Same problem here with a Dell Mini 1012.  Extremely annoying.

---

### Post by kooldino on 2010-12-16
Found this solution for my Dell Mini 1012.  Thank God it works:

[QUOTE="Petri K"]Hi!

This problem affects not just the Lenovo T400 but also for example the new Dell Latitude E4200, HP EliteBook 2530p, Sony Vaio VGN-TT1, Toshiba R600, or anything else with the "Mobile Intel® GM45 Express Chipset" or X4500. I have exactly the same symptoms on my E4200 running intrepid.

The bug most certainly resides in the xserver-xorg-video-intel code. The fact that is manifests itself only with gnome desktop and not with KDE or text mode gives some clue. It is not compiz related as disabling compiz has no effect. I would say that this is a classical multiprocessor concurrency control problem! Disabling all but one core makes the bug disappear.

Here is my suggestion for a workaround. Save in /etc/pm/sleep.d/00CPU with 755 permissions. Note that it has to be called 00CPU so that it gets executed before and after anything else.
```

Code:
#!/bin/sh
# Workaround for concurrency bug in xserver-xorg-video-intel 2:2.4.1-1ubuntu10.
# Save this as /etc/pm/sleep.d/00CPU

. "${PM_FUNCTIONS}"

case "$1" in
	hibernate|suspend)
		for i in /sys/devices/system/cpu/cpu*/online ; do
			echo 0 >$i
		done
		;;
	thaw|resume) 
		sleep 10	# run with one core for 10 secs
		for i in /sys/devices/system/cpu/cpu*/online ; do
			echo 1 >$i
		done
		;;
	*)
		;;
esac

```
Please report if this works for you! The sleep period can easily be made longer if necessary.

Petri K[/QUOTE]

---

### Post by jbogdani on 2011-02-04
Same on AOPEN MINI Pentium M 1.73 GHz. Upgraded from 10.04.

---

### Post by MrKappa on 2012-01-06
Hello' I have a HP Palivion G6 of a fried of mine and none of solutions is working sadly.
It's so bad that suspend and hibernate are so important functions.
When I select suspend then the pc stay with black screen and nothing else, then I can only force to reboot..
Please, any suggestion for me?

---

