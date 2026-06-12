---
title: "No graphical interface in ubuntu, graphics card faulty?"
date: 2011-03-06
forum: Dell Ubuntu Support (CLOSED)
---

### Post by montango on 2011-03-06
Hello,

I didn't find any answer to my questions by browsing forums, so I state them here. If I missed a thread, please tell me so.

I have a Dell Vostro 1510 with a nVidia GeForce 8400M GS card. 

2 weeks ago, my Windows XP just died (the system32 folder is unreadable), so I start using the previously installed ubuntu on a partition on the HDD.

I'm a newbie, so I certainly didn't know how to set things perfectly (I had to update/upgrade the ubuntu OS, I had some problems, but in the end this seemed to work)

Yesterday I got a huge problem though :(: I wanted to upgrade ubuntu 9.10 to 10.04 and the coputer crashed during the process (it just stopped); it had previously done so once or twice yesterday. I guess it was getting too hot, although i have not run any CPU-hungry software (just firefox); I noticed the fan was always very loud in ubuntu, more than in XP.

So now, when I try to start ubuntu, I get the message::(

"ubuntu is running in low-graphics mode

your screen, graphics card, and input device settings could not be detected correctly. You will need to configure these yourself."

After which I am asked to choose between the following:

- Run ubuntu in low-graphics mode just for one session (does not work)
- reconfigure graphics (I get 3 options, none of which works)
- troubleshoot the error (open some files , I think xconf, but I don't know what to do, some advanced knowledge seems required)
- exit to console (works fine, even with wired internet acces)

I tried to reinstall the nvidia driver, found it, installation worked fine, but the error persists.

I'm afarid the nvidia card is broken, I heard this happens on the Vostros, but I didn't have any of the display errors mentioned on 

[http://en.community.dell.com/dell-blogs/Direct2Dell/b/direct2dell/archive/2008/09/12/nvidia-gpu-update-limited-warranty-enhancement-details.aspx](http://en.community.dell.com/dell-blogs/Direct2Dell/b/direct2dell/archive/2008/09/12/nvidia-gpu-update-limited-warranty-enhancement-details.aspx)

namely:

[LIST]
[*]Intermittent video issues
[*]Multiple images
[*]Random characters on the screen
[*]Lines on the screen
[/LIST]
Sometimes, the display froze, but I think it was more firefox related, as the other applications worked; a few times, the standard ubuntu movie player worked bad, but vlc was always ok. But the overheating/crash today might be a sign of a faulty graphics card.:confused:

So, before I try to ask Dell for help (computer is 2,5 years old, warranty expired in september), is there any way to check if the problem is with the video card itself or it's with the ubuntu installation.

I don't even know if I still have the 9.10 or the 10.04, because the upgrade process was interrupted.

By the way, because of the initial installation of ubuntu on a partition of my HDD 2 years ago (when my windows crashed again), I got stuck with the 64bit version of ubuntu (Windows was 32bit).

Please help!:(

---

### Post by montango on 2011-03-06
I'll try to make a fresh install, maybe it works then; but I need to backup my files first; unfortunately I don't know how to send them to an external HDD, because it is not listed in /media/, so I have to send them by scp to some other server...

---

### Post by montango on 2011-03-06
So, I actually managed to install ubuntu from an USB stick (last version 10.10) and everything works fine. I previously backed up my data on an external HDD that I had to mount manually.

---

