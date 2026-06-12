---
title: "Desktop Cube, flat windows!"
date: 2010-05-18
forum: Desktop Environments
---

### Post by ginjaninja405 on 2010-05-18
The windows on my Desktop Cube aren't raised, and in the CompizConfig Settings Manager, I can't find any settings that change it or activate it. When I last had Ubuntu installed, I use to be able to... could anybody help me? 

It seems I don't have all of the Compiz Settings actually, I'm missing some and I wonder where I've gone wrong? Some of the old animations aren't there that I use to use.

Thanks,

Sam

---

### Post by howefield on 2010-05-18
I think you might need to install compiz-fusion-plugins-extra to get the plugin which will give you 3D windows on the cube.

System > Administration > Synaptic Package Manager.

---

### Post by moongia on 2010-05-18
> **ginjaninja405 said:**
> The windows on my Desktop Cube aren't raised, and in the CompizConfig Settings Manager, I can't find any settings that change it or activate it. When I last had Ubuntu installed, I use to be able to... could anybody help me? 

It seems I don't have all of the Compiz Settings actually, I'm missing some and I wonder where I've gone wrong? Some of the old animations aren't there that I use to use.

Thanks,

Sam

go into your synaptic,type compiz,and look for compiz-fusion-plugins-extra.install it and then go into your compizconfig settings manager.and you should see 3d windows..

---

### Post by dv3500ea on 2010-05-18
Make sure [compizconfig-settings-manager]("apt:compizconfig-settings-manager") is installed.
Go to System -> Preferences -> CompizConfig Settings Manager
Under Effects, enable 3D Windows.
You may need to install:
[compiz-fusion-plugins-extra]("apt:compiz-fusion-plugins-extra")
[compiz-fusion-plugins-main]("apt:compiz-fusion-plugins-main")
[compiz-plugins]("apt:compiz-plugins")

---

### Post by ginjaninja405 on 2010-05-18
thank you all! It was successful!

---

