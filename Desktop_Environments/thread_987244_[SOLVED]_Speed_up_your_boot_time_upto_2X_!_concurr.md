---
title: "[SOLVED] Speed up your boot time upto 2X ! concurrency=shell works in Intrepid!"
date: 2008-11-19
forum: Desktop Environments
---

### Post by prshah on 2008-11-19
Summary:

Edit your /etc/init.d/rc file (with "sudo") ```
gksudo gedit /etc/init.d/rc
```, and change the value```
CONCURRENCY=none
``` to value```
CONCURRENCY=shell
```, then reboot. Notice the faster bootup time.

This did work in earlier versions of Ubuntu, but broke with HAL in Gutsy. There was a workaround, (which is also applicable to Hardy) but it's not required in Intrepid!

My bootup time reduced from over 70s to under 35s ! I'm attaching bootchart files to illustrate.

CAVEATS:
[indent]a. At your own risk, please
b. Your mileage may vary
[/indent]

---

### Post by tgpraveen on 2008-11-19
could u also shed some light on what the change actuaaly means? is it completely safe? dont wanan wreck my sys.

others pls share ur results.

---

### Post by king_lear on 2008-11-19
Only a moderate increase in speed in my system
No damages though

---

### Post by prshah on 2008-11-19
> **tgpraveen said:**
> could u also shed some light on what the change actuaaly means? is it completely safe? dont wanan wreck my sys.


concurrency=shell allows certain startup scripts to be executed simultaneously, rather than serially (ie, waiting for scripts to be completed in order).

It didn't work in Gutsy or Hardy since there was a specific issue of a conflict in the load order of dbus and HAL; however there was an easy fix which simply ensured that HAL loaded _after_ dbus.

In Intrepid though, that fix doesn't seem to be required. Just making this change in the /etc/init.d/rc file is enough.

IMPORTANT NOTE: This will only speed up the _boot process_ (When the loading bar (usplash) is active). It should not have any effect on the actual performance of the system. If you feel your entire system is faster then it's probably psychological.

If you run into problems, changing "concurrency" back to "none" should clear it up (you may need the "recovery shell" option in GRUB).

Also, apparently those with multiple processors will benefit most. (Eg, Core 2 Duo, etc)

---

### Post by rbolio on 2008-11-19
well, boot chart claims timing was the same (35 sec) [with auto loggin enabled...]
 but i did *see* boot up bar go faster... so 

Thanks!

---

### Post by prshah on 2008-11-19
> **rbolio said:**
> well, boot chart claims timing was the same (35 sec) [with auto loggin enabled...]
 but i did *see* boot up bar go faster... so 


The bootchart time (near the upper left corner) also shows me only about 1 sec improvement; but the chart's timeline itself shows over 35s improvement. So I'm guessing that the time mentioned is something else; possibly the time _before_ the chart starts.

btw, the boot process ends with the splash screen; so auto-login enabled or not makes no difference in the boot up time (will not show up in bootchart).

---

### Post by der_joachim on 2008-11-20
Please note that this tweak will only work if you have a multicore processor, or multiple processors. Somewhere in the EEE forums I read that for single core single processor machines this tweak will not work or even slow down the system.

Good that the HAL bug is finally squashed. :)

---

