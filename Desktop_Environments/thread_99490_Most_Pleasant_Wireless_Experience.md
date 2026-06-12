---
title: "Most Pleasant Wireless Experience"
date: 2005-12-05
forum: Desktop Environments
---

### Post by joplass on 2005-12-05
I just had my most pleasant wireless experience ever.  I installed Breezy on a friend notebook.  Below is what I did to have his WPC54G Linksys card working in a fly.  Based from past experience on my own notebook and two little utilities in Breezy called ndisgtk and ndiswrapper-utils.  Keep in mind that I was successful with the first try.

Stick your wireless card in your laptop.

Open up Synaptic, type in your user’s password.
Search for “ndis” and the result should have “ndisgtk” and “ndiswrapper-utils”.  Install them both.  Close Synaptic.

Put in the CD-Rom that came with your WPC54G card.  Go to System => Administration the last item in this list will now have “Windows Wireless Driver.  Click it, a new small window opens, click on “Install New Driver” then navigate to your CD-Rom.  Find lsbcmnds.inf, double-click it and you are done.  On the left side of that dialogue box you should see “lsbcmnds” as the install driver.
From the same small dialogue box with “Install New Driver”, click on “Configure Network”.  A new dialogue box will appear with a list of your hardware, the first one is your wireless card activate it and deactivate the Ethernet card (for faster boot).  
Highlight your wireless card again and click property.  Put a check mark on “Enable this connection”, type in your ESSID, type in your WEP key.

Note: you may not need to type in your ESSID, as clicking the drop down arrow should display all wireless connections around you.

I hope this helps someone.

---

### Post by waldorf on 2005-12-05
I was so happy when I saw your post, but it didn't work for me.

I'm able to install the driver no problem.

But when I go to configure the connection it doesn't make the connection. Does it matter that I'm using a WPC54G ver.2?

Any thoughts or suggestions?

Thanks in advance and I appreciate your post.

---

### Post by joplass on 2005-12-05
No, it does not.  That latest installation was actually done with a ver 2.
To start make sure that you turn off your WEP and try you configuration again.

Also try this on your terminal: "sudo modprobe ndiswrapper" and reboot your box the second light of the card will show connection at boot by blinking.
Good luck

---

### Post by waldorf on 2005-12-05
Neither of those things helped either.

I'm not even getting one (the power) light on the card.

Any other thoughts?

Thanks in advance again.

---

### Post by joplass on 2005-12-06
In the terminal type: sudo ndiswrapper -l 
you should see something like:
harware present, software present

Do you see "Windows Wireless Driver" under System => Administration?
If yes, click and see if your driver is listed there.
If it is, remove it using "Remove Driver" and install it again using "Add Driver" 

