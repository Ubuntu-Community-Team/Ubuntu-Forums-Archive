---
title: "Timezone issue..."
date: 2006-08-29
forum: Desktop Environments
---

### Post by hajk on 2006-08-29
I'm trying to run Ubuntu Dapper (latest 686 kernel) in a Parallels VM on my MacBook running OS X. On booting Ubuntu, the time is always two hours later than my local timezone Europe/Amsterdam would have it, and from then on races about four minutes per hour further ahead. Synchronizing manually in the System-Administration-Time-and-Date menu works momentarily by setting the time two hours back, but does not solve the speed issue; the periodic synchronization option doesn't work AFAIK.

I figure that Ubuntu considers system (and OS X) time to be UTC, then adds one hour for the timezone plus one hour for daylight saving. So, a work-around is to pretend that my timezone is Atlantic/Reykjavik (hoping that they switch between daylight and standard time in Iceland at the same dates as in Amsterdam). This works OK, and together with kernel boot option "noapictimer" solves my clock problems.

My question is: how can I tell Ubuntu that system (OS X) time is really local time, and not UTC?

---

### Post by karan on 2007-05-01
I have the exact same issue... running Ubuntu Feisty in parallels on a macbook pro under parallels.  

specifically, my macbook :
    - is set for USA-pacific timezone
    - set to synchronize with time.apple.com
    - says it is 5pm May 1st (which is correct)

my ubuntu vm running in parallels:
    - is set for USA-pacific (los angeles) timezone
    - set to synchronize automatically 
    - has the ntp package installed
    - says 10am May 1st

if i do a % data --utc on ubunto, it says correctly that the UTC time is 5pm

so like the previous poster, i need a way to tell ubuntu that the clock time is not UTC, but rather real time.

any ideas?

thanks,

- k

---

### Post by dcstar on 2007-05-01
> **hajk said:**
> 
.........
My question is: how can I tell Ubuntu that system (OS X) time is really local time, and not UTC?

The Preferences in the Date and Time have a UTC toggle.

---

### Post by Mr_Freez3 on 2007-05-01
To make Ubuntu stop reading the time as UTC and keep your ACTUAL time, do the following:

Open a terminal and type the following line and hit Enter:

sudo gedit /etc/default/rcS

When the file pops up in the Text Editor, near the bottom you will see a line that says:  UTC=yes
Change this line to read:  UTC=no
Click on Save to save this change and then close the file.

Now click on System -> Administration -> Time and Date ...and set your correct time and date.
Next, type this in the terminal and hit Enter:

sudo /etc/init.d/hwclock.sh restart

This will restart your clock with the correct time.


:guitar:

---

