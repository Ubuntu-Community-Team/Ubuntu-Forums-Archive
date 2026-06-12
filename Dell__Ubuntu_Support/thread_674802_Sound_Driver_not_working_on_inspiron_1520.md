---
title: "Sound Driver not working on inspiron 1520"
date: 2008-01-22
forum: Dell  Ubuntu Support
---

### Post by samarjeetsaigal on 2008-01-22
Hi friends,

My System Configuration is
Dell Inspiron 1520
Processor: Core 2 Duo T7250 @2.0 Ghz
Ram: 2 Gigs
Hard Disk: 160 GB SATA
Wirless Adapter: Intel

Now the problem is that my system came pre-installed with Vista Home Premium and i had installed a dual boot of Vista and Ubuntu 7.10 Gutsy. Eveerything is working on Ubuntu but i am not able to update my ubuntu like several codecs and video drivers. 

Even net is also working on my lappy on ubuntu. Can anyone tell me the solution.
Thank You

Regards,
Samarjeet Singh Saigal

---

### Post by Thanoulis on 2008-01-22
What kind of drivers/codecs? What version of Ubuntu 7.10 do you have installed (32bit/64bit)?
Also your post-header says that your sound does not work...

---

### Post by linux23dragon on 2008-01-22
Hi samarjeetsaigal

Open up a terminal and copy paste this following command line (to install the correct sound card drivers).  If you have a Intel HDA sound card.

```
sudo apt-get install linux-backports-modules-generic
```

Then complete the Audio installation using [***[COLOR="Blue"]this post[/COLOR]***]("http://ubuntuforums.org/showthread.php?t=530374&page=9&postcount=#84").


Use [***[COLOR="Blue"]Envy[/COLOR]***]("http://albertomilone.com/nvidia_scripts1.html") to update the graphics drivers.  Thats if you have an Nvidia or ATI card.

There is two Intel drivers you can use for your WiFi card (you are using one now).  Use this [***[COLOR="Blue"]thread[/COLOR]*** ]("http://ubuntuforums.org/showthread.php?t=501195&page=50&showpost=#499")for more information on using the second driver (if needed).

Use the [[COLOR="Blue"]***ubuntuguide***[/COLOR]]("http://ubuntuguide.org/wiki/Ubuntu:Gutsy") to setup anything you need (DVD playback ...).

Don't forget to search for "Dell 1520" in the ubuntu forums if you need more information about your Notebook setup.  And we do need your hardware specs by the way :)

---