If it still does not work go to [http://www.ubuntuforums.org/showthread.php?t=25683&highlight=remove+ndiswrapper](http://www.ubuntuforums.org/showthread.php?t=25683&highlight=remove+ndiswrapper)
use this info to remove everything then use steps on my thread to do a clean install of ndiswrapper and the driver.

Good luck

---

### Post by Mr.Hulot on 2005-12-06
To add an extra information for wireless networking, I have a linksys card that is also not recognized by ubuntu. I followed the same procedure as mentioned before for making ubuntu see the card and here is how to setup WPA encryption. Download wpa_supplicant, install it and then create a wpa_supplicant.conf file in /etc that resembles something like :

[I]network={
          ssid="your network's ssid"
          psk="your secret key here"
          key_mgmt=WPA_PSK
          proto=WPA
}[/I]


then in command line enter:

*wpa_supplicant -iwlan0 -c/etc/wpa_supplicant.conf -w -Dndiswrapper*

then 

*ifup wlan0*

and ... here you go!

---

### Post by ahave2005 on 2005-12-06
I had the exact same problems, all I tried didn't make the lights come on.

My card is a Linksys WPC54G ver 2

What I did, was read a lot of infomation about ndiswrapper, where I found that I manually had to tell ndiswrapper what card number and driver to use.

First I removed the driver included with Ubuntu:

sudo rmmod acx_pci

I then told ndiswrapper the windows driver to use:
sudo ndiswrapper -i lstinds.inf

I found the cardnumber with: 
lspci

From here I found the adress 0000:02:00.0 Texas instruments ACX 111......

Then lspci -n: and as the last entry
0000:02:0 0280: 104c:9066

I then told ndiswrapper to use the driver at this card:
sudo ndiswrapper -d 104c:9066 lstinds

(at this point the lights came on)

Then:
sudo depmod -a

And finally:
sudo modprobe ndiswrapper

If you want the drivers to load at bootup:
sudo ndiswrapper -m
sudo ndiswrapper -hotplug


To permanently remove the old drivers for a acx based card, ie WPC54G ver 2.
(Credit [www.houseofcraig.com](www.houseofcraig.com))

To find the default acx driver:
find /lib/modules/`uname -r` -name "*acx*"

They should be there, IF your card is version 2

To remove your old driver and copy them to /root:
find /lib/modules/`uname -r` -name "*acx*" -exec mv {} /root \;

For more information on ver 2, go to:
[http://www.houseofcraig.net/acx100_howto.php]("http://www.houseofcraig.net/acx100_howto.php")
Wiki Ubuntu wifi (ie. scripts for different locations):
[https://wiki.ubuntu.com/WiFiHowto]("https://wiki.ubuntu.com/WiFiHowto")

And now it works, but it took me a long time, since I haven't used Linux for years.


Good luck
Ahave

---

### Post by waldorf on 2005-12-06
You said:

I found the cardnumber with:
lspci

From here I found the adress 0000:02:00.0 Texas instruments ACX 111......

Then lspci -n: and as the last entry
0000:02:0 0280: 104c:9066
***


I'm not following what I should do here

when I lspci I get:

0000:00:00.0 Host bridge: Intel Corp. 82830 830 Chipset Host Bridge (rev 04)
0000:00:02.0 VGA compatible controller: Intel Corp. 82830 CGC [Chipset Graphics Controller] (rev 04)
0000:00:02.1 Display controller: Intel Corp. 82830 CGC [Chipset Graphics Controller]
0000:00:1d.0 USB Controller: Intel Corp. 82801CA/CAM USB (Hub #1) (rev 02)
0000:00:1d.1 USB Controller: Intel Corp. 82801CA/CAM USB (Hub #2) (rev 02)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev 42)
0000:00:1f.0 ISA bridge: Intel Corp. 82801CAM ISA Bridge (LPC) (rev 02)
0000:00:1f.1 IDE interface: Intel Corp. 82801CAM IDE U100 (rev 02)
0000:00:1f.3 SMBus: Intel Corp. 82801CA/CAM SMBus Controller (rev 02)
0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801CA/CAM AC'97 Audio Controller (rev 02)
0000:00:1f.6 Modem: Intel Corp. 82801CA/CAM AC'97 Modem Controller (rev 02)
0000:02:01.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)
0000:02:04.0 CardBus bridge: O2 Micro, Inc. OZ6912 Cardbus Controller


what am I looking for?

Thanks for the help!!

---

### Post by ahave2005 on 2005-12-07
I would say the last line: 0000:02:04.0 CardBus bridge: O2.......

lspci -n

And find the entry starting with: 0000:02:04.0: ........
where mine was 104c:9066

And continue from there.
/ahave

---

### Post by Vilhelmo on 2005-12-07
Thank you so much! This really made the trick for my wireless network. 
I needed to remove the old module and use the ndiswrapper module. Not difficult, but I didn't knew the commands so I couldn't fix it by my self, and no other help I found on the forum helped... 

Please make some kind of guide for us with acx111 based cards with help ahave2005's post.

---

### Post by waldorf on 2005-12-07
I know its not good form to use lots of capitals and exclamation points but

YAAAAHHHHOOOOOO!!!!!!!

It worked! Thank you all so much!!!

---

### Post by pr0fess0r on 2005-12-07
Hi
I'm having a not so pelasant experience :) My XH8196 802.11g PCI wireless card shows up as Intersil ISL3890 [Prism GT/Prism] and as eth1 in the Netwrk Config. I used ndiswrapper and installed the Windows driver no problem, how do I remove the Ubuntu driver (if I need to) or at least make it treat the card as wlan0?
thanks in advance

Lucas

---

### Post by eJamesPC on 2005-12-15
[QUOTE=ahave2005]
I then told ndiswrapper to use the driver at this card:
sudo ndiswrapper -d 104c:9066 lstinds
[/QUOTE]

I tried to use:
sudo ndiswrapper -d 104c:9066 lstinds

and it gave me an error about the 104c:9066.5.conf file allready exists... 

I had the wireless working for a short period of time, but it did not last through a reboot.  Now I can't get the card to enable, sometimes I have to manually enter:  sudo cardctl insert.  

This is really a drag, but thanks for the great post... great source links with great info:KS 

eJamesPC

---

### Post by Dr. Nick on 2005-12-15
[quote=pr0fess0r]Hi
I'm having a not so pelasant experience :) My XH8196 802.11g PCI wireless card shows up as Intersil ISL3890 [Prism GT/Prism] and as eth1 in the Netwrk Config. I used ndiswrapper and installed the Windows driver no problem, how do I remove the Ubuntu driver (if I need to) or at least make it treat the card as wlan0?
thanks in advance

Lucas[/quote]

to remove the ubuntu driver run lsmod, note the name of the driver it is using then search your hard drive for that file and note the location. Move the driver file to another folder so that it doesnt load. I did this the other day with my prism2 card. 

To fix the eth1 and wlan0 problem edit /etc/network/interfaces and look for the line eth1 and just replace it with wlan0, If you cant find it then open a terminal and type **cat /etc/network/interfaces **and post that here.

Is the card working at all right now?

---

### Post by Revert_360 on 2005-12-27
Hey,
Sorry to bring old topic back but....

I haven't got ndisgtk only ndiswrapper....

At the moment I can't find cd for my lynksys but I have found the drivers from their site. But linux won't read it so..

1) I have heard that there is a program to install Windows supported files onto linux OS is this called wine?

2) Will it install the drivers?

3) Where can I find this program?

This isn't for a laptop but my PC. It connects wireless fine on my XP OS but Linux won't detect it. My Linux is on D:/ drive and XP is on my C:/ drive (if this helps).

Thanks in advanced,

Revert

---

### Post by Dr. Nick on 2005-12-27
[quote=Revert_360]Hey,
Sorry to bring old topic back but....

I haven't got ndisgtk only ndiswrapper....

At the moment I can't find cd for my lynksys but I have found the drivers from their site. But linux won't read it so..

1) I have heard that there is a program to install Windows supported files onto linux OS is this called wine?

