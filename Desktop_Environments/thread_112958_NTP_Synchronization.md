---
title: "NTP Synchronization"
date: 2006-01-05
forum: Desktop Environments
---

### Post by Caleb9849 on 2006-01-05
I am having a problem keeping my clock synched.  I want it to sync with the Ubuntu time server each time I boot up.  It was doing this before.  But lately, it hasn't done it and the clock has been a little bit off.  The problem seems to be that "Clock synchronization" in Ubuntu Menu>System>Administration>Services keeps getting unchecked, even though I keep checking it!  What's the deal?  I really need correct time on this computer because I also use it with MythTV as a DVR.  Thanks in advance.

---

### Post by schilcha on 2006-01-05
Try to determine, if ntpdate is actually skipped at startup via 
```

ll -l /etc/rc?.d/*ntpdate

```
my system gives
> 
lrwxrwxrwx  1 root root 17 2005-11-08 10:15 /etc/rc2.d/S50ntpdate -> ../init.d/ntpdate
lrwxrwxrwx  1 root root 17 2005-11-07 21:50 /etc/rcS.d/S51ntpdate -> ../init.d/ntpdate

This makes sure ntpdate is executed when booted into runlevel 2 (default) and inot single-user mode.

Also check, if there's a line like 
> 
NTPSERVERS="pool.ntp.org"

in the file /etc/defaults/ntpdate

Also, make sure that the file /usr/sbin/ntpdate exists and has execute permission.

---

### Post by Caleb9849 on 2006-01-05
I don't have the command "ll".  How do I get it?  And I don't even have a file called /etc/defaults/ntpdate.  As for /usr/sbin/ntpdate, it looks good.

---

### Post by dcstar on 2006-01-06
[QUOTE=Caleb9849]I don't have the command "ll".  How do I get it?  And I don't even have a file called /etc/defaults/ntpdate.  As for /usr/sbin/ntpdate, it looks good.[/QUOTE]
"ll" is an alias for "ls -l", your default shell may not have it set up.

Do you have the ntpdate and ntp-server packages installed?

---

### Post by Caleb9849 on 2006-01-06
root@calebs:~# ls -l /etc/rc?.d/*ntpdate
lrwxrwxrwx  1 root root 17 2006-01-05 10:27 /etc/rc2.d/S50ntpdate -> ../init.d/ntpdate
lrwxrwxrwx  1 root root 17 2006-01-05 10:27 /etc/rc3.d/S50ntpdate -> ../init.d/ntpdate
lrwxrwxrwx  1 root root 17 2005-12-31 12:08 /etc/rcS.d/S51ntpdate -> ../init.d/ntpdate

That look right?

Also, I had ntpdate installed, but not ntp-server.  I installed ntp-server.  Think that will fix it?

---

### Post by schilcha on 2006-01-06
[QUOTE=Caleb9849]I don't have the command "ll".  How do I get it?  And I don't even have a file called /etc/defaults/ntpdate.  As for /usr/sbin/ntpdate, it looks good.[/QUOTE]

