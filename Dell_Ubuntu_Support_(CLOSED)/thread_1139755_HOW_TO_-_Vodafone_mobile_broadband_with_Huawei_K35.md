---
title: "HOW TO - Vodafone mobile broadband with Huawei K3565 modem"
date: 2009-04-27
forum: Dell Ubuntu Support (CLOSED)
---

### Post by shof2k on 2009-04-27
Hello,
This post is to show you how to use Vodafone mobile broadband with the  Huawei K3565 dongle.  This should also help with other dongles, but I can't be sure as I can't test those.

Instructions
1) Plug in the dongle.  Ubuntu should recognise it automatically and start the new connections wizard.  If not, right click network manager and select Edit connection.  In the network connections window, select the 'mobile broadband' tab and click the add button.

2) Follow the wizard to add a vodafone pay as you go connection.

3) Once complete, edit the connection changing the userid/password to web/web.  

4) Change the APN tp "pp.internet"

5) Check the option that says "connect automatically"

6) In the IPv4 tab set the method to automatic ppp0

You may have to disable wireless to get broadband working the first time.

Note: At the moment, you cannot top up pay-as-you-go broadband via linux, although betavine is developing this, so you will need access to a windows PC.

---

### Post by StewartG on 2009-06-08
Thanks for this, now I just need a Windows PC to sort out topping up.

---

### Post by PaulB98 on 2009-07-05
Hello,

I hope you can help me get my connection sorted out. I thought it looked simple from your instructions, but I didnt manage to follow them

I have the Vodafone PAYG modem working fine on a Windows Vista machine - I can see the phone number , balance etc in the vodafone software. I plugged the dongle into my laptop (running Ubuntu 8.04) but the wizard did not start. I couldn't find anything in Administration -> Networks that corresponded to your description - maybe I'm looking in the wrong place?

What I did then do was have a look on Betavine and attempt to follow the instructions there. I downloaded usb-modeswitch_0.9.4-1_i386.deb and installed it with Gdebi package installer. I also downloaded vodafone-mobile-connect_1.99.17-8_all.deb and installed that with the Gdebi package installer, (which first found 22 dependencies and installed them). I ran vodafone-mobile-connect-card-driver-for-linux from the command line

