---
title: "Ralink Wirless RTL8188CUS LAN dongle nightmare!"
date: 2011-01-28
forum: Desktop Environments
---

### Post by Honahon on 2011-01-28
Gents. 

 I am appealing to the minds far greater than mine.. I have been using this forum with resounding success without having to post for some time, and I am more than impressed with what you can resolve by simply trawling through the archives, on this occasion however, I'm stumped. 

I have a desktop upstairs in my home running 10.10, I have a Ralink Wirless LAN dongle RTL8188CUS with a mini CD with all the drivers etc. Now, when I physically install the dongle Ubuntu does not firstly even acknowledge it's existence, so, I unpack the CD Lynx dir and there seems to be no way to install it? I can't see a code to run in terminal to install.. nothing? I'm not normally too bad a working things out, so unless I'm being a muppet, I would really appreciate some advise. 

Has anyone got any experience of these kinds of installs? is there a specific file I should be running? 

Thanks in advance

J

---

### Post by fireoftroy on 2011-02-28
I was finally able to get this driver working last night.  Basically, you need to expand the driver folder and then use the make and make install commands to compile and install the driver.

Whether you use the CD drivers or download the latest ones from the web, you will need to expand the folder using Archive Manager or equivalent software.  For example I expanded mine to:

**/home/me/drivers/rtl8192CU_linux_v2.0.1324.20110126** (downloaded from the web)

Once this is done, open a terminal and enter super-user mode with:

**$ sudo su**

Once in super-user mode, go to the driver directory and enter:

**# make**

When that completes, enter:

**# make install**

Once this step is done, insert the dongle and it should be recognized.  Then go through your normal wireless connection procedures and you should be done.  If everything is configured correctly (there's always an if), it should be a relatively painless procedure.

---

### Post by Kamil z Mielca on 2011-06-27
I am having the same problem. I can't even compile and use the make or make install commands. I keep getting error messages and nothing wants to work. This is the only thing holding me back from using my Ubuntu machine and I have to keep going back to my Windows OS. I am currently hooked up using my ethernet cable but having a cable strung across the floor of the room is really annoying..

Any way to figure this out??

---

