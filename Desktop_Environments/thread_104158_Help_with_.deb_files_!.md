---
title: "Help with .deb files !"
date: 2005-12-15
forum: Desktop Environments
---

### Post by nolan- on 2005-12-15
Hi,
I am new to Ubuntu and am trying to get my head round how to handle deb files. I usually use synaptic to install anything I want as it is easily removed. 

The reason I would like more info on deb files is that I have been using Klibido, a binary news reader and synaptic has version 0.2.3 (I had installed) but version 0.2.4 has been out for about 3 months now so I decided to uninstall 0.2.3 (in synaptic) and download the deb file for 0.2.4.

I followed the install from the Klibido homepage and everything went well, the command I used was :

```
sudo dpkg -i klibido_0.2.4.1-1_i386.deb
```

Now then, if I wish to uninstall the package what command would I use?
Do I have to remember the exact package name (numbers etc) for the uninstall command?

Thanks for any info!

NoL

---

### Post by kaamos on 2005-12-15
You can check installed packages by
```
dpkg -l | grep **packagename_or_part_of_it**
```
This gives you a list that matches the criteria. Then look for the one you want and type ```
sudo apt-get remove **package**
```
You can of course also open synaptic and remove the package from there. Just search for the name.

Hope this helps!

---

### Post by nolan- on 2005-12-15
Thats brilliant Kaamos thanks!

I wasn't aware that installing a deb file manually would show in synaptic, guess I should have looked!

This thing just gets better :smile: 

NoL

---

