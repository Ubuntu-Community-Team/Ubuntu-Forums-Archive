---
title: "slow waking up from hibernation"
date: 2009-09-13
forum: Dell Ubuntu Support (CLOSED)
---

### Post by geoffm on 2009-09-13
I installed the Dell ISO and I was expecting the computer to wake up faster from hibernation. It doesn't. Waking up from hibernate takes a full minute, while booting from scratch takes 80 seconds. Waking up from suspend takes about 10 seconds, which is ok, and Windows wakes up from **hibernation **in 10 seconds. I would expect ubuntu not to fall behind so much. Does everyone experience an excruciatingly slow wakeup time? If there's no way to make it wake up faster, can someone at least explain to me why waking up is so slow?

---

### Post by seamles on 2009-09-13
i have the same problem. don't know what to do.

---

### Post by radioboy on 2009-12-23
I'm having the same problem.  Actually I'm using Linux Mint, but it's based on Ubuntu.
I have a Dell 1535. It takes longer to wake it up than to boot it from scratch. :(
Suspension to ram works fine on Gnome, but it's very slow when I use KDE.

---

### Post by koba101 on 2010-01-15
actually starting from scratch on my laptop is much faster than hibernate...that's why i never hibernate anymore...it's not usable

---

### Post by v1nsai on 2010-01-16
Wish I had something useful to say but I just wanted to bump and say I'm having the same problem.  It's definitely faster to boot than to wake up.  I've been looking into the problem, there's a guide [here]("https://help.ubuntu.com/community/HibernateWhatHappens") that I've been going through but so far I'm not finding much.

I really expected Linux/Ubuntu to run a lot more smoothly on my new Dell Studio 15 since Dell is selling Ubuntu laptops and all, but it hasn't been very smooth at all :-/

---

### Post by balduin on 2010-05-08
I'm using Lucid right now and I noticed that it wakes up from hibernation almost instantly but hangs for a long time before I can enter my password into the lock screen. 

Do you have the same issue?

---

### Post by v1nsai on 2010-05-08
To be honest, ive completely given up on this issue. Ive been taking the extra few moments to save and close my tabs in firefox and whatever else im working on and just shutdown. it never fails, and boot time is ridiculously fast when im ready to come back, and i can just reopen whatever i was working on.  This has saved me stress and annoyance, and has saved my disk from all the hard reboots i had to do when hibernating froze, i did this so many times my partition table got corrupted and i almost lost everything.  I hate giving up but ill take the stability over the bs ;)

---

### Post by jerenept on 2010-05-08
Hibernation is very slow because all the data in ram is saved to disk and when waking up, it is all retreived from disk, and if you have a lot of ram this can be a very log process.

---

### Post by geoffm on 2010-05-15
Well, the question is, how come Windows wakes up for hibernation in 10 seconds then?

---

### Post by psusi on 2010-05-16
Wow, I just got a new Vostro 13 and immediately installed 10.04 instead of the 9.04 it came with and it was booting in 35 seconds ( now down to 30 after a defrag ) and resumes from suspend in 2.5 seconds.  I have not been using hibernate much since suspend is much faster, but I'm pretty sure it does not take longer than a normal boot.  And yes, I also see the password prompt quickly then it hangs for a second or two before I can type.

I was hoping to get the boot time down to the 10 second area, but it seems the cpu in this thing is rather slow.  It's a celeron 1.3 GHz or something like that.

After installing laptop-mode-tools to get proper hard disk spindown, I get near 4 hours of battery life.  It's pretty nice.

---

### Post by It-Alien on 2010-05-26
I have been facing with this issue (long time for resuming from hybernation and general slowness after) since Ubuntu 9.10.

before 9.10, my notebook was faster in resuming. now it's way faster when booting from poweroff

---

### Post by JayD239 on 2010-06-19
> **balduin said:**
> I'm using Lucid right now and I noticed that it wakes up from hibernation almost instantly but hangs for a long time before I can enter my password into the lock screen. 

Do you have the same issue?

This is exactly the issue i'm having. Booting goes fine, at some point you'll the the black screen where a box to enter you password is supposed to show up. After 30 seconds or so my mouse appears (very laggy at first), and another 30 or so the box appears.

Also, i can often not type in that box after a little while, or it disappears and reappears.

---

### Post by R4kk00n on 2010-08-08
The funny thing here is that system hibernates faster than it wakes up (or so it seems). Isn't disk write speed supposed to be generally lower than read speed?

