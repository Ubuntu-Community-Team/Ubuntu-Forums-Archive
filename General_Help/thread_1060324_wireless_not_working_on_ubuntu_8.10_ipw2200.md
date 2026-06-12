---
title: "wireless not working on ubuntu 8.10 ipw2200"
date: 2009-02-04
forum: General Help
---

### Post by sambita on 2009-02-04
**[COLOR="Red"]Update:[/COLOR]** This thread, originally a call for help, has now become a guide on how to get injection with ipw2200, so, unless youre interested in reading the whole process behind the making of this guide, you may skip right to the [guide]("http://ubuntuforums.org/showthread.php?p=6934824#post6934824") itself.

Original Post:
Hello everyone, i was trying to patch ipw2200 following the steps posted in 

[**this post**]("http://ubuntuforums.org/showthread.php?p=6676753#post6676753"), however, somewhere along the way i messed up, so now im out of wireless. 

Can someone tell me how to reinstall the original driver in the kernel so that i can use wireless again?

Thank you very much and sorry for all the trouble.

---

### Post by sambita on 2009-02-06
Well, ive been able to solve my problem. I'm going to post my solution here, i know this may be very basic to many, but i'll post it in case other noobs out there find it helpful. 

(My kernel version is 2.6.27-11-generic)

Here it goes:

First of all open a terminal and enter:

```
sudo apt-get install build-essential linux-headers-`uname -r`

```

(I created a directory called wireless in my home folder just to keep it tidy)

1) Download the ieee80211 subsystem, in my case this was [ieee80211-1.2.18]("http://ieee80211.sourceforge.net/downloads.php"),  to the "wireless" folder you created.  

2) Open a terminal and enter:
```
tar -xzvf ieee80211-1.2.18.tgz
```

3) Go inside the ieee80211-1.2.18 folder, you'll see a file called ieee80211_module.c, open it and look for every occurrence of 'proc_net' and change it for 'init_net.proc_net'. For example: 
```
ieee80211_proc = proc_mkdir(DRV_NAME, proc_net);
```
to```

ieee80211_proc = proc_mkdir(DRV_NAME, init_net.proc_net);
```

4) In the files ieee80211_crypt_wep.c and ieee80211_crypt_tkip.c
substitute every occurrence of '.page' for '.page_link'
For example:

```
sg.page = virt_to_page(pos);

```to
```
sg.page_link = virt_to_page(pos);

```
5)Download the attachment "ieee80211_wx.c.patch.txt" and save it in the ieee80211-1.2.18 folder then rename it to "ieee80211_wx.c.patch" and in a terminal enter:
```
cd /home/$USER/wireless/ieee80211-1.2.18
patch ieee80211_wx.c ieee80211_wx.c-2.6.27.patch
```

*note: Thanks to arturosevilla for this patch, i found it on [**this post**]("http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=996574&page=2")

6)now type:
```

. remove-old
sudo make SHELL=/bin/bash
sudo make install SHELL=/bin/bash
```

I dont know if it is necessary to use sudo, but i did it anyway. 
Good, now you have the ieee80211 subsystem installed, time to install the driver, for this you need to download the following:

[**ipw2200-1.2.2.tgz**]("http://ipw2200.sourceforge.net/downloads.php")
and
[**firmware v3.0**]("http://ipw2200.sourceforge.net/firmware.php")

save them in the "wireless folder"
 
7) open a terminal and type:
```
cd /home/$USER/wireless
tar -xzvf ipw2200-1.2.2.tgz
cd ipw2200-1.2.2
```

8 ) Download the attachment "ipw2200-1.2.2-2.6.24.patch.txt, save it to your "wireless" folder and rename it to "ipw2200-1.2.2-2.6.24.patch"
Open a terminal and enter:

```

cd /home/$USER/wireless
patch ipw2200-1.2.2/ipw2200.h ipw2200-1.2.2-2.6.24.patch
cd ipw2200-1.2.2
sudo ./remove-old
sudo make SHELL=/bin/bash
sudo make install SHELL=/bin/bash

```

Now all is left to do is copy the firmware to the proper directory, open a terminal and type:

```

cd /home/$USER/wireless
tar -xzvf ipw2200-fw-3.0.tgz
sudo cp ipw2200-fw-3.0/* /lib/firmware/
```

reload the module:
```

rmmod ipw2200
sudo modprobe ipw2200
ifconfig eth1 up
```

and you're set!

I apologize in advance for any mistake, the steps posted here worked for me, but i cannot guarantee that they will work for you. If you have any doubts feel free to post and ill do my best to help you

---

### Post by ttieben on 2009-02-18
Thanks a ton for this post! Followed instructions to the tee as I have same kernel and same ipw2200.

Everything went fine, but here is my error message when airodump-ng eth1 is ran:

ioctl(SIOCSIWMODE) failed: Invalid argument

ARP linktype is set to 1 (Ethernet) - expected ARPHRD_IEEE80211,
ARPHRD_IEEE80211_FULL or ARPHRD_IEEE80211_PRISM instead.  Make
sure RFMON is enabled: run 'airmon-ng start eth1 <#>'
Sysfs injection support was not found either.

I have never seen this message until this recent update.
I ran airmon-ng start eth1, and it didn't change anything.

Any advice?

Thanks,

Tanner

---

### Post by sambita on 2009-02-19
The steps i posted for compililng ipw2200 will not enable  packet injection, in order to do that go to [this page]("http://www.developarts.com/parte1_ipw2200_inyeccion") and download the attachments you see there to the wireless folder you created when following the previous guide. 

**IMPORTANT**: **I have not yet tried to do what im posting here**, its essentially what i believe should work, but **cannot guarantee** that it will, should you encounter any problems let me know and ill try to find the time to test it myself. With that being said, lets go on, shall we?

Follow the instrucionts i wrote, but after step 2 and before step 3 you need to patch ieee80211, so open a terminal and type:
```
patch ieee80211-1.2.18/ieee80211_tx.c ieee80211_inject-1.2.18.patch
patch -p0 < ieee80211-1.2.18-2.6.24.patch

```
Continue with the written instructions and after step 7 and before step 8 open a terminal and enter:
```
patch ipw2200.c ipw2200-1.2.2-inject.patch
patch Makefile ipw2200-1.2.2-make.patch

```

Now, instead of step 8 you'll have to do this:

new 8 ) Download the attachment "ipw2200-1.2.2-2.6.24.patch.txt, save it to your "wireless" folder and rename it to "ipw2200-1.2.2-2.6.24.patch"
Open a terminal and enter:
```

cd /home/$USER/wireless
patch ipw2200-1.2.2/ipw2200.h ipw2200-1.2.2-2.6.24.patch
patch ipw2200-1.2.2/ipw2200.c ipw2200_rtap_fix.patch
cd ipw2200-1.2.2
sudo ./remove-old
sudo make SHELL=/bin/bash
sudo make install SHELL=/bin/bash

```


Now all is left to do is copy the firmware to the proper directory, open a terminal and type:

```

cd /home/$USER/wireless
tar -xzvf ipw2200-fw-3.0.tgz
sudo cp ipw2200-fw-3.0/* /lib/firmware/
```

reload the module:
```

rmmod ipw2200
sudo modprobe ipw2200 rtap_iface=1
ifconfig eth1 up
ifconfig rtap0 up

```

and you're set!

As stated above, i have not yet tried this, so do it at your own risk, if you find any errors while doing it i'll be more than glad to help in any way i can!

---

### Post by Aviator on 2009-02-19
You can always reinstall the kernel modules if you ever messed up the patching process:

```
sudo apt-get --reinstall install linux-image-2.6.27-11-generic
```

---

### Post by Aviator on 2009-02-19
Nice. I followed all the instructions, but after running "patch ipw2200-1.2.2/ipw2200.c ipw2200_rtap_fix.patch", it said something about some thunk not patched correctly (I can't remember the actual error message). I continued anyway, and after running "sudo modprobe ipw2200 rtap_iface=1", the terminal spewed another error message:

```
FATAL: Error inserting ipw2200 (/lib/modules/2.6.27-11-generic/kernel/drivers/net/wireless/ipw2200.ko): Unknown symbol in module, or unknown parameter (see dmesg)

```

---

### Post by ttieben on 2009-02-19
Yeah, i received a similar error:

patch ipw2200-1.2.2/ipw2200.c ipw2200_rtap_fix.patch 

patching file ipw2200-1.2.2/ipw2200.c
Hunk #1 FAILED at 10529.
Hunk #2 succeeded at 11883 (offset 303 lines).
1 out of 2 hunks FAILED -- saving rejects to file ipw2200-1.2.2/ipw2200.c.rej

But i also went through the rest without a problem

I did a test: aireplay-ng -9 eth1
and it did not appear to work.
It looks like i am not able to inject still.
Although it is possible I just don't know the correct commands!

Thanks.

---

### Post by ttieben on 2009-02-19
On the other hand,

I just tried this command on my own router at home which is setup with wep:

aireplay-ng -3 -b (bssid) eth1

and airodump-ng is showing a ton of Data be gathered

Does that mean I am successfully injecting?

Sorry for the rookie questions.

T

---

### Post by sambita on 2009-02-19
I've been doing some research and found out that we need to edit a line in the rtap_fix patch.

So, once again, here's the rewriting of step 8.

new new 8 ) Download the attachment "ipw2200-1.2.2-2.6.24.patch.txt, save it to your "wireless" folder and rename it to "ipw2200-1.2.2-2.6.24.patch"
Open a terminal and enter:
```

cd /home/$USER/wireless
patch ipw2200-1.2.2/ipw2200.h ipw2200-1.2.2-2.6.24.patch
patch ipw2200-1.2.2/ipw2200.c ipw2200_rtap_fix.patch

```

