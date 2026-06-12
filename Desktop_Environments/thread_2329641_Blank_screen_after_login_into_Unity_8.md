---
title: "Blank screen after login into Unity 8"
date: 2016-07-04
forum: Desktop Environments
---

### Post by TBK on 2016-07-04
I'm using Ubuntu 16.04 64 bit. 
I installed Unity 8 using this command:
```
sudo apt install unity8-desktop-session-mir
```
And then I added the stable phone overlay PPA:
```
sudo add-apt-repository ppa:ci-train-ppa-service/stable-phone-overlay
sudo apt update && sudo apt upgrade

```
Reboot . . .
After reboot, I choosed my user name and Unity 8, entered my password and pressed enter then I saw a black blank screen, I tried to wait a few minutes but not thing appear.

Help me, I want to try Unity 8 soon!

CPU: Pentium(R) Dual-Core CPU E6500 @ 2.93GHz × 2 
Graphic: Intel® G41

---

### Post by grahammechanical on 2016-07-04
If I knew the answer I would right now be running the Unity 8 session. I have had this problem for a year or more. I have been informed that adding the phone-overlay PPA is not necessary and will in fact cause the Unity 8 session to crash and burn at some point. And I have had that happen. 

Right now on my 16.10 development installation I get to the desktop but without any app indicators and a Scopes scope that has a black background  and a mouse stuck in the centre of the screen. The desktop has frozen before Unity 8 completed loading. It is GPU lock up.

This is on Nvidia graphics using an open source video drive. As far as I know the best result come with an Intel video adapter. There are a couple of threads about the success and failure of Unity 8 in the Ubuntu Development Section of this forum.

[http://ubuntuforums.org/showthread.php?t=2323279](http://ubuntuforums.org/showthread.php?t=2323279)

[http://ubuntuforums.org/showthread.php?t=2327168](http://ubuntuforums.org/showthread.php?t=2327168)

[http://ubuntuforums.org/showthread.php?t=2327883](http://ubuntuforums.org/showthread.php?t=2327883)

I think that the only solution is to update from time to time and see if things have improved. I do not know of anything else we can do and I have been testing Unity 8 session since 14.04 was released.

Regards.

---

