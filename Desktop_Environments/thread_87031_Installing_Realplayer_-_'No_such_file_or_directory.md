---
title: "Installing Realplayer - 'No such file or directory'"
date: 2005-11-07
forum: Desktop Environments
---

### Post by Jaylon on 2005-11-07
Hello.

I've followed the steps to installing real player - downloaded and moved the file to /usr/local

I did sudo su and navigated to that directory root@xxxx:/usr/local then did /.realplayer.bin 

I get the message: realplay10.bin: No such file or directory

Any ideas?

By the way, the filename was something longer and I renamed it. I had the same problem with the old filename.

---

### Post by adwait on 2005-11-07
Try ./realplay

---

### Post by Jaylon on 2005-11-07
Thanks, but that didn't work either.

---

### Post by TristanMike on 2005-11-07
[QUOTE=Jaylon]Hello.

I've followed the steps to installing real player - downloaded and moved the file to /usr/local

I did sudo su and navigated to that directory root@xxxx:/usr/local then did /.realplayer.bin 

I get the message: realplay10.bin: No such file or directory

Any ideas?

By the way, the filename was something longer and I renamed it. I had the same problem with the old filename.[/QUOTE]Hi, out of curiosity, where did you get the instructions to install realplayer?  You should follow the [wiki](https://wiki.ubuntu.com/RestrictedFormats?action=show&redirect=RealPlayer#head-59a79c66f6fef0a9350390de31797a457ed85cd8) and I recommend just downloading it from real.com and don't even bother with the backports/alternate sources.list. The instructions for installation can also be found on real.com. You should not have to save it anywhere specifically, or change the name of the file, and it should install very smoothly.

Hope this helps.

---

### Post by Jaylon on 2005-11-08
Thanks. I found out there was an error in downloading the original file. I've managed to install the version from real.com, but nothing happens when I choose RealPlayer from the application menu. :???:

---

### Post by ubuntu27 on 2005-11-08
I also have simialr... no I mean EXACT problem. But mine didn't have a error downloading the RealPlayer10GOLD.bin

I been folowwing ths instruction from the WIki: [http://help.ubuntu.com/starterguide/C/faqguide-all.html#id2508483](http://help.ubuntu.com/starterguide/C/faqguide-all.html#id2508483)

This is what I get:
```

ghost@heaven:~$ chmod +x RealPlayer10GOLD.bin
ghost@heaven:~$ sudo ./RealPlayer10GOLD.bin
Password:
./RealPlayer10GOLD.bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory
ghost@heaven:~$ sudo ./RealPlayer10GOLD.bin
./RealPlayer10GOLD.bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory
ghost@heaven:~$ 
```

---

