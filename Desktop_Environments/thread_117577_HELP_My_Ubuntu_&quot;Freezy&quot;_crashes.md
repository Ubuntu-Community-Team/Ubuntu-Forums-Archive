---
title: "HELP: My Ubuntu &quot;Freezy&quot; crashes"
date: 2006-01-15
forum: Desktop Environments
---

### Post by rasmusbp on 2006-01-15
Hi,

I'm new to Linux and Ubuntu (Breezy) and have been using it now for two months or so. I've had problems with Breezy "freezing" on me every now and then, but today I've had three instances where the system completely "freezes" and the only thing I can do is turn off the power and restart. Needless to say, when you're writing an exam paper, this is the type of thing that makes you crawl back to the auld XP....

I hope someone can help me find out what's wrong! I can't seem to find a pattern in this - it often happens when OpenOffice Writer (2.0) is open, but not always. 

Below is listed the last inputs (before the last three crashes) found in the System Log - if that might be helpful!? Thanks anyone! 

Rasmus


[B]
Crash1:[/B]> 
localhost gconfd (root-10762) starting (version 2.12.0), pid 10762 user 'root'
localhost gconfd (root-10762) Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
localhost gconfd (root-10762) Resolved address "xml:readonly:/usr/share/gconf/local.mandatory" to a read-only configuration source at position 1
localhost gconfd (root-10762) Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 2
localhost gconfd (root-10762) Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 3
localhost gconfd (root-10762) Resolved address "xml:readonly:/usr/share/gconf/local.defaults" to a read-only configuration source at position 4
localhost gconfd (root-10762) Resolved address "xml:readonly:/usr/share/gconf/cdd.defaults" to a read-only configuration source at position 5
localhost gconfd (root-10762) Resolved address "xml:readonly:/usr/share/gconf/debian.defaults" to a read-only configuration source at position 6
localhost gconfd (root-10762) Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 7

**Crash2:**
> localhost /USR/SBIN/CRON[9267] (root) CMD (   run-parts --report /etc/cron.hourly)

**Crash3:**
> localhost kernel [4297956.051000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
localhost kernel [4297956.051000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
localhost kernel [4298014.560000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
localhost kernel [4298014.560000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
localhost kernel [4298014.661000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
localhost kernel [4298014.661000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.

---

### Post by GeneralZod on 2006-01-15
There's no serious errors in the log.  When it crashes, can you move the mouse? Can you switch numlock on and off? Have you tested your RAM with memtest? What graphics card + drivers do you have installed?

---

### Post by localzuk on 2006-01-15
None of those seem to be a problem. My guess would be a hardware issue. Is anything overheating? Try doing a memory test from the grub screen (select the MemTest option from the menu - (note my memory of the exact wording is not too great)).

---

### Post by AAUU on 2006-01-15
Try checking out this thread:

[http://ubuntuforums.org/showthread.php?t=76288](http://ubuntuforums.org/showthread.php?t=76288)

It's a lot of posts.  I found that disabling power management fixed my issue.  I've also added the noapic to my default kernel boot up parameters (/boot/grub/menu.lst).  

sudo /etc/init.d/apcid stop

I've been troubleshooting this issue for a few days straight and I haven't done research on exactly what apcid and noapic do.  I had thought the issue was with my firefox.  So I loaded up encap and built my own.  But the problem persisted.  Once I found the thread above, I went through and finally performed those two suggestions above.  It's been slightly under 24 hours with no lockup.  So I'm inclined to believe that one of those two things fixed the issue.  But I'm not clear on exactly what was wrong.  This didn't happen on a new install though.  It was only after the updater software (some kind of automagic apt-get update, check on differences) told me I needed to upgrade some packages and I did.  That's when I pin pointed the issue to start.  It appears that it might be the kernel that gets loaded.  I'm pretty sure that's the case because I preformed a new install and loaded all of the suggested upgrade packages but the kernel, and I didn't have any issues.  Then I upgraded the kernel and bam.

Incidentally, I'd love to hear more about those gconf log entries.  I get a lot of them and I can't seem to find any answers concerning them.  At this point, I may have better luck subscribing to the gconf2 development list.  

Questions appear to get burried in this forum easily.

---

### Post by rasmusbp on 2006-01-17
OK, thanks everyone for helping! 

I performed the memtest overnight - it ran for 10 hours straight without errors. 

When the system freezes, it really does, so I can't move the mouse, enable NumLck or anything like that. Nothing really seems to be overheating as far as I can tell. I've installed the CPU monitor to the menu bar, so I'm following it pretty closely. I have a ATI Mobility Radeon 9600, but I haven't installed the proper drivers, since it worked out-of-the-box when I installed Ubuntu. Other than that, I have installed the ipw2200 drivers to get my intel wlan card working. 

AAUU, thanks for the tip - I'll try to put noapic in the boot up and uninstall powernowd - and report back. With regards to the gconf entries, I haven't a clue what they are?!?

Thanks again  ;)
Rasmus

---

### Post by tkjacobsen on 2006-01-17
Have you installed the proper kernel for your system. If you use a i686 kernel on a pentium 4 it will be much more stable than with the i368 kernel.. 
You can install the kernel images from synaptic, adept or apt:
linux-image-i686                for most newer pentiums
linux-image-k7                   for AMD Duron/Athlon

---

### Post by rasmusbp on 2006-01-17
I am using ubuntu on my Asus laptop with a intel centrino 1.6 Ghz processor. 

btw - when i look in system > administration > device manager, and look under processor, it says "device unknown"........should I be concerned? :confused: 

VH Rasmus

---

### Post by PlatinumPlus on 2006-01-17
I am also on an Asus laptop but the funnies I get are when I reboot my keys no longer work so I can't logon. 

As it is booting, the Caps key responds up to the time the logon screen is displayed then the keys no longer respond. I have changed my Login screen setup to Happy Gnome with Browser. I will change back and see if this continues.

---

### Post by rasmusbp on 2006-01-18
hi again :D 

i uninstalled powernowd and removed apic from the boot-menu (via BUM), and so far I haven't had any crashes! So it seems that the problem was connected to one of the two.

Only thing now is that the CPU is permanently set to 1,6 Ghz, so the fan is on all the time and it's driving me nuts!! Are there alternatives to powernowd to fix this annoyance?

---

### Post by rasmusbp on 2006-01-24
A few days ago I installed linux686 (and all the related headers and stuff), uninstalled the 386, and RE-installed powernowd. And I haven't had any crashes in a few days now! (Apic is also installed)

So, linux386 might have a problem with powernowd, or vice verse...?!?

---

