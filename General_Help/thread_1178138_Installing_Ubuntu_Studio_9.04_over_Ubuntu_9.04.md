---
title: "Installing Ubuntu Studio 9.04 over Ubuntu 9.04?"
date: 2009-06-04
forum: General Help
---

### Post by Nixie Pixel on 2009-06-04
Hello! I have Ubuntu 9.04 installed on my desktop and I would like to try the various multimedia production tools included in Ubuntu Studio (especially the video editing tools). My current installation is separated into /, /home, and swap partitions.

If I install and format /, can I keep /home intact? If so, will I have any compatibility issues?

Or is it better to just back up my data, wipe the drive, and install from scratch?

Thanks!

---

### Post by nikhilk on 2009-06-04
I have done that (re-installing without formatting home partition) without any disastrous results before. As always keep a backup of all your data in /home partition. I keep backup of other stuff as well like "/etc/fstab", "/etc/X11/xorg.conf" etc and also other things that I have customized.

---

### Post by Nixie Pixel on 2009-06-04
I've done the installation of Jaunty on top of Intrepid, and it seemed to work well. My question here is if I put Ubuntu Studio 9.04 on top of a Jaunty installation, and keep /home intact, if I will have the same results?

Thanks again!

---

### Post by pastalavista on 2009-06-04
That is exactly the best way to do it. Just make sure you don't reformat /home... you will have to redownload/install whatever programs you are using now that don't come packaged with Ubuntu Studio.

---

### Post by nikhilk on 2009-06-04
Sorry for digressing a bit from your question but won't installing the required apps in your plain 9.04 be sufficient for you? You can add the Studio repo in your current installation and get those apps. Or you want the customized kernel as well? You can install the low latency kernel as well if you want later so you can just more or less convert your plain Ubuntu installation into a Studio one without an explicit re-install. How does that sound?

---

### Post by fdestat on 2009-06-04
No need to install over.
You can add ubuntu studio packages (even RT kernel) on your standard Ubuntu 9.04 installation.

I did it. 
If I remember well, I only had to add Ubuntu studio repository to my source list and then seach through synaptic for ubuntu studio packages I needed (audio/video/photo).

---

### Post by fdestat on 2009-06-04
This should be also applicable to Jaunty:
[https://help.ubuntu.com/community/UbuntuStudio/UpgradingFromHardy](https://help.ubuntu.com/community/UbuntuStudio/UpgradingFromHardy)

So, no need to modify the source list, just add the required packages.

---

### Post by egalvan on 2009-06-04
I just installed Jaunty, and the only extra repos I enabled were the standard ones on the repo list screen,
and of course I did the medibuntu install 

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)


I can see ubuntu-studio in Synaptic...

---

