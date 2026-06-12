---
title: "GRUB 2 won't listen to new settings."
date: 2011-07-29
forum: Desktop Environments
---

### Post by bv_andy on 2011-07-29
So I installed ubuntu 11.04 x32 (using unetbootin-win-549) next to Win7. Grub installed correctly, it added the win7 boot-loader to the list. 

All I wanted to change was the default selection, from Ubuntu latest kernel to Win 7. I first tried StartUp-Manager but the settings didn't take effect (default was still ubuntu and timeout was still 10, not 5 as I selected). Then I went to manually changing the etc/default/grub with gedit only to find that the new settings where already written there. So I just ran update-grub and tried again. Still nothing. 

My 3rd try has been with Grub Costumizer. Still nothing... the changes were there, I tried changing them a little but after reboot, Grub still had default settings. 

So my question is what am I doing wrong?

I am currently using a workaround by reinstalling win7 bootloader and adding grub to the list using easybcd. Which is good because win7 is the main os (for now) and it cuts a few seconds by bypassing grub. 
But I would still like to know what I missed. I've been reading through the "grub 2 basics" guide but I still can't see what I'm doing wrong.


Thanks for any help. (won't be back until tomorrow.)


**SOLVED**: I did two things today, 1. I reedited  /etc/default/grub with "gksu gedit" (I've seen others use it, I have no idea what it does) it is probably not this what solved it anyway. 

The second is that I ran "update-grub" with sudo (doh), yesterday I forgot to put sudo but it didn't give me any errors, it looked like it updated with no problems (even "/boot/grub/grub.cfg" looked updated).

---

### Post by Steam. on 2011-07-30
Mark thread as solved?Thread Tools>mark thread as solved.

---