Now open ipw2200.c with gedit and look for this line(its about line 10754):

> memcpy(priv->mac_addr, addr->sa_data, ETH_ALEN);

below that line we need to write this one:

> if (rtap_iface)
        memcpy(priv->prom_net_dev->dev_addr, addr->sa_data, ETH_ALEN);

Important: **do not erase the original line**, simply paste the other one below it, so that it looks like this:
> memcpy(priv->mac_addr, addr->sa_data, ETH_ALEN);
if (rtap_iface)
        memcpy(priv->prom_net_dev->dev_addr, addr->sa_data, ETH_ALEN);


now we continue with the same steps as previously posted, open a terminal and enter:
```

cd /home/$USER/wireless
cd ipw2200-1.2.2
sudo ./remove-old
sudo make SHELL=/bin/bash
sudo make install SHELL=/bin/bash

```


Now all is left to do is copy the firmware to the proper directory, open a terminal and type:

```

cd /home/$USER/wireless
tar -xzvf ipw2200-fw-3.0.tgz
sudo cp ipw2200-fw-3.0/* /lib/firmware/
```

reload the module:
```

rmmod ipw2200
sudo modprobe ipw2200 rtap_iface=1
ifconfig eth1 up
ifconfig rtap0 up

```

and that's it!

*Aviator: Thanks for that info, when i originally messed up thats exactly what i wanted to do but didn't know how hehe.

*ttieben: Im not sure if you're being able to inject, if you failed to load the module i'd doubt you would be able to inject. Don't worry about the rookie questions, im a rookie myself!

Please let me know if this works, if it doesnt ill try to compile it myself over the weekend.

---

### Post by ttieben on 2009-02-19
Thanks.  I applied your new changes. 

Is there a sure way i can test my ability to inject?

I felt i was able to inject already before your recent change as I was able to aireplay-ng to my current router/ssid and successfully ran aircrack-ng to get the wep key.

---

### Post by sambita on 2009-02-19
aircrack-ng includes an injection test, just type:

```
aireplay-ng --test eth1
```
or
```
aireplay-ng --test rtap0
```

im not sure which.

More info on aircrack-ng test [**here**]("http://www.aircrack-ng.org/doku.php?id=injection_test")

---

### Post by Aviator on 2009-02-19
Thanks, sambita. Just now I applied you new instructions. The command "patch ipw2200-1.2.2/ipw2200.c ipw2200_rtap_fix.patch" still produces the "hunk failed" error.

I just proceed until I found out that my copy of ipw2200.c at line 10754 doesn't look like the code you've specified. By using my text editor's find tool however I found the exact code at line 10696, so I pasted your two new lines below that line instead. Only that when I compile the module, gcc died telling,

```
error: ‘struct ipw_priv’ has no member named ‘prom_net_dev’
```

---

### Post by sambita on 2009-02-20
Please clarify this for me, did you first edit ipw2200.c and then ram tha patch command, or did you patched it and then edited ipw2200.c?

Make sure to patch it after youve edited the file. Im sorry if this clarification sounds stupid, but i just want to make sure.
Also, did you edit with sudo? you had privileges to save the file right?

If you want to, attach your ipw2200.c file and i'll give it a look.

Im thinking im gonna have to try to compile it too, as i am no expert (obviously), it takes some trial and error for me to get the hang of it, and you guys should not have to suffer for it :).

---

### Post by Aviator on 2009-02-20
Please clarify this for me, did you first edit ipw2200.c and then ram tha patch command, or did you patched it and then edited ipw2200.c?

> I did it both ways and they don't work.

If you want to, attach your ipw2200.c file and i'll give it a look.

> Here's my fresh copy of ipw2200.c, version 1.2.2 right after extracting from the tarball: [http://pastebin.ca/1342776]("http://pastebin.ca/1342776")

---

### Post by sambita on 2009-02-21
Im sorry i havent had much time to look at this, as soon as i get home today im going to try and compile it.

---

### Post by ttieben on 2009-02-21
> **sambita said:**
> aircrack-ng includes an injection test, just type:

```
aireplay-ng --test eth1
```
or
```
aireplay-ng --test rtap0
```

im not sure which.

More info on aircrack-ng test [**here**]("http://www.aircrack-ng.org/doku.php?id=injection_test")

I didn't have any errors while compiling.  The compile went fine.
I ran the test you list above.  It does not say "packet injection is working."  I do not get any errors though during this test, it simply says no answer and lists all the AP's in my area. Any ideas?

---

### Post by sambita on 2009-02-21
ttieben i have just finished compiling myself, as it happened to you, i had no errors while compiling the module, i did get the hunk failure, but editing the two lines as i had posted fixed it for me. After running aireplay-ng i got no answer on broadcast probe request nor directed probe requests, so i find myself in exactly the same position as you. I will investigate this further to see how can it be fixed, once i get to fix it ill post a complete guide to get injection, thanks in advance for your patience.

**Edit**: You need to set your card to monitor mode before testing:
```
airmon-ng start eth1
```

didn't work for me but maybe it will for you.

**WARNING**: After rebooting to make sure all kernel-related changes were applied, NetworkManager(nm-applet) completely crashed my computer, leaving me only with the choice to force a reboot(Ctrl+Alt+F2 didn't work), im now back to the original driver, did anyone else have this problem?

---

### Post by ttieben on 2009-02-21
Here is what i get after a airmon-ng start eth1 and then running the test:

root@tntlaptop:/home/tanner# aireplay-ng --test rtap0
22:51:14  Trying broadcast probe requests...
22:51:16  No Answer...
22:51:16  Found 1 AP 

22:51:16  Trying directed probe requests...
22:51:16  00:12:01:59:1D:3D - channel: 11 - 'digitalroute'
22:51:23   0/30:   0%

The same shows when running test on eth1 as well. I am currently only around 1 AP and it is my own with macfiltering on.

*Sambita- that is weird about the reboot. That did not happen to me.

---

### Post by sambita on 2009-02-22
The crasing problem originated because of some modifications i did on one of the patches, i compiled it again and now everythings working ok, except for the fact that i still dont have injection capabilities. I read on a post that there is a problem with airodump-ng and ipw2200, but that using kismet instead of airodump does the trick, i havent tried this yet and dont know if that will solve the injection issues, i still dont quite understand how it all works. 

Ill try the kismet thing tomorrow, im too tired right now. :)

---

### Post by ploum on 2009-02-23
I followed the whole post and applied some patches by hand to be sure. I also applied the ipw2200-inject patch which is not mentioned in your last version of 8).

It works (as a proof, I now have a rtap0 interface that I didn't had before) but injection is still not working.

I really anything I can do more, any help is appreciated...

---

### Post by sambita on 2009-02-23
> **sambita said:**
> 
Continue with the written instructions and after step 7 and before step 8 open a terminal and enter:
```
patch ipw2200.c ipw2200-1.2.2-inject.patch
patch Makefile ipw2200-1.2.2-make.patch

```


The inject patch is right there, i also have rtap0 but am unable to inject, ive been reading in the past few days but still havent find a solution, as soon as i have one ill post it here.

---

### Post by PookeyMaster on 2009-02-25
Hey sambita, thanks for the guide.

I've finally got ieee80211 stack done successfully but when i try to patch the file ipw2200.c, i get the error:

```
user@ubuntu:~/Desktop/Wireless$ patch ipw2200-1.2.2/ipw2200.c ipw2200_rtap_fix.patch
patching file ipw2200-1.2.2/ipw2200.c
Hunk #1 FAILED at 10748.
Hunk #2 succeeded at 11883 (offset 303 lines).
1 out of 2 hunks FAILED -- saving rejects to file ipw2200-1.2.2/ipw2200.c.rej

```

If I ignore the hunk failure, and continue with sudo make SHELL=/bin/bash i get:

```
user@ubuntu:~/Desktop/Wireless/ipw2200-1.2.2$ sudo make SHELL=/bin/bash
mkdir -p /home/user/Desktop/Wireless/ipw2200-1.2.2/tmp/.tmp_versions
make -C /lib/modules/2.6.27-11-generic/build M=/home/user/Desktop/Wireless/ipw2200-1.2.2 MODVERDIR=/home/user/Desktop/Wireless/ipw2200-1.2.2/tmp/.tmp_versions modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-11-generic'
  CC [M]  /home/user/Desktop/Wireless/ipw2200-1.2.2/ipw2200.o
/home/user/Desktop/Wireless/ipw2200-1.2.2/ipw2200.c: In function ‘ipw_ethtool_set_eeprom’:
/home/user/Desktop/Wireless/ipw2200-1.2.2/ipw2200.c:10823: warning: array subscript is above array bounds
/home/user/Desktop/Wireless/ipw2200-1.2.2/ipw2200.c: In function ‘ipw_eeprom_init_sram’:
/home/user/Desktop/Wireless/ipw2200-1.2.2/ipw2200.c:2857: warning: array subscript is above array bounds
  Building modules, stage 2.
  MODPOST 1 modules
  LD [M]  /home/user/Desktop/Wireless/ipw2200-1.2.2/ipw2200.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-11-generic'

```

Can you please help me find where i'm going wrong... :-|

---

### Post by sambita on 2009-02-25
@PookeyMaster: When patching ipw2200.c with rtap_fix.patch just ignore the hunk failure, but before executing 
```
sudo make SHELL=/bin/bash

```

you need to edit ipw2200, so open ipw2200.c with gedit and look for this line:

> memcpy(priv->mac_addr, addr->sa_data, ETH_ALEN);

below that line you need to write this one:

> if (rtap_iface)
        memcpy(priv->prom_net_dev->dev_addr, addr->sa_data, ETH_ALEN);

Important: **do not erase the original line**, simply paste the other one below it, so that it looks like this:
> memcpy(priv->mac_addr, addr->sa_data, ETH_ALEN);
if (rtap_iface)
        memcpy(priv->prom_net_dev->dev_addr, addr->sa_data, ETH_ALEN);


after that open a terminal, navigate to your ipw2200-1.2.2 folder and enter:
```

sudo ./remove-old
sudo make SHELL=/bin/bash
sudo make install SHELL=/bin/bash

```

and then copy the firmware to /lib/firmaware/your_kernel_version, the way to do this is posted here already. 

cheers!

---

### Post by PookeyMaster on 2009-02-25
Thanks sambita,

The reason it wasn't working was cause i was only copying the firmware to /lib/firmware/ instead of /lib/firmware/2.6.27-11-generic. It still came up with array errors during compiling and it connects to wireless networks but i'm yet to test whether it injects...

Thanks anyway.. :)