---

### Post by jarviser on 2010-08-09
The reason hibernate was invented was because of the abismal boot-up speeds of Windoze. Linux added it unnecessarily IMHO anyways. As we have lightening boot-up now in 10.04, hibernate ceases to be even a consideration, unless you want to rest in the middle of a document edit, in which case you are dicing with disaster anyways. It very often screws 3G and wifi IP assignments anyway.

I have hibernate and sleep disabled on 10.04 and Win7 as both are quicker to boot and you get a fresh start every time. So IMHO hibernate and sleep will go the way of the floppy drive.

---

### Post by 3Miro on 2010-08-31
Same problem on two laptops with 10.04. The funny part is that I didn't have this problem in 8.10.

Suspend/wake up and fresh boot are both very fast. Hibernation down is also fast, hibernation up is as slow as a crippled turtle. I guess don't use hibernation is the only answer ....

---

### Post by epek on 2010-09-03
Hello!

I experienced similar problems on my Asus UL30A. Hibernation was complete in about 16 seconds, wakeup took about two minutes (until login occurred) and some more seconds were consumed, until normal work was possible again.

Reading your and other posts I figured out the following solution for me:

1. install
hibernate
laptop-mode-tools (remove the pm-package which's dependency is broken).

2. edit /etc/default/acpi-support
add "hibernate" to the list of supported methods.

3. edit /etc/hibernate/suspend2.conf
replace Compressor lzf by "Compressor lzo"

4. Furthermore - I don't know, if it is necessary at all - i stopped the mysql and apache2 services within the file suspend2.conf on hibernation. Usually, you don't have that on your laptop. If it is installed, it will sure help in cutting down the memory footprint on hibernation.

->

afterwards - at least in my case - wakeup took about 30 seconds at most, with no applications running.

Further tests will be necessary - please report back.

Should we call this a bug and report it on launchpad?

Regards
Erich

---

### Post by jasxun on 2010-09-17
I confirm that epek's solution worked for me. Before applying the workaround the wakeup procedure from hibernation was very long (>2 min.) and accompanied by a crazy amount of harddisk traffic. Now everything is finally normal.

More notes on my try of the solution: 
1,2: These were necessary steps;
3: I compared both compression methods, lzo is indeed a little bit faster than lzf.
4: Not necessary for me.

---

### Post by radioboy on 2010-09-17
> **epek said:**
> 
hibernate
laptop-mode-tools (remove the pm-package which's dependency is broken).


By that you mean the "pm-utils" package?
Also, for those who have tried, which computer models do you have?

---

### Post by jasxun on 2010-09-17
> **radioboy said:**
> By that you mean the "pm-utils" package?
Also, for those who have tried, which computer models do you have?
I think that should be the "pm-utils-powersave-policy" package.

---

### Post by bilderbuchi on 2010-09-18
i just tried epek's approach, hasn't really changed anything on my laptop (HP 8530w), still slow. :-(
yes, the pm-utils-powersave-policy is meant, it gets removed automatically by synaptic.
a launchpad bug report may be in order...epek, as originator, would you care to submit one?

---

### Post by jasxun on 2010-09-19
Well, my story didn't end there. Although the wakeup speed is indeed faster after applying epek's approach (I don't know why...), it is still not as fast as it can be. I found that when I run 'sudo hibernate' in command console to hibernate the wakeup speed would be much faster than hibernating via Fn-F12 or selecting Hibernate from the shut-down menu. It seems to me the 'hibernate' package was not being used at all, when hibernating through Fn-F12 or shut-down menu.  I put "hibernate" as the *only* hibernation method in '/etc/default/acpi-support', still the same. It seemed to me that 'pm-hibernate' is still called to perform hibernation.

How can we enforce the system to use the 'hibernate' package, instead of 'pm-utils' to perform hibernation?

---

### Post by bilderbuchi on 2010-09-20
i don't even know if the hibernate package is still "state-of-the-art". what is the default method in maverick? the many different methods to hibernate are very confusing...
interesting discovery regarding sudo hibernate - i'll try that out.
re enforce: not the slightest idea...

---

### Post by jasxun on 2010-10-06
> **jasxun said:**
> Well, my story didn't end there. Although the wakeup speed is indeed faster after applying epek's approach (I don't know why...), it is still not as fast as it can be. I found that when I run 'sudo hibernate' in command console to hibernate the wakeup speed would be much faster than hibernating via Fn-F12 or selecting Hibernate from the shut-down menu. It seems to me the 'hibernate' package was not being used at all, when hibernating through Fn-F12 or shut-down menu.  I put "hibernate" as the *only* hibernation method in '/etc/default/acpi-support', still the same. It seemed to me that 'pm-hibernate' is still called to perform hibernation.

How can we enforce the system to use the 'hibernate' package, instead of 'pm-utils' to perform hibernation?

[]("http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=9378826#post9378826")As suggested by [this post]("http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=9378826#post9378826"), I simply did the following to force the usage of 'hibernate' package for hibernation:

```

cd /usr/sbin
sudo mv pm-hibernate{,.orig}
sudo ln -s `which hibernate` pm-hibernate

```

Now when I hit Fn-F12, 's2disk' is actually called to perform hibernation. Both hibernation and wakeup is very fast now (<1min).

---

### Post by radioboy on 2010-11-04
> **jasxun said:**
> As suggested by [this post]("http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=9378826#post9378826"), 

Awesome! That worked for me too. :D

For the record: notebook Dell Studio 1535, ATI Mobility Radeon HD 3400 (using proprietary Catalyst 10.10 driver), 4 GB ram, 5 GB in /swap partition.

---

### Post by wulu on 2011-01-09
Thanks jasxun, that works perfekt on a Lenovo T61
resume time now is less then 15s with 2gb of ram.
Ubuntu 10.10

apt-get install uswsusp
apt-get install hibernate
ln -sf /usr/sbin/hibernate /usr/sbin/pm-hibernate

---

### Post by mkalioby on 2011-03-29
It worked with me too. Ubuntu 10.04 on Toshiba Satelitte Pro 4G RAM .


> **jasxun said:**
> As suggested by [this post]("http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=9378826#post9378826"), I simply did the following to force the usage of 'hibernate' package for hibernation:

```

cd /usr/sbin
sudo mv pm-hibernate{,.orig}
sudo ln -s `which hibernate` pm-hibernate

```Now when I hit Fn-F12, 's2disk' is actually called to perform hibernation. Both hibernation and wakeup is very fast now (<1min).

---

### Post by luispotro on 2011-04-25
> apt-get install uswsusp
apt-get install hibernate
ln -sf /usr/sbin/hibernate /usr/sbin/pm-hibernate

Worked for me on 10.10 (Presario C500 3Gb RAM). Now the hibernate and the wake up processes are more symmetrical (before the wake up was waaaay much slower than hibernation, now hibernation takes a little longer and wake up much more faster) although it's not very aesthetic. Isn't there an option to show some kind of a splash screen instead of the progress?

---

### Post by psusi on 2011-04-25
> **luispotro said:**
> Isn't there an option to show some kind of a splash screen instead of the progress?

No.  It used to be able to do so using usplash, but Ubuntu now uses plymouth.  Once of these days I'm hoping to find the time to modify it to interface with plymouth to provide the nice splash screen.

---

### Post by geoffm on 2011-04-29
mkalioby's solution worked for me (XPS M1330)
hibernating is still a little slow (which I don't care too much about) but wakeup time is much faster (<30sec)

proper commands would be
```
sudo apt-get install uswsusp hibernate
sudo ln -sf /usr/sbin/hibernate /usr/sbin/pm-hibernate
```

waking up from suspend seems to be faster too.

---

### Post by jasxun on 2011-08-11
After upgrading to Natty, this method no longer works. Hibernation seems fine, however resume would get stuck in a system hang (when Ubuntu logo and the progress bar show up, the hard-drive would have some activities with progress bar moving, then everything stops). I had to reverse what I did on Lucid and remove packages 'uswsusp' and 'hibernate', the default hibernation/resume seem to work well now.

---

### Post by radioboy on 2011-08-11
> **jasxun said:**
> After upgrading to Natty, this method no longer works. Hibernation seems fine, however resume would get stuck in a system hang (when Ubuntu logo and the progress bar show up, the hard-drive would have some activities with progress bar moving, then everything stops). I had to reverse what I did on Lucid and remove packages 'uswsusp' and 'hibernate', the default hibernation/resume seem to work well now.

Could you tell us which computer do you have?
I upgraded to natty in my Dell Studio 15, ATI Radeon HD3400, using the Catalyst (proprietary) drivers fetched by Ubuntu after the install, and I still had to do the change to get it working.

---

