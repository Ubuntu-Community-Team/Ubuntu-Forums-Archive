---
title: "time is always wrong"
date: 2006-07-19
forum: Desktop Environments
---

### Post by ghotra on 2006-07-19
Every time I turn my laptop on, the time is always wrong.  I have ntp setup, but this should not be needed---and I'd rather not wait until my clock is sync'd as this screws up all my logs.  I am not dual-booting, so there is no issue with Windows resetting the time.

What is the cause? 

How can I fix this?

---

### Post by reacocard on 2006-07-19
is your time zone set correctly?

---

### Post by ghotra on 2006-07-19
Yes, it is set to Los Angeles, CA.

---

### Post by orlox on 2006-07-19
Is it something from the software? or maybe something hardware related like your CMOS battery running down?

---

### Post by ghotra on 2006-07-19
Well, that is why I am asking. I have no idea what the problem is.  Hopefully someone here will be able to help me out.  This doesn't seem like a difficult problem.  This is a brand new ububntu install on a brand new laptop. I downloaded the iso just 1 week ago. This problem has always occurred and it is quite annoying.

---

### Post by stoffepojken on 2006-07-19
sudo apt-get install ntp

Edit: /me dont read posts correctly

---

### Post by ghotra on 2006-07-19
1) I already have ntp installed

2) ntp does not solve the problem

   2a) ntp merely avoids the problem

   2b) even with ntp, the time is still wrong after every restart, until the next sync

   2c) this means my logs suck since the times will be wrong

Surely, someone know 

1) how to diagnose this

2) how to fix this

This has never been a problem for me before. I will try to dig around more, but I would like it if someone with more experience could help me out.

---

### Post by Blazeix on 2006-07-19
Is the time correct in your BIOS?
Also, in the command line, type the date command. Make sure this is the correct time. If it isn't, set it by using the -s flag.
```

sudo date -s "Wed Jul 19 22:18:35 CDT 2006"

```Change the date/time to whatever it should be, don't use the example time!

Then check to the hardware time. Type 'hwclock' and it will display the hardware time. If it is wrong, sync it with the system time:
```

hwclock --systohc

```

Reboot, and see if that fixed it. Hope this helps!

---

### Post by blitzd on 2006-07-19
How much is the time off by? Hours, minutes?

I've run into issues before with Ubuntu thinking my hw clock is set to UTC when it's actually set to local time. Unfortunately I never quite figured out how to fix it or why it seemed to keep reverting back to UTC (my hw clock is local time and I have been playing with Gentoo for the last while).

---

### Post by ghotra on 2006-07-20
Thanks for the replies....I think I have two separate issues. Now I have just one issue.

It turns out that my BIOS time was slow an hour.  So I moved it forward to 21:12 rather than 20:12.

Then I boot into ubuntu.  The time is 14:12 pm.  So it is off by six hours...this is looking good.

Then I go to my system clock in the taskbar, click Preferences and check "Use UTC".  Now my time is perfect. It reads 21:12

Then ntp suddenly syncs my clock.  Now it reads 04:17.

Naturally, I go to uncheck "Use UTC" and it says 21:17.

So everything is good now.

Now I restart.  Guess what the clock says now.  Well, it is back to 14:22.

What is going on here!  It seems something like what blitzd described.  This is utterly annoying.

---

### Post by fragos on 2006-07-20
This may not be your problem but I found that after installing and activating ntp with Gnome it seemed to install but acted as it never did.  I checked and the correct peices were installed.  When I checked ntp.conf I found there were no servers configured.  I remove the comment # from the server pool and rebooted.  This time, when I used Gnome to select use ntp on boot it acted differently.  This time it gave me a list of servers to select from.  The server pool was already checked per ntp.conf.  For good measure, I added the closest ntp server to Fresno CA to the list.  All seems to work correctly now.

---

### Post by ghotra on 2006-07-20
Thanks fragos.  I checked my ntp.conf and it is definitely working properly.  My time does sync either way. For some reason, though, on reboot, my time is always off....like it is in UTC...but ubuntu thinks my system should be in local time (as does ntp)...so ntp syncs to local time.  When I reboot, my clock is back to UTC and then ntp takes over and resets to local time. Reboot again...

---

### Post by ghotra on 2006-07-20
> **Blazeix said:**
> Is the time correct in your BIOS?
Also, in the command line, type the date command. Make sure this is the correct time. If it isn't, set it by using the -s flag.

Then check to the hardware time. Type 'hwclock' and it will display the hardware time. If it is wrong, sync it with the system time:

Reboot, and see if that fixed it. Hope this helps!

Whoops! I forgot to mention my attempts to the above.

My BIOS time has been fixed now.  The output of "date" is correct.  I am unable to check "hwclock" though.  

```

$ hwclock --show
select() to /dev/rtc to wait for clock tick timed out

```

So...I don't know wha to do about that.

---

### Post by ghotra on 2006-07-20
still unresolved...any new ideas?

---

