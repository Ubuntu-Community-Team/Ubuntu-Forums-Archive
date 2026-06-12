---
title: "Network, internet, and vmware help needed."
date: 2005-12-22
forum: Desktop Environments
---

### Post by link_36p on 2005-12-22
About my third day ever using linux and most things are working perfectly.

My network cord got unpluged and my interent wasnt working after plugging it back in, i tried alot of stuff to fix it, mainly the connection settings in the kde control panel, It showed that eth0 (my connection) was disabled, so i went to admin mode and right clicked and sennsibly selected (enable device?). It said some stuff and the point is it didnt work. After spennding about thirty mintutes searching through the unix manual kubuntu came with I came across a some "dhclient" function thingy, after running the cammand

sudo dhclient eth0 

everything worked again, but at first it wast enabling at boot but thats fixed now.

Anyways my questions are, is there some tool in linux (or ubuntu) that will automatically try to fix/config a working internet connection, or is that the dhclient. Also what is the command to enable a ethernet device?

Second and my most important question is one time on a machine i installed vmware and net stopped working, ive seen this prob before in this forum but the people said probbing in the setup fixes this, but that is what i did and it still didnt work. Would running the dhclient after installing vmware fix this?? and how can i Revert the changes made by vmware if it doesnt.

---

