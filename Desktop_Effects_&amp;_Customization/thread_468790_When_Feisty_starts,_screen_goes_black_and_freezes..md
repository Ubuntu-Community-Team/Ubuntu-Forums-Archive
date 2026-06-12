---
title: "When Feisty starts, screen goes black and freezes. Beryl &amp; xorg problem!"
date: 2007-06-09
forum: Desktop Effects &amp; Customization
---

### Post by Enginirical on 2007-06-09
Hi

After days of just trying to get feisty and beryl installed, I finally got to a point where Beryl was installed along with xgl session by following this: [https://help.ubuntu.com/community/Beryl/ATI/Feisty?highlight=%28beryl%29%7C%28ati%29](https://help.ubuntu.com/community/Beryl/ATI/Feisty?highlight=%28beryl%29%7C%28ati%29)

When selecting xgl session and starting beryl, I got the cube with white faces and beryl ruby cap. It rotated but did nothing else. I followed advice to change color depth to 16 in xorg.conf and now when switching on my machine, ubuntu loads as usual but instead of the login in page I get a black screen which i can't get out of:( (ctrl+Alt+F doesnt work)

How can I change color depth back to 24 through terminal? I didn't make a back up of xorg.conf as I thought if beryl didn't work I could just change it back. Didn't expect it to screw up this much. 

I really really don't want to install again for the thousandth time in 4 days ;( 

Can any one help?

I installed my ATI driver using ENVY, please don't suggest me to revert to xorg driver (sudo dpkg-reconfigure xserer.xorg) as this just hasnt worked on my machine (Asus with ATI MR X1450) and I have tried this countless times since using ubuntu. Im so close to giving up on ubuntu now:(

---

### Post by OzzyFrank on 2007-06-09
Ooops! I didn't see the last bit, and was going to suggest to reconfigure the xserver with:

sudo dpkg-reconfigure xserver-xorg

It's not the answer you were after, but it is a very handy command for being able to get your display settings back within a couple of minutes. I've had troubles with Beryl and trying to use more advanced drivers for my ATI Radeon, and in the end I just reconfigured xorg and have been using a functioning display with the ability to change resolution no problems. Figured it was better to have a fully working system I could see than spend too much time on eye candy that really shouldn't be the focus of my computing. Now if I could get one of those windows managers working again, hehe...

Cheers

---

