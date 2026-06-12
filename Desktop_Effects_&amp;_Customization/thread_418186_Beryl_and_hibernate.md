---
title: "Beryl and hibernate"
date: 2007-04-22
forum: Desktop Effects &amp; Customization
---

### Post by pgilmon on 2007-04-22
Hi all,

I'm using beryl from the beryl-project.org repository under Edgy with nvidia proprietary driver .

Everything works fine, except for hibernation. When I try to hibernate the computer with Beryl activated it just won't wake up. I have tried adding
```
killall beryl
```
in a script in 
```
/etc/acpi/suspend.d/06-disable-beryl.sh
```
Then, after hibernating, the computer wakes up, but I can't write my password to unlock it, althoug I can use Ctrl+Alt+Backspace to restart X and then things get back to work.

Is there any other way to stop Beryl before PC goes to hibernate? I would be great if it could be stopped when hibernating and then started again on wake up.

---

### Post by Bastanteroma on 2007-04-23
These instructions worked for me:

[http://ubuntuforums.org/showthread.php?t=350265&highlight=script+suspend+beryl](http://ubuntuforums.org/showthread.php?t=350265&highlight=script+suspend+beryl)


this one goes in /etc/acpi/suspend.d/25-beryl-suspend.sh
Code:

#!/bin/bash
# /etc/acpi/suspend.d/25-beryl-suspend.sh

pids=""
for pid in `pidof /usr/bin/beryl-manager`
do
ps -o comm= --ppid $pid | grep -q '^beryl$'
if (($? == 0)); then
pids="$pid $pids"
kill -USR2 $pid
fi
done
export BERYLMGRPIDS="$pids"

and this one goes into /etc/acpi/resume.d/99-beryl-resume.sh
Code:

#!/bin/bash
# /etc/acpi/resume.d/99-beryl-resume.sh

for pid in $BERYLMGRPIDS
do
(sleep 10 && kill -USR2 $pid)&
done

---

### Post by fmaste on 2007-06-03
It work for me on my DELL inspiron 9400 (E1705) notebook

I use to have beryl on edgy but I loose suspend and hibernate (which I use a lot). I tried with the scripts to kill beryl when suspending/hibernating, but it didn't work or I had to reopen beryl manually but it was uncomfortable. Not having this feature in a transparent way is like having nothing for me, so I never installed beryl on feisty until today. I like beryl a lot, so I decided to give it another chance with what I found googling.

NOTE: I'm using feisty with beryl installed from the beryl repos, all the other setting are the default ones (I never manually edit xorg.conf or acpi-support and beryl setting were are the default ones) and suspend/hibernate was working out of the box without beryl.

- Disable "Sync To VBlank" in beryl.
It is located on general options of the veryl manager. Just unckeck it.

- Update your /etc/X11/xorg.conf and add an "Option "NvAGP" "1" line in the "Section "Device":
(must look like this)
Section "Device"
...
Option "NvAGP" "1"
EndSection

- Disable warm-booting the video hardware on resume by editing your /etc/default/acpi-support as follows :
# Should we attempt to warm-boot the video hardware on resume?
POST_VIDEO=false

Good luck!!

---

### Post by timzak on 2007-06-04
> **fmaste said:**
> It work for me on my DELL inspiron 9400 (E1705) notebook

I use to have beryl on edgy but I loose suspend and hibernate (which I use a lot). I tried with the scripts to kill beryl when suspending/hibernating, but it didn't work or I had to reopen beryl manually but it was uncomfortable. Not having this feature in a transparent way is like having nothing for me, so I never installed beryl on feisty until today. I like beryl a lot, so I decided to give it another chance with what I found googling.

NOTE: I'm using feisty with beryl installed from the beryl repos, all the other setting are the default ones (I never manually edit xorg.conf or acpi-support and beryl setting were are the default ones) and suspend/hibernate was working out of the box without beryl.

- Disable "Sync To VBlank" in beryl.
It is located on general options of the veryl manager. Just unckeck it.

- Update your /etc/X11/xorg.conf and add an "Option "NvAGP" "1" line in the "Section "Device":
(must look like this)
Section "Device"
...
Option "NvAGP" "1"
EndSection

- Disable warm-booting the video hardware on resume by editing your /etc/default/acpi-support as follows :
# Should we attempt to warm-boot the video hardware on resume?
POST_VIDEO=false

Good luck!!

Cool!  Thank you for this post.  I hadn't posted about this myself yet, was in the process of searching for a solution and yours works for me.

---

