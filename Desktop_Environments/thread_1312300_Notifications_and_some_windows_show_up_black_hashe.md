---
title: "Notifications and some windows show up black hashed??"
date: 2009-11-03
forum: Desktop Environments
---

### Post by mcmunt on 2009-11-03
Have recently updated an old IBM R40 laptop to 9.10 and noticed this weirdness in some app windows and most notification pop-ups. They appear as below in a dark area that has some cross hatching. That dark area in the screenshot is actually System Monitor. The window buttons still seem to work OK and so far, sys monitor is the only app that does this.

I've got visual effects turned off and everything else looks pretty good. When I turn visual effects to normal, the notifications appear in the wrong place and window drawing is messed up. So that's not really an option.

Any ideas?

[IMG]http://dl.getdropbox.com/u/58541/screenshot_001.png[/IMG]

Cheers
Mike
[www.wekadesign.co.nz](www.wekadesign.co.nz)

---

### Post by mcmunt on 2009-11-03
The problem seems to be related to this bug [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/416001]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/416001") and this one in freedesktop [https://bugs.freedesktop.org/show_bug.cgi?id=23668]("https://bugs.freedesktop.org/show_bug.cgi?id=23668").

A potential fix is to edit your xorg.conf as in the Launchpad comment by Grant Bowman. I'm about to try this now.

---

### Post by louieb on 2009-11-03
> They appear as below in a dark area that has some cross hatching. That dark area in the screenshot is actually System Monitor. Get same unreadable mess with the notification balloon and system monitor. IBM T30 here. 
> When I turn visual effects to normal, the notifications appear in the wrong place and window drawing is messed up. When I turn visual effects to normal, the notifications appear in the wrong place and window drawing is messed up.Nice description of what I'm seeing too.
> A potential fix is to edit your xorg.conf as in the Launchpad comment by Grant Bowman. I'm about to try this now.     Thanks I'll try that too.

---

### Post by mcmunt on 2009-11-03
Yep - that fix I mentioned above does the trick. Notification balloons and system monitor show up normally. Hooray! :D

But a few minutes after login, our friendly Xorg process is chewing up the CPU with usage from 10-50% under top. Hopefully it settles down as it's having an effect on basic tasks and things aren't so snappy now.

---

### Post by louieb on 2009-11-05
Thanks again. Worked for me too. 
BTW: I'm dual booting Jaunty and Karmic on the T30.

xorg CPU % in Jaunty bounces around from 4% to 20% most of the time but occasionally spikes to over 50%.

Karmic's xorg CPU %  bounces around the same , but the spikes seem to be higher.

---

### Post by jon.wolski on 2009-11-14
Worked for me, too, on a Thinkpad R32 with the following card:
```
$ lspci | grep -i radeon
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M6 LY

```

---

### Post by mande01 on 2009-11-16
Hello,
I tried this too but it didn't work. I have a T30 with a ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500].

Could someone tell me how to make the xorg.conf edit?
I'm new to all this stuff. I did the following:

sudo gedit /etc/X11/xorg.conf
and added
Section "Device"
        Option     "AccelMethod"                "EXA"
        [...]
EndSection
Then added this
Section "Device"
        Option     "AccelMethod"                "EXA"
EndSection

Could some one tell me what I'm doing wrong, cause when I reboot it gives me a weird login looking for a login name but won't take my login name.
So I go to root at boot and undo the edits to xorg.conf.

Any help would be great, I'm pretty sure I'm just missing some basic step in the xorg.conf process.

Also my memory is really low:
free
                      total       used       free     shared    buffers     cached
Mem:        250172     239548      10624          0      10296      86764
-/+ buffers/cache:     142488     107684
Swap:       626492      75240     551252

I know, I know... I have a motherboard issue that is not allowing the other 256 to be seen.
Could the low memory be my problem?

Thanks,
Derry

---

### Post by pi3832 on 2009-12-04
@

---

