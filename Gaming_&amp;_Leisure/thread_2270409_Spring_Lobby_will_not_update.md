---
title: "Spring Lobby will not update"
date: 2015-03-22
forum: Gaming &amp; Leisure
---

### Post by jamesgill2020 on 2015-03-22
hello. as title suggest, my spring lobby will not update to the newest version.

i have the spring ppa:spring/ppa in my update & software, as found here [https://launchpad.net/~spring/+archive/ubuntu/ppa](https://launchpad.net/~spring/+archive/ubuntu/ppa)

as you can see on the web page the ppa includes the newest springlobby 0.210. but im stuck on 0.169.

i followed intructions from spring, followed instructions from the above site. both of which suggest the following terminal inputs.

i've run sudo apt-get update
sudo apt-get upgrade 
sudo apt-get dist-updrade
and tried various other ways to get this to update, but so far im coming up with nothing.

it runs and looks for the update, just doesnt seem find the new springlobby.

i have ubuntu 14.04 if this helps

im pretty new to linux, but im pretty computer savvy. i feel like im missing something simple.

any help is appreciated. thanks

---

### Post by sffvba[e0rt on 2015-03-24
I you look at - [https://launchpad.net/~spring/+archive/ubuntu/ppa/+packages](https://launchpad.net/~spring/+archive/ubuntu/ppa/+packages) - you will notice that the springlobby packages shows that they failed to compile successfully for the maintainer of this PPA... which basically means there is no working version for it to install so it doesn't.

---

