---
title: "newbie problem"
date: 2012-12-27
forum: Dell Ubuntu Support (CLOSED)
---

### Post by cry5t4l on 2012-12-27
Hi guys, I've just install Ubuntu 12.12 on my Dell XPS 15z , and I have few problems. First I have installed nvidia card. I hope is it correct. But now I stuck on reader 9 in 1. I've found some info about 9in1 but anyone was for Dell 15z. Is any one can help me. I have also problem with webcam. I think when I've install new drivers nvidia bumbleblee I had for short moment webcam, but now it is gone :(  

Can I use all methods from that site : 
[https://wiki.ubuntu.com/HardwareSupport/Machines/Laptops/Dell/XPS/15z#Introduction](https://wiki.ubuntu.com/HardwareSupport/Machines/Laptops/Dell/XPS/15z#Introduction)

I'm asking because I've got ubuntu 12.10 64bits 

Can I bring my Dell to life ??

---

### Post by cry5t4l on 2012-12-28
HI guys I've found solution. Actually my friend help me with this. 
After I put that command in terminal:
 **id** 
I've had that message: 
[B]uid=1000(karol) gid=1000(karol) groups=1000(karol),4(adm),24(cdrom),27(sudo),30(dip),46(plugdev),107(lpadmin),124(sambashare),1001(bumblebee)

[/B]what means - I'm not in the video group, 

after I've edit /etc/group and add/update that line -[B] [COLOR=Red]video:x:44:karol[/COLOR]

[/B]result was[B] 
uid=1000(karol) gid=1000(karol) groups=1000(karol),4(adm),24(cdrom),27(sudo),30(dip),[COLOR=Red]44(video)[/COLOR],46(plugdev),107(lpadmin),124(sambashare),1001(bumblebee)

[/B]and after restart my webcamera is working[B] :)

[/B]Tnx Arthur (my friend) . I hope maybe this info will be helpful for someone with that kind of problem.

---