Sorry for the typo (in fact dcstar was right -- it's my convenience-alias).

Looking at the script executing ntpdate at startup (/etc/init.d/ntpdate), having no file /etc/defaults/ntpdate is ok -- the default ntp-server (pool.ntp.org) is queried. Therefore, I can't really tell you, why ntpdate is not executed during startup.

Installing ntp-server is definitely a good idea, since it will constantly adjust your system's time (not only once at startup). 

If ntp-server works for you, you don't really have to bother why ntpdate's not working correctly. If you still want to track down the reasons, have a look at you log-files, to see what's going wrong.

---

### Post by Caleb9849 on 2006-01-06
Oh, maybe I was unclear....sorry about that.  It does synchronize at startup.  It just doesn't STAY synched.  I can also set it back in sync by re-running the process....but if I leave it alone for a few hours, it gets a couple minutes off, and the longer I leave it alone, the farther off it becomes.

---

### Post by dcstar on 2006-01-06
[QUOTE=Caleb9849]Oh, maybe I was unclear....sorry about that.  It does synchronize at startup.  It just doesn't STAY synched.  I can also set it back in sync by re-running the process....but if I leave it alone for a few hours, it gets a couple minutes off, and the longer I leave it alone, the farther off it becomes.[/QUOTE]
That's what ntp-server does, it regularly keeps it in sync.

---

### Post by Caleb9849 on 2006-01-07
But it seems to me like once at bootup should be enough.  A sophisticated computer clock shouldn't be getting offset like that, should it?

---

### Post by schilcha on 2006-01-07
[QUOTE=Caleb9849]But it seems to me like once at bootup should be enough.[/QUOTE]
It certainly is enough for most desktop systems that are rebooted on a regular basis.

[QUOTE=Caleb9849]A sophisticated computer clock shouldn't be getting offset like that, should it?[/QUOTE]
Unfortunately, no. I guess that external factors (probably temperature, production-batch, ...) affect the duration of ticks in the timer-circuit. 
Anyways, for whatever reasons, computer-clocks (can) diverge from real time pretty fast. So, since you're running an "always-on" system, installing an ntp-daemon (as you did) is the best idea. It's even better than rerunning ntpdate regularily, because the daemon tries to comensate the clock's drift -- I once read through the man-page of xntpd and learned that this topic is a science of itself.

---

### Post by Caleb9849 on 2006-01-07
So....since it's not fixed yet, what would you recommend doing next?

---

### Post by schilcha on 2006-01-07
OK, my fault, I misunderstood you for most of the time...

So, try to (re)start the service manually:
```

sudo /etc/init.d/ntp-server restart

```
for me this looks like this:
> 
 * Stopping NTP server...                                                [ ok ]
 * Starting NTP server...                                                [ ok ]

I guess that starting does not work correctly for you, so have a look at /var/log/daemon.log. For me this looks like this:
> 
Jan  7 23:01:26 smithers ntpd[10130]: ntpd 4.2.0a@1:4.2.0a+stable-8-r Fri Sep  9 16:44:48 UTC 2005 (1)
Jan  7 23:01:26 smithers ntpd[10130]: precision = 3.000 usec
Jan  7 23:01:26 smithers ntpd[10130]: Listening on interface wildcard, 0.0.0.0#123
Jan  7 23:01:26 smithers ntpd[10130]: Listening on interface wildcard, ::#123
Jan  7 23:01:26 smithers ntpd[10130]: Listening on interface lo, 127.0.0.1#123
Jan  7 23:01:26 smithers ntpd[10130]: Listening on interface eth0, 10.42.42.2#123
Jan  7 23:01:26 smithers ntpd[10130]: kernel time sync status 0040


BTW, do you have a firewall that will block ntp-connections?

---

### Post by Caleb9849 on 2006-01-08
I think you are still misunderstanding me, but it's probably my fault.  I can be kind of unclear sometimes.  Sorry.  I can connect to the timeserver and download the correct time without any problem at all.  The clock then synchs to the correct time.  But, it gradually (quickly, though) becomes more and more off.  Within a few hours it's 2 minutes off, after a day it's like 5 minutes off, and after 2 days it's about 10 minutes off, and so on.  It's like the clock is not counting time at the correct speed.

---

### Post by dcstar on 2006-01-08
[QUOTE=Caleb9849]I think you are still misunderstanding me, but it's probably my fault.  I can be kind of unclear sometimes.  Sorry.  I can connect to the timeserver and download the correct time without any problem at all.  The clock then synchs to the correct time.  But, it gradually (quickly, though) becomes more and more off.  Within a few hours it's 2 minutes off, after a day it's like 5 minutes off, and after 2 days it's about 10 minutes off, and so on.  It's like the clock is not counting time at the correct speed.[/QUOTE]
And has has been explained, this is an issue with your hardware.

The "cure" is to install and run the ntp-server package - which will resync your clock on a regular basis, do this and you problems will be solved.

---

### Post by schilcha on 2006-01-08
Now I'm completely lost...

[QUOTE=dcstar][...] this is an issue with your hardware.[/QUOTE]
Yup, that clock is crap.

[QUOTE=dcstar]The "cure" is to install and run the ntp-server package - which will resync your clock on a regular basis, do this and you problems will be solved.[/QUOTE]
I thought Caleb9849 already did that... 
[QUOTE=Caleb9849]Also, I had ntpdate installed, but not ntp-server. I installed ntp-server. Think that will fix it?[/QUOTE]

So, what's up? Doing at startup ntpdate is not enough. So then, is ntp-server installed? Is it running? Is it connecting to the reference clocks? Are there any error messages (from /var/log/daemon.log)?

---

### Post by Caleb9849 on 2006-01-08
Yes, I did already install ntp-server.  The clock still is jacked.  I don't see anything eery in /var/log/daemon.log .... only messages about my network card connecting to my router for DHCP.  So, the hardware clock is trash, then?  Because it was working fine a week ago....does this happen so suddenly?  And, can the clock be replaced without replacing the whole mobo, and if so then for what price?

---

### Post by dcstar on 2006-01-08
[QUOTE=Caleb9849]Yes, I did already install ntp-server.  The clock still is jacked.  I don't see anything eery in /var/log/daemon.log .... only messages about my network card connecting to my router for DHCP.  So, the hardware clock is trash, then?  Because it was working fine a week ago....does this happen so suddenly?  And, can the clock be replaced without replacing the whole mobo, and if so then for what price?[/QUOTE]
Right-click the time on your panel, select "Adjust Date and Time"

Set all of the relevant items, Turn on "Periodically syncronize clock with Internet servers"  and select a Time Server from the list.

---

### Post by Caleb9849 on 2006-01-08
Yeah, okay....um....I tried clicking "adjust date and time" but nothing came up.  So I went to a terminal window and typed "time-admin".  Then the window came up but it was greyed out with the "busy" cursor and it just did that for awhile so I had to kill the window.  Along these same lines, I can't get to the network configuration GUI through the menu icon (but I can get to it by typing "network-admin" which seems strange), and the system seems to have trashed just about all of the MythTV (a freeware DVR) configurations that I had!  What is happening here?  Is my motherboard exploding?

---

### Post by schilcha on 2006-01-09
[QUOTE=Caleb9849]So I went to a terminal window and typed "time-admin".  Then the window came up but it was greyed out with the "busy" cursor and it just did that for awhile so I had to kill the window.[/QUOTE]
On my system, the window was also greyed for quite some time, until the password-request popped up. To get around this, use "sudo time-admin" to start it as root right away.

Have you tried checking if ntpd is running as suggested in post #12?

---

### Post by Caleb9849 on 2006-01-09
Yes, I tried restarting the ntp server.  It's not helping.  On top of that, now I'm having even more trouble starting *any* GUI program that uses gksudo....even if I'm already the root user.  Some of them just sit there and don't start at all.  Anyone know why this may be?  Should I just re-install Ubuntu?

---

### Post by schilcha on 2006-01-10
[QUOTE=Caleb9849]On top of that, now I'm having even more trouble starting *any* GUI program that uses gksudo....even if I'm already the root user.  Some of them just sit there and don't start at all.  Anyone know why this may be?  Should I just re-install Ubuntu?[/QUOTE]
Sorry, really can't help you with that...

But, for your ntpd problem I've one more suggestion: Just read in a thread -- lost the link, sorry -- that ntpd refuses to start, if the clock is far off the reference clocks. Try setting your system time to something that's close the real time and try again.

---

### Post by Caleb9849 on 2006-01-10
I'm telling you, though, I can get the clock synchronized without a problem.  It's just that if I leave it sitting for a while, it gradually but quickly becomes more and more inaccurate.

---

### Post by JLB on 2006-01-10
@ Caleb

I understand your pain :) My clock drifts as well, except my system clock gets faster and faster the longer I leave it alone. One thing I found out is the large disparity between the hardware clock and the system clock. even after a ntpdate sync. Once I sync'd both the system and the hardware clock, things got much better. This may be of some help to you. Try it. It can't hurt :) Check for the disparity by issuing the following:

