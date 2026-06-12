---
title: "Screen refresh rate bug?"
date: 2007-10-11
forum: Desktop Environments
---

### Post by YannL on 2007-10-11
Hi, 

I passed 3 hours trying to get the correct screen size / resolution editing xorg.conf restarting etc...

I wanted the same as in windows:
[[IMG]http://img208.imageshack.us/img208/1768/g90fud6.th.gif[/IMG]](http://img208.imageshack.us/my.php?image=g90fud6.gif)

I checked several guides [http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973) etc.. but no matter what I did the screen wouldn't go in 1600x1200 @ 75Hz 

Then I found out that there was a bug with installing the 3D driver from Nvidia [http://ubuntuforums.org/showthread.php?p=2507392#post2507392](http://ubuntuforums.org/showthread.php?p=2507392#post2507392)

So I decide to run the sudo nvidia-settings

To my surprise the window looks like something more "ubuntu" with drop down for refresh rate and my 75Hz is listed! so I select it and apply and it works! 

So now I thought I only need to set this for my login page which I read previously can be done in the settings / screen resolution / Make default on this computer. 

Now the screen refresh rate is set @ 134Hz :confused: would I ever be able to restart or will it crash? well thats another story. (it worked)

[[IMG]http://img461.imageshack.us/img461/5661/refreshrateissueww6.th.png[/IMG]](http://img461.imageshack.us/my.php?image=refreshrateissueww6.png)

Fact is guys this isn't "ubuntu" or user friendly at all. Changing the screen resolution / refresh rate should be dead easy and it's anything but easy. I saw the 7.10 as few resolution fix but I somehow doubt this will be fixed.. so if you guys can make this easier for 7.14 that will be greatly appreciated! 

Thank you for reading..

---

### Post by studo77 on 2007-10-11
Agree!

trying to get passed 1024*768@60 last time it ****** up my xgl, now on a reinstall and in search of a better guide...

---

