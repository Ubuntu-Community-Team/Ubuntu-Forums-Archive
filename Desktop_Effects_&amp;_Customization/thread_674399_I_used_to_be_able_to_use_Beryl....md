---
title: "I used to be able to use Beryl..."
date: 2008-01-21
forum: Desktop Effects &amp; Customization
---

### Post by SZF2001 on 2008-01-21
It's an odd thing... I used to have Feisty, installed Beryl and it worked like a charm on my crappy 32MB video card. I can't specifcally tell you what card it is...

I forgot the command, but from what HardInfo tells me it's this:

nVidia Corporation NV11 [GeForce2 MX/MX 400]

So yea, pretty old, and I really don't see the need to upgrade to a new card unless that's the ONLY way to get this working...

Anyway. So Beryl used to work. now I have Gutsy on the same machine and I can't manage to have Compiz-Fusion going... I used to have Compiz and Beryl working on Feisty, so I'm just wondering whats the deal here?

I installed the "NVIDIA accelerated graphics driver" from the Restricted Drivers manager, same as I did in Feisty. Should I compile my own driver from the NVIDIA website or something? I can't get any effects working and I KNOW this card can pull it off...

---

### Post by FuturePilot on 2008-01-21
There's a restriction on Nvidia cards with less than 64 MB in the Gutsy Compiz Wrapper. Most likely due to the black window bug. There's a way around it, but I wouldn't recommend it because when I tried it on my GeForce2 Go 32 MB all I got was black windows.
```
gksudo gedit /usr/bin/compiz
```
Find this section, it's near the top
```
# Minimum amount of memory (in kilo bytes) that nVidia cards need
# to be allowed to start
# Set to 262144 to require 256MB
NVIDIA_MEMORY="65536" # 64MB
NVIDIA_SETTINGS="nvidia-settings" # Assume it's in the path by default
```
You need to adjust the NVIDIA_MEMORY number.
```
# Minimum amount of memory (in kilo bytes) that nVidia cards need
# to be allowed to start
# Set to 262144 to require 256MB
NVIDIA_MEMORY=[B][COLOR="Red"]"30000" # 32MB
[/COLOR][/B]NVIDIA_SETTINGS="nvidia-settings" # Assume it's in the path by default
```
You can try it but don't be surprised if you get black windows and sluggish performance. That's how it was with mine even with the --indirect-rendering option.

---

### Post by SZF2001 on 2008-01-21
Interesting...

Can you say, set it at 54? Or does it all need to be evened by it's double? (example: 2x2 = 4, 32x32 = 64, etc)

---

### Post by FuturePilot on 2008-01-21
You can set it to anything really. But you just have to make sure it's lower or equal to the amount of RAM your graphics card has or else it won't work.

---

