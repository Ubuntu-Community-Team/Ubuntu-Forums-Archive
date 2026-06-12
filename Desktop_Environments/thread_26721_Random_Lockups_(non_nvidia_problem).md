---
title: "Random Lockups (non nvidia problem)"
date: 2005-04-13
forum: Desktop Environments
---

### Post by DazeD on 2005-04-13
These random lockups are completely RANDOM and getting more and more frequent. Firts i tried the memtest86+ and it returned no bad memory. I next tried the nvidia driver fix posted on these forums, and returned no change. I had warty about a month and my computer was on 90% of that month without a single lockup. I update to hoary and immediately i start getting these lockups. During the process of trying to make this post i had to reboot 5 times before i could even finish posting this. Sometimes it locks up before it even loads the login screen other times it locks up after 24 hours of being up. Most days i cant get by without having it lockup 2-6 times. It's getting to the point where its incredibly frustrating and id like to hear a fix before i revert back to warty because hoary is great besides this. Someone please help me!

---

### Post by hal8000 on 2005-04-13
I'm new to Ubuntu myself, but I think ou need to break down your problem a little. Do
the reboots only happen running X-windows? Have you tried ctrl-alt-f1 and working at the console only? If this appears stable then you are looking at the configuration of the x window server, graphics driver or similar.

You say this was stable before updating to Hoary. Perhaps you may need to perform a clean install and not an upgrade. Hope someone can give you a better answer.

---

### Post by DazeD on 2005-04-13
i forgot to mention this, but when i ssh in to my computer the ssh client aswell LOCKS UP when my computer locks up. The keyboard and mouse both infact lock up to i cant ctrl alt backspace or anything else. If i did a clean install id lose all my work and stuff on my computer and i cant be having that seeing is how im on dialup and i have maybe 40 gigs worth of stuff.

---

### Post by jsien on 2005-04-13
HI

HAve you tried to disable your Apm or CPU frequency scaling in the BIOS?

---

### Post by DazeD on 2005-04-13
[QUOTE=][/QUOTE]
 I have no idea what that is...id like to give it a try but could i just get a quick explination of what it does and then how to do it?

---

### Post by farnsworth on 2005-04-13
update-rc.d can remove startup daemons.  APM can definitely give problems
ex. "sudo update-rc.d -f apmd remove"

You might want to look at your X logs as well, [ /var/log/Xorg.0.log ] it might contain some useful info.

---

### Post by Dr Gonzo on 2005-04-13
A hard lock is definitely a kernel panic.  Can you attempt to run an old kernel image?  Most likely, you've got one lurking around in /boot.  See if running an old kernel helps, then try re-apt-getting the one you're currently using.  apt-get has a force-reinstall option from the command line.  I'd also redo the restricted-modules package.

Upgrading shouldn't cause this problem, by the way, unless something got corrupted on install.

---

### Post by wanger123 on 2005-05-15
Hi DazeD, I am having similar probs on my new dell9300 laptop. Not quite as frequently as you, but still the laptop locks up hard and a reboot is required every time. Probably happens 2-3 times per day (8hrs). Just wondering how you were getting on?
ps I have the ATI X300 (sigh)

wanger

---

### Post by Vin_L on 2005-05-18
I too have had this problem on my AMD Athelon 1700+ system with Asus AN266-E MB and Nvidia GeForce MX video card. I am totally new to linux and am having fun trying to get things working just right. I have not yet done the nvidia fix and thought that might be my problem but when I saw this post I thought maybe not. Have you tried any of the suggestions given here? Did they work? Also how are you re-booting? I have had to hard boot with the reset button each time this happens and I wonder what kind of damage, if any, this does to the file system.

Hope you can respond

VL

---

### Post by DazeD on 2005-07-25
[QUOTE=][/QUOTE]
 i have learned almost to cope with the lockups as i have tried everything i could nothing seems to work...sometimes the lockups will dissapear for a week and come back and hit me every five minutes but i don't know what to do and just hope the next kernel fixes my problem

---

### Post by zho40 on 2005-07-25
Try keeping a non blank cd in the cdrom drive.  I had the same problem and your choices are keep the cd  in the drive or patch your kernel.  There is a bug causing a race condition w/ ide devices.

---

### Post by astronerd on 2005-07-26
Hi all, I have been having this problem as well and here is what I have discovered / heppened to me.  I used to run FC3 on my box before ubuntu and this would happen with FC3 fairly often.  I have a Dell desktop with the ATI X300 btw.   With FC3 I was running the 2.6.10 kernel and then upgraded to the 2.6.11 one, which is stable for FC3.  After that no more lock ups.  SO then I switched to ubuntu, and since the stock kernel is 2.6.10 I have been getitng lock ups again.  Unfor. the 2.6.11 kernel isnt stable for ubuntu(thats what I have been told and when I tried it they were right) I have tried all the other possiblilites that I could find on the net, but nothing has worked like the kernel upgrade in FC3.  So maybe when the 2.6.11 kernel comes out that will fix this??  Sorry for all the rambling, its just what worked in my experience.  Anyone else have this working or somethign similar?
Charles

---

