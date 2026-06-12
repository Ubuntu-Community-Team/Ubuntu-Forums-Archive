---
title: "Need help in setting resolution to 1280x1024 with NVIDIA driver! - Ubuntu 10.10"
date: 2010-12-21
forum: Desktop Environments
---

### Post by Green Moon on 2010-12-21
Yeah so I need help in setting my resolution to 1280x1024. Problem is, that the NVIDIA X Server Settings does not display such a resolution and I want to use that! My monitor is an LCD capable of upto 1280x1024 75HZ resolution. I'm using Ubuntu 10.10.

I did the xrandr command to check what resolutions are available and its output was:

Failed to get size of gamma for output default
Screen 0: minimum 320 x 240, current 1024 x 768, maximum 1024 x 768
default connected 1024x768+0+0 0mm x 0mm
   1024x768       50.0     60.0* 
   800x600        51.0     52.0     53.0  
   680x384        54.0     55.0  
   640x480        56.0  
   512x384        57.0  
   400x300        58.0  
   320x240        59.0  
__________________

In NVIDIA X Server Settings, the list of available resolutions are:
(all of the above)
1152x864
1360x768

_________________

I have NVIDIA GeForce 9500GT. I've been searching online for a fix to this, but all of them are either obsolete or mixed. Any help?

---

### Post by PhantmKllr on 2010-12-21
Download the Nvidia supported graphics card drivers from the Nvidia website:

[http://www.nvidia.com/Download/index.aspx]("http://www.nvidia.com/Download/index.aspx")

---

### Post by Green Moon on 2010-12-21
I have the latest driver. And when I go to NVIDIA's website, they tell me to use the latest package as it is more stable than their driver. Yet, there's no option to switch to 1280x1024 from the current 1024x768 resolution for me. :(

---

### Post by PhantmKllr on 2010-12-21
I would still use the driver from the Nvidia website, if only for the support.

---

### Post by Green Moon on 2010-12-22
Okay, I shall try that... But last time I could not install it due to some error. I shall try again and report back with an output.

---

### Post by PhantmKllr on 2010-12-22
I'll be eagerly awaiting the results. :popcorn:

---

### Post by Green Moon on 2010-12-22
Turns out that the NVIDIA driver I just installled from their website is exactly the same thing as the package... :S So I made no progress there. :(

---

### Post by PhantmKllr on 2010-12-22
> **Green Moon said:**
> Turns out that the NVIDIA driver I just installled from their website is exactly the same thing as the package... :S So I made no progress there. :(

Sorry to hear that. I don't think that I can help you any more, as I don't have much experience with Nvidia graphics cards. Sorry.

---

### Post by Lone_Joker on 2010-12-23
Try adding a modeline to your xorg.conf file. If possible I would use a windows program called Powerstrip to get the modeline for you. I'm not sure if you can install it under WINE.

Try running
```
cvt --reduced 1280 1024 75
```

hopefully it will give you a working modeline. You can just paste the modeline into your xorg.conf file under the Monitor section.

For reference: [http://en.gentoo-wiki.com/wiki/X.Org/Modelines](http://en.gentoo-wiki.com/wiki/X.Org/Modelines)

---

### Post by Green Moon on 2010-12-23
I tried everything it told me to, but it didn't work. :( Thanks for trying to help anyways. :)

---

### Post by Frogs Hair on 2010-12-23
1024 x 1280 is my native resolution , but I'm at 60 Hz. using Nvidia current from the jockey.

---

### Post by Green Moon on 2011-01-09
Haven't posted in a while, but I kinda solved this problem. I bought a DVI-D cable to replace this VGA cable. Somehow, it detected my monitor's name and resolutions. I guess it had trouble identifying what the monitor's capable of which is why I never got that option. This cable gave me the resolution I wanted, so I shall mark this as solved. :)

(P.S DVI is MUCH better than VGA!)

---

