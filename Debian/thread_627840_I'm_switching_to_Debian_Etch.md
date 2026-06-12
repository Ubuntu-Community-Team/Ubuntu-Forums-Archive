---
title: "I'm switching to Debian Etch"
date: 2007-11-30
forum: Debian
---

### Post by staticvoid on 2007-11-30
So... I've downloaded the debian netinstall and I am going to make the switch tonight.

Anything I should know? I would really like to start with a clean slate. What windows manager and such should I install? how bout doing something like

sudo apt-get install gnome-desktop

is that possible??

or how about getting xfce, fluxbox or something else installed?

I have a need for speed :P


sv

---

### Post by yabbadabbadont on 2007-11-30
Unlike the Ubuntu installer, the debian installer will let you choose which desktop related packages you would like to install.  If you have a fast net connection, install whichever window manager/desktop environment you like.  If you have a slow one, you might consider fluxbox or openbox as they have minimal requirements and thus smaller downloads.

---

### Post by init1 on 2007-11-30
> **staticvoid said:**
> So... I've downloaded the debian netinstall and I am going to make the switch tonight.

Anything I should know? I would really like to start with a clean slate. What windows manager and such should I install? how bout doing something like

sudo apt-get install gnome-desktop

is that possible??

or how about getting xfce, fluxbox or something else installed?

I have a need for speed :P


sv
I usually do a minimal install, and then add the packages I want latter. If you want X, do a 
```

apt-get install xorg

```
For fluxbox
```

apt-get install fluxbox

```
For XFCE4
```

apt-get install xfce4

```

---

### Post by staticvoid on 2007-11-30
ok, i'll check out openbox never heard of it..

And how does it do with laptops? I nottice you can select a "laptop" option which configurze stuff...?

sv

---

### Post by staticvoid on 2007-11-30
wow. this shouls be handy:
apt-get install xorg

i would have just gone straight
apt-get install gnome

or something..

---

### Post by staticvoid on 2007-11-30
WOW

I saw some openbox themes.

I love the simplicity!!

any suggestions? I plan to use this windows manager... so wait... how do I get it? just install xorg then openbox then reboot? and I get a graphical interface?

sv

---

### Post by staticvoid on 2007-11-30
conky looks very interesting as a system monitor...
apt-get install conky??

yes, i went and found that out on the website

sv


2. feh show background

3. conky to system monitor, or some other lightweight tray/dock display program.

WHAT IS FEH?

---

### Post by Mithrilhall on 2007-11-30
Debian :KS is the greatest thing since sliced bread. I'm sure you'll love it.

---

### Post by staticvoid on 2007-11-30
thanx for the encouragement :)

I just hope I can get it up and running. I've heard so much about how terrific it is.

I plan on getting it up clean with NOTHin' on it and then put openbox, then put audacious, and then get gtk and stuff then win32 codecs....

a slow process to creat a custom system..  :P

sv

---

### Post by init1 on 2007-11-30
> **staticvoid said:**
> conky looks very interesting as a system monitor...
apt-get install conky??

yes, i went and found that out on the website

sv


2. feh show background

3. conky to system monitor, or some other lightweight tray/dock display program.

WHAT IS FEH?
Feh is an image viewer. It's very simple but it works fine. I think it can be used to set a background.

---

### Post by init1 on 2007-11-30
> **staticvoid said:**
> ok, i'll check out openbox never heard of it..

And how does it do with laptops? I nottice you can select a "laptop" option which configurze stuff...?

sv
It runs fine on my laptop. I didn't choose the laptop package.

---

### Post by staticvoid on 2007-12-01
Ok folks, its installed!!

and boy am I scared. 

It did not detect my wireless network connection. I have an  Intel PRO/ Wireless 2200 802.11b and I want to connect to a WEP encrypted wireless network.

How can I do this via command line?

Oh, and would anyone recomend openbox for stability? And how bout simplicity and ease of use? If I pop in a USB drive does it get automatically mounted? thanx,

sv

---

### Post by Tenken on 2007-12-01
I just started messing around with openbox and it's working out great on my laptop. Like init1 said feh is an image viewer and can be used to set the background in openbox because it doesn't have a background manager of its own. I would also recommend installing obmenu and obconf which are very helpful for configuring the system if you aren't very good with XML like me :). As far as panels go try pypanel , there is a great sample config file in the Arch linux thread.

EDIT: Openbox isn't responsible for mounting drives, file managers like Nautilus are. I personally use Thunar because it is lightweight and it can automount USB drives

---

### Post by staticvoid on 2007-12-01
aha, *thunar*, now I think I am understanding it. This is soooo cool.
talk about light weight :)

any ideas on getting hooked up to the net to a wireless router prtected by WEP?? I'll need that first


sv

---

### Post by Tenken on 2007-12-01
[Here]("http://www.cyberciti.biz/tips/howto-ubuntu-linux-convert-dhcp-network-configuration-to-static-ip-configuration.html") is a good start for setting up the network, I think adding this line will work for WEP, but I'm not sure because I don't run Ubuntu on my laptop.

