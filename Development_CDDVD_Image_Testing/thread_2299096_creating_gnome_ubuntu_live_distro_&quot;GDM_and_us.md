---
title: "creating gnome ubuntu live distro: &quot;GDM and user authentication failure&quot;"
date: 2015-10-15
forum: Development CD/DVD Image Testing
---

### Post by danjde on 2015-10-15
Hi friends, 
I'm building a custom live Ubuntu Gnome 3.12.2 based, 
**Only** if I create a new user, set password and add him to sudo group, 

setting by dpkg-reconfigure, GDM ad default greeter, obtain a black  screen and going to the first console appear  "authentication failure"  message. 

otherwise, 
using dpkg-reconfigure and select the Lightdm as default greeter all  work fine: the greeter show the login screen and the user is able to  authenticate. 

Instead 
if I do not use any user, and set GDM ad default greeter, all work fine,  but no login screen appear and the user goes directly to its desktop. 


For build the iso I'm using the Ubuntu directive:  [https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization) 

Could you help me find a solution to this problem? 


many thanks!

---