2) Will it install the drivers?

3) Where can I find this program?

This isn't for a laptop but my PC. It connects wireless fine on my XP OS but Linux won't detect it. My Linux is on D:/ drive and XP is on my C:/ drive (if this helps).

Thanks in advanced,

Revert[/quote]


You need the .inf and .sys files, most likely what you downloaded from linksys was a .exe. wine wont help you out here, try to open the .exe in file-roller in linux to extract it. If that fails reboot into windows and use winzip or similar to try and extract the file from linksys.

ndisgtk most likely is in universe repository, open synaptic and look for the repository prefrences and enable it, if you cant find it just search the forums for "enable universe" or similar and you should see how to do it.

---

### Post by Revert_360 on 2005-12-27
Ok thank you, I'll try that now.
Do I get the .inf and .sys from the ubuntu cd? Also what is this file-roller and where can I find it?

Sorry to be a pain but I really am a newbbiee.

Revert

---

### Post by Muskoka on 2005-12-27
Would like to say hello to everyone, my first post. I to was having alot of trouble getting drivers loaded for this card. What worked for me was to do exactly as the original poster stated but I had to download the newest drivers from the linksys site to get the lsbcmnds.inf to load. Look at the lsbcmnds.inf file (from the d/l drivers) with a text editor and you will see the driver ver. "DriverVer=07/17/2003, 3.30.15.0" instead of "DriverVer=02/12/2003, 3.10.39.7" that came with the original cd. My cd version is 1.1, the card is a version 2. It may have just been a fluke but this was the only way I could get the .inf to load, hope this helps.