### Post by tgpraveen on 2008-11-20
ok so not of much use for me on pentium 4. :-(

---

### Post by snowpine on 2008-11-20
It did not appear to speed up the boot on my atom-based eee pc.

---

### Post by Shwefty on 2008-11-20
Thanks for the tip! I have a Centrino Duo in my laptop, but with changing the script my boot time increases from 77 seconds with "none" to 83 seconds with "shell".    :(  That's measuring from hitting <Enter> in Grub to seeing my Wireless Network needs access to keyring prompt.  Auto-login.

So, double check your boot-times before and after you do this to see if it helps you!  (which just because it didn't for me doesn't me it won't help you)

---

### Post by thierrybo on 2008-11-21
:( I have Intel Core 2 Duo E8400 and Intrepid 64 bit and I only decreased my boot time by 1 second; from 40 to 39s.  I have automatic login and i count from grub to the display of two gnome task bars.

Well, just intalled bootchart : 25s to 23 seconds. We are far away from 2X

---

### Post by thierrybo on 2008-11-21
> **prshah said:**
> 
My bootup time reduced from over 70s to under 35s ! I'm attaching bootchart files to illustrate.


prshah, your first bootchat seems strange. The display time in the upper left corner should match the end of the time line to the right, and yours is not. It shows 31 sec and should display ~70 seconds as your timeline.:???:

---

### Post by der_joachim on 2008-11-22
> **Shwefty said:**
> Thanks for the tip! I have a Centrino Duo in my laptop, but with changing the script my boot time increases from 77 seconds with "none" to 83 seconds with "shell".    :(  That's measuring from hitting <Enter> in Grub to seeing my Wireless Network needs access to keyring prompt.  Auto-login.

I do not think that the wireless network measurement is a good one. For some reason my wireless network (using network manager)  needs anywhere between 1 second and a few minutes to automagically start connecting to my home wlan. For a more objective measurement, check your bootchart.

There is another way to decrease bootup time: profiling. See [http://ubuntuforums.org/showthread.php?t=254263&highlight=profile+boot](http://ubuntuforums.org/showthread.php?t=254263&highlight=profile+boot) . As with the tweak described above: use at your own risk.

---

### Post by habtool on 2008-11-22
If you using the new 'private' folder that is encrypted, this may not mount at boot.
(If you use concurrency=shell)

You can mount it manually of course.

Just a heads up incase someone 'looses' there private folder with email etc in it and then panics ;)

---

### Post by CandyKiller on 2008-11-23
Could someone please explain to me how you track your boot time?  I'd like to see my results with the 'none' and 'shell'

---

### Post by tgpraveen on 2008-11-23
use a stopwatch maybe ur mobiel has one or just use a clock man.

---

### Post by amaroKer on 2008-11-23
Sweet.  Accelerated from ~35 to 28 seconds.  Nice tip.

---

### Post by al_capone on 2009-01-25
hi
my boot time went down from 54 to 45 secs with this tweak. However this is timed with a stopwatch and measured from hitting enter in grub. I have a Core 2 Duo Prosecor 1.86 Ghz in a Dell Vostro.

---

### Post by Copitox on 2009-01-25
How can your computers boot on 35 seconds! i'm dual booting Windows Seven and Ubuntu. Windows seven takes like 40 seconds from grub to a usable desktop and this are my Ubuntu times:


Shell= 74 seconds

None= 1:17 (33 boot bar filling) (44 from the filled bar to a usable desktop)

I'm using a Turion 64x2 with 2G ram... could you PLEASE help to get a decent boot time?

---

### Post by thierrybo on 2009-01-25
Don't know with windows 7 (Vista ?), but with my XP SP1 optimized for performance and no firewall / anti-virus, I boot exactly in 40 seconds from grub to a usable desktop, so exactly the same time as Ubuntu (see my post above), also optimized for performances.

---

### Post by Jakey_TheSnake on 2009-01-31
> **snowpine said:**
> It did not appear to speed up the boot on my atom-based eee pc.

[http://lwn.net/Articles/299483/](http://lwn.net/Articles/299483/)

EEE pc boot in 5 seconds. 


It sped up my boot from 50 seconds to 40 seconds, meh.

---

### Post by mister_p_1998 on 2009-02-02
So is it worth upgrading my P4 3ghz to a dual-core, power wise?
Will I see a power improvement? I know Its more energy efficient, but if its no faster, I wont bother...

Steve

---

### Post by halovivek on 2009-02-02
will it increase the boot up speed for 64-bit ubuntu 8.10.
after this whether i will not get any problem with another programs?

---

### Post by thierrybo on 2009-02-02
Well,

from all the post except the thread starter, you will gain from 2 sec (me), to 9 seconds.

---

### Post by mr-biggles on 2009-05-18
My Acer Aspire One with this hack and others now has a boot time of  15.92 seconds (Y)

---

### Post by udippel on 2009-05-18
Would you care the share the others??
When do you start measuring, btw,. and when do you stop?

---

### Post by hojthojt on 2009-05-18
Hi,
tried this tip it on my tx1151ea with an AMD Turion 64 X2 TL-60 running Ubuntu 9.04. No measurable difference. I have 50 sec from grub to the graphical login prompt.

regards
HojtHojt

---

### Post by shreepads on 2009-10-08
No appreciable difference here after setting concurrency=shell...

Same timings as below before and after
- 31 s from hitting enter in grub list to sign-in prompt
- 20 s from hitting enter after entering login/ password to complete desktop display

Hmm time to run profile/ bootchart?

Details:
Ubuntu 8.04 Hardy Desktop, kernel 2.6.24-24-generic
Intel Core2Duo E7200 on Intel DG33FB motherboard, 2 GB RAM
3 NTFS, 2 ext3, 1 swap partition on single 3gbps SATA drive
ADSL+ modem connected (via LAN) at startup

---

### Post by RJARRRPCGP on 2009-10-25
Looks like an invalid argument and thus ignored. Sorry. :(

(That's why no better boot time)

---

### Post by NoBugs! on 2011-01-26
Wow, this cut down boot time from almost 2 minutes to about 1 minute, on Ubuntu 10.04... but I thought this type of boot optimization was enabled by default?

---

### Post by khamil8686 on 2011-01-26
this sped up my system boot from 70sec to 40sec, i just wonder if theres any way to protect against startup program dependencies, like if one program requires another to run, is there any way of making sure that the first program starts up first before running the second? like if i add start up programs in the future

i have an AMD Phenom II X4 940 processor and 4GB of ddr2 ram
Kubuntu 10.10 Maverick Meerkat

---

