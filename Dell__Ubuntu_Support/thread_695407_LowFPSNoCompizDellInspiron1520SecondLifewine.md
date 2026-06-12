---
title: "LowFPS/NoCompiz/DellInspiron1520/SecondLife/wine"
date: 2008-02-13
forum: Dell  Ubuntu Support
---

### Post by MrTripi on 2008-02-13
ok, so i think I've encountered a major/error glitch in either second life, wine, or Ubuntu.  This is really pushing me to the edge, as everything was working "PERFECTLY" up until this point.  

I just received a new Inspiron 1520 so I decided to uninstall Vista and throw Ubuntu on there instead seeing as how I'm trying to gain more experience with different operating systems.  Everything was going fine, unfortunately I tend to play this game called Second Life every now and then.  It works fine, there's a linux alpha release, however it's missing certain features so I decided to try and get the windows version working via Wine-and here's where I went wrong.

It installed just fine, however whenever I tried to run the game my screen would literally turn red and some message would pop up.  I can't read the message because the screen is so red so I decide to ctrl+alt+backspace.  I did this three times before giving up.

Immediately upon starting the OS over again I realized compiz wasn't working however I chose to ignore it.  Then I start up the linux version of Second Life and realize the FPS is extremely low-way lower than before.  So I start Nexuiz to see if it has the same problem, it did-so did Diablo2(wine).  

Not knowing what was wrong, I decided to reinstall my drivers using envy again-unfortunately it still didn't work.  I tried sudo dpkg-reconfigure xserver-org, no good.  I use synaptic and reinstalled Wine, I installed the nvidia-glx-new package-absolutely nothing has worked.  

This is really pissing me off at this point because I can't even fathom how a game, which I had to run through an emulator, could have possibly caused so much havok on my system.  It just blows my mind, if anyone has any solid suggestions I'd appreciate it a great deal.  I've had to reinstall this OS numerous times in the past , and frankly I'd rather not be forced into switching back to Vista because I can't figure the damn thing out.  Thanks in advance for any advice.

---

### Post by MrTripi on 2008-02-13
btw, I have a Nvidia Geforce 8400M GS graphic card.

---

### Post by MrTripi on 2008-02-13
right...so still no solutions.  Just deleted all my nvidia drivers, removed envy drivers, restart the computer then installed the open-source-->then restricted drivers again.  Not sure if this bug has anything to do with my problem. 

[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/98641](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/98641)

pretty much out of ideas at this point.  If it really is a bug then performing clean install number 3536362 would just solve the problem  until I decide to update my packages by mistake one day.  I can't believe no one else has had this problem until now.  Tried reinstalling new version of wine knowing it wouldn't work.

Whatever my issue is, I'm assuming it has something to do with my drivers or at least the way they where installed.

---

