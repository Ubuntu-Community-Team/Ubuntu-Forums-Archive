---
title: "help a ubuntu newbie please. its about the launcher and workspaces"
date: 2011-07-19
forum: Desktop Environments
---

### Post by dynomite1988 on 2011-07-19
I just updated to ubuntu 11.04. I saw on the website it should have a launcher and workspaces included with it. However I cannot get either of those to appear. is there something I am supposed to download or do something with the settings to get it to appear? I would like to use the feature. 
Thanks in advance for your help

---

### Post by trollolo on 2011-07-19
the default desktop environment for ubuntu 11.04 and foward is Unity, which looks like so: [http://www.neowin.net/images/uploaded/Ubuntu_10.10_Maverick_Meerkat_Netbook_Live_USB.png](http://www.neowin.net/images/uploaded/Ubuntu_10.10_Maverick_Meerkat_Netbook_Live_USB.png)
 
If you aren't seeing that, then either when you logged in, you're selecting ubuntu classic (which is Gnome 2.X), or you've gotten rid of it through Synaptic Package manager.

---

### Post by coffeecat on 2011-07-20
> **trollolo said:**
> 
If you aren't seeing that, then either when you logged in, you're selecting ubuntu classic (which is Gnome 2.X), or you've gotten rid of it through Synaptic Package manager.

@dynomite1988, or the most common reason for seeing the classic gnome desktop instead of the Unity desktop (the one with the launcher) in 11.04 is a graphics/driver combination that doesn't support the 3d acceleration needed for Unity. Most (but not all) Intel and ATI graphics chipsets will give you Unity out of the box with their respective open source video drivers. Nvidia cards will not and will need the proprietary driver installed. What video card do you have? If you are not sure, open a terminal (Applications -> Accessories) and post the output of:

```
lspci | grep VGA
```

---

