---
title: "Sudden failure to boot"
date: 2005-01-31
forum: Desktop Environments
---

### Post by Davepet on 2005-01-31
Dell Lattude CPiA 366xt (Pii-366, 128 MB, neomagic sound & video)

I installed about a week ago & has been working fine. This morning boot up stalled after "starting portmap daemon -  OK" ...3 times.

I dropped back to the next lower 686 kernel & it booted to the desktop, but the desktop was frozen.
Same frozen desktop with the 386 kernel.

Booted windoze, did my banking, spent about an hour & half in here looking for answers. No luck.

Rebooted into Ubuntu & the default kernel booted right up.

Have others seen this? Any info about where to look for problems?

Thanks,
Dave

---

### Post by Davepet on 2005-02-03
This continues to occur, & booting windoze seems to "fix" it for at least one boot. I'd rather find another fix though.

When it does boot up, the next step after the portmap daemon says it is "resetting ALSA" &then that it can't...sorry, I'll write the error down next time it comes up.

Dave

---

### Post by Wim Sturkenboom on 2005-02-03
Anything in the logfiles (/var/log/.....) ?

---

### Post by Davepet on 2005-02-03
Funny you should ask, I just took a look in a bunch of the log files tonight & didn't notice anything about ALSA, or anything else odd.

It booted right up tonight, so all I got was "restoring ALSA mixer settings"  there's lots more, of course.

Intermitant problems are maddening....

Dave

---

### Post by Davepet on 2005-02-05
OK, finally got the entire message:
----------------------------------
Restoring Alsa mixer settings alsactl:set_control:966:cannot write control '2:0:0:CD playback switch:0' : invalid argument
-----------------------------------

This message appears after the "starting portmap daemon"  message when the machine boots successully, so I'm assuming that on some boots the machine is choking on this.

Why sometimes it does & other times it doesn't is beyond my comprehension.

At this point I'd even appreciate wild speculation, since so far no one seems to actually know what's going on ;o)

Dave

---

### Post by Wim Sturkenboom on 2005-02-07
google search on [cannot write control '2:0:0:CD ](http://www.google.co.za/search?hl=en&q=cannot+write+control+%272%3A0%3A0%3ACD+&btnG=Google+Search&meta=)
Hope some of the info is usefull.

---

### Post by Davepet on 2005-02-07
Well, those pages only told me that others have seen the same problem, but they led me to the ALSA project page where I found the  info for neomagic cards:

[http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Neomagic&card=MagicMedia+256AV.&chip=NM2200&module=nm256](http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Neomagic&card=MagicMedia+256AV.&chip=NM2200&module=nm256)

Right at the top:
Known bugs:- driver often hangs up at boot time. 

I'm still looking to see if it's been fixed in later versions of ALSA. I also noticed that Ubuntu doesn't seen to be loading the ALSA driver as that page describes.

I'm going to try & change the title of this thread to include "Neomagic" so others with this card can find it easier.


Thanks,
Dave

---

### Post by fritzel67 on 2005-02-09
I have the same problem on my CPiA 366 laptop (also Neomagic audio/video). I have found that unplugging the laptop, and pulling the battery out for a few secs seems to resolve the issue as well. I suspect that may be functioning as a hard reset of the sound card, and that this may be why the problem is intermittent with the ALSA drivers. I have yet to find a fix/resolution more acceptable though.

---

### Post by fritzel67 on 2005-02-09
After posting here today, I tried something based on the possibility that the ALSA store/restore stuff isn't really what was causing my boot hang problems. I tried adding "acpi=off" and "apm=off" to /boot/grub/menu.lst. I then added "apm" to /etc/modules. I've now rebooted multiple times and haven't got stuck once.

Please post any feedback.

Thanks.

---

### Post by Davepet on 2005-02-09
Interesting, I had done all that except "apm=off" so maybe that's the key.
The last 2 or 3 boots have been trouble free, though, so not sure if I want to mess with it ;o)

Dave

---

### Post by fritzel67 on 2005-02-10
Alas, it appears that my hangs appear to have been caused by ACPI and not ALSA. What was misleading is the fact that when ACPI was enabled, the ACPI module actually displayed an "OK" during the init process. This is what initially led me to believe that it was the next process in the load order (ALSA restore) which was getting stuck. In retrospect, it was not that at all, as it appears that ACPI was only loading successfully 50% of the time. After trying several ACPI/APM settings, here is what appears to have finally resolved the init hang issue during boot on my Dell CPiA 366 laptop:

1. Reverted any changes made to the ALSA config files back to default values.
2. Disabled ACPI and enabled APM power management as follows:

a. Edit /etc/modules and add [COLOR=Red]apm[/COLOR] to the list 

b. Edit /boot/grub/menu.lst and change the kernel line as follows (add acpi=off):

kernel   /vmlinuz-2.6.8.1-3-386 root=/dev/hda4 ro quiet splash [COLOR=Red]acpi=off[/COLOR]

c. Edit the #kopt line of /boot/grub/menu.lst so that it ends with [COLOR=Red]apm=on[/COLOR]

d. Add [COLOR=Red]shpchp[/COLOR] and [COLOR=Red]pciehp[/COLOR] to the end of the /etc/hotplug/blacklist file (they don't work with APM, and error out during boot anyway)

e. In order to make sure this change propagates to future kernel upgrades, you'll also want to edit the default line in /boot/grub/menu.lst as follows (add acpi=off):

# nonaltoptions=quiet splash [COLOR=Red]acpi=off[/COLOR]

After those changes, I've been able to reboot (both warm and cold) without a problem. I still receive an error when ALSA restore tries to run during the init process, but this appears to be non-critical, as the init process continues on normally. I really like the Ubuntu distro, and it runs great on this older laptop (even detected my WiFi card), but this boot hang problem has been a real pain until now. 

fritzel67

---

### Post by Davepet on 2005-02-10
fritzel67,

Just to be clear, in an earlier post, you said you set "apm=off" & your last post says you set "apm=on" in the grub menu. Was there a typo & if so which one is correct?

Step "c" is the only one that I hadn't done before you posted, & I still had the problem, but for some reason, even without "c", my last 5 or 6 boots have gone normally.

If there are any further developements, I'll post here.

Dave

---

### Post by Davepet on 2005-02-11
Update: It failed to boot this AM, so I tried the shutdown/unplug power routine which worked (& is faster than rebooting to windoze).

I've now added apm=on in mmy grub file & will report back later after a reboot.

I sure hope it wasn't supposed to be apm=off ;o)

Dave

---

### Post by fritzel67 on 2005-02-11
Dave,

Yes, sorry for the confusion. The #kopt line should end with apm=on. From what I've gathered, ACPI is partially "broken" on the CPiA laptops, and the last solution I posted disables ACPI and enables APM. I'm on my second day, and have yet to get stuck.

If you still hang after making the above change, I'd be curious to find out if during your init process, you still see ACPI trying to load.

fritzel67

---

### Post by Davepet on 2005-02-11
ACPI isn't *partially* broken on these machines, it's so broken that in order to apply the most recent BIOS upgrade (A15, I believe) dell has a mandatory patch that keeps w98 from trying to use ACPI.

I've had to manually disable ACPI via cheat codes in order to get Knoppix to boot at all & had to disable it in other distros as well. I couldn't get Ubuntu to first boot after install without disableing it, so it's unlikely that it's still trying to start.

I won't boot again until tommorrow, but will report my results either way.

Dave

---

### Post by Davepet on 2005-02-15
Just a quick update, this problem seems better, but it's not beaten. 2 out of the last 6 boots hung.

No idea what to check next, any thoughts?

Dave

---

