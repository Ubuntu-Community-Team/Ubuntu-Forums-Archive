---
title: "Ugent!!! Help!! I lost all permissions!!"
date: 2009-02-05
forum: General Help
---

### Post by fattredd on 2009-02-05
i DONT KNOW WHY, BUT I LOST ALL PERMISIONS ON MY SYSTEM. i CANT  EVEN OPEN THE TERMINAL! THIS IS MY ONLY account! PLEASE HELP!!!


(IF WE CAN FIX THIS then TALK ABOUT WHAT HAPPENED IT WOULD BE NICE... BECAUSE I CANT EVEN SEE WHAT IM TYPING... ALL I SEE IS BOXES WITH NUMBERS IN THEM...)

i HAVE IMPORTANT FILES ON THIS COMPUTER AND I CANT REINSTALL (UNLESS THERE IS A WAY TO KEEP OLD FILES WHEN REInSTALLING?)

---

### Post by fattredd on 2009-02-05
The only reason i have firefox is because i had it open before the error happened... so the sooner i fix this the better...


Edit: I just checked, and i cant even access the help file... i can only use the one firefox that i have open...

---

### Post by lykwydchykyn on 2009-02-05
I don't know how we can fix it without talking about what happened.  What do you mean you lost all permissions?  What did you do?

---

### Post by fattredd on 2009-02-05
i didnt do anything... but i cant even open a folder...

---

### Post by fattredd on 2009-02-05
Please help!!!!!!!!!!!

---

### Post by smo0th on 2009-02-05
so, system got spontaneously buggy? from my experience, linux systems don't do that, and if there's nothing else to remember and identify as possible cause I'll just press the restart button and wait for a reboot, if you get trouble booting/logging then we could discuss, but before pressing the restart button try just restarting the x-server by pressing ctrl+alt+backspace, anyway, that's just what I would do.

---

### Post by lykwydchykyn on 2009-02-05
Don't panic.

Because it comes down to this:  Either your HDD is hosed, and the system is beyond hope, or it's not.  Either way, nothing you do at this point is going to change that.

Open a tab in firefox and put in this URL:
file:///var/log/syslog

If you can open that, post the contents here.

---

### Post by fattredd on 2009-02-05
i cant open it... or anything else...

I just switched to my laptop because now i can see what i type...

---

### Post by fattredd on 2009-02-05
Please help!!

---

### Post by fattredd on 2009-02-05
Bump

---

### Post by fattredd on 2009-02-05
please help me....

i need it as soon as i can get it

---

### Post by jerome1232 on 2009-02-05
Did you try a reboot? Did it work? Can you try booting from a live cd, then mounting your partitions?

--edit-- please don't bump your post for 24 hours

---edit--- I would mount my paritions see if all the files are still there and etc.., run a fsck on them, install smartmontools while on the live cd and run a self-test on my drives to make sure they are functioning correctly

[https://help.ubuntu.com/community/Smartmontools](https://help.ubuntu.com/community/Smartmontools)
[https://wiki.ubuntu.com/Smartmontools](https://wiki.ubuntu.com/Smartmontools)

---

### Post by canadiandude007 on 2009-02-05
One thing that you can do if you have the Ubuntu CD is boot up the system to that image and it should at least give you some normalcy in which you can check the file system on your current system and feasibly reset any permissions.

---

### Post by waspbr on 2009-02-05
yep, if that were to happen to me, I would get a live cd and run a live session, then I would explore my HDD and transfer any important files  I eed to a USB drive for safety.

I can't really imagine how this happened tho.

---

### Post by albinootje on 2009-02-05
> **fattredd said:**
> i DONT KNOW WHY, BUT I LOST ALL PERMISIONS ON MY SYSTEM. i CANT  EVEN OPEN THE TERMINAL! 

Can you boot from the Ubuntu installation cdrom, use the "try without installing", and post the output of the following :
```

sudo fdisk -l
lspci

```
Thanks.

---

