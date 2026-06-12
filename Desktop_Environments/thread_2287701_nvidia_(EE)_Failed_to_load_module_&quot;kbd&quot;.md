---
title: "nvidia: (EE) Failed to load module &quot;kbd&quot;"
date: 2015-07-21
forum: Desktop Environments
---

### Post by odror on 2015-07-21
Hi

I get the following error in Xorg.0.log

```
  1783.465] (II) LoadModule: "kbd"
[  1783.465] (WW) Warning, couldn't open module kbd
[  1783.465] (II) UnloadModule: "kbd"
[  1783.465] (II) Unloading kbd
[  1783.465] (EE) Failed to load module "kbd" (module does not exist, 0)
[  1783.465] (II) NVIDIA dlloader X Driver  352.21  Tue Jun  9 20:58:55 PDT 2015

```

I am probably missing the nvidia kbd module. Does anyone knows which nvidia package is missing. It is also possible that the location is incorrect. Although the other modules were loaded correctly.

(this is a non-standard installation of nvidia inside a container)

---

### Post by papibe on 2015-07-21
Hi odror.

'kbd' (short for keyboard) is an Xorg keyboard module, not a Nvidia module. If your keyboard is working, I wouldn't worry about it since there are other modern input modules for keyboards.

My guess is Xorg is going through the automatic process of hardware detection. You may avoid unnecessary probing by creating a custom /etc/xorg.conf. What I personally do, is let the nvidia driver generate one for me:
```
sudo nvidia-xconfig
``` 
Hope it helps. Let us know how it goes.
Regards.

---

### Post by odror on 2015-07-21
problem fixed

I had to install xserver-xorg-input-kbd

---

