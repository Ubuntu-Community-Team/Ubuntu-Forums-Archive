---
title: "No panels or sound on Ubuntu 10.04"
date: 2012-07-10
forum: Desktop Environments
---

### Post by BenJetson on 2012-07-10
I am totally new to Ubuntu, and have been using it for a week or two now, and am now starting to run into some issues. :( I am currently running Ubuntu 10.04 on an old custom built tower of mine.

[LIST]
[*]My first (main) problem is that,just a day or so ago, my panels disappeared from my desktop, and the only thing I see on screen are my launchers on the desktop. Have no idea how it happened.
[*][COLOR="Blue"]I have moved the sound problem to the **Hardware** forum.[/COLOR] [See thread HERE]("http://ubuntuforums.org/showthread.php?p=12091798#post12091798")
[/LIST]

Please Help!

---

### Post by jmfal on 2012-07-10
Welcome to Ubuntu 

Run this in a terminal to fix the missing panel

[http://www.ubuntugeek.com/tiphow-to-restore-accidently-deleted-top-panel-in-ubuntu-10-04-lucid.html](http://www.ubuntugeek.com/tiphow-to-restore-accidently-deleted-top-panel-in-ubuntu-10-04-lucid.html)

Hopefully when the panel is restored you can unmute the sound

---

### Post by BenJetson on 2012-07-10
> **jmfal said:**
> Welcome to Ubuntu 

Run this in a terminal to fix the missing panel

[http://www.ubuntugeek.com/tiphow-to-restore-accidently-deleted-top-panel-in-ubuntu-10-04-lucid.html](http://www.ubuntugeek.com/tiphow-to-restore-accidently-deleted-top-panel-in-ubuntu-10-04-lucid.html)

Hopefully when the panel is restored you can unmute the sound
I don't believe it worked, I ran the commands, and then rebooted my machine, still no panels. I've tried logging in using a "Failsafe GNOME" session, that didn't work either. Other suggestions or ideas? 

> Hopefully when the panel is restored you can unmute the sound
Even with my panels on, there is no sound. My sound card is not detected, not muted. Can't get ASLA Mixer to come up either, maybe ASLA is not installed?

---

### Post by BenJetson on 2012-07-10
Just a question: I know Microsoft Windows has System Restore, is there something similar that I can use on Ubuntu (built-in)?

---

### Post by jmfal on 2012-07-10
Read this , the first command is similar but should work, you can try the second one if it doesn't..

[http://ubuntuforums.org/showthread.php?t=1520623](http://ubuntuforums.org/showthread.php?t=1520623)

---

### Post by BenJetson on 2012-07-10
Sorry, no dice with that one either. :(
Can I somehow recover my machine from a LiveCD?

---

### Post by jmfal on 2012-07-10
Lets try this before you try the live cd

Restart and get to grub screen(see link) select recovery kernal and select "dpkg fix broken packages and follow prompts.
 When that is done at the command prompt enter

```
 startx
```
 and follow prompts.

---

### Post by BenJetson on 2012-07-10
Got past GRUB screen, selected recovery (2nd option from top), and from there, i saw a bunch of stuff load, and then this popped up, and then everything stopped.

> fsck from util-linux-ng 2.17.2
Ubuntu: clean, 183227/4685824 files, 1327368/18738176 blocks
*Starting apparmor profiles                skipping profile in /etc/apparmor.d/disable:usr.bin.firefox
                                                [OK]
*setting sensors limits*                         [OK]
skip stopping firewall:ufw (not enabled)
_

The last little underscore on that quote represents the cursor that keeps blinking on screen. Can't type anything. Pressing enter does nothing.

Note:I have recently moved the sound problem to the Hardware forum. [See thread HERE]("http://ubuntuforums.org/showthread.php?p=12091798#post12091798")

---

### Post by jmfal on 2012-07-10
Sorry for taking so long to get back, had some thunder storms roll thru had to shut down for a little while.
YOU can try and restart with the live cd and try  "fsck"

I haven't done it in while so I can't help to much.

---

### Post by BenJetson on 2012-07-11
You mean run that in a terminal? Or from the LiveCD's grub screen?

Thanks for all your help, and Have a great day. :)

---

### Post by jmfal on 2012-07-11
Reboot to the live cd.

Make sure that partitions that you want to check/repair are not mounted.

One fix I looked at said hdd might be failing, another said that he repaired it using fsck.

YOU can try and reboot to the recovery kernal and run 

```
sudo service lightdm start    
```

then

```
  startx
```

if the first command didn't get you to login screen.

---

### Post by BenJetson on 2012-07-11
Just decided: I need to upgrade anyway, I'm installing Ubuntu Desktop 10.10 LTS. I can't upgrade this machine to 12.04 because it is older, and it would slow it down due to the processor being old. The processor is an AMD Athlon XP, and I am  Dual-Booting XP Home and Ubuntu.

Thanks for your help, have a great day. :)

---

### Post by jmfal on 2012-07-11
What are your specs maybe you can run 12.04

10.10 is end of life, no more updates and security patches

---