I now have an application which starts up ok and looks very like the Windows version. I created a profile using the suggested default for the UK, and then edited it as per your instructions  to say User/password = 'web'  (was ('vodafone') Preferred = 3g, Authentication mode = default, App host = pp.internet (was 'internet') , DNS = not static. If I press Connect, it says on the status bar that it is connected to vodafone 3g , but the connection speed is zero. I can't access any internet pages, so it isn't really connected. 

Is editing this profile the same as editing a connection in Network Manager? What do you think is wrong - DNS numbers (where can I find the static ones to try instead?) Is 'default' ok for authentication? Or can I bypass this piece of software altogether and just use the modem (I can top up and get the balance etc from the Windows machine)

Any help would be appreciated!

---

### Post by shof2k on 2009-07-07
First make sure you have a compatible dongle.  I can only vouch for the K3565 as that is what I use.

If you've don't get the 'Mobile Broadband Connection Wizard' automatically, you can start it by going to Preferences - Network Connections.  Select the Mobile Broadband tab, then click the Add button to start the wizard.  Work your way through the wizard and finally click close.  

Re open network connections and edit the mobile broadband option with the settings mentioned above.

Bettervine provides alternate connection software.  You can't use it with Ubuntu network manager, so one must be disabled. I've used both, but prefer Ubuntu as it feels 'cleaner' with the multitude of dependencies.

---

### Post by PaulB98 on 2009-07-07
It is a K3565, with a Dell laptop and ubuntu 8.04. I definitely don't get a wizard starting, and I can't see a menu item that says Preferences -> Network Connections. There is System-> Preferences -> Network Proxy, System -> Administration ->Network and System -> Administration ->Network Tools

Only System -> Administration ->Network looks relevant here. It has a Connections tab with 2 entries - one says 'wired' the other 'point to point'. If I press 'unlock' I can select the 'point to point' item  and edit its properties. These look a bit like you say, but there is no tab called 'mobile broadband' Am I on an old version of something?  I can tick 'enable this connection', set connection type to 'GPRS/UMTS' and set Access Point Name = pp.internet, username = web, password = web. There is another tab called 'modem' under Properties. It asks for modem port (picklist eg /devttyS1), dial type (tones or pulse) and volume. I have tried various combinations but nothing seems to work. Am I in the right place or have I missed something completely?

---

### Post by shof2k on 2009-07-10
The issue maybe that 8.04 doesn't fully support mobile broadband. I've only used it with Intrepid, 8.10 and Jaunty 9.04.   I seem to remember that this was a newer feature. I have another laptop with 8.04 installed, so I'll give it a go there.

---

### Post by shof2k on 2009-07-10
Right, Hardy (8.04) doesn't support mobile broadband, so you can either upgrade or keep trying with bettervine.

---

### Post by PaulB98 on 2009-07-15
This turned out to be a bigger project than I had in mind. However - SUCCESS! This posting made via my mobile broadband modem, installed on 9.04 Jaunty. Once I'd done the upgrade, following the instructions for the modem took about 10 seconds, so THANK YOU very much!

Cheers
Paul

---

### Post by ugm6hr on 2009-07-15
Indeed, with Jaunty 9.04, most 3G modems work easily.

My O2 pay-as-you-go 3G mobile broadband (only £20 from carphone warehouse) plugged in, and with a simple edit of the connection, worked:

Number *99#
Username o2bb
Password password
APN m-bb.o2.co.uk

Other settings as default O2 pay-as-you-go (UK).

Unfortunately, the coverage is not great in lots of areas...

The modem is an E160 (according to the label), but Ubuntu detects as E220.

---

### Post by SilverWave on 2009-07-15
Mine was a Huawei E220 (HSDPA)/Huawei E270 (HSUPA) acording to the pop up.

Works great! Picked one up from Tesco's and it worked out of the box in Ubuntu 9.04 no problem :D

The key is to plug the dongle in then reboot that got the wizard working and I chose "Vodafone TopUp and Go" and next and that was it.
Good site here:
[https://wiki.ubuntu.com/NetworkManager/Hardware/3G](https://wiki.ubuntu.com/NetworkManager/Hardware/3G)

Also looks as if there are Linux packages here:
[https://forge.betavine.net/projects/vodafonemobilec/](https://forge.betavine.net/projects/vodafonemobilec/)

I will have a look at this later - for the time being I can just boot in to fista to check usage. I'm using a HP laptop 550.

Speed looks good as well checked out the BBC coverage of the space shuttle - page load was fast the video played fine.

Thanks for the help, it put me on the right track!

:)

---

### Post by kuenn on 2009-11-01
this is my summary on how i get Betavine working on my ubuntu 8.04 ....
hope it's helpful to someone .....

VODAFONE K3565 MOBILE CONNECT INSTALLATION INSTRUCTIONS for UBUNTU 8.04.
--------------------------------------------------------------------------------------------

* get onto a working internet connection (e.g: your ethernet one)

* Google for Betavine Mobile Freeware 
      [https://forge.betavine.net/projects/vodafonemobilec/](https://forge.betavine.net/projects/vodafonemobilec/)
 
* Download from this page these DEB packages:

     - ozerocdoff                          (get the latest version)
     - usb-modeswitch                 (get the latest version)
     - vodafone-mobile-connect    (get the latest version)

 Note: i used this steps on UBUNTU 8.04 64Bits

* Install them in a command line terminal

     sudo dpkg -i ozerocdoff_0.4-2_amd64.deb
     sudo dpkg -i usb-modeswitch_0.9.7_amd64.deb
     sudo dpkg -i vodafone-mobile-connect_2.15.01-1_all.deb

* When doing above steps, you will possibly have unresolved dependencies problems. To solve them execute:

     From the top of UBUNTU "PANEL" 
    -> select "System"     
    -> "Administration" 
    -> "Synaptic Manager" 
    -> "Search" the required packages and install one by one  

* If everything has gone fine you can plug in the modem, and execute the driver with:

     vodafone-mobile-connect-card-driver-for-linux

* if you want to debug problems, use the command that come with the package:

     vodafone-mobile-connect-card-driver-for-linux-debug

* if you get into problem connecting and GUI hang , try setting the folder permission and run the vodafone debug command again. good to reboot machine after changes:  

    cd /etc/ppp/peers
    ls -ld wvdial*
    ls -ld .
    sudo ls -lRt > ./ls-lRt-2009-11-01.log 
    sudo ls -al /etc/ppp/peers/wvdial.distrib >> ls-lRt-2009-11-01.log 

    cd /etc/ppp/peers
    sudo mv wvdial wvdial.orig
    sudo chmod 777 .             (not sure of security impact here, any advice will be great)

    Maybe/Maybe not neccessary 
(tell me if you tested the steps, not sure about security impact here, any advice will be great)
    sudo chmod 755 /etc/ppp/peers/wvdial.distrib 

    vodafone-mobile-connect-card-driver-for-linux-debug

GOOD Luck .....

---

### Post by acesabe on 2010-01-20
Follow instructions linked to here:

[http://ubuntuforums.org/showpost.php?p=8212598&postcount=3](http://ubuntuforums.org/showpost.php?p=8212598&postcount=3)

to get newer network-manager packages - this resolved the lack of plug and play functionallity in the dongle on a 9.10 upgraded box I had to sort.

Also for Vodafone I changed to ppbundle.internet and user:spec1alw0rd >> web:web

---

### Post by Nightstrike2009 on 2010-01-21
I have a Huawei K3565 v2 Vodafone modem and can't get it to work in Karmic 9.10 though it works in 9.04 fine.

> **By shof2k:**Note: At the moment, you cannot top up pay-as-you-go broadband via linux, although betavine is developing this, so you will need access to a windows PC.

This information is misleading you CAN top up via pay-as-you-go on vodafone you access the website sign up for a vodafone account, log in and click "activate top up" on the web link, IT IS possible via official websites (or at least vodafone anyhow) in firefox 3, thats the way I top up on Ubuntu 9.04. Hope this helps other Ubuntu users.

> **By StewartG:**Thanks for this, now I just need a Windows PC to sort out topping up.

You can on Ubuntu. :-)

It's relevant to ubuntu version of the windows helper wizard but not to the offical Vodafone website. :-) 
(Not trying to upstage or offend just trying to help)

---

### Post by Rakaan on 2010-05-11
> **shof2k said:**
> Hello,
This post is to show you how to use Vodafone mobile broadband with the  Huawei K3565 dongle.  This should also help with other dongles, but I can't be sure as I can't test those.

Instructions
1) Plug in the dongle.  Ubuntu should recognise it automatically and start the new connections wizard.  If not, right click network manager and select Edit connection.  In the network connections window, select the 'mobile broadband' tab and click the add button.

2) Follow the wizard to add a vodafone pay as you go connection.

3) Once complete, edit the connection changing the userid/password to web/web.  

