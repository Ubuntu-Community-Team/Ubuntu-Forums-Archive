---
title: "Kubuntu Login falls back to login screen"
date: 2007-03-11
forum: Desktop Environments
---

### Post by anabelle on 2007-03-11
Hi, im having a very annoying problem at the login screen of my kubuntu 6.10.

When i type my username and password it goes to a black screen and then back to the login.

so i switched to console (ctrl+alt+f2) and tried to login there, it worked fine.

I decided to do a "apt-get update" to try to fix any problems since last time i was running adept it returned some errors. But it returned LOTS of errors, about some duplicated entries i think, it told me maybe i shoud try "apt-get update" to fix those errors, i did, and got the same errors back again.

I rebooted my pc, this time in recovery mode, i logged on and typed " sudo startx" 
the login screen appeared, but this time when i tried to login it began loading normally but got stuck at loading desktop and then just a blue screen, all i cand o is move my mouse around.

I tried logging in as different user with no luck. 

What may be happening, im back in windows now but i don't like it anymore :( i want my kubuntu back!

please help me.

---

### Post by anabelle on 2007-03-11
Ok, i got it working now, it was a rally dumb problem.

My harddisk got full.... and that is what happens when you have a full disk in kubuntu (weird, it should just say the disk is full and stop scaring noobs)

i found out booting in recovery mode and writing

```
df -h
```

it said disk 100% used

then i did

```
sudo aptitude clean
```

and it left me some free space, enough to login. Now im cleaning up a little and will never leave ktorrent downloading big files over the weekend LOL

:lolflag:

---