---

### Post by EmmeDa on 2009-03-07
Great Post

Actual I messed up my wlan with the instructions from the first post of sambita, because I did first MAKE and then patched the files :( 

Following the steps in the right order my wlan appeared to be fixed again and what i actual wanted to say is, that it worked for Ubuntu 8.10 with Kernel 2.6.27-13-generic.

---

### Post by Friendless on 2009-03-12
Just want to say thanks for this great post, I used it for my ipw3945, had issues with the IEEE installation. IWL3945 has an issue where it can not change the Mac Address and associate with an AP which is a critical aspect in my job, I almost went out to buy a different wireless device to fix this issue. Now I can easily switch between drivers for whatever I need to do.

---

### Post by DoxSearch on 2009-03-12
dox@dox-laptop:~/wifi$ sudo modprobe ipw2200 rtap_iface=1
FATAL: Error inserting ipw2200 (/lib/modules/2.6.27-11-generic/kernel/drivers/net/wireless/ipw2200.ko): Unknown symbol in module, or unknown parameter (see dmesg)


can someone tell me what i goof'd on?

[96613.644332] ipw2200: Failed to send SYSTEM_CONFIG: Already sending a command.
[98214.105989] ipw2200 0000:02:03.0: PCI INT A disabled
[98248.640764] ipw2200: disagrees about version of symbol ieee80211_wx_get_encodeext
[98248.640774] ipw2200: Unknown symbol ieee80211_wx_get_encodeext
[98248.641209] ipw2200: disagrees about version of symbol ieee80211_wx_set_encode
[98248.641212] ipw2200: Unknown symbol ieee80211_wx_set_encode
[98248.641334] ipw2200: disagrees about version of symbol ieee80211_wx_get_encode
[98248.641337] ipw2200: Unknown symbol ieee80211_wx_get_encode
[98248.641766] ipw2200: disagrees about version of symbol ieee80211_txb_free
[98248.641769] ipw2200: Unknown symbol ieee80211_txb_free
[98248.641960] ipw2200: disagrees about version of symbol ieee80211_wx_set_encodeext
[98248.641963] ipw2200: Unknown symbol ieee80211_wx_set_encodeext
[98248.642332] ipw2200: disagrees about version of symbol ieee80211_wx_get_scan
[98248.642335] ipw2200: Unknown symbol ieee80211_wx_get_scan
[98248.648127] ipw2200: disagrees about version of symbol ieee80211_rx
[98248.648132] ipw2200: Unknown symbol ieee80211_rx
[98248.649146] ipw2200: disagrees about version of symbol ieee80211_rx_mgt
[98248.649149] ipw2200: Unknown symbol ieee80211_rx_mgt
[98248.649360] ipw2200: disagrees about version of symbol free_ieee80211
[98248.649363] ipw2200: Unknown symbol free_ieee80211
[98248.650107] ipw2200: disagrees about version of symbol alloc_ieee80211
[98248.650110] ipw2200: Unknown symbol alloc_ieee80211
[98564.101330] ipw2200: disagrees about version of symbol ieee80211_wx_get_encodeext
[98564.101342] ipw2200: Unknown symbol ieee80211_wx_get_encodeext
[98564.101777] ipw2200: disagrees about version of symbol ieee80211_wx_set_encode
[98564.101780] ipw2200: Unknown symbol ieee80211_wx_set_encode
[98564.101901] ipw2200: disagrees about version of symbol ieee80211_wx_get_encode
[98564.101904] ipw2200: Unknown symbol ieee80211_wx_get_encode
[98564.102333] ipw2200: disagrees about version of symbol ieee80211_txb_free
[98564.102336] ipw2200: Unknown symbol ieee80211_txb_free
[98564.102528] ipw2200: disagrees about version of symbol ieee80211_wx_set_encodeext
[98564.102531] ipw2200: Unknown symbol ieee80211_wx_set_encodeext
[98564.102900] ipw2200: disagrees about version of symbol ieee80211_wx_get_scan
[98564.102903] ipw2200: Unknown symbol ieee80211_wx_get_scan
[98564.110429] ipw2200: disagrees about version of symbol ieee80211_rx
[98564.110434] ipw2200: Unknown symbol ieee80211_rx
[98564.111447] ipw2200: disagrees about version of symbol ieee80211_rx_mgt
[98564.111450] ipw2200: Unknown symbol ieee80211_rx_mgt
[98564.111662] ipw2200: disagrees about version of symbol free_ieee80211
[98564.111664] ipw2200: Unknown symbol free_ieee80211
[98564.112426] ipw2200: disagrees about version of symbol alloc_ieee80211
[98564.112428] ipw2200: Unknown symbol alloc_ieee80211
[103441.952624] ipw2200: disagrees about version of symbol ieee80211_wx_get_encodeext
[103441.952642] ipw2200: Unknown symbol ieee80211_wx_get_encodeext
[103441.953795] ipw2200: disagrees about version of symbol ieee80211_wx_set_encode
[103441.953803] ipw2200: Unknown symbol ieee80211_wx_set_encode
[103441.954120] ipw2200: disagrees about version of symbol ieee80211_wx_get_encode
[103441.954128] ipw2200: Unknown symbol ieee80211_wx_get_encode
[103441.955265] ipw2200: disagrees about version of symbol ieee80211_txb_free
[103441.955273] ipw2200: Unknown symbol ieee80211_txb_free
[103441.955778] ipw2200: disagrees about version of symbol ieee80211_wx_set_encodeext
[103441.955786] ipw2200: Unknown symbol ieee80211_wx_set_encodeext
[103441.956785] ipw2200: disagrees about version of symbol ieee80211_wx_get_scan
[103441.956793] ipw2200: Unknown symbol ieee80211_wx_get_scan
[103441.960633] ipw2200: disagrees about version of symbol ieee80211_rx
[103441.960643] ipw2200: Unknown symbol ieee80211_rx
[103441.963337] ipw2200: disagrees about version of symbol ieee80211_rx_mgt
[103441.963345] ipw2200: Unknown symbol ieee80211_rx_mgt
[103441.963901] ipw2200: disagrees about version of symbol free_ieee80211
[103441.963909] ipw2200: Unknown symbol free_ieee80211
[103441.965911] ipw2200: disagrees about version of symbol alloc_ieee80211
[103441.965919] ipw2200: Unknown symbol alloc_ieee80211

---

### Post by thoraz on 2009-03-12
rmmod your ieee drivers and modprobe the new one.. or simply reboot

---

### Post by sambita on 2009-03-12
Im really glad you guys are finding this post helpful!

@DoxSearch:let me know if your problem persists

---

### Post by DoxSearch on 2009-03-13
I am heading out of town for a few days, I will try again monday more than likely and update yall.

Rebooting doesnt work btw. I will redo it all again,


where can i get this patch at? 
ipw2200_rtap_fix.patch

---

### Post by sambita on 2009-03-14
you can find ipw2200_rtap_fix.patch [here]("http://nexus.developarts.com/parte1_ipw2200_inyeccion")

be sure to read carefully the steps you have to follow in order to compile ipw2200.

---

### Post by flatcoke on 2009-03-19
Thanks to the OP, this thread provided tons of information about how to get injection to work on ipw2200.


I've had the same problem. Just FYI, if your wireless is screw up to a point where you don't care anymore if injection works(like me >_<), you can check my solution. Took me two days to figure out [http://ubuntuforums.org/showthread.php?p=6920127](http://ubuntuforums.org/showthread.php?p=6920127)

---

### Post by DoxSearch on 2009-03-21
dox@dox-laptop:~/wifi/patch/ipw2200-1.2.2$ sudo make SHELL=/bin/bash

mkdir -p /home/dox/wifi/patch/ipw2200-1.2.2/tmp/.tmp_versions
make -C /lib/modules/2.6.27-11-generic/build M=/home/dox/wifi/patch/ipw2200-1.2.2 MODVERDIR=/home/dox/wifi/patch/ipw2200-1.2.2/tmp/.tmp_versions modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-11-generic'
  CC [M]  /home/dox/wifi/patch/ipw2200-1.2.2/ipw2200.o
/home/dox/wifi/patch/ipw2200-1.2.2/ipw2200.c: In function ‘ipw_net_set_mac_address’:
/home/dox/wifi/patch/ipw2200-1.2.2/ipw2200.c:10697: error: ‘rtap_iface’ undeclared (first use in this function)
/home/dox/wifi/patch/ipw2200-1.2.2/ipw2200.c:10697: error: (Each undeclared identifier is reported only once
/home/dox/wifi/patch/ipw2200-1.2.2/ipw2200.c:10697: error: for each function it appears in.)
/home/dox/wifi/patch/ipw2200-1.2.2/ipw2200.c:10698: error: ‘struct ipw_priv’ has no member named ‘prom_net_dev’
/home/dox/wifi/patch/ipw2200-1.2.2/ipw2200.c:10698: error: ‘struct ipw_priv’ has no member named ‘prom_net_dev’
make[2]: *** [/home/dox/wifi/patch/ipw2200-1.2.2/ipw2200.o] Error 1
make[1]: *** [_module_/home/dox/wifi/patch/ipw2200-1.2.2] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-11-generic'
make: *** [modules] Error 2



Ok so i took another whack at it. No luck. Now I am without wifi again. I really would like to play around with injection but I am just having no luck here.

---

### Post by sambita on 2009-03-21
If you are simply interested in getting your wireless working again, you can just open a terminal and type:
```

sudo apt-get --reinstall install linux-image-2.6.27-11-generic

```
The following is a guide on how to get injection, its basically a summarize of all my posts in this thread, i thought it was time to get them all in one organized guide so as to avoid confusion, here it goes.

First of all open a terminal and enter:

```
sudo apt-get install build-essential linux-headers-`uname -r`

```

create a directory called wireless in your home folder, just to keep it tidy.

1)Download the zip attached to this post and extract its contents to the "wireless" folder you created. Also Download the ieee80211 subsystem, [ieee80211-1.2.18]("http://ieee80211.sourceforge.net/downloads.php"),  to the "wireless" folder.  

2) Open a terminal and enter:
```
cd /home/$USER/wireless
tar -xzvf ieee80211-1.2.18.tgz
patch ieee80211-1.2.18/ieee80211_tx.c ieee80211_inject-1.2.18.patch
patch -p0 < ieee80211-1.2.18-2.6.24.patch
```

