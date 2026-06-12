---
title: "kvpnc ubuntu 11.04 unable to find on side pane"
date: 2011-04-28
forum: Desktop Environments
---

### Post by topgun446 on 2011-04-28
Hello All,

I was using KVpnc from 10.04 and today I upgraded to 11.04, however I am facing a lot of issues, here are a few

1. The minimized KVpnc disappears after connect, no clue where it goes, the other go to Unity Side Bar.

2. Once connected since I cannot see it, how do I disconnect it? I tried opening it from applications again, this time around it says it cannot resolve my VPN server.

3. I see multiple instances of KVpnc running when I do a ps -ef

Thanks for the help, I'm thinking why I upgraded :(

Regards,
Sam

---

### Post by topgun446 on 2011-04-29
> **topgun446 said:**
> Hello All,

I was using KVpnc from 10.04 and today I upgraded to 11.04, however I am facing a lot of issues, here are a few

1. The minimized KVpnc disappears after connect, no clue where it goes, the other go to Unity Side Bar.


1. First, open KVpnc from applications, it will show in the Unity Launcher(UL), right click on the icon on UL and select "Keep in launcher".
2. Kill all instances of KVpnc from terminal "sudo kill -TERM <pid>" find the pid from ps -ef.
3. Now launch KVpnc from the UL and in Menu got to Settings -> Configure KVpnc -> General -> Uncheck "Do not quit by clicking the close button" ; Connect -> Uncheck "Minimize after connect"

> 
2. Once connected since I cannot see it, how do I disconnect it? I tried opening it from applications again, this time around it says it cannot resolve my VPN server.
The 3rd point is very important, if you do not do this, KVpnc goes into the background and in UL I have not come across any other area which keeps a check on the apps running in the backgroud, like the right hand bottom corner in windows or right hand top corner in Ubuntu uptill 10.04 LTS.


I hope this workaround is fixed by guys from KVpnc and there is some form of noticfication of the applications running in the background.

---

