---
title: "usb Time not equal to hardware time"
date: 2009-06-20
forum: General Help
---

### Post by kndlewis on 2009-06-20
I successfully installed 9.04 onto a usb stick.  When I boot to this version, the time is 4 hours behind the hardware.  That is, the time is correct when I boot to windows XP or Ubuntu 9.04 on the hard disk but on the usb stick, the time is off. 
If I change it from within the usb boot then it changes to 4 hours ahead when booting to one of the OS's on the hard disk.  I checked '$ date' and it shows the correct time zone but with the time 4 hours slow.
I checked it on my laptop and it's 4 hours behind there, also.  
Is there a place where the OS time might be different from the system time?
I'm pretty sure I checked the correct time zone during the install process.  But there must be a way to adjust it now without messing up the time on the hardware.  
I hope someone can point me in the right direction.  Thanks

---

### Post by kndlewis on 2009-06-21
As a work-around, I have installed the screenlet clock and set that to read 4 hours ahead.
At least I have something that shows the correct time on my desktop.

---

### Post by sedawk on 2009-06-21
Check the time zone shown by "date" on the command line.
Most likely the time zone configured on the usb stick is wrong.

It the time zone is not the problem execute 
"hwclock -hctosys" manually and check if that changes
the time as it should.

Have you enabled "NTP" to synchronize time with some
server in the internet?

---

### Post by CatKiller on 2009-06-21
> **kndlewis said:**
> Is there a place where the OS time might be different from the system time?

Yes.

The UNIX way, which Linux has inherited, is to have the hardware clock set to UTC which is strictly increasing, rather than local time which goes backwards at least once a year because of daylight savings time and messes up your cron jobs, rsync and version-control systems.

The Windows way is to set the hardware clock set to local time and paper over the cracks with inconsistent applications.

Since your hard-drive Ubuntu installation shows the same time as your Windows installation, you're probably using local time for your hardware clock. You probably want to tell your USB install to do the same. You can do this by editing /etc/default/rcS to include the line UTC=no.

---

### Post by kndlewis on 2009-06-21
Thanks for the replies.

sedawk, the 'date' comand shows the correct time zone (EDT) with the time 4 hours behind. Executing 'hwclock --hctosys' does not change the display! Running 'hwclock --show' says the time is 4 hours behind! Which explains why the display is off. But Why! I did try the time sync in both automatic and manual.

CatKiller, I edited the /etc/default/reS file to change the UTC=yes to be UTC=no and there was no difference in the clock display. I restarted the system to verify.

I can change my time zone to Atlantic/Azores and the toolbar clock is correct.  I'll see how it performs on some hardware at work tomorrow.

---

### Post by kndlewis on 2009-06-22
I give up!  Today at work I found a laptop that I could boot my new jaunty usb stick.
The time on the toolbar was 6 hours slow!
So now I'm home on the same machine that I was on yesterday and the toolbar time is correct?????!!!!!
I'll just keep the screenlet clock to show an offset if the toolbar is incorrect.
It must have something to do with the way the usb stick is getting initialized during the boot sequence?  It's not consistent so how are we supposed to solve it?
Thanks for reading.  If anyone else has this issue, i would like to hear.  Am I the only one?

---

