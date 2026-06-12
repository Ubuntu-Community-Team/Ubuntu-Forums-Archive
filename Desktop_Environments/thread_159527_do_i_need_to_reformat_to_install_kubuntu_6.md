---
title: "do i need to reformat to install kubuntu 6?"
date: 2006-04-13
forum: Desktop Environments
---

### Post by zeltak on 2006-04-13
Hi All

I have a stupid Q. I want to upgrade soon to the new kubuntu 6. i have 5.1 now. I noticed that i need to dl a kubuntu CD for that. do i reformat, install over   it in boot mode or from within kde? how do you upgrade your distro (its the first time for me :) ).

thx alot

Zeltak

---

### Post by gnu2tux on 2006-04-13
You don't need to download kubuntu --

all you need to do is edit /etc/apt/sources.list (eg: gksu gedit /etc/apt/sources.list)

change all occurrances in there of the word breezy to dapper

then do sudo apt-get update && apt-get upgrade && apt-get dist-upgrade

finally, once you've upgraded to dapper (6.06), install kubuntu:

sudo apt-get install kubuntu-desktop

Done!

---

### Post by RS3York on 2006-04-14
A couple things to note though.

First, if you're using the PLF repositories...They don't have any Dapper repos yet.  So you shouldn't change that over from Breezy to Dapper.

Second, while you technically should never have to format and reinstall a Debian (and therefore K/Ubuntu) system sometimes it's a good idea to do so.  I know that my Breezy system ran much better when I did a pure install than when I upgraded it from Hoary.  Of course this is just an individual experience and presumably the transition gets smoother with each release...so, YMMV.

---