[COLOR="Red"][SIZE="4"]Steps 3 and 4 have been dismissed, i have left them here only for future reference.[/SIZE][/COLOR]

> 3) Go inside the ieee80211-1.2.18 folder, you'll see a file called ieee80211_module.c, open it and look for every occurrence of 'proc_net' and change it for 'init_net.proc_net'. For example: 
```
ieee80211_proc = proc_mkdir(DRV_NAME, proc_net);
```
to```

ieee80211_proc = proc_mkdir(DRV_NAME, init_net.proc_net);
```

4) In the files ieee80211_crypt_wep.c and ieee80211_crypt_tkip.c
substitute every occurrence of '.page' for '.page_link'
For example:

```
sg.page = virt_to_page(pos);

```to
```
sg.page_link = virt_to_page(pos);

```

5) In a terminal enter:
```
cd /home/$USER/wireless
patch ieee80211-1.2.18/ieee80211_wx.c ieee80211_wx.c-2.6.27.patch
```

*note: Thanks to arturosevilla for this patch, i found it on [**this post**]("http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=996574&page=2")

6)now type:
```

cd /home/$USER/wireless/ieee80211-1.2.18
. remove-old
sudo make SHELL=/bin/bash
sudo make install SHELL=/bin/bash
```

I dont know if it is necessary to use sudo, but i did it anyway. 
Good, now you have the ieee80211 subsystem installed, time to install the driver, for this you need to download the following:

[**ipw2200-1.2.2.tgz**]("http://ipw2200.sourceforge.net/downloads.php")
and
[**firmware v3.0**]("http://ipw2200.sourceforge.net/firmware.php")

save them in the "wireless folder"
 
7) open a terminal and type:
```
cd /home/$USER/wireless
tar -xzvf ipw2200-1.2.2.tgz
patch ipw2200-1.2.2/ipw2200.c ipw2200-1.2.2-inject.patch
patch ipw2200-1.2.2/Makefile ipw2200-1.2.2-make.patch
patch ipw2200-1.2.2/ipw2200.h ipw2200-1.2.2-2.6.24.patch
patch ipw2200-1.2.2/ipw2200.c ipw2200_rtap_fix.patch

```


Now open ipw2200.c with gedit and look for this line(use Ctrl + F to look for it):

> memcpy(priv->mac_addr, addr->sa_data, ETH_ALEN);

below that line we need to write this one:

> if (rtap_iface)
        memcpy(priv->prom_net_dev->dev_addr, addr->sa_data, ETH_ALEN);

Important: **do not erase the original line**, simply paste the other one below it, so that it looks like this:
> memcpy(priv->mac_addr, addr->sa_data, ETH_ALEN);
if (rtap_iface)
        memcpy(priv->prom_net_dev->dev_addr, addr->sa_data, ETH_ALEN);


now open a terminal and enter:
```

cd /home/$USER/wireless
cd ipw2200-1.2.2
sudo ./remove-old
sudo make SHELL=/bin/bash
sudo make install SHELL=/bin/bash

```

Now all is left to do is copy the firmware to the proper directory, open a terminal and type:

```

cd /home/$USER/wireless
tar -xzvf ipw2200-fw-3.0.tgz
sudo cp ipw2200-fw-3.0/* /lib/firmware/`uname -r`/

```

reload the module:
```

rmmod ipw2200
sudo modprobe ipw2200
ifconfig eth1 up
```

And that's it!

If you have any problems while doing this just let me know.

---

### Post by DoxSearch on 2009-03-22
How do I know which subsystem is correct?

---

### Post by sambita on 2009-03-22
The link i provided (ieee80211-1.2.18 ) should work for you, when i said "in my case" i meant it in case there was a newer version when someone read the post, ill edit that now.

---

### Post by machinehead101 on 2009-03-25
im having the same issue as dox here

im getting the following

```
*****@laptop:~/wireless/ipw2200-1.2.1$ sudo ./remove-oldChecking in /lib/modules/2.6.27-11-generic/build/ for ipw2x00 components...
*****@laptop:~/wireless/ipw2200-1.2.1$ sudo make SHELL=/bin/bashmkdir -p /home/*****/wireless/ipw2200-1.2.1/tmp/.tmp_versions
make -C /lib/modules/2.6.27-11-generic/build M=/home/*****/wireless/ipw2200-1.2.1 MODVERDIR=/home/*****/wireless/ipw2200-1.2.1/tmp/.tmp_versions modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-11-generic'
  CC [M]  /home/*****/wireless/ipw2200-1.2.1/ipw2200.o
/home/*****/wireless/ipw2200-1.2.1/ipw2200.c: In function ‘ipw_handle_mgmt_packet’:
/home/*****/wireless/ipw2200-1.2.1/ipw2200.c:8346: error: ‘struct sk_buff’ has no member named ‘mac’
/home/*****/wireless/ipw2200-1.2.1/ipw2200.c: In function ‘ipw_net_set_mac_address’:
/home/*****/wireless/ipw2200-1.2.1/ipw2200.c:10645: error: ‘rtap_iface’ undeclared (first use in this function)
/home/*****/wireless/ipw2200-1.2.1/ipw2200.c:10645: error: (Each undeclared identifier is reported only once
/home/*****/wireless/ipw2200-1.2.1/ipw2200.c:10645: error: for each function it appears in.)
/home/*****/wireless/ipw2200-1.2.1/ipw2200.c:10646: error: ‘struct ipw_priv’ has no member named ‘prom_net_dev’
/home/*****/wireless/ipw2200-1.2.1/ipw2200.c:10646: error: ‘struct ipw_priv’ has no member named ‘prom_net_dev’
make[2]: *** [/home/*****/wireless/ipw2200-1.2.1/ipw2200.o] Error 1
make[1]: *** [_module_/home/*****/wireless/ipw2200-1.2.1] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-11-generic'
make: *** [modules] Error 2
```

would love to see somone help me get this resolved any help is apreciated

---

### Post by sambita on 2009-03-25
@machinehead: You're using ipw2200-1.2.1, the patches i provide are for ipw2200-1.2.2 
The guide did well for me, but ill follow it once more tomorrow to double check in case somethings wrong in it, causing the mistakes you have.

Sorry for the delay to answer

---

### Post by machinehead101 on 2009-03-28
i did retry with 1.2.2 drivers to no avail getting the same error messages will try agiain tomorrow after ive had more sleep

---

### Post by sambita on 2009-03-28
im really sorry, i found two commands missing in the guide, i edited, the only thing that changed is step 7), The attached tar provides the files needed, it is only the patching of those files that was missing in the guide. Once again i apologize and hope this corrections make it work for you.

