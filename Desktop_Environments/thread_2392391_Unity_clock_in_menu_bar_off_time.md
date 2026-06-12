---
title: "Unity clock in menu bar off time"
date: 2018-05-20
forum: Desktop Environments
---

### Post by Skaperen on 2018-05-20
i have the clock enabled in the menu bar for most of my usernames in Unity.  but in one of them that clock shows the wrong time, 31 seconds behind the system time (as seen by the _date_ command and a C program that calls _gettimeofday()_).

**anyone know how this could happen and/or how to fix it** (i disabled it and re-enabled it and it is still behind by 31 seconds).

i would think that a clock program would just show the system time and if not getting it every second, it would get it at least every hour.  i saw this problem before the top of the hour that just passed and the error is still there.

i am running Ubuntu 16.04.4 last upgraded May 11.

---

### Post by TheFu on 2018-05-21
I would check
* configured TZ variables - timezone settings choose what gets displayed. TZ differences around the world aren't 30 seconds off, but in some places they are 15/30 minutes different, which seems very odd to people in the western hemisphere where all our TZs are 1 hour off.
* BIOS battery - time issues are often battery issues
* new userid setups - to remove system-wide question and determine it is or isn't specific to 1 userid.

---

### Post by Skaperen on 2018-05-21
the user having the problem is "admin" which is the name i entered when installing Ubuntu 16.04 LTS fresh from a USB memory stick with the ISO image dd-d to it.  when i boot up "admin" is the user that is automatically logged in to get things started.  i then start a terminal to get a command line.  a script in there prompts me for more passwords which are for things like a passphrase for an encrypted file system.  i log 11 more users on, some of which have their home directory in the encrypted file system.

all other users have the correct time in their menu bar.  this suggests to me that it is *not* a system wide problem, such as the kernel clock.  the fact that the time can vary by user suggests that the code/module/process/thread doing the clock display is not getting time from the system/kernel clock.

the "admin" user logged in much earlier than the other users, which were logged in automatically as a group about 15 seconds apart (slowly to give their instance of Unity plenty of time to get everything it runs started and stable).  users were logged in using "dm-tool switch-to-user $username" which i have no reason to believe will affect the menu bar time.

today is a new day.  i booted up about 3 hours ago before posting this.  **the time offset is not happening today.**

---

### Post by TheFu on 2018-05-22
Here's how it should work

Internally, there is only 1 clock which is based on UTC.  The system has a default timezone which it displays the UTC based on  constantly updated TZ tables.  There is also formatting based on the locale settings.

15 Unity sessions is a bunch for any system. Unity is heavy.  I'd bet that switch-user was never intended to be used for more than a family and probably not tested for more than 5 users.

During different times, the system will be busy which can cause lags for GUI processes.  If it comes back, can you try a lighter DE - like LXDE?

User HOME directory encryption has been deprecated in 18.04 for a few reasons, mainly performance and less security than FDE.

If the problem doesn't exist any more, please mark the thread solved.

---

### Post by Skaperen on 2018-05-22
actually, it's only 12 sessions.  the drop-down list won't show more than 12.  11 sessions have 9 workspaces each and one has 4 workspaces.  6 of the sessions have terminal processes running with active bash shells.  the others have a dedicated purpose only involving firefox.  the session named "forums" has a mix.  the system tends to not feel busy unless i am doing some heavy stuff like full file scans or a massive recompile (typically only 2-4 times a day). 

all 12 sessions run fine and were running fine when the clock was off time.  this laptop has 4core x 2ghz on 16gb.

yet another day and the problem has not come back.  if it is off by some fraction of a second, i won't notice this.

nothing was solved.  the problem remains _unreproducible_.  there is no available marking for that.  i don't want to mislead people into believing that if they spend the time to read the posts in this thread, they will get a solution.

---

