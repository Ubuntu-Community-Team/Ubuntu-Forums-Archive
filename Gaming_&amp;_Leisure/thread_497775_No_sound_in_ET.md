---
title: "No sound in ET"
date: 2007-07-10
forum: Gaming &amp; Leisure
---

### Post by saggio on 2007-07-10
I've followed the instructions on how to get sound working [here]("http://http://ubuntuforums.org/showthread.php?t=362231"), but I've had no luck. 

```

----------sound initialization --------
/dev/dsp: Input/output error
Could not mmap /dev/dsp

-----------------------------------------

```

I'm not sure what I should be doing, here. All other sound works fine on my system (running audacious right now). Is there some config file that I need to tweak?

---

### Post by Kumeelyun on 2007-07-10
I had a problem with sound not working in UT2K4 even though the program ran fine.

After looking on a few forums I ran across a post saying that the Flash plug-in for Firefox doesn't like sharing sound with other programs if it is running first. I quit Firefox, started up UT2K4 and it worked perfectly.

I don't know if you have Firefox running while you're trying to play the game, but if you do, you might want to give it a try.

---

### Post by Contrast on 2007-07-10
If you're using Kubuntu, you may need to disable the sound system as I did - System Settings -> Sound System -> Uncheck "Enable the sound system" -> Apply -> Enjoy. Hope this helps.

---

### Post by chuckyp on 2007-07-10
The following command worked for me.

sudo echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss

---

### Post by saggio on 2007-07-10
> **chuckyp said:**
> The following command worked for me.

sudo echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss

It says permission denied. 

>  	If you're using Kubuntu, you may need to disable the sound system as I did - System Settings -> Sound System -> Uncheck "Enable the sound system" -> Apply -> Enjoy. Hope this helps.

I run Fluxbox, so I do pretty much everything from the terminal...Thanks for the reply though.

---

### Post by FoolsGold_MKII on 2007-07-10
> **saggio said:**
> It says permission denied.
That's because he's a n00b, and forgot to tell you how to do it properly. :)

su bash
echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
exit

Run et.

If this works (which it should), run

sudo gedit /etc/rc.local

and stick the "echo ...." line above in the file but **before** the "exit 0". That way the fix will be run every boot.

---

### Post by Doctoxic on 2007-07-11
or try this:

[https://help.ubuntu.com/community/EnemyTerritory]("https://help.ubuntu.com/community/EnemyTerritory")


doc

---

### Post by saggio on 2007-07-11
> **Doctoxic said:**
> or try this:

[https://help.ubuntu.com/community/EnemyTerritory]("https://help.ubuntu.com/community/EnemyTerritory")


doc

Okay, I followed the instructions for the sound troubling shooting and created the script and everything. But it still wont' work!

This is what I get, now:

```

------- sound initialization -------
/dev/dsp: Invalid argument
Could not open /dev/dsp
------------------------------------

```

This is really frustrating! Any ideas?

---

### Post by Doctoxic on 2007-07-12
for me it only worked with sound when i run it with the sudo command

doc

---

### Post by ~LoKe on 2007-07-12
Did you even try this?
> sudo su
echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
echo "et.x86 0 0 disable" > /proc/asound/card0/pcm0p/oss
exit

---

### Post by saggio on 2007-07-12
> **~LoKe said:**
> Did you even try this?

Yes, multiple times. Doesn't do anything.

---

### Post by whistle on 2007-07-12
Someone posted this in these forums as a scripted way to get sound to work... try putting this in a file and running it.

```
#!/bin/bash
if [[ ! $(grep 'et.x86' /proc/asound/card0/pcm0p/oss) ]]; then
 gksudo "bash -c 'echo \"et.x86 0 0 direct\" >> /proc/asound/card0/pcm0p/oss'"
fi
if [[ ! $(grep 'et.x86' /proc/asound/card0/pcm0c/oss) ]]; then
 gksudo "bash -c 'echo \"et.x86 0 0 disable\" >> /proc/asound/card0/pcm0c/oss'"
fi
et
exit 0
```

---

### Post by saggio on 2007-07-12
That doesn't work either. :( 

Man, I having no luck...

---

### Post by whistle on 2007-07-12
I also tried "SDL sound for ET" on this forum... both the script I gave you and that (SDL) worked alternatively for a while until the script was the only one that worked, if that makes sense (kind of in a hurry).  Search SDL Support, or something like that...

---

