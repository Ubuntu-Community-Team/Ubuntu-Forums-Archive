---
title: "Xserver Freezes When RAM Ussage Is Over 1GB"
date: 2008-06-06
forum: Desktop Environments
---

### Post by Brando569 on 2008-06-06
I never experienced this problem before because my ram usage was never really over about 5-600mb. I recently found a superkaramba system monitor theme that I really like and it has about 10 widgets I use, along with logwatch and liquid weather. when I open up a few pages in firefox to get me above 1gb the xserver/kde/compiz becomes really slow and will eventually freeze and Ill have to do a hard reboot.

at first i thought it was compiz, but it wasnt, then i thought it was the new nvidia driver i installed so i had xconfig create a basic config file but the freezes still happened. so that limits it down to either kde or the xserver. im using kde 3.5.9 and xserver 7.3 from the repositiories. compiz-fusion has also been a little laggy compared to when i was using it in mint 4.0

edit: I dont think has to do with memory usage since it froze when it was around ~750mb, and its not a kde problem since ive read on here that gnome users are having the same problem

---

### Post by kcnnc on 2008-07-17
Had similar problem/symptom with Gnome too.

1G RAM, AMD64, nVidia GeForce 6200

---

### Post by stitchmysmile93 on 2008-07-17
This is kind of funny I had the same problem tonight I think it was because I was running a game and when I closed it it wasn't shut down completely. So I restarted and installed the compiz fusion icon it lets me change between compiz and metacity.

If you don't care to have the icon then you can just run metacity --replace . Then Biggest reason I don't keep compiz running is because it's on my laptop and I noticed that when I'm running that or a game or a game with compiz in the background it gets really hot.. So Know I have the icon and I have it set to metacity. I still have compiz it's still fun to use to show off with lol that's about it...

---

### Post by Brando569 on 2008-07-17
i believe it was actually a kernel issue, after reading around for awhile i found out that a lot of people were having similar problems but they werent related to x, so i compiled a new kernel and havent had a problem since. ubuntu fixed this problem in 8.04.1.

also i found out that my massive amount of ram usage was from stuff being cached and not really in use by programs.

---

