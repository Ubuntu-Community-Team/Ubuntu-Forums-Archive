---
title: "Install and run Ubuntu from USB"
date: 2009-04-04
forum: General Help
---

### Post by xtracool_protik on 2009-04-04
Hi guys,
 I'm interested using my old hardware (pretty old) 128MB RAM and make it into a server which will be accessed via LAN/Network through ssh. So the question is - I don't have any HDD, hence would like to use 2GB pen drive as my primary HDD. I know methods to make USB pen drive bootable and all however wat should I do in this case as I probably won't have monitor attached to system and RAM is pretty low as well. Thus I want completely text based installation and running as well - NO GUI.
 Can anyone help. If there is something similar around please redirect me 
 And ya for installation I can use another computer thats not the problem the problem is how should I install?

---

### Post by dmizer on 2009-04-05
What kind of server do you want?

Just for future information, the tutorials and tips section is for posting howto's, not requesting them.

---

### Post by xtracool_protik on 2009-04-05
Ohh really sorry but I was confused about where to post it.
 Anyway its an old computer and I just want to put my web pages there as I've a laptop and can't keep it at apartment all the time so calling old computer as server and I don't need a processing power or storage at all, hence even an old one is okay. However it doesn't have hard disk so trying to fix it with USB key.
 And thanks a lot for response, if possible please move it to proper section.

---

### Post by dmizer on 2009-04-05
The biggest problem I see with doing what you want to do is that running from a USB key will be memory intensive because (just as with a live cd) most of the OS is loaded into RAM. So, even if your website doesn't use a lot of CPU, it will use and need RAM. That said, actually doing what you want to do shouldn't be difficult

Something else to consider is that read/write times to USB would be of concern (considerably slower than IDE) for a web server. Also, flash memory has a limited amount of writes. Hosting a webserver off a USB key could kill the flash memory really quickly. You'd be much better off hosting it on a hard drive if you can get your hands on one.

Another alternative (if you have a cdrom drive) would be to host your site with knoppix live cd, and store all your web files on the USB key. Though this option would also be RAM intensive.

While I realize you're probably trying to do what you can with resources immediately available, you should look hard for a small capacity HDD. Most any hard drive you find below 10gig is considered worthless and you should be able to get them for nothing.

As the OS, I suggest going as light as possible. The only Ubuntu release I think might fit what you're looking for would be the Ubuntu minimal CD: [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

You could probably do much better with something like ARCH or Debian though.

---

### Post by xtracool_protik on 2009-04-05
RAM intensive - yes I know Live CD option would be RAM intensive thats why I was looking at something where I can install and run OS from pen drive.

Still limited number of read/writes would be a great problem so I should better look for HDD maybe will ask in school if they have something they want to discard.

And minimalCD looks cool will give it a try - maybe not for server but just to checkout.

Thanks a lot :KS

---

### Post by dmizer on 2009-04-05
On a minimal install (or any install really), all you need to do in order to install a webserver is:
```
sudo tasksel install lamp-server
```

Take a look at this guide for remote CLI administration: [https://help.ubuntu.com/community/AdvancedOpenSSH](https://help.ubuntu.com/community/AdvancedOpenSSH)

---

### Post by xtracool_protik on 2009-04-06
Thanks dmizer,
 I have some experience working with ssh so I suppose it would be easy to work on. 
 Anyway to install on USB - just put the USB and at the time of drive selection and mount point - select USB key (but then motherboard needs to support USB booting), that worked for me however my motherboard doesn't support it.  
 And got one 6GB for 9$ :) - ebay 
 Yet to try minimal install, but it seems interesting. will try to go through documentation. It got my attention to something but I'm not sure should I ask here - its about putting Ubuntu on cellphone.

---