```
wireless-enc s:Secret_password
```

---

### Post by staticvoid on 2007-12-01
I'm running debian.
I'm gonna try:

nano /etc/network/interfaces

and fill in my info. 

Then I'll try that command.

how do I figure out my DHCP host name?
where are the config files that say my ESSID, my wireless network name?

thnx,

sv

---

### Post by init1 on 2007-12-01
> **staticvoid said:**
> Ok folks, its installed!!

and boy am I scared. 

It did not detect my wireless network connection. I have an  Intel PRO/ Wireless 2200 802.11b and I want to connect to a WEP encrypted wireless network.

How can I do this via command line?

Oh, and would anyone recomend openbox for stability? And how bout simplicity and ease of use? If I pop in a USB drive does it get automatically mounted? thanx,

sv
I never got my wireless configured in Debian. Of course I do have an unsupported Broadcom card, and NDISwrapper is the only way it will work. Mepis is the only distro that properly configures my card. 
Debian will not automount any drives by default. There are programs that do this though.

---

### Post by staticvoid on 2007-12-01
ok,

thats good to know. But I thought hardware support is in the kernal..right? My wireless card worked under ubuntu, show it should work with Debian...correcto?

Can I set THUNAR to automount devices? and will I have a fast system with XFCE and openbox?

exploring,
sv

---

### Post by init1 on 2007-12-01
> **staticvoid said:**
> ok,

thats good to know. But I thought hardware support is in the kernal..right? My wireless card worked under ubuntu, show it should work with Debian...correcto?

Can I set THUNAR to automount devices? and will I have a fast system with XFCE and openbox?

exploring,
sv
Not always. It all depends on your card. 
I guess it depends on what you mean by fast. Was Gnome fast in Ubuntu?

---

### Post by Tenken on 2007-12-01
> how do I figure out my DHCP host name?
where are the config files that say my ESSID, my wireless network name?

I'm not sure what you mean by DHCP host name, but all your network info goes in the /etc/network/interfaces file. He is a sample using a static ip on the wlan0 interface.

```
auto wlan0
iface wlan0 inet static
address 192.168.1.2
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1 # the ip address of your wireless rotuer
wireless-essid  myNetworkName
wireless-key     s:MySecretKey
wireless-channel 11
wireless-mode    managed

```

---

### Post by staticvoid on 2007-12-02
ok, I see, I'll have to remember where that file is. mine only says

```
auto lo
iface lo inet loopback

```

---

### Post by Tenken on 2007-12-02
It looks like it didn't detect your wireless card, try running

```
iwconfig
```

to detect your wireless interfaces or

```
ifconfig
```

to see all of your network interfaces

---

### Post by staticvoid on 2007-12-02
awesome, well it is detecting it now. :)
I'll see if it wrote anything to the network file
sv

---

### Post by ubuntu-freak on 2008-01-06
> **staticvoid said:**
> thanx for the encouragement :)

I just hope I can get it up and running. I've heard so much about how terrific it is.

I plan on getting it up clean with NOTHin' on it and then put openbox, then put audacious, and then get gtk and stuff then win32 codecs....

a slow process to creat a custom system..  :P

sv

 
Why not have both? Don't forget Ubuntu IS Debian. The Ubuntu devs themselves describe Ubuntu as a 'Stable version of Debian Sid for the desktop'.
 
Give pure Debian a try though. You will learn more about Linux. Just remember you can have both if you want.
 
Nathan

---

### Post by staticvoid on 2008-01-07
ok,
well, i'd rather not dual boot, and yes ubuntu is debian... but i'd want a pure debian distro... i guess. I'm not sure what I want :) 

sv

---

### Post by maybeway36 on 2008-01-07
Stable version of sid? I think that might be an oxymoron. :P

---

### Post by ubuntu-freak on 2008-01-07
> **maybeway36 said:**
> Stable version of sid? I think that might be an oxymoron. :P

Haha yeah:)
 
Well that's the aim. It is much less unpredictable than pure sid though. Ubuntu devs do a great job taming it considering there are only 15 of them and they still work for Debian too. 
 
Nathan

---

### Post by davtaine on 2008-01-08
> **maybeway36 said:**
> Stable version of sid? I think that might be an oxymoron. :P

No its not oxymoron. Stable version of sid? It is called sidux :)

---

### Post by staticvoid on 2008-01-08
sidux... looks neat :)

---

### Post by notwen on 2008-01-09
I run Etch w/ Flux/xfce on it for my file server.  It's great. =]  That said, if I enjoyed KDE more, sidux would be superb.

---

### Post by staticvoid on 2008-01-09
awesome, what is your hardware specs?

and by a server, you mean: you have two comps, one with no monitor but connected with a localhost dconnection open?

sv  :)

---

### Post by Mithrilhall on 2008-01-11
You could always try Sidux.

---

### Post by Antman on 2008-01-12
> **Mithrilhall said:**
> You could always try Sidux.

+1 :guitar:

---

### Post by dptxp on 2008-01-13
> **Mithrilhall said:**
> You could always try Sidux.

+2:guitar:

---

