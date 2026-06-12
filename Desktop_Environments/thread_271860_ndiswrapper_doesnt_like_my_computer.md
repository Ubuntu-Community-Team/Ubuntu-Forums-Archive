---
title: "ndiswrapper doesnt like my computer"
date: 2006-10-05
forum: Desktop Environments
---

### Post by shortflip on 2006-10-05
hey all, im new to ubuntu and very excited about it. I'm having trouble getting my wireless to work on my Compaq V2000 laptop with the IPW2200 wifi card in it. 

I installed ndiswrapper, and I downloaded the latest driver on my friends windows machine, extracted the INF, sent it to my linux box (I'm connected via 10/100), 

but when I use the sudo ndiswrapper -i w22n51 command, it installs but then says I have an invalid driver when I use the ndiswrapper -l command. Any thoughts?

I got the driver link from the ndiswrapper wiki.

---

### Post by pjbgravely on 2006-10-05
The card should be supported in the kernel.

[http://www.thinkwiki.org/wiki/Ipw2200]("http://www.thinkwiki.org/wiki/Ipw2200")

If you have to use ndiswrapper you will have to stop the native driver from loading. I forgot where to blacklist it but can look it up if you need too. Make sure you have NetworkManager installed, for simple WPA configuration. 

Paul

---

