---
title: "cannot log onto wireless network on xubutnu"
date: 2007-05-28
forum: Desktop Environments
---

### Post by soundsystem00 on 2007-05-28
a menu seems to be missing.&#12288;i need to find a networking option where you can find the wireless network closest to you. the xubuntu does not have admin options on drop down menu. network settings is the only option but there is suppose to be another network optino than that. please help me get online so i can hit up beryl.&#12288;thanks

---

### Post by HW_Hack on 2007-05-28
I'm still learning the finer points of Ubuntu/Linux - But --- go to   Add/Remove  menu ----- next to Show select   Ubuntu Supported applications  ----- in the search box   enter - wireless  

Your search should net you  KNetworkManager ---- this should be the front-end GUI for getting wireless working 

good luck

---

### Post by soundsystem00 on 2007-05-29
the only problem with that is that adding programs requires me to be online.

---

### Post by soundsystem00 on 2007-05-29
I get to the network menu and it has two options. Wired network (lan cable input) or Dial up.. There is no wireless options. I'm guessing that xubuntu cant find my network card even though ubuntu can. God knows where i'll find those drivers!

---

### Post by meborc on 2007-05-30
if you type "ifconfig" in the terminal, what is the output?

there should be a section starting with wlan0 (or similar) if your wireless card is dedected and running

otherwise search these forums and [http://wiki.ubuntu.com](http://wiki.ubuntu.com) for your wifi card make and model

---

