---
title: "Random Freezes"
date: 2006-11-21
forum: Desktop Environments
---

### Post by dgtester on 2006-11-21
I've been getting random crashes on edgy. I *think* that they only happen when using the newest nvidia driver. They happen more commonly with Beryl/Compiz, and much less commonly with metacity (but they do still happen with metacity). Basically what happens is that everything freezes (keyboard doesn't work, mouse cursor doesn't move), and I have to do a hard reboot. Usually it happens when I'm doing something graphical such as resizing, or more commonly, just closing a window.

As my machine starts back up from one of these crashes, I get the following apparently fatal error:

"Could not kill pid 1785. No such process"

The pid is *always* 1785, don't ask me why, and my computer fails to ever go any further than this. When I do another hard reboot, it starts up normally. Does anyone have any ideas?

I've seen lots of other threads discussing random crashes on edgy, and most of them mention nvidia, so I suppose its related -- but none of them ever offer a solution :-(

---

### Post by andreag on 2006-12-19
I have a similar problem with compiz and an Intel card, so possibly the problem are not the nvidia drivers.

---

### Post by atarileaf on 2006-12-22
Did anyone find a solution to this problem? I've got the same Kill Pid problem on boot up that freezes the system but the number that comes up for me is 1855 everytime. ](*,)

---

### Post by Nikron on 2007-01-07
I have this exact same problem, except my mouse still moves.  Anyone know the answer?

---

### Post by mysticmarks on 2007-01-15
This is my only issue with ubuntu at the moment. I've extensively researched the threads, this is affecting users in every catagory, not just video drivers. I use ati, same thing. tried every suggested fix. it is coming up for firefox threads, video cards, plugins, etc. None of these are resolving the issue. I am finding that it is really a problem for AMD users. direct this one to ubuntu team leaders. It is a big issue. Thread searches for freezes, locks up, etc. will all be erily familiar to you all.

---

### Post by mysticmarks on 2007-01-15
Also, the file not found is simply the left over information from whatever task you were workin on. (ie- browsing,etc.) if the error repeats at boot, run the recovery mode from grub and it should get you back up. I have found that the freeze can be forced if you scroll very fast through any large data, that is on the web or in your file browser. I almost want to point a finger at the nautilus system, but too early for that.

---

### Post by zarknl on 2007-01-21
Hi everyone,

I have this "could not kill pid" not after a system crash but randomly when starting up, and till now on iMac and Macmini (so ppc ubuntu Edgy...)

Would be nice if it's cured!

Thanks!

Marc.

later i found this: [http://ubuntuforums.org/showthread.php?t=323536](http://ubuntuforums.org/showthread.php?t=323536) don't know if this does it...

(remove "quiet splash" from kernel startup options...)

---

### Post by Nikron on 2007-01-26
I got rid of this problem by updating my drivers...

using this thread..

[http://www.ubuntuforums.org/showthread.php?t=255929](http://www.ubuntuforums.org/showthread.php?t=255929)

---

### Post by atarileaf on 2007-01-27
For me, I had to remove the "break=bottom" command that was in my grub menu. When I did that, I no longer recieved the boot freeze.

---

