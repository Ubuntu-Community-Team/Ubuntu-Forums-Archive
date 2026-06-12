---
title: "Getting crashed on Dell Inspiron 6000"
date: 2009-02-23
forum: Dell Ubuntu Support (CLOSED)
---

### Post by praveensripati on 2009-02-23
Hi,

I am running Ubuntu Intrepid on a Dell Inspiron 6000 with all the latest updates.

Once in a while all the icons, images on the desktop get replaced with a 'X' characters, sometimes the  desktop wallpaper is replaced with a white background and I am not able to use any of the menu options. The shutdown is also not complete and I have to a hard shutdown.

I ran fsck and there were no errors.

Is it that a process got crashed ? How do I resolve this problem ?

Thanks,
Praveen

---

### Post by praveensripati on 2009-02-24
Sometimes Firefox also doesn't respond. I checked the FF Error Console and it has

"Failed to load XPCOM component: /usr/lib/xulrunner-1.9.0.1/components/libpyloader.so"
"Failed to load XPCOM component: /usr/lib/xulrunner-1.9.0.1/components/pyabout.py"

BTW, I have about 10 FF Addons (not sure if they are causing the problem.

I entered the Ctrl-Alt-Backspace key combination to restart X and there was not much progress.

Thanks,
Praveen

---

### Post by hockeyhead019 on 2009-02-24
does it crash randomly? like what are you doing when this happens?

---

### Post by praveensripati on 2009-02-25
@hockeyhead019

I haven't found any pattern when it occurs. But the last time it occurred was I had Firefox open with GMail and GReader Tabs.

---

### Post by dotdot on 2009-04-08
i have exactly the same problem.
bought laptop the other day.
installed 8.10..
ran through the update procedure - quite a few patches...

now today the box is hanging regularly.

can't get any key to work apart from the power off button.

it would appear there's a deadlock happening somewhere - but where ?
have checked the messages file - nothing untoward in there.

(ie 

Apr  8 09:33:30 6k kernel: [   74.571056] NET: Registered protocol family 10
Apr  8 09:33:30 6k kernel: [   74.572762] lo: Disabled Privacy Extensions
Apr  8 09:33:30 6k kernel: [   74.574529] ADDRCONF(NETDEV_UP): eth0: link is not ready
Apr  8 09:45:59 6k syslogd 1.5.0#2ubuntu6: restart.
Apr  8 09:45:59 6k kernel: Inspecting /boot/System.map-2.6.27-11-generic
Apr  8 09:45:59 6k kernel: Cannot find map file.
Apr  8 09:45:59 6k kernel: Loaded 51032 symbols from 98 modules. )



i do get the feeling the video driver is simply dying - not sure how to troubleshoot this.


any ideas folks ?

---

### Post by dotdot on 2009-04-08
issue resolved.

i deinstalled compiz & compiz-core.

no problems since - I'd know by now i'm hammering it... and no problems ;)

cheers

---

### Post by remiprev on 2009-04-08
> **praveensripati said:**
> Once in a while all the icons, images on the desktop get replaced with a 'X' characters, sometimes the  desktop wallpaper is replaced with a white background and I am not able to use any of the menu options. The shutdown is also not complete and I have to a hard shutdown

I had the **exact same problem** with my laptop (an Inspiron 6000) a few months ago. I thought it had something to do with the hard drive being corrupted because a lots of the messages I got were related to the *ext3* filesystem.

I didn't found a solution though. All I did was format my hard drive and reinstall Ubuntu on it. I didn't get that problem since then. Sorry I can't give you more help than this...

---

