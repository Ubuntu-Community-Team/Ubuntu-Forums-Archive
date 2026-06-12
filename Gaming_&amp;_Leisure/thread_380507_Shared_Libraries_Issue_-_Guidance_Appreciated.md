---
title: "Shared Libraries Issue - Guidance Appreciated"
date: 2007-03-09
forum: Gaming &amp; Leisure
---

### Post by smithbrian86 on 2007-03-09
HI there,

I am trying to install and run Danger from the Deep on my system. I haven't had any problems up until I attempt to load the program in which I get the following message:

> root@brian-desktop:/usr/games# dangerdeep
dangerdeep: error while loading shared libraries: libSDL_net-1.2.so.0: cannot open shared object file: No such file or directory

I loaded the Synaptic Package manager and ran a search for **libSDL_net-1.2.so.0** as well as well several slight varations on the name, and it didn't return any results at all.

I subsequently googled this file **libSDL_net-1.2.so.0** and found it on a Debian Linux page. I downloaded the file, extracted it - and am wondering where on my system I should be placing this file. 

Can anyone give me any help with this?

Thanks in Advance.

---

### Post by RomeReactor on 2007-03-09
Hi. If the libsdl you downloaded is a .DEB file, just double-click on it to install it. Otherwise, look for it in Synaptic as **libsdl-net1.2**; you need Universe repositories enabled in Synaptic. For that, look [here]("http://www.ubuntuforums.org/showpost.php?p=2253469&postcount=4").

---

