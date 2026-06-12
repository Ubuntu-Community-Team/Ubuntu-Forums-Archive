---
title: "How to package the installed software?"
date: 2009-06-03
forum: General Help
---

### Post by feistybee on 2009-06-03
Dear fellas,

I have installed jaunty. And installed following packages,
[LIST]
[*]VLC
[*]XMMS
[*]Audacious
[*]Acrobat Reader
[*]Wine
[/LIST]

Now using Dust theme and my ubuntu desktop is awesome. My question is everytime I install ubuntu I need to install these packages again. Is there anyway I can package the installed VLC, extra softwares in to .deb files. So later I can install those.

Everytime I install these thru apt-get it takes considerable time, and I am having less bandwidth internet connection.

Please help me.

---

### Post by mcduck on 2009-06-03
No, you can't. At least not in any easy way.

But when you installed them, the package manager stored the .deb packages it downloaded to /var/cache/apt/archives. You can simply grab the packages from there, and when you do a new install either put them into same place so that the package manager doesn't ahve to downlaod them again, or install the .deb packages directly.

---

### Post by Soul-Sing on 2009-06-03
* VLC
    * XMMS
    * Audacious
    * Acrobat Reader
    * Wine

You can copy the ./home preferences. Thats easy.
to install the (often new releases/versions!)software above will take
40 sec?

---

### Post by feistybee on 2009-06-03
Not only these packages. I want to install further softwares also. I have installed flash plugins, codecs etc etc.

My Vista is giving problem with wireless drivers. So I want to remove Vista and install jaunty again. I want to change the partitions.

So next time, I want to install the packages which I installed thru apt-get.

I will try the /var/cache/apt/archives and let u know. Thx

---

### Post by regala on 2009-06-03
> **feistybee said:**
> Not only these packages. I want to install further softwares also. I have installed flash plugins, codecs etc etc.

My Vista is giving problem with wireless drivers. So I want to remove Vista and install jaunty again. I want to change the partitions.

So next time, I want to install the packages which I installed thru apt-get.

I will try the /var/cache/apt/archives and let u know. Thx

in case of misunderstanding, understand that putting the .deb files in /var/cache/apt/archives, will not install them automatically. You still will have to manually install them with apt{-get,itude} or synaptic.

br, mathieu

---

### Post by edm1 on 2009-06-03
Check out [APTonCD]("http://aptoncd.sourceforge.net/").

---

### Post by Entropy_Sam on 2009-06-03
Another alternative would be simply to boot from a Live CD/USB, archive your entire desktop once you have your "Perfect Install" set up, burn the archive to a CD and simply extract that from a Live CD/USB next time you reinstall. If you install it to a machine with different hard drives and/or partitions, there might be some necessary tweaks to /etc/fstab and /boot/grub/menu.lst to get this running, but it should work like that.

---

### Post by feistybee on 2009-06-03
thanks a lot. Aptoncd seems good option. /var/cache/apt/archives is also a good option. I shall try and let u know.

---

