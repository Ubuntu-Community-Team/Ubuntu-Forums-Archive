---
title: "Unity sidebar disappeared after a 194MB update on 11.04"
date: 2011-07-30
forum: Desktop Environments
---

### Post by LukasHCFC on 2011-07-30
(solved)

Hi,

After installing Ubuntu 11.04 again, I have downloaded an update (194 MB). However, when I restarted my computer, instead of the Unity sidebar showing up, it loaded up the panels at the top and the bottom. I have made sure that in the login screen I selected 'Ubuntu' instead of 'Ubuntu Classic', but it still shows the Classic panels. This has happened in the past whenever I installed 11.04 and downloaded the updates.

Is there anything I can do to get it back? Please bear in mind I am not very familiar with Linux yet.

Thanks

---

### Post by coffeecat on 2011-07-30
It does sound as though you are getting the classic desktop instead of Unity. If you were getting Unity before, then this points towards a video driver issue. Had you installed a proprietary video driver through the "Additional Drivers" utility (Jockey), this would have been updated automatically in the event of a kernel update. However, if you install a proprietary video driver downloaded from the manufacturer's website (nvidia or ATI) and install this manually, this has to be re-installed after every kernel update. So - my guess is that you installed a proprietary video driver and installed it manually and that the 194MB update included a kernel update.

Questions:

What video card do you have?
Did you install a proprietary driver?
If yes to the previous question, did you install this using Additional Drivers or using a downloaded driver?

---

### Post by LukasHCFC on 2011-07-30
Thanks for the response

My video card is 'Nvidia GeForce 7200 GS / 7300 SE', which is pretty old.

I installed the proprietary driver using the 'Additional Drivers' application. At first I tried installing the recommended current version driver, but after installing it and restarting the computer, it would freeze as soon as Ubuntu loaded up. Unity did show up, but everything was completely frozen. Then I used safe mode and changed it to the 'version 173' driver, and Unity worked fine after restarting.

I tried opening the Additional Drivers application now, and under the version 173 driver it says 'Driver is activated but not currently in use'. Also, before the update, there was an experimental 3D driver on the list, but it's not there anymore.

---

### Post by coffeecat on 2011-07-30
I have read that some of the 7*** series can be problematic in Unity, but I can't remember the details.

OK - a few thoughts. First, the 'Driver is activated but not currently in use' message is a bug and you can ignore it. Everyone with a nvidia card is seeing this. In theory the nvidia-current driver should support your card (it says "GPUs such as GeForce series 6 or newer are supported." in the package description), but if it froze your system then I agree that you needed to try the 173.

I'm not quite clear - you say:

> Then I used safe mode and changed it to the 'version 173' driver, and Unity worked fine after restarting.

Is Unity working now with the 173 driver installed? If so, ignore the activated and not in use message. If not, here's how to retrieve the experimental package:

Open Synaptic and install the package libgl1-mesa-dri-experimental. That is the experimental 3d driver that Jockey offers at first and then tantalisingly removes from view for reasons that are obscure. Or rather, it is an experimental package that complements the open source nouveau driver to give it 3d capabilities. Once you have the experimental package installed, use Additional Drivers to disable the proprietary driver and then reboot. Hopefully, you should get Unity with the open source nouveau driver.

---

### Post by LukasHCFC on 2011-07-30
When I changed it to the 173 version, it was working fine, but that was before the update, and after the update everything looks the same as Ubuntu Classic.

I've opened Synaptic, searched for the experimental driver, and it says that it's already installed. I'm going to disable the current driver and reboot the machine now

EDIT: Removed the current driver and restarted. Now, when I open Additional Drivers, it says that the experimental 3D driver is activated. It still loads up Ubuntu Classic. Before the update, the experimental driver loaded up Unity, but it wasn't as smooth as version 173

---

### Post by coffeecat on 2011-07-30
I'm sorry to hear that. It sounds as if the update has affected both the 173 proprietary driver and the experimental driver - at least as far as your GeForce 7200GS card running Unity is concerned.

I found this thread:

[http://ubuntuforums.org/showthread.php?t=1779482](http://ubuntuforums.org/showthread.php?t=1779482)

It seems to describe your problem, even though it was over a month ago. Anyway, there's some sort of workaround described in the last post. It sounds an ugly hack to me, but if it works so be it.

If you want to add that line to /etc/environment, you need to open a text editor with root privileges, thus:

```
gksudo gedit /etc/environment
```

Make the edit, save and I guess you may need to reboot.

Good luck with that!

---

### Post by LukasHCFC on 2011-07-30
EDIT: It works, thanks for all the help!

---