---

### Post by machinehead101 on 2009-03-28
well drivers compiled and i was able to load them with no issue.. but im having no luck with injection now... i dunno if the following  maybe the problem.. im no expert just asking


```
  CC [M]  /home/*****/wireless/ipw2200-1.2.2/ipw2200.o
/home/*****/wireless/ipw2200-1.2.2/ipw2200.c: In function &#8216;ipw_ethtool_set_eeprom&#8217;:
/home/*****/wireless/ipw2200-1.2.2/ipw2200.c:10823: warning: array subscript is above array bounds
/home/*****/wireless/ipw2200-1.2.2/ipw2200.c: In function &#8216;ipw_eeprom_init_sram&#8217;:
/home/*****/wireless/ipw2200-1.2.2/ipw2200.c:2857: warning: array subscript is above array bounds
  Building modules, stage 2.
  MODPOST 1 modules

```

---

### Post by sambita on 2009-04-02
what command generates that output? im afraid im no expert either, but ill try and see what i can do.

---

### Post by machinehead101 on 2009-04-05
make or make install generated that i cant remember ... im pretty sure make

---

### Post by dafuzzbudd on 2009-04-17
just successfully went through all steps,

received no errors but injection still doesnt seem to work.

im thinking about going to ubuntu 8.04

---

### Post by MaskedMarauder on 2009-04-19
I'm having problems with this too... the problems seem a bit different though.

I'm using kernel 2.6.27-11.

I DLed the packages listed in the guide. (there's a newer firmware (3.1), but I went with the 3.0 to avoid possible incompatibilities)

the ipw2200-1.2.2 patches went OK, mostly.  I'm not sure the second ipw2200.c patch is still valid.  The contexts were way off.  The first failed and the second succeeded. (is there another 1.2.2 out there?)

ieee80211 builds and loads without error or warning


when I reload the ipw2200 module, I get: > FATAL: Error inserting ipw2200 (/lib/modules/2.6.27-11-generic/updates/ipw2200.ko): Unknown symbol in module, or unknown parameter (see dmesg)


dmesg sez:

> 
[   25.804786] ipw2200: disagrees about version of symbol ieee80211_wx_get_encodeext
[   25.804792] ipw2200: Unknown symbol ieee80211_wx_get_encodeext
[   25.805183] ipw2200: disagrees about version of symbol ieee80211_wx_set_encode
[   25.805185] ipw2200: Unknown symbol ieee80211_wx_set_encode
[   25.805282] ipw2200: disagrees about version of symbol ieee80211_wx_get_encode
[   25.805285] ipw2200: Unknown symbol ieee80211_wx_get_encode
[   25.805672] ipw2200: disagrees about version of symbol ieee80211_txb_free
[   25.805674] ipw2200: Unknown symbol ieee80211_txb_free
[   25.805838] ipw2200: disagrees about version of symbol ieee80211_wx_set_encodeext
[   25.805840] ipw2200: Unknown symbol ieee80211_wx_set_encodeext
[   25.806346] ipw2200: disagrees about version of symbol ieee80211_wx_get_scan
[   25.806348] ipw2200: Unknown symbol ieee80211_wx_get_scan
[   25.806552] ipw2200: disagrees about version of symbol ieee80211_freq_to_channel
[   25.806555] ipw2200: Unknown symbol ieee80211_freq_to_channel
[   25.807148] ipw2200: disagrees about version of symbol ieee80211_set_geo
[   25.807151] ipw2200: Unknown symbol ieee80211_set_geo
[   25.807650] ipw2200: disagrees about version of symbol ieee80211_rx
[   25.807652] ipw2200: Unknown symbol ieee80211_rx
[   25.807963] ipw2200: disagrees about version of symbol ieee80211_channel_to_index
[   25.807966] ipw2200: Unknown symbol ieee80211_channel_to_index
[   25.808743] ipw2200: disagrees about version of symbol ieee80211_rx_mgt
[   25.808746] ipw2200: Unknown symbol ieee80211_rx_mgt
[   25.808843] ipw2200: disagrees about version of symbol ieee80211_get_geo
[   25.808846] ipw2200: Unknown symbol ieee80211_get_geo
[   25.809029] ipw2200: disagrees about version of symbol free_ieee80211
[   25.809032] ipw2200: Unknown symbol free_ieee80211
[   25.809579] ipw2200: disagrees about version of symbol ieee80211_is_valid_channel
[   25.809582] ipw2200: Unknown symbol ieee80211_is_valid_channel
[   25.809830] ipw2200: disagrees about version of symbol alloc_ieee80211
[   25.809833] ipw2200: Unknown symbol alloc_ieee80211


---

### Post by dafuzzbudd on 2009-04-22
i think the second line is supposed to fail because then you're supposed to manual change it

i get no errors past that slight hinderance.  but then injectino still doesnt work :(

im thinking about just buying a new card.

---

### Post by dafuzzbudd on 2009-05-08
Ive been researchnig the Awus036h card.  I plan on purchasing it in an hour. 

Anyway, installation instructions for that card tell the user to blacklist the old mac80211 driver to let the ieee80211 one take over.  Is this something ipw2200 users need to do also?  

After i get this new card working I'd still like to get basic functionality out of my ipw2200.  I'm new to linux and all this trial and error is helping me learn.

---

### Post by al_bozorgi on 2009-05-08
tank you sambita and all other friends 

my problem is solved :guitar:

---

### Post by AlexGriffon on 2009-05-21
Hi I try to install my wireless as well. And I have some trouble :)

I followed your step-by-step tutorial and I get some error in step 6 while 'make'. Here some bash lines:

```

root@alex-laptop:/home/alex/Desktop/wireless/ieee80211-1.2.18# [COLOR=Red]sudo make SHELL=/bin/bash[/COLOR]
Checking in /lib/modules/2.6.24-24-generic for ieee80211 components...
make -C /lib/modules/2.6.24-24-generic/build M=/home/alex/Desktop/wireless/ieee80211-1.2.18 modules
make[1]: Betrete Verzeichnis '/usr/src/linux-headers-2.6.24-24-generic'
  CC [M]  /home/alex/Desktop/wireless/ieee80211-1.2.18/ieee80211_module.o
  CC [M]  /home/alex/Desktop/wireless/ieee80211-1.2.18/ieee80211_tx.o
  CC [M]  /home/alex/Desktop/wireless/ieee80211-1.2.18/ieee80211_rx.o
  CC [M]  /home/alex/Desktop/wireless/ieee80211-1.2.18/ieee80211_wx.o
[COLOR=Red]/home/alex/Desktop/wireless/ieee80211-1.2.18/ieee80211_wx.c: In Funktion »ieee80211_translate_scan«:
/home/alex/Desktop/wireless/ieee80211-1.2.18/ieee80211_wx.c:62: Warnung: Übergabe des Arguments 1 von »iwe_stream_add_event« von inkompatiblem Zeigertyp
/home/alex/Desktop/wireless/ieee80211-1.2.18/ieee80211_wx.c:62: Warnung: Übergabe des Arguments 3 von »iwe_stream_add_event« von inkompatiblem Zeigertyp
/home/alex/Desktop/wireless/ieee80211-1.2.18/ieee80211_wx.c:62: Warnung: Übergabe des Arguments 4 von »iwe_stream_add_event«  erzeugt Ganzzahl von Zeiger ohne Typkonvertierung
/home/alex/Desktop/wireless/ieee80211-1.2.18/ieee80211_wx.c:62: Fehler: zu viele Argumente für Funktion »iwe_stream_add_event«
/home/alex/Desktop/wireless/ieee80211-1.2.18/ieee80211_wx.c:71: Warnung: Übergabe des Arguments 1 von »iwe_stream_add_point« von inkompatiblem Zeigertyp
/home/alex/Desktop/wireless/ieee80211-1.2.18/ieee80211_wx.c:71: Warnung: Übergabe des Arguments 3 von »iwe_stream_add_point« von inkompatiblem Zeigertyp[/COLOR]

*[...more... pointer errors...]*

[COLOR=Red]/home/alex/Desktop/wireless/ieee80211-1.2.18/ieee80211_wx.c:249: Warnung: Übergabe des Arguments 4 von »iwe_stream_add_point« von inkompatiblem Zeigertyp
/home/alex/Desktop/wireless/ieee80211-1.2.18/ieee80211_wx.c:249: Fehler: zu viele Argumente für Funktion »iwe_stream_add_point«
/home/alex/Desktop/wireless/ieee80211-1.2.18/ieee80211_wx.c:270: Warnung: Übergabe des Arguments 1 von »iwe_stream_add_point« von inkompatiblem Zeigertyp
/home/alex/Desktop/wireless/ieee80211-1.2.18/ieee80211_wx.c:270: Warnung: Übergabe des Arguments 3 von »iwe_stream_add_point« von inkompatiblem Zeigertyp
/home/alex/Desktop/wireless/ieee80211-1.2.18/ieee80211_wx.c:270: Warnung: Übergabe des Arguments 4 von »iwe_stream_add_point« von inkompatiblem Zeigertyp
/home/alex/Desktop/wireless/ieee80211-1.2.18/ieee80211_wx.c:270: Fehler: zu viele Argumente für Funktion »iwe_stream_add_point«[/COLOR]
make[2]: *** [/home/alex/Desktop/wireless/ieee80211-1.2.18/ieee80211_wx.o] Fehler 1
make[1]: *** [_module_/home/alex/Desktop/wireless/ieee80211-1.2.18] Fehler 2
make[1]: Verlasse Verzeichnis '/usr/src/linux-headers-2.6.24-24-generic'
make: *** [modules] Fehler 2

```Translation (German -> English).
---
[COLOR=Red][COLOR=Black]Warnung: Übergabe des Arguments 1 von »iwe_stream_add_event« von inkompatiblem Zeigertyp

Warning: Argument 1 in [/COLOR][/COLOR][COLOR=Red][COLOR=Black]»iwe_stream_add_event« is incompatible pointertyp [/COLOR][/COLOR]
[COLOR=Black]---
[/COLOR][COLOR=Black]Fehler: zu viele Argumente für Funktion »iwe_stream_add_event«

Error: to many arguments in function [/COLOR][COLOR=Black]»iwe_stream_add_event«
---[/COLOR][COLOR=Red]

[COLOR=Black]so i got heaps of warning ans a few errors with pointers...?! I hope the bash lines are helpfull, i can post the full bash output as well.. :)