---

### Post by Revert_360 on 2005-12-27
So,
Your saying to change it? 

from

```
"DriverVer=07/17/2003, 3.30.15.0" 
```
to
```
"DriverVer=02/12/2003, 3.10.39.7"
```


> Muskoka 
Would like to say hello to everyone, my first post. I to was having alot of trouble getting drivers loaded for this card. What worked for me was to do exactly as the original poster stated but I had to download the newest drivers from the linksys site to get the lsbcmnds.inf to load. Look at the lsbcmnds.inf file (from the d/l drivers) with a text editor and you will see the driver ver. "DriverVer=07/17/2003, 3.30.15.0" instead of "DriverVer=02/12/2003, 3.10.39.7" that came with the original cd. My cd version is 1.1, the card is a version 2. It may have just been a fluke but this was the only way I could get the .inf to load, hope this helps. 



Revert

---

### Post by Dr. Nick on 2005-12-27
[quote=Revert_360]Ok thank you, I'll try that now.
Do I get the .inf and .sys from the ubuntu cd? Also what is this file-roller and where can I find it?

Sorry to be a pain but I really am a newbbiee.

Revert[/quote]

the .inf and .sys come from the drivers you downloaded from linksys, they are inside the .exe file but you need an unzip program to get them out which is file roller avaible through synaptic, but should be installed by default. 

If you can access your windows partition from ubuntu then I suggest you go into windows and download the driver from linksys and use something like winzip to extract the driver and then reboot into Ubuntu and copy the files to your home folder then continue on to set up  ndiswrapper.

You shouldnt have to change anything in the driver files for them to work, just make sure you get the correct drivers for your card version as the different versions of the same model of linksys can be drastically different.

---

### Post by Revert_360 on 2005-12-27
Ok, thank you.
I shall try it and post my results.

Revert

---

### Post by Muskoka on 2005-12-27
Revert 360, sorry about the confusion. Don't alter the .inf file. Go to the linksys site and d/l the latest drivers for the card. You can see the driver version by opening the .inf in a text editor. For me the drivers off the cd didn't work but the ones I got from the linksys site did?? Here's the link to the drivers.

[http://www.linksys.com/servlet/Satellite?childpagename=US%2FLayout&packedargs=c%3DL_Download_C2%26cid%3D1115417109934%26sku%3D1115416827032&pagename=Linksys%2FCommon%2FVisitorWrapper](http://www.linksys.com/servlet/Satellite?childpagename=US%2FLayout&packedargs=c%3DL_Download_C2%26cid%3D1115417109934%26sku%3D1115416827032&pagename=Linksys%2FCommon%2FVisitorWrapper)

---

### Post by Revert_360 on 2005-12-27
[QUOTE=Muskoka]Revert 360, sorry about the confusion. Don't alter the .inf file. Go to the linksys site and d/l the latest drivers for the card. You can see the driver version by opening the .inf in a text editor. For me the drivers off the cd didn't work but the ones I got from the linksys site did?? Here's the link to the drivers.

[http://www.linksys.com/servlet/Satellite?childpagename=US%2FLayout&packedargs=c%3DL_Download_C2%26cid%3D1115417109934%26sku%3D1115416827032&pagename=Linksys%2FCommon%2FVisitorWrapper](http://www.linksys.com/servlet/Satellite?childpagename=US%2FLayout&packedargs=c%3DL_Download_C2%26cid%3D1115417109934%26sku%3D1115416827032&pagename=Linksys%2FCommon%2FVisitorWrapper)[/QUOTE]


Ahh sorry. Thank you :).

So I exicute them using file-roller? and then it should be happy and detect the drivers and hook em up to linsys and I should  connect?


Revert.

---

### Post by Dr. Nick on 2005-12-28
If you can use file roller to get the inf and sys files out of the exe you then plug them 2 files into ndiswrapper using either gtkndis or one of the howto found around here, Then you should be able to set it up and connect

---

### Post by Revert_360 on 2006-02-02
Sorry for brinign old topic back but..
Still can't get it to connect. File roller couldn't use it. I need compatablie linux drivers.

---

