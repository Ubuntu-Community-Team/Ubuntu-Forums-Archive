---
title: "Dual Boot Help"
date: 2006-09-11
forum: Desktop Environments
---

### Post by alleykat on 2006-09-11
I installed Ubuntu on a second hard drive and like the way it works. This is the first time to install Linux for me. I did this by swapping out the windows xp pro hard drive and installing a spare hard drive. Now I want to be able to run both on same machine, can I just put the XP drive back in and then add the Ubuntu hard drive as slave? What will I need to do to get it to boot up to the hard drive I would like to use?

---

### Post by turbojugend_gr on 2006-09-11
Boy you did a very ugly task by swapping your old drive. You see ubuntu setup would handle everything if it was in... You have 2 choices, either re-installing ubuntu with bith harddisks plugged, or going the rough way.

**1st choice**: First of all since you just used ubuntu for a short time you won't loose much, in fact you may not loose anything (if you care about not loosing anything, post so I can give a hint on that too, it is easy but since you are brand new on linux, I do not want to mess you up with too much information now). --> SO you have both your disks plugged in, you go into your BIOS setup (usually by hitting delete on startup) and set your system to boot from CD (you know how  to do that since you installed ubuntu :) ). You go for the installation again, you folow the process as before, and when you get to partition setup pay attention: you make sure windows drive-partition do not have FORMAT sign on it, and you ask the bootloader-grub to be installed on your master disk( that would most propably be the windoz one for  you). then you proceed with the process as you did before, and adter reboot a boot menu will appear for you to choose from! Feel free to ask additional info.

**2nd choice**: It is pretty dificult for you now, but if you do not want to perform the above again ask me and I 'll provide the info. Just in case you need a general plan for it, you should edit the /etc/fstab file as a root and make several changes on to it before plugging your windoz drive. Since you seem not knowing what you should change there you should provide some oinfo so I can hit back on that.

I certainly go for the 1st one... your choice though ;)

---

### Post by alleykat on 2006-09-11
OK so what I need to do is leave both hard drives in and re-load Ubuntu onto the second drive again? This will fix it so I can boot into windoze or Ubuntu? Windoze does not see the hard drive under My Computer but it is there if you go to thru Admin tools and look at the hard drives. Will I be able to access files on the windoze HD when using Ubuntu?

---

### Post by alleykat on 2006-09-11
I got it going now. Thanks :D

---

### Post by turbojugend_gr on 2006-09-12
See that was easy right? If you have any issue hit back on this forums...

---