I guess the problem is in the c code, but maybe i have the wrong kernel version?!
[/COLOR][/COLOR]```

root@alex-laptop:/home/alex/Desktop/wireless/ieee80211-1.2.18# cat /proc/version
Linux version 2.6.24-24-generic (buildd@rothera) (gcc version 4.2.4 (Ubuntu 4.2.4-1ubuntu4)) #1 SMP Wed Apr 15 15:54:25 UTC 2009

```[COLOR=Red][COLOR=Black] 
Hope you can help me, thanks!!
Alex
[/COLOR][/COLOR]

---

### Post by PookeyMaster on 2009-05-21
Hey AlexGriffon,

Have you downloaded the linux-image-headers, build-essential and the others? Did you apply all the patches in the correct order. Also, don't worry if there are a few small errors; it seems to be normal when compiling.

@MaskedMarauder, I have the same problem as you... it loads the ipw2200 driver but as soon as you try rmmod ipw2200 it removes it but you can't get it back :(

Sambita, are you able to help us??? All I can think of doing is doing a re- make install for ipw as the ieee80211 installed flawlessly.

Also, i'm currently doing this on 9.04 and once i have it working, i was wondering if there is a way of making an image of the kernel (a custom one) to use whenever i upgrade ubuntu. I've read up on creating a custom kernel but most places talk about adding patches for drivers before compiling...

---

### Post by AlexGriffon on 2009-05-24
Hello again,

thanks for your reply. I did all steps in the tutorial till I hit to the first mistake/error.

So i run successfully :
sudo apt-get --reinstall install linux-image-2.6.27-11-generic
and

sudo apt-get install build-essential linux-headers-`uname -r`
and the steps from 1-5.

Friends of me told me that wireless should work out-of-the box in the newest ubuntu version, is that true? Never tried that before I start working on it ;)

Cheers, Alex

---

### Post by AlexGriffon on 2009-05-25
Hi,

my wireless was working out of the box! So I didn't get this tutorial running, but wireless is working anyway!

So I don't work at this problem any more, thanks for your help anyway.

Cheers, Alex

---

### Post by dcarde on 2009-05-26
FATAL: Error inserting ipw2200 (ipw2200.ko): Unknown symbol in module, or unknown parameter (see dmesg)
 
 SOLUTION
  lsmod | grep ieee80211
 sudo rmmod (all that displayed with previous command)
