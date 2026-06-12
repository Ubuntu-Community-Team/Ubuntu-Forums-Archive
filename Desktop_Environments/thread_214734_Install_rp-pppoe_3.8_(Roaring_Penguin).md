---
title: "Install rp-pppoe 3.8 (Roaring Penguin)"
date: 2006-07-13
forum: Desktop Environments
---

### Post by foots2015 on 2006-07-13
I am trying to set up dsl on ubuntu and as i was looking around i stumbled upon rp-pppoe which should take care of my problems. 

Since I am a total noob i need step by step insructions on how to convert this over to .deb since it is a rpm, compile, setup, install, whatever, etc, so i can get the program up and running. Another thing is that all of the instuctions I have found have you download the package while in Ubuntu, but that is a problem for me since the internet isn't working yet in ubuntu. But thankfully I dual booted and i can use the internet on windows. Anyway so what I did was download the package in windows and moved it to my ubuntu desktop... where it now remains. So how do I get this installed and running... without getting the package from online, but instead getting it from my desktop?

Please help a desperate noob](*,)

---

### Post by manzuk on 2006-07-13
Well, a friend of mine had a similar problem few months ago. Although we solved it, I don't remember exactly what we did but I'll try to help you.


_**Just as general information**_

There are two types of ADSL modems, Ethernet (those which use a cable like telephone's) and USB (which obviously connect through usb)

Ethernet ADSL modems are easier to config. Why? Because we JUST have to find a way to tell the ADSLmodem to establish an internet connection with the ISP. And that's where PPPoE gets into the action (but I'll explain later how)

In the other hand, some USB ADSL modems are not propertly detected when plugged in, and that's because the computer doesn't have the necessary drivers. So we have to find them, compile them, and install them. A real pain, but not the end of the world (I might write a HowTo...)


_**Your particular problem**_

If your modem is Ethernet (or if it's USB and you know your computer has detected it fine), then you need these packages:

**pppoe** & **pppoeconf**

Where to get them? There's quiet an useful page for this cases [http://packages.ubuntulinux.org](http://packages.ubuntulinux.org)
There you can search and download packages from the official repositories. So go there (under win) and get those packages! And install them under linux (double click, and Gdebi will do the rest)

Check again that your modem is connected to your PC (and if it's USB, remember the "link" or whatever is called led should be on)

Now run from a terminal
```
pppoeconf
```
and cross your fingers...

Lets say everything went fine. Now you have to edit /etc/ppp/peers/dsl-provider 
Remember you need SuperUser rights, so you should run: ```
gksu gedit /etc/ppp/peers/dsl-provider
```

Where it says ```
#user myusername@myprovider.net
``` replace "***myusername@myprovider.net***" with your actual user, and delete the "***#***" at the begining.

Now edit /etc/ppp/pap-secrets (here is where your password goes)
Again SuperUser rights needed, so ```
gksu gedit /etc/ppp/pap-secrets
```

At the end it says ```
#	*	password
``` replace "***password***" with your real pass, and **I think** you should delete the "#"

**Let's try the connection!!!**

From a terminal run:
```
pppd call dsl-provider
```
and go to [www.google.com](www.google.com)
Or if it doesn't work, you can try with
```
sudo pppd call dsl-provider
```

**_Final comments_**

I can't remember whether pppoeconf did the username and pass stuff for you or not, so I put it just in case.
I might be forgetting something...
Hope this helps you. (tell me later if it worked)

---

### Post by foots2015 on 2006-07-13
Thank's Manzuk for the easy to understand post. I am going to give it a try and see if it works!

---

### Post by foots2015 on 2006-07-13
It works !!! :p 

I did what You said and firefox works now. I also disabled IPV6 and set the MTU to 1452.

Thank you for the help you are a lifesaver!!!

---

### Post by manzuk on 2006-07-13
Happy to hear that!
But please, tell me, did you have to do something I didn't mention? And just to know... which was the right one? "sudo pppd call ..." or "pppd call.."

---

### Post by foots2015 on 2006-07-14
> **manzuk said:**
> Happy to hear that!
But please, tell me, did you have to do something I didn't mention? And just to know... which was the right one? "sudo pppd call ..." or "pppd call.."

I didn't have to do anything you didn't mention besides setting the mtu and disabling IPv6. 

I think that it is sudo pppd call, but I don't remember :???:

---

### Post by foots2015 on 2006-07-14
> **foots2015 said:**
> I didn't have to do anything you didn't mention besides setting the mtu and disabling IPv6. 

I think that it is sudo pppd call, but I don't remember :???:

By the way, setting MTU and disabling IPv6 were specific for my problem, but they could affect other people to depending on their situation.

---

### Post by oss_monkey on 2006-07-19
> **manzuk said:**
> _**Your particular problem**_

If your modem is Ethernet (or if it's USB and you know your computer has detected it fine), then you need these packages:

**pppoe** & **pppoeconf**

Where to get them? There's quiet an useful page for this cases [http://packages.ubuntulinux.org](http://packages.ubuntulinux.org)
There you can search and download packages from the official repositories. So go there (under win) and get those packages! And install them under linux (double click, and Gdebi will do the rest)

Check again that your modem is connected to your PC (and if it's USB, remember the "link" or whatever is called led should be on)

Now run from a terminal
```
pppoeconf
```
and cross your fingers...


Woohoo! Thanks man! All I had to do was start pppoe and let xubuntu do all the configuring. At the end of the config, it gave the instructions to connect:

**to connect:** [FONT="Courier New"]pon dsl-provider[/FONT]
**to disconnect:** [FONT="Courier New"]poff[/FONT]
**for a status update:** [FONT="Courier New"]plog[/FONT]

Again, thanks, man! :)

---

### Post by neymac on 2006-09-15
It did work for me, thanks. Without sudo, just pppd call dsl-provider.

---

### Post by motin on 2007-08-13
This thread doesn't mention rp-pppoe at all!

Here are basic instructions from the Unofficial Ubuntu Starter Guide:

> Q: How to install Broadband ADSL/PPPoE Client (RP-PPPoE)?

   1. Read General Notes
   2. Read How to install Basic Compilers (build-essential)?
   3.

      wget -c [http://frankandjacq.com/ubuntuguide/rp-pppoe-3.5.tar.gz](http://frankandjacq.com/ubuntuguide/rp-pppoe-3.5.tar.gz)
      sudo tar zxvf rp-pppoe-3.5.tar.gz -C /opt/
      sudo chown -R root:root /opt/rp-pppoe-3.5/
      sudo gedit /usr/share/applications/RP-PPPoE.desktop

   4. Insert the following lines into the new file

      [Desktop Entry]
      Name=RP-PPPoE
      Comment=RP-PPPoE
      Exec=gksudo /opt/rp-pppoe-3.5/go-gui
      Icon=
      Terminal=false
      Type=Application
      Categories=Application;Network;

   5. Save the edited file (sample)
   6. Read How to refresh GNOME panel?
   7. Applications -> Internet -> RP-PPPoE


---