hwclock && date

Now here is how I sync up my hardware clock and system time:

sudo ntpdate clock2.redhat.com && sudo hwclock --systohc

Another thing I found out was, If I had the ntp-server package installed, cron would not run my ntpdate script that I keep in /etc/cron.hourly.

---

### Post by JLB on 2006-01-11
some additional information. After running this machine for a while, I have determined that the hardware clock is the one actually keeping good time. 

it is the system clock that , for me, is speeding up. I read for others it lags.

One thing that has improved the drift is to actually have married up the system clcok and the hardware clock as I descibed previously. The amount of system clock drift has lessened. I can't explain why %).

My thoughts on this, and I need to research this some more, is that my system's "tick" is set slightly fast in <insert applicable program name here>. I have read that this is not an uncommon problem but I read stories about it on older version of other distro's.

I will be following their posts and experimenting.

At least I know my hardware clock is NOT screwy. So it stands to reason that this can be fixed through some minor editing or just live with a cron job to sync the system clock.

---

### Post by Caleb9849 on 2006-01-11
Okay, this is really screwy:

caleb@:~$ hwclock && date
Wed 11 Jan 2006 06:44:00 PM MST  -0.168097 seconds
Wed Jan 11 18:14:00 MST 2006

Neither of these times is correct.  My accurate wristwatch reports 6:04 PM.