sudo modprobe ipw2200
 
 worked for me, maybe for you
 
 
 reference:  [http://ubuntuforums.org/archive/index.php/t-242556.html](http://ubuntuforums.org/archive/index.php/t-242556.html)

---

### Post by joebrueske on 2009-06-14
Sambita,

Thank you for posting this. When I tried patching the drivers that came with Jaunty after I installed it, my wireless broke and this fixed it. Thanks for all your research.

Time to make sure that packet injection works. I'll post any challenges I have.

Thanks again!

EDIT:
As I followed the instructions provided on older tutorials, I ran into an error when initializing rtap0 as an interface. Two things to try if it's not showing up when you use iwconfig. One: reboot! Two: (and this happened in Jaunty) all config files in /etc/modprobe.d **must** have the _.conf_ extension. So, before you reboot make sure that your *Options* file is named *options.conf* and you shouldn't have a problem when you sudo modprobe ipw2200 rtap_iface=1.

Now, as for putting it into monitor mode is now a challenge with NetworkManager. I found [this post]("http://ubuntuforums.org/showpost.php?p=4812890&postcount=2") helpful in taking out NetworkManager for a while. :P
```
killall nm-applet
```
Personally I don't use the rtap0 interface, but some people do, and I thought I'd mention this. However, NetworkManager is a pain in the NECK if you manually switch the default interface to monitor mode. It's just too bad that you can't tell NetworkManager to switch to monitor mode. Now THAT would be nice. That way you don't have to kill the process and restart it after you're done.

Oh, well. At least it all works now!

---

### Post by mikimis on 2009-06-15
For some reason I can't figure out the subsystem just won't compile...I've been trying this for days now and I can't find any other information other then the same few forum posts (this one being the best so far) and I just can't get it. Here's what I get:

```
mikimis@mikimis-laptop:~/wireless/ieee80211-1.2.18$ sudo make install SHELL=/bin/bash
make -C /lib/modules/2.6.28-11-generic/build M=/home/mikimis/wireless/ieee80211-1.2.18 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-11-generic'
  CC [M]  /home/mikimis/wireless/ieee80211-1.2.18/ieee80211_module.o
/home/mikimis/wireless/ieee80211-1.2.18/ieee80211_module.c: In function ‘ieee80211_init’:
/home/mikimis/wireless/ieee80211-1.2.18/ieee80211_module.c:268: error: ‘struct net’ has no member named ‘init_net’
/home/mikimis/wireless/ieee80211-1.2.18/ieee80211_module.c:277: error: ‘struct net’ has no member named ‘init_net’
/home/mikimis/wireless/ieee80211-1.2.18/ieee80211_module.c: In function ‘ieee80211_exit’:
/home/mikimis/wireless/ieee80211-1.2.18/ieee80211_module.c:297: error: ‘struct net’ has no member named ‘init_net’
make[2]: *** [/home/mikimis/wireless/ieee80211-1.2.18/ieee80211_module.o] Error 1
make[1]: *** [_module_/home/mikimis/wireless/ieee80211-1.2.18] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-11-generic'
make: *** [modules] Error 2

```

Looks like the problem has something to do with 'init_net' but I have no idea how to remedy this.  Ideas?  Am I missing something ridiculously simple?  Hopefully...

---

### Post by sambita on 2009-07-08
Well, it must have been months since i last posted here, ive been crazy with work and university, but luckily  it seems most of you have been able to solve your problems thanks to the contribution of other helpful guys around here.

Anyway, mikimis: are you sure you followed steps 2-5 correctly?? my best guess is a misspell when editing ieee80211_module.c but to be sure id recommend doing steps 2 to 5 all over again. I hope this helps even though its been 3 weeks since you posted, or better yet, lets hope youve already been able to solve this.

---

### Post by PookeyMaster on 2009-07-08
dcarde, that worked for getting my wireless up and running, however, i have been unable to crack my wireless network, so i am assuming that something is still not quite right?

---

### Post by mpw on 2009-07-19
Hello,

you said that some smaller erros would be no problem. But my make and so my make install don't compile correctly. 

They both stop with the error 2 (as so often posted in the posts before).

How can I solve that problem. I followed the tutorial STEP BY STEP.

I don't know what I can do..

Has someone more ideas? Could someone fix that error 2?

By the way, I'm using ubuntu 9.04

Thanks,
MPW

---

### Post by skyline2412 on 2009-07-20
I posted a guide about 9.04 which has a very seemed way with 8.10

[Link]("http://www.p1mp4m.es/index.php?showtopic=135")

Well I experienced some issues(curiously I think to remember i had the same issue in both versions 8.10 and 9.04)with the patched, not compiling, just probing it, it seems that once it's been patched, while connecting to WPA networks the system literally stuck up, completely freezes. In WEP Wifi Networks case it simply doesnt connect the manager lunch a new Conf Windows to reenter the password one and one again, but its ok with no encryption wifi networks thats why i suppose that the problem is in the following files:

· ieee80211_crypt_wep.c
· ieee80211_crypt_tkip.c

Any ideas sambita?
I know in your tutorial you patched (.page -> .page_link or something like that ) both files but in the last version they appear already patched.

Anyone else has had this issue?

All the post is refered to:
· Kubuntu Jaunty Jackalope (9.04)
· KDE4
· ieee80211-1.2.18
· ipw2200-1.2.2
· ipw2200-fw-3.1
Patches i aplied:
· ieee80211-2.6.18+linux-2.6.24.diff.txt
· ieee80211_wx.c-2.6.27.patch.txt
· ipw2200-1.2.2-inject.patch
· ipw2200-1.2.2-make.patch
· ipw2200-1.2.2-2.6.24.patch
· ipw2200_rtap_fix.patch
And Add Manually
```
if (rtap_iface)
        memcpy(priv->prom_net_dev->dev_addr, addr->sa_data, ETH_ALEN);
```
to ipw2200.c

Any Ideas, Suggestions and adviced are welcome. (come on! illuminate me)
Thanks for your attention & sorry for my english.

---

### Post by skyline2412 on 2009-07-20
Oops maybe i was mistaken but in

```
patch -p0 < ieee80211-1.2.18-2.6.24.patch
```
you are patching this files:

· patching file ieee80211-1.2.18/ieee80211_crypt_tkip.c
· patching file ieee80211-1.2.18/ieee80211_crypt_wep.c
· patching file ieee80211-1.2.18/ieee80211_module.c

I opened the patch file and saw things like this:

-	sg.page = virt_to_page(pos);
+	sg_assign_page(&sg, virt_to_page(pos)

aparently you're replacing all sg.page expressions, but why are you saying in the followings step of your [Guide Post]("http://ubuntuforums.org/showpost.php?p=6934824&postcount=34") to replace .page for .page_link? I cannot applied the patch and replace after that, i only can do one of those things because "ieee80211-1.2.18-2.6.24.patch" already patch it but in another way

---

### Post by sambita on 2009-07-20
Wow, thats really got me puzzled! im sure i had to do those steps when i wrote the guide, however i just followed it myself to try it out and as you point, there is no need to edit any of the ieee80211... files. ill scratch those parts from the guide.

Howewver other than that i had no problem with the stpes, i did use firmware 3.0 but i seriously doubt using 3.1 makes any difference. 

@mpw: what make gives the error message?

---

### Post by skyline2412 on 2009-07-20
Well finally it appears to work, maybe if i have luck, it will keep working tomorrow hehe.

Sambita I remade all the patch files and reduced them to 2 files to be less annoying.

My patches has one differences in "format" with your guide ones. I dont think it has importance but...

in the patch in ipw2200_module.c you replace:

· ****.page
to
· *assign_page(&dir,...);

I replace

· ****.page
to
· ****.page_link

Well thats all i think.
I will include all commands and link to attached patches files.

See you

---

### Post by sambita on 2009-07-20
Great! Thanks for your contribution.

---

### Post by skyline2412 on 2009-07-21
Hello again!
As I promised..

The guide is [SIZE="4"][HERE]("http://www.p1mp4m.es/index.php?showtopic=137")[/SIZE]
but if you dont want to register there...(:cry::roll:) i post here...

```
cd
tar zxvf ieee80211-1.2.18.tgz 
tar zxvf ipw2200-1.2.2.tgz 
tar zxvf ipw2200-fw-3.1.tgz
 
patch -p0 < ieee80211-1.2.18_p1mp4m.patch 
patch -p0 < ipw2200-1.2.2_p1mp4m.patch
 
cd ieee80211-1.2.18/
chmod +x remove-old
sudo ./remove-old
sudo make SHELL=/bin/bash
sudo make install SHELL=/bin/bash

cd ../ipw2200-1.2.2/
chmod +x remove-old 
sudo ./remove-old 
sudo make SHELL=/bin/bash
sudo make install SHELL=/bin/bash

cd ..
sudo cp ipw2200-fw-3.1/* /lib/firmware/`uname -r`/

kate /etc/modprobe.d/options.conf
"options ipw2200 rtap_iface=1 led=1"

sudo rmmod ipw2200
lsmod | grep ieee80211
sudo rmmod (all that displayed with previous command)

sudo modprobe ipw2200 rtap_iface=1
```

---

### Post by mpw on 2009-07-23
Thanks skyline2412 for this great post!
I could not understand the spanish version - as I'm from Germany, but the short guide worked well for me.

You're the guru of ubuntu networking! I'm searching around internet for hours and days. Since a week I haven't had wifi anymore! Thank you very much.

There are just two litte points:

1. When you copy the firmware the order is not corretly. First you move into the directory of the firmware and than your copy starts with /ipw2200....  - that's double!
2. This config file does not exsist: /etc/modeprobe.d/options.conf
I just used normal modprobe.
But probably I'll have to do this each time starting the computer, isn't it?

Regards,
MPW

/edit: Okay, I just booted again, it still works. So the point concerning the /etc/modprobe.d/options.conf can be replaced by sudo modprobe .....

---

### Post by skyline2412 on 2009-07-23
Well thanks for the advice, I am glad to colaborate, I already change the "double" mistake you discovered.

With the second point I used /etc/modprobe.d/options.conf because I read somwhere thats the older path /etc/modprobe.d/options is gonna be unsupported/change in the future to /etc/modprobe.d/options.conf
Nowadays, both of them are supported so..you can choose at this point.

Happy Wifi-Cracking

---

### Post by mpw on 2009-07-23
Unfortunalty it still doesn't work here aswell:

Passiv listening is no problem (even workes before I started all this patching), but I can't do a successfull fake authentication.

What I did:

```

Disabled the macfilter of my router (just to be sure that this is not the problem)

```Then I started as in the tutorial 
[link]http://www.aircrack-ng.org/doku.php?id=how_to_crack_wep_with_no_clients[/link]

```

sudo ifconfig eth1 down
sudo iwconfig eth1 mode monitor
sudo ifconfig eth1 up

sudo airmon-ng start eth1 11

```this caused:
```

sudo airmon-ng start eth1 11


Found 5 processes that could cause trouble.
If airodump-ng, aireplay-ng or airtun-ng stops working after
a short period of time, you may want to kill (some of) them!
-e 
PID    Name
6810    NetworkManager
6828    wpa_supplicant
6834    avahi-daemon
6835    avahi-daemon
9374    dhclient
Process with PID 9374 (dhclient) is running on interface eth1


Interface    Chipset        Driver

eth1        Intel 2200BG    ipw2200 (monitor mode enabled)

```So I killed the processes with 
```
sudo kill xxxx
```Then I started the faked authentication:

```

sudo aireplay-ng -1 0 -e SecretLAN -a 00:??:??:??:??:?? -h ??:??:??:e0:5e:c9 rtap0
15:19:46  Waiting for beacon frame (BSSID: ??:??:??:??:F0:66) on channel 11

15:19:46  Sending Authentication Request (Open System)

15:19:48  Sending Authentication Request (Open System)

15:19:50  Sending Authentication Request (Open System)

15:19:52  Sending Authentication Request (Open System)

15:19:54  Sending Authentication Request (Open System)

15:19:56  Sending Authentication Request (Open System)

15:19:58  Sending Authentication Request (Open System)

15:20:00  Sending Authentication Request (Open System)

15:20:02  Sending Authentication Request (Open System)

15:20:04  Sending Authentication Request (Open System)

15:20:06  Sending Authentication Request (Open System)

15:20:08  Sending Authentication Request (Open System)

15:20:10  Sending Authentication Request (Open System)

15:20:12  Sending Authentication Request (Open System)

15:20:14  Sending Authentication Request (Open System)

15:20:16  Sending Authentication Request (Open System)
Attack was unsuccessful. Possible reasons:

    * Perhaps MAC address filtering is enabled.
    * Check that the BSSID (-a option) is correct.
    * Try to change the number of packets (-o option).
    * The driver/card doesn't support injection.
    * This attack sometimes fails against some APs.
    * The card is not on the same channel as the AP.
    * You're too far from the AP. Get closer, or lower
      the transmit rate.

```What can I do?

*The Mac filtering is defnitivly disabled (as I did before starting hacking)
* BSSID is correct as I just copied it

Maybe my driver still doesn't support injection?

Thanks for any help.

Regards
MPW

**/edit: Is there a possibility to check if injection is working? Or is this already the proof that is doesn't?**

---

### Post by skyline2412 on 2009-07-23
Same situation, maybe if nobody can help us we could use 1.2.1 ipw2200 version, I remember that version worked for me long time ago..i think i had 7.04 or 7.10 ubuntu versions while i was proving for the first time.

I hope not to be force to this.

---

### Post by mpw on 2009-07-23
> **skyline2412 said:**
> Same situation, maybe if nobody can help us we could use 1.2.1 ipw2200 version, I remember that version worked for me long time ago..i think i had 7.04 or 7.10 ubuntu versions while i was proving for the first time.

I hope not to be force to this.


What would be the problem with the old driver?

---

### Post by skyline2412 on 2009-08-01
Not sure about the probably problems..
maybe we cannot compile the patch ipw2200 with the new ieee..

dont know but i am tired probing this wifi card. xD

Apparently evreything is ok (rtap0 is up) but maybe someone would recommend any test to ensure(?) all work correct?

---

### Post by mpw on 2009-08-02
> **skyline2412 said:**
> Not sure about the probably problems..
maybe we cannot compile the patch ipw2200 with the new ieee..

dont know but i am tired probing this wifi card. xD

Apparently evreything is ok (rtap0 is up) but maybe someone would recommend any test to ensure(?) all work correct?

Hi,

thanks for your comment allthough you're tired. Let me say I'm too.

The point is:
The patch doesn't help anyway. It just creates the new rtap0 which has no further new functions.
The monitor mode worked already with my normal ethX-device.

Injection doesn't work.

So all this patching is just a waste of time.
There is absoulutly no improvement.

What I ask me - as I'm new to the ubuntu/Linux-community:
1. Is this a newer problem, did the card, the driver once work with an older version? Even the injection?
2. Is this an old card? My notebook is about 5 years old, or are there newer versions of this card which have similar problems? So I mean is this a general problem or do just a few people have problems with this card?

Maybe we should just edit the tutorial on aircrack-ng.org and write that this card won't support injection.

I think I'll try an usb wifi-card. Trying the mine is annoying.

If someone has ideas left - please post them.

Bye
MPW

---

### Post by skyline2412 on 2009-08-02
Well depends in whats 'new' for you I´ve got this issue in other distribs, but i can ensure i was able to inject traffic with the wifi card with some distrib (i think it was like 7.04 or 7.10, too far from the present)

the newest intel wifi card is (I think) 3945 series which are imposible to patch to use injection, or thats what i remember to read.

Any help, experiences(Like exactly patch method and exactly commands used to inject traffic..) with ipw2200(2915 abg) are welcome

Bytes

---

### Post by PookeyMaster on 2009-08-03
I was able to successfully inject with Ubuntu 8.04. I recently upgraded to 9.04 and have subsequently lost the ability to inject....

---

### Post by DejitaruJin on 2009-08-06
9.04 is the first version I've tried this in, so it was a challenge, to say the least ;) I was pretty hopeful when, after a good solid day of messing with it, the files finally compiled properly (except for the minor warnings), and I was able to activate the patched driver. However, I too am unable to utilize any kind of injection. From what I understand, this is rather important, such that it's the entire point of the patched drivers. Does injection actually work for anyone on 9.04?

---

### Post by recognitium on 2009-08-06
> **sambita said:**
> 
If you have any problems while doing this just let me know.

I tried to do exactly what your steps said. I have kernel 2.6.28-14.

I got a hunk error while doing the last patch (patch ipw2200-1.2.2/ipw2200.c ipw2200_rtap_fix.patch).

When doing modprobe I got de unknown symbol error, and dmesg showed many disagrees from ipw2200 yo ieee82011 archives versions...

What should i do?

Thanks

---

### Post by PookeyMaster on 2009-08-06
What Ubuntu version are you using recognitium?

It all worked perfectly for me under 8.04 but not 9.04, where i am missing injection.

It is my belief that it would take too long to work out what was causing the error, however i do think it is the kernel. When i had 8.04, i updated the kernel, just before going to 9.04 and it broke the patching/injection.

I had originally intended to compile my own version of the 8.04 kernel with the patch in it and distribute it (unsupported)to this thread to solve the patching issues people were having. However, after doing research, i found that even with a quad core desktop, it would still take well over 24 hours to compile and have a working kernel image, assuming it worked first time. After reading that, i decided it wasnt worth it.

---

### Post by mpw on 2009-08-10
[http://ubuntuforums.org/showthread.php?p=7748336](http://ubuntuforums.org/showthread.php?p=7748336)

Here they think aswell, that the problem is the newer kernel.

Is there a live cd availbe with the patched drivers and a working version of aircrack?

---

### Post by skyline2412 on 2009-08-11
> **recognitium said:**
> I tried to do exactly what your steps said. I have kernel 2.6.28-14.

I got a hunk error while doing the last patch (patch ipw2200-1.2.2/ipw2200.c ipw2200_rtap_fix.patch).

When doing modprobe I got de unknown symbol error, and dmesg showed many disagrees from ipw2200 yo ieee82011 archives versions...

What should i do?

Thanks

The Hunk error indicates that the patch you used is not completely correct, I posted above new patches to use and a mini-tut...
;)

> **mpw said:**
> [http://ubuntuforums.org/showthread.php?p=7748336](http://ubuntuforums.org/showthread.php?p=7748336)

Here they think aswell, that the problem is the newer kernel.

Is there a live cd availbe with the patched drivers and a working version of aircrack?

I suppose you could use wifislax to try it.

In the post you linked appear some interesting information :)
Apart from that I read we can use the command:
sudo aireplay-ng -9 <interface>
to verify our driver injection feature is enable/correct.

---

### Post by PookeyMaster on 2009-08-11
> **mpw said:**
> [http://ubuntuforums.org/showthread.php?p=7748336](http://ubuntuforums.org/showthread.php?p=7748336)

Here they think aswell, that the problem is the newer kernel.

Is there a live cd availbe with the patched drivers and a working version of aircrack?

There is Backtrack 4. I tried it a while ago and the live cd works, but you have to patch the kernel and its alot of work each time you load the cd.

In the short term, you could try using 9.04, but downloading and installing the kernel that originally came with 8.04, as we know that one works. You can then boot 9.04 using the 8.04 kernel and see if the patched drivers work.

Good Luck. :)

---

### Post by mpw on 2009-08-13
Hello,

as I am realativly new to ubuntu and to the whole linux, I have no idea why the newer kernel doesn't work.
Something was changed....

Does anybody know how we could fix the newer kernel?

By the way, I use the no-working-patched-driver version and over the night, my computer has forgotten about my eth1 and my rtap0. I can't use wifi anymore. And I have no idea how to fix it. Does anybody know from where I might get the original drivers used by ubuntu, before i started all this patching?

Regards,
MPW

/edit: After an auto-update it works again. Stupid. Even if injection it had worked, it wouldn't work now. :-(

---

### Post by BinaryMn on 2009-09-10
> **thoraz said:**
> rmmod your ieee drivers and modprobe the new one.. or simply reboot
Thank you for this post.

Followed the instructions at [http://ubuntuforums.org/showpost.php?p=6688433](http://ubuntuforums.org/showpost.php?p=6688433) and when I went to modprobe the new driver, I started getting the same error the OP was getting.

sudo rmmod ieee80211 && sudo rmmod ieee80211_crypt fixed the problem.

---

### Post by PookeyMaster on 2009-09-10
Thats good news

---

### Post by Murdoc_of_puts on 2009-09-15
Ok guys, here's a new one.

Network manager won't access a wep encoded network, even when I Know there's no errors in the password (Worked in windows on a diff comp).  However, it's not the wireless modem itself, as I can connect to free/open networks just fine.   What's going on here?  I used the main guide in this thread, could something in there have affected things negativetly?

---

### Post by ahmedmoh.fathy on 2010-02-20
Checking in /lib/modules/2.6.31-17-generic for ieee80211 components...
make -C /lib/modules/2.6.31-17-generic/build M=/home/fathy/Public/Wireless/ieee80211-1.2.18 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-17-generic'
  CC [M]  /home/fathy/Public/Wireless/ieee80211-1.2.18/ieee80211_module.o
/home/fathy/Public/Wireless/ieee80211-1.2.18/ieee80211_module.c: In function ‘alloc_ieee80211’:
/home/fathy/Public/Wireless/ieee80211-1.2.18/ieee80211_module.c:148: error: ‘struct net_device’ has no member named ‘hard_start_xmit’
/home/fathy/Public/Wireless/ieee80211-1.2.18/ieee80211_module.c:149: error: ‘struct net_device’ has no member named ‘change_mtu’
/home/fathy/Public/Wireless/ieee80211-1.2.18/ieee80211_module.c:153: error: ‘struct net_device’ has no member named ‘get_stats’
make[2]: *** [/home/fathy/Public/Wireless/ieee80211-1.2.18/ieee80211_module.o] Error 1
make[1]: *** [_module_/home/fathy/Public/Wireless/ieee80211-1.2.18] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-17-generic'
make: *** [modules] Error 2

can any body help

---

### Post by aalkounis on 2010-03-23
```
~/wireless/ieee80211-1.2.18 $ sudo make SHELL=/bin/bash
Checking in /lib/modules/2.6.31-14-generic for ieee80211 components...
make -C /lib/modules/2.6.31-14-generic/build M=/home/aalkounis/wireless/ieee80211-1.2.18 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-14-generic'
  CC [M]  /home/aalkounis/wireless/ieee80211-1.2.18/ieee80211_module.o
/home/aalkounis/wireless/ieee80211-1.2.18/ieee80211_module.c: In function ‘alloc_ieee80211’:
/home/aalkounis/wireless/ieee80211-1.2.18/ieee80211_module.c:148: error: ‘struct net_device’ has no member named ‘hard_start_xmit’
/home/aalkounis/wireless/ieee80211-1.2.18/ieee80211_module.c:149: error: ‘struct net_device’ has no member named ‘change_mtu’
/home/aalkounis/wireless/ieee80211-1.2.18/ieee80211_module.c:153: error: ‘struct net_device’ has no member named ‘get_stats’
make[2]: *** [/home/aalkounis/wireless/ieee80211-1.2.18/ieee80211_module.o] Error 1
make[1]: *** [_module_/home/aalkounis/wireless/ieee80211-1.2.18] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-14-generic'
make: *** [modules] Error 2
```

3-days i am trying...CAN ANYONE HELP??????????? i am about to blow my brains :confused: :frown: ](*,)        i have tried the solution by **skyline2412** i wished to all the gods that it would work but....

---

### Post by mpw on 2010-03-24
Upgrade to 9.10 - it work's out of the box. (It should - fore me it does, so I hope for you it's gonna too)

---

### Post by klugen on 2010-05-10
Sorry I'm writing in so old theme but I have the same problem as the last guy wrote. I have Ubuntu 9.10 amd64 and ipw2200 doesn't work out of box. the message is the same as 2 posts ago. Can anyone help?

---

### Post by szubert on 2011-02-10
I've this same problem any help?
Ubuntu 10.10
2.6.35

---

