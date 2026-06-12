---
title: "Cant Boot After Install?"
date: 2006-08-05
forum: Desktop Environments
---

### Post by khughes on 2006-08-05
I have 3 laptops and a server that I have installed ubuntu (dapper) on and all of them work perfectly. I never had any problems. But I have this older Compaq desktop that I have been trying to install dapper on and every time the install finishes and the computer reboots, I get a screen saying:

DISK BOOT FAILURE, INSERT SYSTEM DISK AND PRESS ENTER.

I have tried reinstalling about 5 different times, some from the live cd and some from the alternate install cd. Either way I still come up with the same result. I dont know what could be causing this. If anyone has any suggestions let me know. Thanks.

---

### Post by ozorba on 2006-08-05
Can it be that your bios setting is incorrect? Check your boot device in BIOS settings. If the HDD is not in your boot device list you will get this problem.

---

### Post by khughes on 2006-08-05
No, I just changed my bios to boot directly to the harddrive only to see and I get the same error message.

---

### Post by joople on 2006-08-06
I have this exact same problem.  it is driving me nuts.  I too have installed several times in all sorts of ways.

I have 2 hdd, Master (Linux), Slave (Winxp). I get the same error message "DISK BOOT FAILURE, INSERT SYSTEM DISK AND PRESS ENTERThen if a change the boot order in BIOS I can obviously boot into Windows though.

When I had Master (Winxp) and Slave (Linux), After install and reboot I got grub to show up, but it would give me a please wait... and give me an "Error 25".  What in the world is going on?  When I go into Terminal on live cd And can see linux is thier with the "sudo fdisk -lu" command.  I even re-installed Grub a couple times in the terminal. PLEASE HELP.

---

### Post by khughes on 2006-08-06
> **joople said:**
> I have this exact same problem.  it is driving me nuts.  I too have installed several times in all sorts of ways.

I have 2 hdd, Master (Linux), Slave (Winxp). I get the same error message "DISK BOOT FAILURE, INSERT SYSTEM DISK AND PRESS ENTERThen if a change the boot order in BIOS I can obviously boot into Windows though.

Well, I fixed my problem last night and the solution was very weird but you may want to try it. What I did was got inside my pc and changed the jumper settings on the back of my hard drive to CS instead of Master. After that it booted right up. You may want to try changing both drives to CS and seeing if that works. I got some info after googling the error message which hinted me to try it so obviously I am not the only one who has experienced this specific issue. Let me know if it works.

---

### Post by joople on 2006-08-07
Thanks a lot for the post, but unfortunatly this did not resolve my problem ](*,) ; hopefully somebody has answers.  I also googled but can't find anything specific to my problem it sucks cause i've ruined the whole weekend.  well I shouldn't say that I've learned a lot in te process. so not all is lost.  Again Thanks.

---