caleb@:~$ sudo ntpdate clock2.redhat.com && sudo hwclock --systohc
11 Jan 18:14:32 ntpdate[32731]: the NTP socket is in use, exiting

And both my system and hardware clocks remain off after this.

---

### Post by schilcha on 2006-01-12
[QUOTE=Caleb9849]
caleb@:~$ sudo ntpdate clock2.redhat.com && sudo hwclock --systohc
11 Jan 18:14:32 ntpdate[32731]: the NTP socket is in use, exiting
[/QUOTE]

You have to stop ntp-server (sudo /etc/init.d/ntp-server stop) before running ntpdate

---

### Post by JLB on 2006-01-13
> Another thing I found out was, If I had the ntp-server package installed, cron would not run my ntpdate script that I keep in /etc/cron.hourly.

You can't have the ntp-server running. :) use ```
sudo /etc/init.d/ntp-server stop
``` or remove the ntp-server package.

---

### Post by kcoolsae on 2006-01-13
I have almost the same problems (on 64-bit Ubuntu Breezy)

the clock drifts quite a bit (15min a day)
ntpdate works (so firewall, network are OK)
ntp-server seems to work (although I think once or twice the ntpd-process quietly died)
However, the clock does not automatically adjust to Internet time

The following seems to solve the problem, but I would be glad to hear about a 'cleaner' solution

in /etc/init.d/ntp-server, change the line

RUNASUSER=ntp

into 

RUNASUSER=root

I will have to wait a day to be sure, but this seems to work.

---

### Post by kcoolsae on 2006-01-13
Sorry, it seems i was too optimistic. The trick from the previous mail does not seem to work.

I have also tried running the ntp-server in a 32-bit chroot environment, but that did not seem to help either.

Any more ideas?

BTW. Does anyone know of a way to test whether the ntp-server is actually working. apart from setting the time 5 minutes off and then waiting half an hour and see whether things changed?

---

### Post by schilcha on 2006-01-14
[QUOTE=kcoolsae]BTW. Does anyone know of a way to test whether the ntp-server is actually working. apart from setting the time 5 minutes off and then waiting half an hour and see whether things changed?[/QUOTE]

I digged around in ntp a little. I found a tool called "ntpq" (it's installed with the package ntp). Once you start it, it drops you to its own command line. Here's what I did and what I got:
```

$ ntpq
ntpq> association

ind assID status  conf reach auth condition  last_event cnt
===========================================================
  1 39756  9614   yes   yes  none  sys.peer   reachable  1
  2 39757  9414   yes   yes  none  candidat   reachable  1
  3 39758  9014   yes   yes  none    reject   reachable  1
ntpq> peers
     remote           refid      st t when poll reach   delay   offset  jitter