### Post by jimbob on 2006-07-20
It sounds to me that your system thinks it should use the UTC.

I had this problem a while back and it was due to my mistake when I installed Ubuntu in selecting 'use UTC -> yes'.

Don't remember exactly what I did to fix it though.

What is returned when you type $echo $TZ 
If you right click on the clock and select preferences, is the 'use UTC' box checked?
_________________________________________      
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by ghotra on 2006-08-02
Thanks for the replies everyone. I managed to solve the problem. I wish someone could have pointed me to the solution earlier, as it was quite simple. I guess I'm left feeling one of two things:

1) users very familiar with ubuntu do not read these posts
2) users very familiar with ubutnu do not bother to reply to these posts

Anyway, here is the solution.

1) My bios is set for localtime (and I don't think I can change that).
2) When I run time-admin, a time-zone is selected: America/Los_Angeles
3) When I right-click on the clock, use UTC is not checked.

This is how my machine looks when I turn it on. 

The time is wrong.  If I right-click on the clock and select "Use UTC" then the time is correct.  However, when NTP updates my clock to localtime, then the time displayed on the clock applet is incorrect again (and can be corrected by unchecking "Use UTC".

Running "date" displays the same time as the clock applet (so is also incorrect).

Running "hwclock --show" fails.  I am on a laptop.  The only way hwclock works is if I run:  "hwclock --directisa --show".

Upon running that command, the time displayed by "hwclock" matches that displayed by "date" and also by the clock applet.  So the problem still exists everywhere.

However, running "hwclock --directisa --localtime --show" displays the proper time.

So now I know how to get the proper time. The issue is just getting ubuntu to do what I want.  A quick look around points to:

/etc/default/rcS

there I found 

  UTC=yes

I'm not sure why it was set like that even though I had selected a time-zone with time-admin.  My guess is (as someone suggested) that I selected "UTC" during my install.

So I turn UTC=no.

This almost works.  Now I need to edit: /etc/init.d/hwclock.sh
and set:

HWCLOCKPARS="--directisa"

Everything works now.

/etc/init.d/hwclock.sh restart

So problem solved.

$ date

---

### Post by barkhat on 2007-06-02
> **ghotra said:**
> Thanks for the replies everyone. I managed to solve the problem. I wish someone could have pointed me to the solution earlier, as it was quite simple. I guess I'm left feeling one of two things:

1) users very familiar with ubuntu do not read these posts
2) users very familiar with ubutnu do not bother to reply to these posts

Anyway, here is the solution.

1) My bios is set for localtime (and I don't think I can change that).
2) When I run time-admin, a time-zone is selected: America/Los_Angeles
3) When I right-click on the clock, use UTC is not checked.

This is how my machine looks when I turn it on. 

The time is wrong.  If I right-click on the clock and select "Use UTC" then the time is correct.  However, when NTP updates my clock to localtime, then the time displayed on the clock applet is incorrect again (and can be corrected by unchecking "Use UTC".

Running "date" displays the same time as the clock applet (so is also incorrect).

Running "hwclock --show" fails.  I am on a laptop.  The only way hwclock works is if I run:  "hwclock --directisa --show".

Upon running that command, the time displayed by "hwclock" matches that displayed by "date" and also by the clock applet.  So the problem still exists everywhere.

However, running "hwclock --directisa --localtime --show" displays the proper time.

So now I know how to get the proper time. The issue is just getting ubuntu to do what I want.  A quick look around points to:

/etc/default/rcS

there I found 

  UTC=yes

I'm not sure why it was set like that even though I had selected a time-zone with time-admin.  My guess is (as someone suggested) that I selected "UTC" during my install.

So I turn UTC=no.

This almost works.  Now I need to edit: /etc/init.d/hwclock.sh
and set:

HWCLOCKPARS="--directisa"

Everything works now.

/etc/init.d/hwclock.sh restart

So problem solved.

$ date



This is my trouble, too.  Trying to follow these instructions but having trouble.  When I gedit the file it won't let me save saying I don't have permissions.  When I save to my desktop and try to copy over to the /etc/default/ directory, I get an error saying "sudo: timestamp too far in the future: Jun  1 21:30:48 2007" even though my clock is currently (at this minute showing the right time.  

Please help!  I'm still new to Linux!

---

### Post by ghotra on 2007-06-02
When you gedit and file and try to save....make sure you do:

$ sudo gedit /etc/default/rcS

That should take care of any permission issues.

If you have troubles with a sudo timestamp.....wait a bit....or delete ~/.sudo_as_admin_successful....while waiting don't touch your clock.  Then try the above command again.

---

### Post by therage on 2007-06-09
Thanks for working this problem out ghotra.  I had the same problem on an old Dell Latitude C600 laptop I just installed 7.04 Feisty Fawn on.  Following your directions worked like a charm.
-Bill

---

### Post by AstarothCY on 2007-07-23
Thank you SO MUCH. Fix works perfectly. I only had to change UTC=yes to UTC=no, btw, I didn't have to do the other stuff.

---

