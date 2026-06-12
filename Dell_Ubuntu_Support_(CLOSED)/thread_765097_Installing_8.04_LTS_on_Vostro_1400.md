---
title: "Installing 8.04 LTS on Vostro 1400"
date: 2008-04-24
forum: Dell Ubuntu Support (CLOSED)
---

### Post by mindtrades on 2008-04-24
Hi!!
I have been having sleepless nights waiting for ubuntu 8.04..
Finally have started downloading iso and will install asap!!!:popcorn:
Have anyone installed the same on vostro 1400.
Are there any bugs or things that needs attention?

Config:
N/w : broadcom netlink ethernet
sound: sigmatel high defination audio 

As a newbie , i would require some help for the same..

---

### Post by user_linux08 on 2008-04-24
I have just ordered a new Vostro 1400, after which I will install the new Hardy Heron (or is that "Harem").

One recommendation I would proposed for the newbies (like myself) to consider. It is a good idea to have the /home directory on a separate partition of its own. This way you shield your data in case you will need to clean install or re-install the OS.

The way I did in the past. I gave only 10GB for the OS itself, the rest of the partition was dedicated to the /HOME directory. Since I intend to use Windows less and less, I partitioned it to no more then 40-50GB of space.

---

### Post by mindtrades on 2008-04-25
I would like people sharing their experiance of ubuntu with dell vostro 1400.

---

### Post by floyd4one on 2008-04-26
see my post here:
[http://ubuntuforums.org/showthread.php?t=766591&highlight=vostro+1400](http://ubuntuforums.org/showthread.php?t=766591&highlight=vostro+1400)

also, audio works, but i don't remember if i had to do anything special. in any case, any workarounds are readily available on forums/google.

cheers.

---

### Post by neptho on 2008-04-26
I dunno about an initial install..

I had to back out the 'snd-intel-hda model=5stack' modprobe hack from 7.10 to get it to work in 8.04; it killed and ate my 7.10 keyboard prefs (I lost ksnapshot and other keyboard bindings), and I had to put a little hack in because evidently it won't load my iwl3945 drivers faster than it tries to ifup the interface, so I have to ifdown, sleep 2s, ifup.

All in all, it's taken less work to make it work than Debian by itself, but I'm still a bit disappointed, as all of this hardware is, well, pretty standard.

---

### Post by Keyper7 on 2008-04-26
Didn't install it yet (lack of free time) but the Live CD already impressed me:

- No more black screen instead of splash screen (common problem in gutsy).
- No need for safe graphics mode for my GeForce 8400M GS.
- Wireless (intel 3945) working out of the box. LED wasn't working, but after installing
linux-backports-modules-hardy and reloading the iwl3945 module, a nice and shiny blue light appeared. :)
- Sound worked out of the box.
- Both headphone jacks worked out of the box, both properly disabled the speaker
when I plugged a phone and both can be used at the same time.
- Internal mic working out of the box and analog mic jack also working.

