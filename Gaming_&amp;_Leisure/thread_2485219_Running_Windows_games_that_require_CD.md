---
title: "Running Windows games that require CD"
date: 2023-03-23
forum: Gaming &amp; Leisure
---

### Post by truij on 2023-03-23
Hey, I'm moving from Windows to Ubuntu (keeping Windows install), and I am trying to get as much games possible from Windows to Linux, but I'm struggling with Roller Coaster Tycoon 3.
Because it installs just fine, but when starting it up, it gives an error by the anti copy system that it can find the CD. How to fix this?

---

### Post by DuckHook on 2023-03-23
What do you mean by "keeping Windows install?"

There are so many ways.

One way is to run the game in a VM that has Windows installed.

if you have lots of storage and don't mind the inefficiency, then one method that I've used is to copy the CD as an ISO file, then mount the ISO persistently into the VM as a CD disk drive as, for example, Windows drive "Z". 

If you are running RCT3 in Linux with WINE, then the same strategy can be used, but the ISO must be be loop mounted to appear as a CD drive. This one involves further tuning settings.

There are other methods that might involve offending RCT3's EULA so cannot be discussed on these forums.

---

### Post by truij on 2023-03-23
With "keeping Windows" I mean that I dont delete the Windows install.
And I would like to run RCT 3 straight from Ubuntu without virtual machines.

---

### Post by DuckHook on 2023-03-23
Then you have the following options:

[LIST=1]
[*]Run existing copy using WINE. This requires finessing the CD drive using loopback device as per above.
[*]Buy a steam version.
[*]Buy a GOG version that has CD key disabled.
[/LIST]
I use the last technique. Yes, I'm repaying for the games, but the cost is insignificant (especially when on sale) and they run almost seamlessly on WINE.

Anything involving WINE should be checked out on WINEHQ Database first, to make sure that it's workable.

---

