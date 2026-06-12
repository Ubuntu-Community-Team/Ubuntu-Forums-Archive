---
title: "monitor showing &quot;out of range&quot;"
date: 2009-03-15
forum: General Help
---

### Post by abhishek.182 on 2009-03-15
hi guys

i installed ubuntu8.10  and thenn i updated it......i also updated my display drivers (onboard NVIDIA)but then when i restarted .....
resolution of login screen was fine "1440x900" (which is my screen's max resolution supported )
when i enter my username and password it accepts but.......suddenly

my monitor displays "out of range......80.8khz/65Hz"

i am not getting wat is hapening actually to monitor
n plz give me a solution urgently its important.....

thanx in advance

---

### Post by perrti-y02 on 2009-03-15
Basically what it says is that the output from the computer is too high quality (or low quality) for the monitor. The only way I know of sorting this out is borrowing a screen from a friend that can do almost any resolution and changing the settings using that one.

---

### Post by LiamWilson on 2009-03-15
Or try booting into recovery mode or an old kernal, and change the screen resolution. 

If that doesn't work, and you you want to try perrti-y02's suggestion, I'd suggest an old CRT monitor (The big fat ones)

---

### Post by abhishek.182 on 2009-03-15
can you tell me how to change resolution in recovery mode....in detail
i hav tried to reconfigure the xorg.conf file in recovery mode...
nothing helped it

---

### Post by miegiel on 2009-03-15
> **abhishek.182 said:**
> hi guys

i installed ubuntu8.10  and thenn i updated it......i also updated my display drivers (onboard NVIDIA)but then when i restarted .....
resolution of login screen was fine "1440x900" (which is my screen's max resolution supported )
when i enter my username and password it accepts but.......suddenly

my monitor displays "out of range......80.8khz/65Hz"

i am not getting wat is hapening actually to monitor
n plz give me a solution urgently its important.....

thanx in advance

Try to findout how to set your refreshrate, it's probably to high. And check in your monitor manual or online what refreshrate your monitor can handle at 1440x900 (it's the Hz number, don't go above it).

---

### Post by LiamWilson on 2009-03-17
> **abhishek.182 said:**
> can you tell me how to change resolution in recovery mode....in detail
i hav tried to reconfigure the xorg.conf file in recovery mode...
nothing helped it

System > Preferences (Or Administration) > Monitor

---

### Post by hp owner on 2009-03-17
i just had the same problem, boot into the recovery mode and highlight the bottom phrase and hit enter, then reboot, it worked for me

---

### Post by chewit on 2009-03-17
I always have that problem.

Best thing to do is, unplug your montior. Boot up. When Ubuntu is finished booting (give it 5mins max), plug your monitor in. Ubuntu will see it as a generic monitor. That always works for me.

---

### Post by abhishek.182 on 2009-03-18
hey guys
thanks alot for ur suggestions were worth to me and they helped me alot
now my screen's resolution is fine

---