==============================================================================
*ns3.univie.ac.a 131.130.251.17   2 u   16   64  377    9.754   -0.207   1.310
+ferret.eicat.ca 204.123.2.5      2 u   15   64  377  141.997   -0.207   1.940
 LOCAL(0)        LOCAL(0)        13 l   17   64  377    0.000    0.000   0.004

```
As far as I understood the docs, the output means that there is one server, my machine trusts most. It has the condition "sys.peer" in the first block of output and is marked with "*" as first character in the second block -- it's ns3.univie.ac.at. Then there's anoter (candidat / "+") -- it's ferret.eicat.ca. The third server is my local clock. It is rejected -- wouldn't make much sense to synchronize to my own clock. 

Have a look at your output -- maybe you can gain some insights into your problem from this. 

BTW: obviously, the conditions of the reference-clocks are determined after some period of time -- so give your system a couple of minutes after starting ntp-server before you try it. 

Also, there's another implementation of ntpd in the repositories: open-ntp (or something like this). Maybe this works better than ntp-server...

Good Luck!

---

### Post by Caleb9849 on 2006-01-16
Okay, I got the hwclock thing to work.  I'm going to see how this works for a few days and let you know if I have trouble again.  Thanks.

---

### Post by elwood_j_blues on 2006-01-17
[QUOTE=Caleb9849]Okay, I got the hwclock thing to work.  I'm going to see how this works for a few days and let you know if I have trouble again.  Thanks.[/QUOTE]

Actually, I have the same problem. However, running ntpdate every hour-or-so does not seem to be a too clean solution as some applications may go nuts if the time "jumps" forth (or even worse: back).

ntp-server should slow down or speed up the system clock according to the amount of time it is off the NTP reference. However, I never had success with that tool before. I will start testing it again though. Maybe I can get it to run.

15 minutes off a day are simply way too much to live with ;)

---

### Post by kcoolsae on 2006-01-17
The problem is a known kernel bug, which should be solved in the kernel included with the next version of Ubuntu (Dapper Drake). In the meantime here is something that worked for me: I added the boot time kernel option 'notsc':

Edit /boot/grub/menu.lst (as root). Change the line that reads something like

# kopt=root=/dev/mapper/main-root ro

into 

# kopt=root=/dev/mapper/main-root ro notsc

(Important: the /dev/mapper/main-root will most probably be something else in your setup, like /dev/hda1 or /dev/sda1. Simply add the notsc to the end of the line.)

Then run update-grub (as root) and reboot. Wait for a day to see whether things work.

My kernel: 2.6.12-10-amd64-k8-smp on an AMD64 dual core processor

I have also tried the options 'no_timer_check noapic' suggested elsewhere on this forum, but this did not help.

Good luck!

---

### Post by kcoolsae on 2006-01-18
Update to previous post:

This morning my clock was 15 minutes fast (the system clock that is, the hardware clock was fine). So it seems that the solution suggested above only worked for a day. 
I now added a simple script to /etc/cron.hourly which synchronizes the system clock with the hardware clock. I hope this helps

This script consists of a single line:

( sleep 300; hwclock --hctosys ) &

which was written into the file /etc/cron.hourly/clock and then made executable.

---

### Post by kcoolsae on 2006-01-18
The above did not help either, but I am not giving up yet.

Does anybody know how to interpret the following output (IP-adresses were scrambled) ?

Two minutes after machine reboot:

```
# ntpq -pn
     remote           refid      st t when poll reach   delay   offset  jitter
==============================================================================
+111.222.333.444  222.333.444.555   3 u   44   64  377    0.410   -3.198   0.512
*199.299.399.499  199.299.599.699   2 u   44   64  377    1.443    2.024   0.417

```

Approx 15 minutes later:

```
# ntpq -pn
     remote           refid      st t when poll reach   delay   offset  jitter
==============================================================================
*111.222.333.444  222.333.444.555    3 u    1  128  377    0.412  -3228.6 898.287
 199.299.399.499  199.299.599.699    2 u    6  128  377    1.458  -4626.3 1240.17

```

I am wrong to think that the numbers in the two columns on the right are way too large?

---

