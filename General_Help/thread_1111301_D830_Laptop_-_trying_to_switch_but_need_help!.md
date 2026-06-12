---
title: "D830 Laptop - trying to switch but need help!"
date: 2009-03-30
forum: General Help
---

### Post by u.2 on 2009-03-30
Hi,
I am making the big switch and I am not entirely new to linux but never used it day in/out on my primary machine and haven't done a ton.

I have a few issues and I Haven't gotten any replies in the other forums on how to fix them entirely. SO here goes.

I have a Dell D830 laptop - 4gb ram - should I use the 32 or 64bit version of Ubuntu? I am using 32 now but plan to host VM systems on it using vmworkstation or virtual box.

SO far my main issues are:
1. NIC Settings don't stay - I setup a static IP config and it stays there but every reboot I get a new connection for "auto" and it defaults to that. Then the original DHCP connection it makes also is there even though I deleted that. "Done all this via the gui" in the panel tray.

2. Dual monitors - the resolution on my laptop even without dual is not right, it should be in the 1400's but it is at 1024x768 and I can't pick bigger?
Then my dual monitor settings, once I dock my laptop in the morning and power it up, I can't login because my primary screen goes to my main monitor but nothing shows up, and I end up hard powering off. I found the fix is to shut off the external monitor but there must be an easier way then shutting that off each time I dock it?

3. RDP client - HELP - I have to manage windows servers. I am using the built in Terminal Server Client on ubuntu and if I don't immediately "Grab" the window when it goes to open to a server and move it to the middle of the screen then I can't use my mouse on either screen and the keyboard stays locked in the RDP screen, so I tab around to log out and then try to catch the window and move it somewhere else on the screen once it starts opening.

4. How to run these gui apps as sudo? Is that my problem?

5. How come ubuntu doesn't prompt for root permissions like the other linux distro's I have tried and how do I get my settings to stay and ensure I get the right file permissions when I creat files?

6. How do I run the gui apps for system settings to that my settings save to the right place?

7. Should I try version 9.0.4 since it is supposed to fix some bugs?

8. How do I rescan or update my video card driver?

---

### Post by kanikilu on 2009-03-30
> 3. RDP client - HELP - I have to manage windows servers. I am using the built in Terminal Server Client on ubuntu and if I don't immediately "Grab" the window when it goes to open to a server and move it to the middle of the screen then I can't use my mouse on either screen and the keyboard stays locked in the RDP screen, so I tab around to log out and then try to catch the window and move it somewhere else on the screen once it starts opening. Hmm, I'm not sure why it's doing that, but under the Display tab in the Terminal Server Client, what is the "Remote Desktop Size" set to? If it's set to "default" or "full screen", try setting a specific size like 1024x768 or 1152x864.

> 4. How to run these gui apps as sudo? Is that my problem? Generally speaking, you don't need to run apps as su (expect in the case of something like synaptic), but if you need to, you can use ```
gksu app
```

> 8. How do I rescan or update my video card driver?Look under System > Administration > Hardware Drivers to see if there are any restricted drivers available.

I know for you it seems easier to just put all your questions in one thread, but for people coming to try to help, it's a bit daunting to have a laundry-list of problems to try to tackle, and some may not decide to post at all, even if they know the answer to one of our questions.

I would suggest prioritizing your list and post the questions one at a time.

---

### Post by 3Miro on 2009-03-30
Static IP settings under ubuntu area somewhat iffy. On one machine I removed the Gnome Network manager and did it manually. On another, I replaced the  GNM with WICD:

[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

There is a way to do the static IP thing with the Gnome manager. I read somewhere that you have to keep the old connection and simply add another connection. I have not verified that, but I guess you can try. (i.e. Create a new static IP connection and then reboot to see what happens). 

For the video card, on 8.10 and 8.04.2 you only get the choice of nVidia 173 and 177. My advice is to install 177, reboot. Then go to synaptic package manager and install:
```

nvidia-180-kernel-source
nvidia-180-modaliases
nvidia-glx-180

```
Reboot.

9.04 should give you the option for 180 from the start (but 9.04 is still in Beta).

---

### Post by u.2 on 2009-03-30
Thx,

I did add a new connection with a static and deleted the existing entries, but after each reboot it recreates a new Network Connection.

I am trying to verify what Video Driver card I have in my laptop, I think it is an intel and not the nvidia but have to check.
Is there anything else I can do?  How is the upgrade from beta 9x to the stable version?  Will I have to start over?

As for the RDP client, I will try a specific window size, but I think I have it set to the 800x600 already statically.

What is the best way to build it up, should I find the hardware on the machine within windows first or use the dell site to find out what is in the system and then know specifically so if an issue comes up I have the specs?  Is there a hardware scanner for linux?

---

### Post by Yellow Pasque on 2009-03-30
> I have a Dell D830 laptop - 4gb ram - should I use the 32 or 64bit version of Ubuntu? I am using 32 now but plan to host VM systems on it using vmworkstation or virtual box.
Using 64-bit should give you a performance boost with virtualization (and other apps that make use of large integers). It will also allow you to use all of your RAM (unless your BIOS is buggy).

---

