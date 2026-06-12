---
title: "Upgrading made my soundcard disappear ?"
date: 2008-01-04
forum: Desktop Environments
---

### Post by tadeusz666 on 2008-01-04
Hi everybody,

Im running Gutsy AMD64 and had no problems with my soundcard (MCP51 High
Definition Audio) that worked out of the box.

So booting up after x-mas holidays, gave me new upgrades that i unfortunately 
didnt read carefully, cos after i upgraded and rebooted, i got a:

No volume control GStreamer plugins and/or devices found 

so i did some reading around this forum and the internet in general with the above
error output and couldnt really find out what exactly happend.

I did a:

 sudo lshw -class sound

and got this:

 *-multimedia UNCLAIMED  
       description: Audio device
       product: MCP51 High Definition Audio
       vendor: nVidia Corporation
       physical id: 10.1
       bus info: pci@0000:00:10.1
       version: a2
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list
       configuration: latency=0 maxlatency=5 mingnt=2

Which i think means it can find my soundcard ...

and I then did a:

cat /proc/asound/cards

and it said:

--- no soundcards ---

So does it mean that i have to install my card again ? Or could it be that
user-permission-issue ive read about somewhere ?? 

Any clue would be much appreciated as im quite new to Ubuntu and linux.

Thanks in advance 

T

---

