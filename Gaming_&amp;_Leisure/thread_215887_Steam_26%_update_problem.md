---
title: "Steam 26% update problem"
date: 2006-07-14
forum: Gaming &amp; Leisure
---

### Post by stratotak on 2006-07-14
Im having the  problems with installing steam.running lates wine and it when it installs and starts to update it gets to 26% but never finishes updating..Been to wine site and all they had to say was to try..killall wine ..killall wineserver   ..killall wine-preloader..wineboot...over and over till it worked..I must have been at it fore 10-15 minutes trying to get it to get past the 26% problem..anyone else run into problem and have away around it??I just want to be able to play Day Of Defeat dont care about the source games..

---

### Post by stratotak on 2006-07-14
OK..got it to install..dont know why it did it this time .I was doing the  same thing before but for some reason this time it installed..i used  after it quit at 26% i entered killall wine-preloader..then from steam directory  entered  wine Steam.exe and it went ahead and installed..now I have a problwm when I try to play game..I got error message  :wrong pixel format"..anyone???

---

### Post by toipot on 2006-07-14
Okies, that 26% is a common problem

Take a look at this:
[http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Steam](http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Steam)


Specifically
Q: Steam crashes at 26% of the update with a "Sharing violation"

Run the following command in the console (substitute the path to steam executables with your path)

    *
      wine C:\Program Files\Steam\SteamTmp.exe SelfUpdate "C:\Program Files\Steam\Steam.exe" 14


Id say that error of yours is due to it not updating properly :)

---