If all of those are kept after I do a full install (and I see no reason why they wouldn't),
that means that ALL hardware problems my Vostro 1400 had with Gutsy have been solved.

---

### Post by user_linux08 on 2008-05-09
I had no problem loading the ubuntu inside windows. All went well except the dreaded wireless (bcm4312 ver 1.0) not working.
However, I wish to partition the HD and load the ubuntu on its own partition and seperate /home partition.

NEVER MIND - PROBLEM SOLVED

---

### Post by user_linux08 on 2008-05-17
> **mindtrades said:**
> I would like people sharing their experiance of ubuntu with dell vostro 1400.
There 2 forms to install the ubuntu.
1. inside Windows (XP)
2. Partition the HD and install ubuntu on its own logic drive.

I tried both. in windows I had problem with the wireless. it would not respond. The whole prospect of being under windows should make one very nervous.
However after partitioning (Used Norton's Partition Magic) the drive. everything, except the microphone, it works fine.

mic is not recording

---

### Post by Keyper7 on 2008-05-17
user_linux08, try this:

Open Volume Control (right click on the volume applet near the clock), go to the options tab and select "Digital Mic" on "Digital Input Source".

---

### Post by omegamike3 on 2008-05-19
I initially upgraded from 7.10. It worked, though I started running into some suspend and sound issues. Mainly being, I could no longer suspend the laptop and the whole problem with sound after suspend came back, even though I had it working just fine. So I did a wipe and clean install. So far it's gone well. The wireless drivers (Dell 1490) that are installed by default work. Not fantastically yet, but they're much better than those with previous releases. The biggest complaint being that there were too many dropped connections and some speed issues. ndiswrapper solved these problems, just as it has in the past. Sound worked on the fresh install, but there were still problems after a suspend. The final thing is that there are some issues with suspend now which weren't an issue in 7.10. I've been able to narrow it down to a possible problem with the power state during suspension, meaning, was it running on the battery or on A/C power when suspended. There appears to be a problem then when reviving the computer if I change this state. It will wake up, give me the password dialog box but I have no keyboard or mouse control. Plugging in externals will work just fine, but a restart of the computer is necessary to bring back the native keyboard and trackpad. It might possibly be an issue with mapping after a suspend, as from time to time if I press, for instance, '9' on the keyboard, the computer will hibernate. However, if I bring it back from hibernation, the computer will be completely fine and even restore everything from the original suspend. So, there are some quirks but otherwise things are good. I especially enjoy that I can now watch any videos with Compiz enabled, as this was previously an issue with the x3100.

---

### Post by ukripper on 2008-05-21
Is the hard-disk ticking bug(load/unload cycle) still in hardy ( Vostro 1400). Can anyone confirm that for me? as on gutsy there was and I had to use workaround to fix that in 7.10

Bug:[https://launchpad.net/ubuntu/+source/acpi-support/+bug/59695](https://launchpad.net/ubuntu/+source/acpi-support/+bug/59695)

This is very critical bug and I really hope that is fixed in Hardy!


From the above link: an interesting post:

"ethanay  wrote on 2008-05-12:  (permalink)

[I][B]my laptop is running extremely well with Ubuntu after some configuration (and a lot of learning on my part). but this isn't a "windows vs linux" thread.

for people without heat problems, the ugly fixes for /etc/pm/*.d/ or /etc/acpi/*.d/ will work just fine. However, for people who have heat problems or require shock protection, the solution is much more complicated. furthermore, a solution for everyone is the most complicated, because it has to take into account both of the previous.

like someone else has pointed out, an ugly fix such as hdparm -B 254 is NOT a viable fix for Canonical to release for everyone because some people are dealing with excessive heat problems. This means that they have to work much harder to develop a more sophisticated solution to the problem that will be OK for everyone: appropriate apm settings for both unoptimized hdd i/o and also settings to optimize hdd i/o to allow for aggressive apm. given the complex software environment that this situation exists in, that takes time to develop and test.

however, i agree with others pointing out that it seems communication from Canonical to the general user population on this issue has been extremely lacking. that seems to me to be the bigger issue that this bug has exposed. either this is a fluke, or Canonical needs to use a more effective communications model in order to get messages out to the general user base.[/B][/I]"

---

### Post by user_linux08 on 2008-05-27
After re-installing the Hardy on the same partition (w/o formatting), now I have no network. Wired and wireless. The wireless light glows (from the windows driver). however on Hardy, I haven't been able to get Internet connection.

 I do have the bcm43xx-fwcutter (and b43-fwcutter). Also ndiswrapper-common & ndiswrapper-utils-1.9 installed.


Any suggestions please, how to connect to Internet..

thanks

---

### Post by ukripper on 2008-05-28
> **user_linux08 said:**
> After re-installing the Hardy on the same partition (w/o formatting), now I have no network. Wired and wireless. The wireless light glows (from the windows driver). however on Hardy, I haven't been able to get Internet connection.

 I do have the bcm43xx-fwcutter (and b43-fwcutter). Also ndiswrapper-common & ndiswrapper-utils-1.9 installed.


Any suggestions please, how to connect to Internet..

thanks

Strange it should be working out of the box both wireless and wired. Wireless is using iwl3945 in Hardy which I switched to even in gutsy as ipw3945 and problems in gutsy. iwl3945 is used out of the box in Hardy's kernel. You shouldn't have any problems at all. Can you do the following in terminal:
```
lsmod
```
```
lspci
```
```
dmesg | less
```

---

