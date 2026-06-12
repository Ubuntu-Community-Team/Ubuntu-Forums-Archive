---
title: "Sound Card with Wubi and 8.10"
date: 2008-12-02
forum: General Help
---

### Post by linesma on 2008-12-02
I used Wubi to install Ubuntu on my Vista machine.  I am having a problems with my sound card.  I have a Creative XFi-Extreme Music.  I downloaded the driver from Creative and installed it.  Upon reboot it works fine.  I shut down at the end of the day, and when I boot back to Ubuntu, I have to re-install my sound drivers.  Is this normal or did I miss a step?

Thanks,

Linesma

---

### Post by Jammanuser on 2008-12-02
> **linesma said:**
> 
I used Wubi to install Ubuntu on my Vista machine.  


wait...STOP!!! *warning bell sounds* 

i have only **one** thing to say: u might want to install ubuntu on a **actual** partition **real** soon, if u don't want to have the same "crc error" and then on next line "system halted" error message that prevents u from booting into ubuntu after about...a WEEK??? 

i did the exact same thing, and that was the end result! ^ 
so just fyi...i think u should install Ubuntu 8.10 on a SEPARATE partition than Vista, so u don't obtain the same result as me! ;)

Good luck! ):P

---

### Post by linesma on 2008-12-02
> **Jammanuser said:**
> wait...STOP!!! *warning bell sounds* 

i have only **one** thing to say: u might want to install ubuntu on a **actual** partition **real** soon, if u don't want to have the same "crc error" and then on next line "system halted" error message that prevents u from booting into ubuntu after about...a WEEK??? 

i did the exact same thing, and that was the end result! ^ 
so just fyi...i think u should install Ubuntu 8.10 on a SEPARATE partition than Vista, so u don't obtain the same result as me! ;)

Good luck! ):P

That is what I wanted to do, but I lacked the knowledge. I work with computers, but dual booting is one thing I never learned to set up. Is there as guide out there to do just that?

Thanks,

Linesma

---

### Post by abn91c on 2008-12-02
if you followed the forum sound installation guide here [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449) this is your last step to save the sound card
sudo alsactl store 0

---

### Post by Jammanuser on 2008-12-02
> **linesma said:**
> That is what I wanted to do, but I lacked the knowledge. I work with computers, but dual booting is one thing I never learned to set up. Is there as guide out there to do just that?

Thanks,

Linesma

here you go:
[http://apcmag.com/how_to_dualboot_vi...lled_first.htm](http://apcmag.com/how_to_dualboot_vi...lled_first.htm)

good luck and enjoy ubuntu

u can also check out this thread, where this issue is discussed:

[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)

Good luck and let me know how it goes! :D

---

### Post by linesma on 2008-12-03
> **abn91c said:**
> if you followed the forum sound installation guide here [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449) this is your last step to save the sound card
sudo alsactl store 0

Thanks. That is the step I missed. Did not have to do that on my laptop. Will have to try that when I get home from work.

linesma

---

### Post by linesma on 2008-12-03
> **Jammanuser said:**
> here you go:
[http://apcmag.com/how_to_dualboot_vi...lled_first.htm](http://apcmag.com/how_to_dualboot_vi...lled_first.htm)

good luck and enjoy ubuntu

u can also check out this thread, where this issue is discussed:

[http://ubuntuforums.org/showthread.php?t=963716](http://ubuntuforums.org/showthread.php?t=963716)

Good luck and let me know how it goes! :D

Thanks! Will check it out. Will give it a shot this weekend. I'll let you know how it goes.

linesma

---