4) Change the APN tp "pp.internet"

5) Check the option that says "connect automatically"

6) In the IPv4 tab set the method to automatic ppp0

You may have to disable wireless to get broadband working the first time.

Note: At the moment, you cannot top up pay-as-you-go broadband via linux, although betavine is developing this, so you will need access to a windows PC.

Just wanted to say thank you as it worked for me perfectly on dell mini 910 with ubuntu 10 and voafone :)

---

### Post by RainKap on 2010-07-29
Thanks from me too - in my case Acer Aspire One with UNE 10,04 on Vodafone. The only wrinkle is that I'll have to use my wife's Win XP laptop for top-up...

Ian

---

### Post by corkscrew on 2011-01-24
great how to but this might help other people, mine set up and recognized dongle and network but would,nt connect. I fixed this by changing APN to PPBUNDLE.INTERNET and it connected straight away

---

### Post by ollimorg on 2012-04-12
Just a late addition to this thread. I'm running Lubuntu 11.10 (Oneiric) and using a Huawei 3565 Rev2 Vodafone Mobile Broadband dongle on a Top-Up-And-Go (UK) tariff:

No trouble getting the dongle to work - just plugged it in, activated the Network Connections wizard and it worked ...

...SLIGHT SNAG ...

... wanted to check my balance - its easy using the Vodafone Mobile Connect software under Windows but the driver/connection manager software in Oneiric doesn't have that functionality ...

SOLUTION:

(1) Take the SIM out of the dongle and put it in an unlocked mobile phone;

(2) Open a browser on your PC/laptop/etc using any other network connection you have;

(3) Register for My Vodafone using that connection ... you are asked to input the phone number of the dongle's SIM (which you have just put in a mobile phone) ... then Vodafone responds by texting a confirmation code to the mobile phone, which you can enter into the registration menu;

(4) Complete the registration using the browser.

(5) Put the SIM back in the dongle

Now you have a My Vodafone account and you can log into it using the dongle to provide your network connection ... once logged in you can check your balance/top-up etc via your My Vodafone page.

Doing it that way you don't need the functionality of the Windows Vodafone Mobile Connect software and you can then get along quite happily using only the Oneiric Network Connection manager.

Hope this provides a useful update to a (nearly) dormant thread.


Cheers, all
ollimorg :p

---

